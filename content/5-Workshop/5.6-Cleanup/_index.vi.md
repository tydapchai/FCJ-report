---
title : "Dọn dẹp"
date: 2025-09-09
weight : 6
chapter : false
pre : " <b> 5.6. </b> "

---

#### Tổng quan

Chúc mừng bạn đã hoàn thành workshop MapVibe!

Trong workshop này, bạn đã học:
- Cách thiết lập monorepo với TurboRepo và Bun
- Cách triển khai hạ tầng serverless sử dụng Terraform
- Cách xây dựng và triển khai ứng dụng React
- Cách cấu hình các dịch vụ AWS (Lambda, RDS, API Gateway, CloudFront, Cognito)
- Cách tích hợp các dịch vụ AI (Bedrock, Rekognition, Textract)

#### Dọn dẹp Tài nguyên

Để tránh chi phí liên tục, hãy dọn dẹp tất cả tài nguyên AWS khi bạn hoàn thành.

##### 1. Xóa Hạ tầng với Terraform

Cách dễ nhất để dọn dẹp là sử dụng Terraform:

```bash
cd infrastructure/terraform

# Xem lại những gì sẽ bị xóa
terraform plan -destroy

# Xóa tất cả tài nguyên
terraform destroy
```

Lệnh này sẽ xóa:
- Tất cả Lambda functions
- API Gateway
- RDS database instance
- CloudFront distributions
- S3 buckets (nếu trống)
- Cognito User Pool
- VPC và tài nguyên networking
- Route53 hosted zones
- WAF web ACLs
- Secrets Manager secrets

**Lưu ý**: Một số tài nguyên có thể mất thời gian để xóa (ví dụ: RDS final snapshot, CloudFront propagation).

##### 2. Dọn dẹp Thủ công (nếu cần)

Nếu Terraform destroy không xóa hết mọi thứ, hãy dọn dẹp thủ công:

**S3 Buckets:**
```bash
# Liệt kê buckets
aws s3 ls | grep mapvibe

# Làm trống và xóa từng bucket
aws s3 rm s3://bucket-name --recursive
aws s3 rb s3://bucket-name
```

**CloudWatch Logs:**
```bash
# Xóa log groups
aws logs describe-log-groups --query "logGroups[?contains(logGroupName, 'mapvibe')]" --output table
aws logs delete-log-group --log-group-name <log-group-name>
```

**Route53 Hosted Zones:**
```bash
# Liệt kê hosted zones
aws route53 list-hosted-zones --query "HostedZones[?contains(Name, 'mapvibe')]"

# Xóa hosted zone (yêu cầu xóa tất cả records trước)
aws route53 delete-hosted-zone --id <hosted-zone-id>
```

##### 3. Xác minh Dọn dẹp

Xác minh tất cả tài nguyên đã được xóa:

```bash
# Kiểm tra Lambda functions
aws lambda list-functions --query "Functions[?contains(FunctionName, 'mapvibe')]"

# Kiểm tra S3 buckets
aws s3 ls | grep mapvibe

# Kiểm tra RDS instances
aws rds describe-db-instances --query "DBInstances[?contains(DBInstanceIdentifier, 'mapvibe')]"
```

#### Lưu ý quan trọng

- **Mất dữ liệu**: Xóa hạ tầng sẽ xóa tất cả dữ liệu (database, S3 objects, v.v.)
- **Backup**: Xuất bất kỳ dữ liệu quan trọng nào trước khi dọn dẹp
- **Chi phí**: Một số tài nguyên (như RDS snapshots) có thể phát sinh chi phí lưu trữ tối thiểu
- **DNS**: Nếu sử dụng custom domain, cập nhật DNS records sau khi dọn dẹp

#### Bước tiếp theo

Sau khi dọn dẹp:
1. Xem lại những gì bạn đã học
2. Thử nghiệm với các sửa đổi
3. Xem xét các mẫu triển khai production
4. Khám phá các dịch vụ AWS bổ sung

Cảm ơn bạn đã hoàn thành workshop MapVibe!
