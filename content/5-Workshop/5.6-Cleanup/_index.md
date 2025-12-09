---
title : "Cleanup"
date: 2025-09-09
weight : 6
chapter : false
pre : " <b> 5.6. </b> "

---

#### Overview

Congratulations on completing the MapVibe workshop!

In this workshop, you learned:
- How to set up a monorepo with TurboRepo and Bun
- How to deploy serverless infrastructure using Terraform
- How to build and deploy React applications
- How to configure AWS services (Lambda, RDS, API Gateway, CloudFront, Cognito)
- How to integrate AI services (Bedrock, Rekognition, Textract)

#### Cleanup Resources

To avoid ongoing costs, clean up all AWS resources when you're done.

##### 1. Destroy Infrastructure with Terraform

The easiest way to clean up is using Terraform:

```bash
cd infrastructure/terraform

# Review what will be destroyed
terraform plan -destroy

# Destroy all resources
terraform destroy
```

This will remove:
- All Lambda functions
- API Gateway
- RDS database instance
- CloudFront distributions
- S3 buckets (if empty)
- Cognito User Pool
- VPC and networking resources
- Route53 hosted zones
- WAF web ACLs
- Secrets Manager secrets

**Note**: Some resources may take time to delete (e.g., RDS final snapshot, CloudFront propagation).

##### 2. Manual Cleanup (if needed)

If Terraform destroy doesn't remove everything, manually clean up:

**S3 Buckets:**
```bash
# List buckets
aws s3 ls | grep mapvibe

# Empty and delete each bucket
aws s3 rm s3://bucket-name --recursive
aws s3 rb s3://bucket-name
```

**CloudWatch Logs:**
```bash
# Delete log groups
aws logs describe-log-groups --query "logGroups[?contains(logGroupName, 'mapvibe')]" --output table
aws logs delete-log-group --log-group-name <log-group-name>
```

**Route53 Hosted Zones:**
```bash
# List hosted zones
aws route53 list-hosted-zones --query "HostedZones[?contains(Name, 'mapvibe')]"

# Delete hosted zone (requires deleting all records first)
aws route53 delete-hosted-zone --id <hosted-zone-id>
```

##### 3. Verify Cleanup

Verify all resources are deleted:

```bash
# Check Lambda functions
aws lambda list-functions --query "Functions[?contains(FunctionName, 'mapvibe')]"

# Check S3 buckets
aws s3 ls | grep mapvibe

# Check RDS instances
aws rds describe-db-instances --query "DBInstances[?contains(DBInstanceIdentifier, 'mapvibe')]"
```

#### Important Notes

- **Data Loss**: Destroying infrastructure will delete all data (database, S3 objects, etc.)
- **Backup**: Export any important data before cleanup
- **Costs**: Some resources (like RDS snapshots) may incur minimal storage costs
- **DNS**: If using a custom domain, update DNS records after cleanup

#### Next Steps

After cleanup:
1. Review what you learned
2. Experiment with modifications
3. Consider production deployment patterns
4. Explore additional AWS services

Thank you for completing the MapVibe workshop!
