---
title : "Infrastructure Setup"
date: 2025-09-09
weight : 4
chapter : false
pre : " <b> 5.4. </b> "

---

#### Overview

In this section, you will set up the AWS infrastructure for MapVibe using Terraform. The infrastructure includes:

- **VPC and Networking** - Virtual Private Cloud with subnets and security groups
- **RDS PostgreSQL** - Database for storing application data
- **Lambda Functions** - Serverless compute for API and processing
- **API Gateway** - REST API endpoint management
- **CloudFront & S3** - CDN and static asset storage
- **Cognito** - User authentication and authorization
- **Route53 & ACM** - DNS and SSL certificate management
- **WAF** - Web Application Firewall for security
- **Secrets Manager** - Secure credential storage

#### Terraform Configuration

The infrastructure is defined in `infrastructure/terraform/` using Terraform modules for each AWS service.

#### Content

- [Terraform Setup](5.4.1-prepare/)
- [Deploy Infrastructure](5.4.2-create-interface-enpoint/)
- [Verify Deployment](5.4.3-test-endpoint/)
- [Configure Services](5.4.4-dns-simulation/)
