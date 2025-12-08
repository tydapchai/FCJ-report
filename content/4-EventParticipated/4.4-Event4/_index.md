---
title: "Event 4"
date: "2025-11-17"
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---
# Summary Report: "DevOps on AWS – AWS Cloud Mastery Series #2"

## Event Overview

| | |
|---|---|
| **Event Name** | DevOps on AWS – AWS Cloud Mastery Series #2 |
| **Date** | November 17, 2025 |
| **Role** | Attendee |
| **Format** | On-site technical session |
| **Duration** | Full-day session |
| **Location** | 26th floor, Bitexco Financial Tower, District 1, Ho Chi Minh City, Vietnam |

This session was the second installment of the AWS Cloud Mastery Series, focusing specifically on DevOps principles and practices using AWS services. The event covered how to implement modern DevOps workflows, automate software delivery, and operate applications at scale on AWS.

---

## Session Agenda

### Introduction to DevOps Principles

**What is DevOps?:** Understanding the cultural and technical movement

**Core Principles:**
- Collaboration between development and operations
- Automation of manual processes
- Continuous integration and continuous delivery (CI/CD)
- Infrastructure as Code (IaC)
- Monitoring and observability
- Feedback loops and continuous improvement

---

### Infrastructure as Code (IaC)

#### AWS CloudFormation
- **Overview:** AWS's native IaC service
- **Template Structure:** Understanding JSON/YAML CloudFormation templates
- **Resources and Properties:** Defining AWS resources declaratively
- **Parameters and Mappings:** Making templates reusable and flexible
- **Outputs:** Exposing important values from stacks
- **Stack Management:** Creating, updating, and deleting stacks
- **Best Practices:**
  - Template organization and modularity
  - Version control for templates
  - Stack policies and change sets
  - Drift detection

#### Terraform on AWS
- **Terraform Overview:** Open-source IaC tool
- **Terraform vs CloudFormation:** Understanding the differences
- **HCL Syntax:** Writing Terraform configuration files
- **State Management:** Understanding Terraform state
- **Providers:** Using the AWS provider
- **Modules:** Creating reusable infrastructure components
- **Workspaces:** Managing multiple environments
- **Best Practices:**
  - Remote state backends
  - Variable management
  - Module design patterns

#### Infrastructure Patterns
- **Multi-Environment Management:** Dev, staging, production
- **Parameterization:** Making infrastructure configurable
- **Reusability:** DRY principles in infrastructure code
- **Testing Infrastructure:** Validating infrastructure changes

---

### CI/CD Pipelines

#### AWS CodePipeline
- **Pipeline Concepts:** Understanding pipeline stages and actions
- **Source Stage:** Integrating with source control (GitHub, CodeCommit, S3)
- **Build Stage:** Compiling and packaging applications
- **Deploy Stage:** Deploying to various environments
- **Approval Actions:** Manual gates for production deployments
- **Pipeline Triggers:** Automating pipeline execution
- **Pipeline Visualization:** Monitoring pipeline execution

#### AWS CodeBuild
- **Build Projects:** Defining build configurations
- **Buildspec Files:** YAML-based build instructions
- **Build Environments:** Choosing compute types and images
- **Artifacts:** Managing build outputs
- **Caching:** Speeding up builds with caching strategies
- **Environment Variables:** Securely managing secrets
- **Build Logs:** Debugging failed builds

#### AWS CodeDeploy
- **Deployment Concepts:** Understanding deployment strategies
- **In-Place Deployments:** Updating existing instances
- **Blue/Green Deployments:** Zero-downtime deployments
- **Rolling Deployments:** Gradual instance updates
- **Deployment Groups:** Organizing deployment targets
- **AppSpec Files:** Defining deployment instructions
- **Deployment Monitoring:** Tracking deployment progress

#### Integration with Other Services
- **AWS CodeCommit:** Managed Git repositories
- **GitHub Integration:** Using GitHub as source
- **S3 Artifacts:** Storing build artifacts
- **Lambda Deployments:** Deploying serverless functions
- **ECS Deployments:** Container deployment strategies
- **EC2 Deployments:** Traditional application deployments

---

### Container Deployment Strategies

#### Amazon ECS Deployment
- **ECS Service Updates:** Rolling updates for ECS services
- **Task Definitions:** Defining container configurations
- **Service Auto-scaling:** Automatically adjusting capacity
- **Blue/Green with ECS:** Zero-downtime container deployments
- **Health Checks:** Ensuring service reliability
- **Load Balancing:** Distributing traffic across tasks

#### Amazon EKS Deployment
- **Kubernetes on AWS:** Managed Kubernetes service
- **Deployment Strategies:** Rolling updates, canary, blue/green
- **Helm Charts:** Package management for Kubernetes
- **GitOps:** Using Git as source of truth for Kubernetes
- **CI/CD for Kubernetes:** Integrating with CodePipeline

#### Container Best Practices
- **Image Management:** Versioning and tagging strategies
- **Security Scanning:** Scanning container images for vulnerabilities
- **Multi-stage Builds:** Optimizing image sizes
- **Registry Management:** Using Amazon ECR effectively

---

### Serverless Deployment

