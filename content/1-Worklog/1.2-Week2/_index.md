---
title: "Week 2 Worklog"
date: "2025-09-11"
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---




### Week 2 Objectives

- Get acquainted with First Cloud Journey members and internship rules.
- Learn core AWS concepts: Management Console, CLI, programmatic access, Infrastructure as Code (IaC), and basic storage and database services.

### Tasks carried out this week

| Day | Task | Start Date | Completion Date | Reference |
| --- | ---- | ---------- | --------------- | --------- |
| 2 | Overview of AWS service categories (Compute, Storage, Networking, Database) | 15/09/2025 | 15/09/2025 | Datacamp |
| 3 | Overview of AWS service categories (Compute, Storage, Networking, Database) | 15/09/2025 | 16/09/2025 | cloudjourney docs |
| 4 | Create AWS Free Tier account; install & configure AWS CLI; run basic CLI commands | 17/09/2025 | 17/09/2025 | https://cloudjourney.awsstudygroup.com/ |
| 5 | Study EC2 fundamentals (instance types, AMIs, EBS, SSH, Elastic IP) | 19/09/2025 | 19/09/2025 | AWS documentation |
| 6 | Hands-on practice: launch EC2, SSH into instance, attach EBS volume | 20/09/2025 | 21/09/2025 | Hands-on lab,Datacamp |


### Key learnings and reference notes

#### 1. AWS Management Console

How it works:
- Web-based graphical interface — sign in at https://console.aws.amazon.com and operate resources manually.
- Create, modify, and delete resources using point-and-click forms.

Summary:

| Criterion | AWS Management Console |
| --------- | ---------------------- |
| Interface | Web GUI |
| Automation level | Low — manual step-by-step operations |
| Deployment speed | Slower for large numbers of resources |
| Ease of use | Easy for beginners |
| Advantages | Intuitive; good for monitoring resource state |
| Limitations | Hard to reproduce configurations, error-prone, no built-in version control |

Example: To launch an EC2 instance — Console → EC2 → Launch Instance → fill settings → run.

---

#### 2. Programmatic Access (CLI / SDK / API)

How it works:
- Access AWS via API, AWS CLI, or SDKs (Boto3 for Python, AWS SDK for JavaScript/Node.js, etc.).
- Allows automation through commands or code.

Summary:

| Criterion | Programmatic Access |
| --------- | ------------------- |
| Interface | CLI or code (SDK/API) |
| Automation level | Higher than Console |
| Integration | Easy to use in scripts, CI/CD pipelines |
| Advantages | Fast, scalable, supports batch operations and DevOps integration |
| Limitations | Requires technical skills and correct IAM configuration |

Example CLI command:

```
aws ec2 run-instances --image-id ami-123456 --instance-type t3.micro
```

Or use Boto3 (Python) to create instances programmatically.

---

#### 3. Infrastructure as Code (IaC)

How it works:
- Define the entire infrastructure as code instead of manual steps.
- Tools: AWS CloudFormation, Terraform, AWS CDK.
- IaC enables consistent, repeatable deployments and is managed via version control.

Summary:

| Criterion | Infrastructure as Code (IaC) |
| --------- | ---------------------------- |
| Interface | Configuration files (YAML, JSON, HCL, TypeScript) |
| Automation level | Very high |
| Advantages | Automated, version-controlled, easy to replicate environments |
| Limitations | Requires understanding of templates and configuration management |
| Best suited for | DevOps, production, CI/CD, large-scale systems |

CloudFormation example:

```
Resources:
  MyEC2:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t3.micro
      ImageId: ami-123456
```

Terraform example:

```
resource "aws_instance" "example" {
  ami           = "ami-123456"
  instance_type = "t3.micro"
}
```

---

#### 4. Quick comparison summary

| Criterion | AWS Management Console | Programmatic Access | Infrastructure as Code |
| --------- | ---------------------- | ------------------- | ---------------------- |
| Interaction | Web GUI (manual) | CLI / API | Write infrastructure code |
| Automation | Low | Medium | Very high |
| Repeatability | No | Limited | Easy |
| Version control | No | Partially | Yes |
| Beginner friendliness | Easy | Medium | Harder |
| Suitable for | Learning, demos, quick tasks | Scripts, small CI/CD tasks | Large systems, mature DevOps |

Conclusion:
- Management Console: good for learning, demos, and quick manual tasks.
- Programmatic Access: use for automation scripts and pipeline integration.
- IaC: use for professional, scalable environments with version control and reproducibility.

---

### Infrastructure fundamentals (summary)

1. Global Footprint
- AWS operates 30+ regions worldwide and 550+ points of presence.
- Each region is a major geographic area that hosts multiple AWS services.

