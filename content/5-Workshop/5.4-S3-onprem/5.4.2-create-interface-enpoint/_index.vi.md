---
title : "Triển khai Hạ tầng"
date: 2025-09-09
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "

---

#### Triển khai với Terraform

Triển khai hạ tầng:

```bash
cd infrastructure/terraform
terraform apply
```

Lệnh này sẽ tạo tất cả tài nguyên AWS. Quá trình có thể mất 15-30 phút.

#### Những gì được tạo

Cấu hình Terraform tạo:

1. **Module VPC**
   - VPC với public subnets
   - Internet Gateway
   - Route tables
   - Security groups

2. **Module RDS**
   - Instance cơ sở dữ liệu PostgreSQL (db.t3.micro)
   - Credentials database được lưu trong Secrets Manager
   - Khả năng truy cập công cộng (cho MVP)

3. **Secrets Manager**
   - Secret credentials database
   - Mật khẩu an toàn được tạo tự động

4. **Module Cognito**
   - User Pool cho xác thực
   - User Pool Client
   - Custom domain (login.mapvibe.site)
   - Tích hợp Google OAuth tùy chọn

5. **Các hàm Lambda**
   - Lambda API (REST API chính)
   - Lambda Embeddings (tích hợp Bedrock)
   - Lambda RAG (tìm kiếm AI)
   - Lambda OCR Menu (Textract)
   - Lambda Rekognition (kiểm duyệt nội dung)
   - Lambda Review Aggregate
   - Lambda S3 Trigger
   - Lambda Migration

6. **API Gateway**
   - REST API với custom domain
   - Tích hợp Lambda
   - Cognito authorizers
   - Cấu hình CORS

7. **S3 & CloudFront**
   - S3 bucket cho tài sản tĩnh
   - S3 bucket cho ảnh
   - CloudFront distribution
   - Tích hợp WAF
   - Custom domain (mapvibe.site)

8. **Route53 & ACM**
   - Hosted zone cho domain
   - Chứng chỉ SSL
   - DNS records

9. **WAF**
   - Web ACL cho CloudFront
   - Quy tắc bảo mật

#### Theo dõi Triển khai

Xem output của Terraform để theo dõi tiến trình. Bạn sẽ thấy:
- Tài nguyên đang được tạo
- Bất kỳ lỗi hoặc cảnh báo nào
- Giá trị output (URLs, ARNs, v.v.)

#### Lưu Outputs

Sau khi triển khai, lưu các outputs:

```bash
terraform output > outputs.txt
```

Các outputs quan trọng bao gồm:
- API Gateway URL
- CloudFront URLs
- Cognito User Pool ID
- RDS endpoint
- Database secret ARN
