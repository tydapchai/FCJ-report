---
title : "Verify Deployment"
date: 2025-09-09
weight : 3
chapter : false
pre : " <b> 5.4.3 </b> "

---

#### Verify Resources

After deployment, verify that all resources were created successfully:

##### 1. Check VPC

```bash
aws ec2 describe-vpcs --filters "Name=tag:Project,Values=mapvibe"
```

##### 2. Check RDS

```bash
aws rds describe-db-instances --query "DBInstances[?contains(DBInstanceIdentifier, 'mapvibe')]"
```

##### 3. Check Lambda Functions

```bash
aws lambda list-functions --query "Functions[?contains(FunctionName, 'mapvibe')]"
```

##### 4. Check API Gateway

```bash
aws apigateway get-rest-apis --query "items[?contains(name, 'mapvibe')]"
```

##### 5. Check CloudFront

```bash
aws cloudfront list-distributions --query "DistributionList.Items[?contains(Aliases.Items[0], 'mapvibe')]"
```

##### 6. Check Cognito

```bash
aws cognito-idp list-user-pools --max-results 10 --query "UserPools[?contains(Name, 'mapvibe')]"
```

##### 7. Check S3 Buckets

```bash
aws s3 ls | grep mapvibe
```

#### Test API Endpoint

Test the API Gateway endpoint:

```bash
# Get API Gateway URL from Terraform output
API_URL=$(terraform output -raw api_gateway_url)

# Test health endpoint (if available)
curl $API_URL/health
```

#### Check Database Connection

Retrieve database credentials and test connection:

```bash
# Get secret ARN
SECRET_ARN=$(terraform output -raw db_secret_arn)

# Get credentials
aws secretsmanager get-secret-value --secret-id $SECRET_ARN

# Test connection (requires psql)
# Use credentials from secret to connect
```

#### Verify CloudFront Distribution

Check CloudFront distribution status:

```bash
DIST_ID=$(terraform output -raw cloudfront_distribution_id)
aws cloudfront get-distribution --id $DIST_ID
```

Wait for status to be "Deployed" before accessing the site.
