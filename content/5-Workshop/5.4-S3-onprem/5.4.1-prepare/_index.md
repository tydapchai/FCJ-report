---
title : "Terraform Setup"
date: 2025-09-09
weight : 1
chapter : false
pre : " <b> 5.4.1 </b> "

---

#### Prerequisites

Before deploying infrastructure, ensure you have:

1. **Terraform installed** (>= 1.0)
2. **AWS CLI configured** with appropriate credentials
3. **AWS account** with necessary permissions

#### Configure Terraform Variables

Navigate to the infrastructure directory:

```bash
cd infrastructure/terraform
```

Create a `terraform.tfvars` file (or use environment variables):

```hcl
aws_region     = "ap-southeast-1"
environment    = "mvp"
project_name   = "mapvibe"
db_name        = "mapvibe"

# Optional: Google OAuth
google_client_id     = ""
google_client_secret = ""
```

#### Initialize Terraform

Initialize Terraform to download providers:

```bash
terraform init
```

This will:
- Download the AWS provider
- Set up the backend (if configured)
- Initialize modules

#### Review Terraform Plan

Before applying, review what will be created:

```bash
terraform plan
```

This shows:
- Resources to be created
- Resources to be modified
- Resources to be destroyed

#### Important Notes

- **Cost**: This infrastructure will create billable AWS resources
- **Region**: Default is `ap-southeast-1` (Singapore)
- **WAF**: Requires `us-east-1` for CloudFront (handled automatically)
- **Database**: RDS instance will be created (db.t3.micro for MVP)
- **Domain**: You'll need a domain name for Route53 (e.g., mapvibe.site)

#### Next Steps

Once Terraform is initialized and configured, proceed to deploy the infrastructure.
