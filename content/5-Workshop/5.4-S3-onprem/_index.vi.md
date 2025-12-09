---
title : "Thiết lập Hạ tầng"
date: 2025-09-09
weight : 4
chapter : false
pre : " <b> 5.4. </b> "

---

#### Tổng quan

Trong phần này, bạn sẽ thiết lập hạ tầng AWS cho MapVibe sử dụng Terraform. Hạ tầng bao gồm:

- **VPC và Networking** - Virtual Private Cloud với subnets và security groups
- **RDS PostgreSQL** - Cơ sở dữ liệu để lưu trữ dữ liệu ứng dụng
- **Lambda Functions** - Serverless compute cho API và xử lý
- **API Gateway** - Quản lý REST API endpoints
- **CloudFront & S3** - CDN và lưu trữ tài sản tĩnh
- **Cognito** - Xác thực và ủy quyền người dùng
- **Route53 & ACM** - Quản lý DNS và chứng chỉ SSL
- **WAF** - Tường lửa ứng dụng web cho bảo mật
- **Secrets Manager** - Lưu trữ credentials an toàn

#### Cấu hình Terraform

Hạ tầng được định nghĩa trong `infrastructure/terraform/` sử dụng các module Terraform cho mỗi dịch vụ AWS.

#### Nội dung

- [Thiết lập Terraform](5.4.1-prepare/)
- [Triển khai Hạ tầng](5.4.2-create-interface-enpoint/)
- [Xác minh Triển khai](5.4.3-test-endpoint/)
- [Cấu hình Dịch vụ](5.4.4-dns-simulation/)
