---
title : "Cấu trúc dự án"
date: 2025-09-09
weight : 3
chapter : false
pre : " <b> 5.3. </b> "

---

#### Kiến trúc Monorepo

MapVibe sử dụng kiến trúc **monorepo** được quản lý bởi **TurboRepo** và **Bun**. Điều này cho phép:
- Chia sẻ code và dependencies giữa nhiều ứng dụng
- Build hiệu quả với caching
- Công cụ và cấu hình nhất quán
- Quản lý dependencies đơn giản hóa

#### Cấu trúc thư mục

```
mapvibe/
├── apps/                    # Ứng dụng
│   ├── web/                 # Ứng dụng frontend chính
│   ├── admin/               # Bảng điều khiển admin
│   └── api/                 # Hàm Lambda API backend
├── packages/                # Packages dùng chung
│   ├── types/               # Định nghĩa kiểu TypeScript
│   ├── ui-components/      # Components React dùng chung
│   ├── database/            # Lớp truy cập database (Kysely)
│   ├── api-functions/      # Tiện ích API dùng chung
│   ├── utils/               # Tiện ích chung
│   └── constants/           # Hằng số dùng chung
├── infrastructure/          # Infrastructure as Code
│   ├── terraform/           # Cấu hình Terraform
│   │   ├── main.tf          # Cấu hình chính
│   │   └── modules/         # Các module Terraform
│   └── s3-cloudfront/       # Cấu hình S3 và CloudFront
├── scripts/                 # Scripts triển khai và build
├── package.json             # Cấu hình package gốc
├── turbo.json               # Cấu hình TurboRepo
└── tsconfig.json            # Cấu hình TypeScript
```

#### Ứng dụng

1. **`apps/web`** - Ứng dụng web chính dành cho người dùng
   - Xây dựng với React 19, Vite và TailwindCSS
   - Tính năng: Tìm kiếm, khám phá địa điểm, đánh giá, hồ sơ người dùng
   - Triển khai lên S3 + CloudFront

2. **`apps/admin`** - Bảng điều khiển admin
   - Xây dựng với React 19, Vite và TailwindCSS
   - Tính năng: Kiểm duyệt nội dung, phân tích, quản lý người dùng
   - Triển khai lên S3 + CloudFront riêng

3. **`apps/api`** - Hàm Lambda API chính
   - Xử lý các REST API endpoints
   - Tích hợp với RDS, S3, Cognito, Bedrock
   - Xây dựng với TypeScript và Node.js

#### Packages dùng chung

- **`packages/types`** - Các kiểu và interface TypeScript dùng chung
- **`packages/ui-components`** - Các component UI React có thể tái sử dụng
- **`packages/database`** - Lớp truy cập database sử dụng Kysely
- **`packages/utils`** - Các hàm tiện ích chung
- **`packages/constants`** - Các hằng số ứng dụng

#### Hạ tầng

Thư mục `infrastructure/` chứa các module Terraform cho:
- VPC và networking
- Cơ sở dữ liệu RDS PostgreSQL
- Các hàm Lambda (API, embeddings, RAG, OCR, Rekognition, v.v.)
- API Gateway
- CloudFront và S3
- Cognito User Pool
- Route53 và ACM
- WAF

#### Nội dung

- [Thiết lập Monorepo](5.3.1-create-gwe/)
- [Chi tiết Ứng dụng](5.3.2-test-gwe/)
