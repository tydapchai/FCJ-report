---
title: "Blog 1"
date: "2025-09-11"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# Unlocking Commercial AI Models in AWS GovCloud (US): Secure Cross-Partition Access with Amazon Bedrock

In this blog post, we present three solutions that enable workloads in AWS GovCloud (US) to securely connect to the commercial partition of Amazon Web Services (AWS) for inference with Amazon Bedrock. Each approach has its own strengths and trade-offs, and by the end of this post, you'll be able to determine which option best suits your organization.

Generative AI is evolving rapidly, with new foundation models (FMs) and capabilities being released regularly. These capabilities are introduced first in the AWS commercial partition. For organizations operating in sensitive, highly regulated environments, the challenge is keeping pace with this innovation while rapidly prototyping, gathering customer feedback, and maturing new capabilities into mission-ready solutions.

---

## How Cross-Partition Access Works

Workloads in AWS GovCloud (US) call Amazon Bedrock by sending requests to the service API in the commercial partition. Instead of calling an Amazon Bedrock endpoint within AWS GovCloud (US), applications route requests through a chosen network connection to the commercial partition where Amazon Bedrock resides.

Since AWS GovCloud (US) and commercial partitions don't have natural internal connectivity, they are logically and physically isolated. For communication, organizations must use connections like public endpoints, AWS Site-to-Site VPN, or AWS Direct Connect. These connections carry requests between partitions.

When traffic flows between AWS GovCloud (US) and commercial, it typically traverses the AWS backbone. As the Amazon VPC FAQ explains: "Network packets that originate from AWS and are destined for AWS resources always travel across the global AWS network, except for traffic to or from the China Regions." For more details, see Introduction to Network Transformation on AWS.

---

## Security and Authentication

Amazon Bedrock uses service APIs over HTTPS, encrypting requests with TLS from AWS GovCloud (US) to the commercial partition. This ensures encryption for cross-partition communication regardless of connection method. For workloads requiring FIPS 140-validated cryptographic modules, Bedrock provides FIPS endpoints as documented in AWS General Reference for Amazon Bedrock.

Application logic always resides entirely within AWS GovCloud (US):
- Amazon API Gateway exposes endpoints to workloads
- AWS Lambda processes requests
- AWS Secrets Manager stores Amazon Bedrock API keys
- Amazon CloudWatch in AWS GovCloud (US) logs for performance monitoring
- AWS CloudTrail in the commercial partition provides API call audit logs

---

---

## Architecture Guidance

The main change since the last presentation of the overall architecture is the decomposition of a single service into a set of smaller services to improve maintainability and flexibility. Integrating a large volume of diverse healthcare data often requires specialized connectors for each format; by keeping them encapsulated separately as microservices, we can add, remove, and modify each connector without affecting the others. The microservices are loosely coupled via publish/subscribe messaging centered in what I call the “pub/sub hub.”

This solution represents what I would consider another reasonable sprint iteration from my last post. The scope is still limited to the ingestion and basic parsing of **HL7v2 messages** formatted in **Encoding Rules 7 (ER7)** through a REST interface.

**The solution architecture is now as follows:**

> *Figure 1. Overall architecture; colored boxes represent distinct services.*

---

While the term *microservices* has some inherent ambiguity, certain traits are common:  
- Small, autonomous, loosely coupled  
- Reusable, communicating through well-defined interfaces  
- Specialized to do one thing well  
- Often implemented in an **event-driven architecture**

When determining where to draw boundaries between microservices, consider:  
- **Intrinsic**: technology used, performance, reliability, scalability  
- **Extrinsic**: dependent functionality, rate of change, reusability  
- **Human**: team ownership, managing *cognitive load*

---

## Three Connection Options

There are three ways to connect from AWS GovCloud (US) to the commercial partition. The choice depends on security requirements, performance needs, and operational considerations.

### Option 1: Public Endpoints

The simplest approach uses the AWS backbone to connect GovCloud (US) to the commercial partition. GovCloud (US) applications send HTTPS to API Gateway. TLS encrypts transmission; IAM and Secrets Manager control authentication, keeping sensitive information separate.

Requirements in commercial partition:
- Amazon Bedrock API key for authentication
- Enabled model access for each FM to be used
- Inference profiles for required models (like Claude 4)

This solution is suitable for proof-of-concept or experimental projects needing rapid deployment, potentially complete within weeks with minimal infrastructure. However, traffic routes through the internet, so it doesn't provide the highest security level.

### Option 2: AWS Site-to-Site VPN with Private Endpoints

For organizations wanting higher security, avoiding public internet, AWS Site-to-Site VPN creates an encrypted "tunnel" between GovCloud (US) and commercial VPCs. All traffic flows through the VPN tunnel, enhancing security. VPC endpoints keep traffic within AWS.

