---
title : "Prerequisites"
date: 2025-09-09
weight : 2
chapter : false
pre : " <b> 5.2. </b> "

---

#### Required Software

Before starting this workshop, ensure you have the following installed:

1. **Bun** (>= 1.3.2)
   - Download from: https://bun.sh
   - Verify installation: `bun --version`

2. **Node.js** (>= 24.11.1)
   - Required for some tooling
   - Download from: https://nodejs.org

3. **Terraform** (>= 1.0)
   - Required for infrastructure deployment
   - Download from: https://www.terraform.io/downloads
   - Verify installation: `terraform --version`

4. **AWS CLI** (>= 2.0)
   - Required for AWS operations
   - Download from: https://aws.amazon.com/cli/
   - Configure with: `aws configure`

5. **Git**
   - For cloning the repository
   - Download from: https://git-scm.com/

#### AWS Account Requirements

1. **AWS Account** with appropriate permissions
   - You need an AWS account with permissions to create and manage:
     - VPC, Subnets, Security Groups
     - RDS (PostgreSQL)
     - Lambda functions
     - API Gateway
     - CloudFront distributions
     - S3 buckets
     - Cognito User Pools
     - Route53 hosted zones
     - ACM certificates
     - WAF web ACLs
     - Secrets Manager
     - IAM roles and policies

2. **AWS Region**
   - This workshop uses **ap-southeast-1** (Singapore) by default
   - WAF requires **us-east-1** (N. Virginia) for CloudFront

3. **AWS Credentials**
   - Configure AWS CLI with your credentials:
     ```bash
     aws configure
     ```
   - Or set environment variables:
     ```bash
     export AWS_ACCESS_KEY_ID=your_access_key
     export AWS_SECRET_ACCESS_KEY=your_secret_key
     export AWS_DEFAULT_REGION=ap-southeast-1
     ```

#### Environment Variables

You will need to create `.env` files for the project:

1. **Root `.env` file** - For infrastructure variables
2. **`apps/web/.env`** - For frontend configuration
3. **`apps/admin/.env`** - For admin dashboard configuration

Contact the project maintainer for the required environment variables.

#### Optional: Google OAuth (for Cognito)

If you want to enable Google OAuth login:
- Create a Google OAuth 2.0 client ID and secret
- Add them to your Terraform variables

#### Verify Prerequisites

Run the following commands to verify your setup:

```bash
# Check Bun
bun --version

# Check Node.js
node --version

# Check Terraform
terraform --version

# Check AWS CLI
aws --version

# Check AWS credentials
aws sts get-caller-identity
```

If all commands succeed, you're ready to proceed!
