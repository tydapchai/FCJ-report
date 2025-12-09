---
title : "Cấu hình Dịch vụ"
date: 2025-09-09
weight : 4
chapter : false
pre : " <b> 5.4.4 </b> "

---

#### Cấu hình Biến môi trường

Sau khi triển khai hạ tầng, cấu hình biến môi trường cho ứng dụng:

##### Cấu hình Frontend (`apps/web/.env`)

```env
VITE_API_URL=https://api.mapvibe.site
VITE_COGNITO_USER_POOL_ID=<từ-terraform-output>
VITE_COGNITO_CLIENT_ID=<từ-terraform-output>
VITE_COGNITO_REGION=ap-southeast-1
VITE_CLOUDFRONT_DOMAIN=https://mapvibe.site
```

##### Cấu hình Admin (`apps/admin/.env`)

```env
VITE_API_URL=https://api.mapvibe.site
VITE_COGNITO_USER_POOL_ID=<từ-terraform-output>
VITE_COGNITO_CLIENT_ID=<từ-terraform-output>
VITE_COGNITO_REGION=ap-southeast-1
```

#### Chạy Database Migrations

Chạy database migrations sử dụng Lambda migration:

```bash
# Lấy tên Lambda migration
MIGRATION_LAMBDA=$(terraform output -raw migration_lambda_name)

# Gọi migration
aws lambda invoke \
  --function-name $MIGRATION_LAMBDA \
  --payload '{}' \
  response.json

# Kiểm tra response
cat response.json
```

#### Cấu hình Cognito

1. **Thiết lập User Pool attributes** (nếu cần)
2. **Cấu hình OAuth providers** (Google, v.v.)
3. **Thiết lập xác minh email/SMS** (nếu cần)

#### Cập nhật Biến môi trường Lambda

Một số hàm Lambda có thể cần thêm biến môi trường. Kiểm tra Terraform outputs và cập nhật nếu cần.

#### Kiểm tra Endpoints

Kiểm tra các endpoints đã triển khai:

1. **API Gateway**: `https://api.mapvibe.site`
2. **Frontend**: `https://mapvibe.site`
3. **Admin**: `https://admin.mapvibe.site`
4. **Cognito Hosted UI**: `https://login.mapvibe.site`

#### Bước tiếp theo

Sau khi hạ tầng được triển khai và cấu hình:
1. Build và triển khai ứng dụng frontend
2. Triển khai các hàm Lambda
3. Kiểm tra hệ thống hoàn chỉnh
