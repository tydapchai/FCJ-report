---
title : "Yêu cầu tiên quyết"
date: 2025-09-09
weight : 2
chapter : false
pre : " <b> 5.2. </b> "

---

#### Phần mềm cần thiết

Trước khi bắt đầu workshop này, hãy đảm bảo bạn đã cài đặt các phần mềm sau:

1. **Bun** (>= 1.3.2)
   - Tải từ: https://bun.sh
   - Kiểm tra cài đặt: `bun --version`

2. **Node.js** (>= 24.11.1)
   - Cần thiết cho một số công cụ
   - Tải từ: https://nodejs.org

3. **Terraform** (>= 1.0)
   - Cần thiết để triển khai hạ tầng
   - Tải từ: https://www.terraform.io/downloads
   - Kiểm tra cài đặt: `terraform --version`

4. **AWS CLI** (>= 2.0)
   - Cần thiết cho các thao tác AWS
   - Tải từ: https://aws.amazon.com/cli/
   - Cấu hình với: `aws configure`

5. **Git**
   - Để clone repository
   - Tải từ: https://git-scm.com/

#### Yêu cầu tài khoản AWS

1. **Tài khoản AWS** với quyền phù hợp
   - Bạn cần tài khoản AWS với quyền tạo và quản lý:
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
     - IAM roles và policies

2. **AWS Region**
   - Workshop này sử dụng **ap-southeast-1** (Singapore) làm mặc định
   - WAF yêu cầu **us-east-1** (N. Virginia) cho CloudFront

3. **AWS Credentials**
   - Cấu hình AWS CLI với credentials của bạn:
     ```bash
     aws configure
     ```
   - Hoặc thiết lập biến môi trường:
     ```bash
     export AWS_ACCESS_KEY_ID=your_access_key
     export AWS_SECRET_ACCESS_KEY=your_secret_key
     export AWS_DEFAULT_REGION=ap-southeast-1
     ```

#### Biến môi trường

Bạn sẽ cần tạo các file `.env` cho dự án:

1. **File `.env` gốc** - Cho các biến hạ tầng
2. **`apps/web/.env`** - Cho cấu hình frontend
3. **`apps/admin/.env`** - Cho cấu hình admin dashboard

Liên hệ người duy trì dự án để lấy các biến môi trường cần thiết.

#### Tùy chọn: Google OAuth (cho Cognito)

Nếu bạn muốn bật đăng nhập Google OAuth:
- Tạo Google OAuth 2.0 client ID và secret
- Thêm chúng vào các biến Terraform của bạn

#### Xác minh Yêu cầu tiên quyết

Chạy các lệnh sau để xác minh thiết lập của bạn:

```bash
# Kiểm tra Bun
bun --version

# Kiểm tra Node.js
node --version

# Kiểm tra Terraform
terraform --version

# Kiểm tra AWS CLI
aws --version

# Kiểm tra AWS credentials
aws sts get-caller-identity
```

Nếu tất cả các lệnh thành công, bạn đã sẵn sàng để tiếp tục!