#### AWS Lambda Deployment
- **Function Deployment:** Deploying Lambda functions
- **Versioning and Aliases:** Managing function versions
- **Canary Deployments:** Gradual rollout of function updates
- **Lambda Layers:** Sharing code and dependencies
- **Environment Variables:** Managing configuration
- **Dead Letter Queues:** Handling failures

#### Serverless Application Model (SAM)
- **SAM Overview:** Framework for serverless applications
- **SAM Templates:** Defining serverless resources
- **SAM CLI:** Local development and deployment
- **SAM Pipeline:** CI/CD for SAM applications

#### API Gateway Deployment
- **API Versioning:** Managing API versions
- **Stage Management:** Dev, staging, production stages
- **Canary Releases:** Testing new API versions
- **Throttling and Caching:** Performance optimization

---

### Monitoring and Observability

#### Amazon CloudWatch
- **Metrics:** Collecting and visualizing metrics
- **Logs:** Centralized log management
- **Alarms:** Setting up automated alerts
- **Dashboards:** Creating custom monitoring dashboards
- **Insights:** Analyzing log data
- **Composite Alarms:** Complex alerting logic

#### AWS X-Ray
- **Distributed Tracing:** Understanding request flows
- **Service Maps:** Visualizing application architecture
- **Performance Analysis:** Identifying bottlenecks
- **Error Tracking:** Finding and fixing issues

#### Additional Observability Tools
- **CloudWatch Synthetics:** Monitoring application availability
- **CloudWatch Contributor Insights:** Analyzing high-cardinality data
- **CloudWatch Logs Insights:** Querying log data
- **Third-party Integrations:** Datadog, New Relic, etc.

---

### Advanced DevOps Topics

#### Infrastructure Testing
- **Unit Testing:** Testing infrastructure code
- **Integration Testing:** Validating infrastructure changes
- **Compliance Testing:** Ensuring security and compliance
- **Tools:** Terratest, Pulumi Testing, etc.

#### Security in DevOps
- **Secrets Management:** AWS Secrets Manager
- **IAM Roles:** Least privilege access
- **Security Scanning:** Automated security checks
- **Compliance:** Meeting regulatory requirements

#### Cost Optimization
- **Resource Tagging:** Tracking costs
- **Right-sizing:** Choosing appropriate instance types
- **Reserved Instances:** Cost savings strategies
- **Spot Instances:** Using Spot for cost optimization

#### Multi-Account Strategies
- **AWS Organizations:** Managing multiple accounts
- **Account Structure:** Organizing accounts by environment/team
- **Cross-Account Deployments:** Deploying across accounts
- **Centralized Logging:** Aggregating logs from multiple accounts

---

## Key Technical Learnings

### DevOps Culture and Practices
- Understanding that DevOps is both a cultural shift and a set of technical practices
- The importance of automation in reducing manual errors and increasing speed
- How feedback loops enable continuous improvement

### Infrastructure as Code
- IaC enables version control, repeatability, and consistency
- Both CloudFormation and Terraform have their strengths
- Modular, reusable infrastructure code is essential for scale

### CI/CD Implementation
- CI/CD pipelines automate the software delivery process
- Different deployment strategies suit different use cases
- Testing and validation should be integrated into pipelines

### Monitoring and Observability
- Comprehensive monitoring is essential for operating applications
- Logs, metrics, and traces provide different but complementary insights
- Proactive monitoring helps prevent issues before they impact users

---

## Personal Takeaways

### Technical Skills
- Learned how DevOps practices and AWS tooling fit together to automate the software delivery lifecycle
- Understand how to design CI/CD pipelines for different types of applications
- Gained practical knowledge of Infrastructure as Code principles and tools

### Best Practices
- The importance of starting with simple automation and gradually increasing complexity
- How to balance speed and safety in deployment processes
- The value of comprehensive monitoring and observability

### Practical Application
- Can now design CI/CD pipelines for containerized and serverless applications
- Understand how to use Infrastructure as Code to manage AWS resources
- Know how to implement monitoring and alerting for applications

### Career Development
- This event reinforced what I learned in other workshops about building and operating applications on AWS
- See how DevOps skills are essential for modern software development
- Motivated to continue learning about advanced DevOps practices and tools

---

## Event Experience

This session provided a comprehensive overview of DevOps on AWS, covering everything from basic concepts to advanced practices. The combination of theory and practical examples made complex topics accessible.

The focus on real-world scenarios and best practices was particularly valuable. Understanding not just how to use tools, but when and why to use them, helped me develop a more strategic view of DevOps.

The event structure allowed for good coverage of both foundational concepts and advanced topics, making it valuable for attendees at different experience levels.

#### Event Photos

![CloudWatch Overview - Monitoring Dashboard](/images/event-4/cloudwatch-overview.png)

![CloudWatch - Metrics and Logs](/images/event-4/cloudwatch.png)

![Docker vs VM - Container Comparison](/images/event-4/docker%20vs%20VM.png)

![Amazon ECS - Container Orchestration](/images/event-4/ECS%20.png)

![AWS X-Ray - Distributed Tracing](/images/event-4/x-ray.png)
