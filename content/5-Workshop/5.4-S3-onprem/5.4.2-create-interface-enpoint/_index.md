---
title : "Deploy Infrastructure"
date: 2025-09-09
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "

---

#### Deploy with Terraform

Deploy the infrastructure:

```bash
cd infrastructure/terraform
terraform apply
```

This will create all AWS resources. The process may take 15-30 minutes.

#### What Gets Created

The Terraform configuration creates:

1. **VPC Module**
   - VPC with public subnets
   - Internet Gateway
   - Route tables
   - Security groups

2. **RDS Module**
   - PostgreSQL database instance (db.t3.micro)
   - Database credentials stored in Secrets Manager
   - Public accessibility (for MVP)

3. **Secrets Manager**
   - Database credentials secret
   - Auto-generated secure password

4. **Cognito Module**
   - User Pool for authentication
   - User Pool Client
   - Custom domain (login.mapvibe.site)
   - Optional Google OAuth integration

5. **Lambda Functions**
   - API Lambda (main REST API)
   - Embeddings Lambda (Bedrock integration)
   - RAG Lambda (AI search)
   - OCR Menu Lambda (Textract)
   - Rekognition Lambda (content moderation)
   - Review Aggregate Lambda
   - S3 Trigger Lambda
   - Migration Lambda

6. **API Gateway**
   - REST API with custom domain
   - Lambda integrations
   - Cognito authorizers
   - CORS configuration

7. **S3 & CloudFront**
   - S3 bucket for static assets
   - S3 bucket for photos
   - CloudFront distribution
   - WAF integration
   - Custom domain (mapvibe.site)

8. **Route53 & ACM**
   - Hosted zone for domain
   - SSL certificates
   - DNS records

9. **WAF**
   - Web ACL for CloudFront
   - Security rules

#### Monitor Deployment

Watch the Terraform output for progress. You'll see:
- Resources being created
- Any errors or warnings
- Output values (URLs, ARNs, etc.)

#### Save Outputs

After deployment, save the outputs:

```bash
terraform output > outputs.txt
```

Important outputs include:
- API Gateway URL
- CloudFront URLs
- Cognito User Pool ID
- RDS endpoint
- Database secret ARN
