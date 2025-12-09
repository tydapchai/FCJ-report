---
title : "Xác minh Triển khai"
date: 2025-09-09
weight : 3
chapter : false
pre : " <b> 5.4.3 </b> "

---

#### Xác minh Tài nguyên

Sau khi triển khai, xác minh rằng tất cả tài nguyên đã được tạo thành công:

##### 1. Kiểm tra VPC

```bash
aws ec2 describe-vpcs --filters "Name=tag:Project,Values=mapvibe"
```

##### 2. Kiểm tra RDS

```bash
aws rds describe-db-instances --query "DBInstances[?contains(DBInstanceIdentifier, 'mapvibe')]"
```

##### 3. Kiểm tra Lambda Functions

```bash
aws lambda list-functions --query "Functions[?contains(FunctionName, 'mapvibe')]"
```

##### 4. Kiểm tra API Gateway

```bash
aws apigateway get-rest-apis --query "items[?contains(name, 'mapvibe')]"
```

##### 5. Kiểm tra CloudFront

```bash
aws cloudfront list-distributions --query "DistributionList.Items[?contains(Aliases.Items[0], 'mapvibe')]"
```

##### 6. Kiểm tra Cognito

```bash
aws cognito-idp list-user-pools --max-results 10 --query "UserPools[?contains(Name, 'mapvibe')]"
```

##### 7. Kiểm tra S3 Buckets

```bash
aws s3 ls | grep mapvibe
```

#### Kiểm tra API Endpoint

Kiểm tra API Gateway endpoint:

```bash
# Lấy API Gateway URL từ Terraform output
API_URL=$(terraform output -raw api_gateway_url)

# Kiểm tra health endpoint (nếu có)
curl $API_URL/health
```

#### Kiểm tra Kết nối Database

Lấy credentials database và kiểm tra kết nối:

```bash
# Lấy secret ARN
SECRET_ARN=$(terraform output -raw db_secret_arn)

# Lấy credentials
aws secretsmanager get-secret-value --secret-id $SECRET_ARN

# Kiểm tra kết nối (yêu cầu psql)
# Sử dụng credentials từ secret để kết nối
```

#### Xác minh CloudFront Distribution

Kiểm tra trạng thái CloudFront distribution:

```bash
DIST_ID=$(terraform output -raw cloudfront_distribution_id)
aws cloudfront get-distribution --id $DIST_ID
```

Đợi trạng thái là "Deployed" trước khi truy cập trang web.
