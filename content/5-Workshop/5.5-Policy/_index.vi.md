---
title : "Phát triển & Triển khai"
date: 2025-09-09
weight : 5
chapter : false
pre : " <b> 5.5. </b> "

---

#### Tổng quan

Phần này bao gồm quy trình phát triển và quy trình triển khai cho các ứng dụng MapVibe.

#### Quy trình Phát triển

1. **Phát triển Local**
   - Chạy ứng dụng frontend local với `bun run dev`
   - Kiểm tra API local với `bun run dev` trong `apps/api`
   - Sử dụng database local hoặc kết nối đến dev RDS

2. **Quy trình Build**
   - Build tất cả packages: `bun run build`
   - Build ứng dụng cụ thể: `cd apps/web && bun run build`

3. **Testing**
   - Kiểm tra kiểu: `bun run type-check`
   - Linting: `bun run lint`

#### Quy trình Triển khai

##### Triển khai Hạ tầng

```bash
cd infrastructure/terraform
terraform apply
```

##### Triển khai API

```bash
# Build API
cd apps/api
bun run build

# Triển khai sử dụng script
bun run deploy
# Hoặc sử dụng: pwsh ../../scripts/deploy-api.ps1
```

##### Triển khai Frontend (Web)

```bash
# Build frontend
cd apps/web
bun run build

# Triển khai lên S3 + CloudFront
bun run deploy
```

##### Triển khai Admin Dashboard

```bash
# Build admin
cd apps/admin
bun run build

# Triển khai sử dụng script
pwsh ../../scripts/deploy-admin.ps1
```

##### Chạy Database Migrations

```bash
pwsh scripts/deploy-migrate.ps1
```

#### Scripts Triển khai

Thư mục `scripts/` chứa các script PowerShell cho triển khai:
- `deploy-api.ps1` - Triển khai API Lambda
- `deploy-admin.ps1` - Triển khai admin dashboard
- `deploy-migrate.ps1` - Chạy database migrations
- `build-all-lambdas.ps1` - Build tất cả Lambda functions

#### Best Practices

1. **Luôn kiểm tra local** trước khi triển khai
2. **Sử dụng cấu hình theo môi trường**
3. **Theo dõi CloudWatch logs** sau khi triển khai
4. **Xác minh triển khai** bằng cách kiểm tra endpoints
5. **Giữ hạ tầng đồng bộ** với thay đổi code
