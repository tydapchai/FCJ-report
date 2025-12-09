---
title : "Configure Services"
date: 2025-09-09
weight : 4
chapter : false
pre : " <b> 5.4.4 </b> "

---

#### Configure Environment Variables

After infrastructure deployment, configure environment variables for applications:

##### Frontend Configuration (`apps/web/.env`)

```env
VITE_API_URL=https://api.mapvibe.site
VITE_COGNITO_USER_POOL_ID=<from-terraform-output>
VITE_COGNITO_CLIENT_ID=<from-terraform-output>
VITE_COGNITO_REGION=ap-southeast-1
VITE_CLOUDFRONT_DOMAIN=https://mapvibe.site
```

##### Admin Configuration (`apps/admin/.env`)

```env
VITE_API_URL=https://api.mapvibe.site
VITE_COGNITO_USER_POOL_ID=<from-terraform-output>
VITE_COGNITO_CLIENT_ID=<from-terraform-output>
VITE_COGNITO_REGION=ap-southeast-1
```

#### Run Database Migrations

Run database migrations using the migration Lambda:

```bash
# Get migration Lambda name
MIGRATION_LAMBDA=$(terraform output -raw migration_lambda_name)

# Invoke migration
aws lambda invoke \
  --function-name $MIGRATION_LAMBDA \
  --payload '{}' \
  response.json

# Check response
cat response.json
```

#### Configure Cognito

1. **Set up User Pool attributes** (if needed)
2. **Configure OAuth providers** (Google, etc.)
3. **Set up email/SMS verification** (if needed)

#### Update Lambda Environment Variables

Some Lambda functions may need additional environment variables. Check Terraform outputs and update if necessary.

#### Test Endpoints

Test the deployed endpoints:

1. **API Gateway**: `https://api.mapvibe.site`
2. **Frontend**: `https://mapvibe.site`
3. **Admin**: `https://admin.mapvibe.site`
4. **Cognito Hosted UI**: `https://login.mapvibe.site`

#### Next Steps

Once infrastructure is deployed and configured:
1. Build and deploy frontend applications
2. Deploy Lambda functions
3. Test the complete system