2. Data Centers
- Located within regions; house servers, storage, and networking equipment.
- Designed for high availability, redundant power and cooling, and strong security.

3. Availability Zones (AZs)
- Each region has multiple AZs — independent facilities with separate power, cooling, and networking.
- AZs enable fault tolerance and high availability; if one AZ fails, others maintain operations.

4. Edge Locations
- 400+ Edge Locations globally; used by Amazon CloudFront to cache data near end users.
- Reduce latency and accelerate content delivery.

5. Example: Black Friday
- During peak traffic (e.g., Black Friday): Data centers handle compute and storage load; AZs provide redundancy; Edge Locations deliver cached content quickly.
- Result: reliable, low-latency performance at global scale.

---

### Database overview

1. Role of Databases
- Databases store, manage, and retrieve structured or unstructured data efficiently.

2. Types of Databases

| Type | Description | AWS Service | Best Use Cases |
| ---- | ----------- | ----------- | -------------- |
| Relational (SQL) | Structured data with defined relationships | Amazon RDS (MySQL, PostgreSQL, Oracle, SQL Server) | ERP, CRM, finance, e-commerce |
| NoSQL | Flexible schema, high-performance key-value store | Amazon DynamoDB | Gaming, IoT, session management, real-time apps |

3. Amazon RDS
- Fully managed relational DB service; handles provisioning, patching, backups, and scaling.

4. Amazon DynamoDB
- Serverless NoSQL with single-digit millisecond latency; scales automatically with no infrastructure management.

5. Other DB offerings

| Service | Type | Use Case |
| ------- | ---- | -------- |
| Amazon ElastiCache | In-memory cache | Improve performance & reduce DB load |
| Amazon Neptune | Graph DB | Social networks, recommendation engines |
| Amazon DocumentDB | Document store (MongoDB-compatible) | Content management, product catalogs |
| Amazon Timestream | Time-series DB | IoT telemetry, operational analytics |
| Amazon QLDB | Ledger DB | Immutable, cryptographically verifiable logs |

6. AWS Database Migration Service (DMS)
- Enables migrations with minimal downtime; supports homogeneous and heterogeneous migrations; useful for on-premises → AWS migrations.

---

### Storage overview

1. Role of Storage
- Provides durable, scalable, and secure data storage for files, backups, and archives.

2. Types of Storage

| Type | Description | AWS Service | Typical Use |
| ---- | ----------- | ----------- | ----------- |
| Direct / Active Storage | Frequently accessed data; fast retrieval | Amazon S3 | Websites, mobile apps, analytics, backups |
| Archival Storage | Infrequently accessed data, long-term retention | Amazon Glacier | Archives, compliance, disaster recovery |

3. Amazon S3
- Object storage designed for scalability, availability, and durability (11 9s).
- Use cases: website hosting, backup & restore, content delivery, big data.
- Features: versioning, encryption, lifecycle policies, cross-region replication.

4. S3 Storage Classes

| Class | Description | Use Case |
| ----- | ----------- | -------- |
| S3 Standard | High performance for frequent access | Websites, content delivery |
| S3 Intelligent-Tiering | Automatically moves data between tiers based on usage | Unpredictable access patterns |
| S3 Standard-IA | Lower cost for infrequent but rapid access | Backups, DR |
| S3 Glacier | Low-cost archival, retrieval minutes–hours | Long-term archives |
| S3 Glacier Deep Archive | Lowest-cost storage, retrieval hours–days | Regulatory/compliance retention |

5. Amazon Glacier
- Archival storage for data that must be retained securely and cheaply; retrieval options: Expedited, Standard, Bulk.

6. Other Storage Services

| Service | Type | Use Case |
| ------- | ---- | -------- |
| Amazon EBS | Block storage | Persistent storage for EC2 instances |
| Amazon EFS | File storage | Shared access across multiple instances |
| Amazon FSx | Managed file systems | Enterprise or HPC workloads |
| AWS Storage Gateway | Hybrid cloud storage | Connect on-premises to AWS for backups/caching |

---

### Week 2 Achievements

- Gained practical familiarity with the AWS Management Console, AWS CLI, and basic programmatic workflows.
- Created and configured an AWS account and AWS CLI (access key, secret key, default region).
- Launched an EC2 instance, connected via SSH, and attached an EBS volume during hands-on practice.
- Compiled notes comparing Console, CLI, and IaC, and summarized infrastructure concepts, database offerings, and storage options.

### Next steps

1. Practice IaC: author a simple CloudFormation template or Terraform configuration to recreate the EC2 + EBS setup used in practice.
2. Explore additional DB services (RDS engines, DynamoDB patterns) and caching with ElastiCache.
3. Automate a small deployment pipeline using AWS CLI scripts and verify repeatable deployments.

---

_End of Week 2 worklog._

