---
title : "Thiết lập Terraform"
date: 2025-09-09
weight : 1
chapter : false
pre : " <b> 5.4.1 </b> "

---

#### Yêu cầu tiên quyết

Trước khi triển khai hạ tầng, hãy đảm bảo bạn có:

1. **Terraform đã cài đặt** (>= 1.0)
2. **AWS CLI đã cấu hình** với credentials phù hợp
3. **Tài khoản AWS** với các quyền cần thiết

#### Cấu hình Biến Terraform

Điều hướng đến thư mục infrastructure:

```bash
cd infrastructure/terraform
```

Tạo file `terraform.tfvars` (hoặc sử dụng biến môi trường):

```hcl
aws_region     = "ap-southeast-1"
environment    = "mvp"
project_name   = "mapvibe"
db_name        = "mapvibe"

# Tùy chọn: Google OAuth
google_client_id     = ""
google_client_secret = ""
```

#### Khởi tạo Terraform

Khởi tạo Terraform để tải providers:

```bash
terraform init
```

Lệnh này sẽ:
- Tải AWS provider
- Thiết lập backend (nếu được cấu hình)
- Khởi tạo modules

#### Xem lại Terraform Plan

Trước khi apply, xem lại những gì sẽ được tạo:

```bash
terraform plan
```

Lệnh này hiển thị:
- Tài nguyên sẽ được tạo
- Tài nguyên sẽ được sửa đổi
- Tài nguyên sẽ bị xóa

#### Lưu ý quan trọng

- **Chi phí**: Hạ tầng này sẽ tạo các tài nguyên AWS có tính phí
- **Region**: Mặc định là `ap-southeast-1` (Singapore)
- **WAF**: Yêu cầu `us-east-1` cho CloudFront (được xử lý tự động)
- **Database**: Instance RDS sẽ được tạo (db.t3.micro cho MVP)
- **Domain**: Bạn sẽ cần tên miền cho Route53 (ví dụ: mapvibe.site)

#### Bước tiếp theo

Sau khi Terraform được khởi tạo và cấu hình, tiến hành triển khai hạ tầng.
