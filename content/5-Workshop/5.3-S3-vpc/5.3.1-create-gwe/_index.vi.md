---
title : "Thiết lập Monorepo"
date: 2025-09-09
weight : 1
chapter : false
pre : " <b> 5.3.1 </b> "

---

#### Clone Repository

Đầu tiên, clone repository MapVibe:

```bash
git clone <repository-url>
cd mapvibe
```

#### Cài đặt Dependencies

Cài đặt tất cả dependencies bằng Bun:

```bash
bun install
```

Lệnh này sẽ cài đặt dependencies cho tất cả workspaces trong monorepo.

#### Cấu hình Workspace

Dự án sử dụng Bun workspaces được định nghĩa trong `package.json`:

```json
{
  "workspaces": [
    "apps/*",
    "packages/*",
    "infrastructure"
  ]
}
```

#### Cấu hình TurboRepo

TurboRepo được cấu hình trong `turbo.json` để quản lý build pipelines:

- **build** - Build tất cả packages và apps
- **dev** - Chạy development servers
- **lint** - Lint tất cả code
- **type-check** - Kiểm tra kiểu TypeScript
- **deploy** - Triển khai ứng dụng

#### Scripts Phát triển

Các script phổ biến có sẵn ở root:

```bash
# Khởi động tất cả development servers
bun run dev

# Build tất cả packages và apps
bun run build

# Lint tất cả code
bun run lint

# Kiểm tra kiểu
bun run type-check

# Format code
bun run format
```

#### Biến môi trường

Tạo các file `.env` khi cần:

1. `.env` gốc - Cho các biến hạ tầng
2. `apps/web/.env` - Cho cấu hình frontend
3. `apps/admin/.env` - Cho admin dashboard

Liên hệ người duy trì dự án để lấy các biến môi trường cần thiết.

#### Xác minh Thiết lập

Xác minh thiết lập của bạn bằng cách chạy:

```bash
# Kiểm tra phiên bản Bun
bun --version

# Cài đặt dependencies
bun install

# Chạy type check
bun run type-check
```

Nếu tất cả các lệnh thành công, monorepo của bạn đã sẵn sàng để phát triển!