Requirements in commercial partition:
- Everything from Option 1
- Configured VPN gateway connecting to GovCloud (US)
- Created VPC endpoints for AWS service access without internet routing

This approach is better for production environments, offering better compliance and security, though more complex and time-consuming to deploy.

### Option 3: AWS Direct Connect

This option uses AWS Direct Connect to create private connections between GovCloud (US) and commercial partition, providing highest throughput, lowest latency, suitable for mission-critical AI workloads or high volumes. VPC endpoints keep traffic within AWS, avoiding internet.

Requirements in commercial partition:
- Everything from Option 1
- Direct Connect gateway, multiple connections from each partition to customer network for routing
- VPC endpoints for AWS access without internet routing

This solution provides strongest security and consistent SLA-backed performance. However, requires complex network infrastructure deployment, taking weeks/months depending on partners and locations.

---

## Choosing the Right Connection

Selection depends on compliance requirements, data sensitivity, and existing network infrastructure. For testing, public endpoints with TLS encryption might suffice; production workloads typically use VPN or Direct Connect from the start.

Important considerations:
1. **Data Flow**: Data accompanying prompts will transfer to Amazon Bedrock in the commercial partition
2. **Compliance**: Organizations must verify processes align with security regulations
3. **Cost**: Data transfer fees apply for cross-partition traffic in both accounts
4. **Security Requirements**: Choose connection method matching security policies and data type from the beginning

Each option offers different advantages:
- **Direct Connect**: Absolute path control, entirely private data transmission
- **Site-to-Site VPN**: Good middle ground with encrypted transmission
- **Public Endpoints**: Fastest to deploy but less controlled routing

---

## Authors

**Tyler Replogle**
Principal Solutions Architect and Technical Database Leader at AWS for global public sector. Helps AWS Partners and customers operate mission-critical solutions on AWS.

**Doug Hairfield**
Senior Solutions Architect helping organizations harness AI power for practical problems. Experienced in designing workloads in high-compliance environments.

**Michael Pitcher**
Senior Solutions Architecture Manager at AWS. Works closely with partners to support public sector customer end goals. Experienced in security and compliance.

**Vin Minichino**
Senior Solutions Architect at AWS, supporting federal healthcare service partners. Father of two, RV travel enthusiast, and maker/creator.

---

## The Pub/Sub Hub

Using a **hub-and-spoke** architecture (or message broker) works well with a small number of tightly related microservices.  
- Each microservice depends only on the *hub*  
- Inter-microservice connections are limited to the contents of the published message  
- Reduces the number of synchronous calls since pub/sub is a one-way asynchronous *push*

Drawback: **coordination and monitoring** are needed to avoid microservices processing the wrong message.

---

## Core Microservice

Provides foundational data and communication layer, including:  
- **Amazon S3** bucket for data  
- **Amazon DynamoDB** for data catalog  
- **AWS Lambda** to write messages into the data lake and catalog  
- **Amazon SNS** topic as the *hub*  
- **Amazon S3** bucket for artifacts such as Lambda code

> Only allow indirect write access to the data lake through a Lambda function → ensures consistency.

---

## Front Door Microservice

- Provides an API Gateway for external REST interaction  
- Authentication & authorization based on **OIDC** via **Amazon Cognito**  
- Self-managed *deduplication* mechanism using DynamoDB instead of SNS FIFO because:  
  1. SNS deduplication TTL is only 5 minutes  
  2. SNS FIFO requires SQS FIFO  
  3. Ability to proactively notify the sender that the message is a duplicate  

---

## Staging ER7 Microservice

- Lambda “trigger” subscribed to the pub/sub hub, filtering messages by attribute  
- Step Functions Express Workflow to convert ER7 → JSON  
- Two Lambdas:  
  1. Fix ER7 formatting (newline, carriage return)  
  2. Parsing logic  
- Result or error is pushed back into the pub/sub hub  

---

## New Features in the Solution

### 1. AWS CloudFormation Cross-Stack References
Example *outputs* in the core microservice:
```yaml
Outputs:
  Bucket:
    Value: !Ref Bucket
    Export:
      Name: !Sub ${AWS::StackName}-Bucket
  ArtifactBucket:
    Value: !Ref ArtifactBucket
    Export:
      Name: !Sub ${AWS::StackName}-ArtifactBucket
  Topic:
    Value: !Ref Topic
    Export:
      Name: !Sub ${AWS::StackName}-Topic
  Catalog:
    Value: !Ref Catalog
    Export:
      Name: !Sub ${AWS::StackName}-Catalog
  CatalogArn:
    Value: !GetAtt Catalog.Arn
    Export:
      Name: !Sub ${AWS::StackName}-CatalogArn
