---
title: "Workshop"
date: 2025-09-09
weight: 5
chapter: false
pre: " <b> 5. </b> "
---
# MapVibe - Xây dựng Nền tảng Khám phá Địa điểm với AI

#### Tổng quan

**MapVibe** là một ứng dụng web hiện đại giúp người dùng khám phá các địa điểm ăn uống và hoạt động bằng cách sử dụng truy vấn ngôn ngữ tự nhiên được hỗ trợ bởi các dịch vụ AI của AWS. Được xây dựng với kiến trúc monorepo sử dụng TurboRepo và Bun, MapVibe tận dụng các dịch vụ serverless của AWS để cung cấp một giải pháp có khả năng mở rộng và tối ưu chi phí.

Trong workshop này, bạn sẽ học cách:
- Thiết lập và cấu hình cấu trúc dự án monorepo
- Triển khai hạ tầng sử dụng Terraform trên AWS
- Xây dựng và triển khai các hàm Lambda serverless
- Cấu hình các dịch vụ AWS bao gồm RDS, Cognito, CloudFront, API Gateway và Bedrock
- Phát triển ứng dụng full-stack với frontend React và backend Node.js

Dự án thể hiện các mẫu kiến trúc cloud hiện đại sử dụng:
- **Kiến trúc Monorepo** - TurboRepo để quản lý build và dependencies hiệu quả
- **Backend Serverless** - Các hàm AWS Lambda cho API endpoints và xử lý
- **Tích hợp AI** - AWS Bedrock cho xử lý ngôn ngữ tự nhiên và embeddings
- **Infrastructure as Code** - Terraform để quản lý tài nguyên AWS
- **Frontend Hiện đại** - React 19 với Vite và TailwindCSS

#### Nội dung

1. [Tổng quan về workshop](5.1-Workshop-overview/)
2. [Yêu cầu tiên quyết](5.2-Prerequiste/)
3. [Cấu trúc dự án](5.3-S3-vpc/)
4. [Thiết lập hạ tầng](5.4-S3-onprem/)
5. [Phát triển & Triển khai](5.5-Policy/)
6. [Dọn dẹp](5.6-Cleanup/)
