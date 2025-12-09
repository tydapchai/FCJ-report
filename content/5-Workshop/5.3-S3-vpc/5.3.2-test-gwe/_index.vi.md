---
title : "Chi tiết Ứng dụng"
date: 2025-09-09
weight : 2
chapter : false
pre : " <b> 5.3.2 </b> "

---

#### Ứng dụng Frontend

##### Ứng dụng Web (`apps/web`)

Ứng dụng chính dành cho người dùng được xây dựng với:
- **React 19** - React mới nhất với các tính năng concurrent
- **Vite** - Công cụ build và dev server nhanh
- **TailwindCSS** - Framework CSS utility-first
- **React Router** - Routing phía client
- **TanStack Query** - Fetch và cache dữ liệu
- **TipTap** - Trình soạn thảo văn bản phong phú cho đánh giá

**Tính năng chính:**
- Tìm kiếm ngôn ngữ tự nhiên sử dụng AI
- Khám phá và đề xuất địa điểm
- Đánh giá và xếp hạng của người dùng
- Tải lên ảnh
- Hồ sơ người dùng và địa điểm đã lưu
- Thiết kế responsive cho mobile và desktop

**Phát triển:**
```bash
cd apps/web
bun run dev
```

**Build:**
```bash
bun run build
```

##### Admin Dashboard (`apps/admin`)

Giao diện admin để quản lý nội dung:
- **React 19** với Vite
- **TailwindCSS** cho styling
- Components và pages dành riêng cho admin

**Tính năng chính:**
- Kiểm duyệt nội dung
- Quản lý người dùng
- Bảng điều khiển phân tích
- Quy trình phê duyệt địa điểm
- Quản lý đánh giá

**Phát triển:**
```bash
cd apps/admin
bun run dev
```

#### Backend API (`apps/api`)

Hàm Lambda API chính xử lý:
- REST API endpoints
- Xác thực với Cognito
- Thao tác database với Kysely
- Thao tác S3 cho ảnh
- Tích hợp với AWS Bedrock
- Xử lý hàng đợi SQS

**Handlers chính:**
- Places (CRUD, tìm kiếm, gần đây)
- Reviews (tạo, vote, comment)
- Users (hồ sơ, ảnh, thống kê)
- Photos (tải lên, xóa)
- Activities (theo dõi)

**Phát triển:**
```bash
cd apps/api
bun run dev
```

**Build:**
```bash
bun run build
```

#### Các hàm Lambda

Các hàm Lambda chuyên biệt trong hạ tầng:

1. **lambda-embeddings** - Tạo embeddings cho địa điểm sử dụng Bedrock
2. **lambda-rag** - Retrieval Augmented Generation cho tìm kiếm AI
3. **lambda-ocr-menu** - Trích xuất văn bản từ ảnh menu sử dụng Textract
4. **lambda-rekognition** - Kiểm duyệt nội dung sử dụng Rekognition
5. **lambda-review-aggregate** - Tổng hợp thống kê đánh giá
6. **lambda-s3-trigger** - Xử lý sự kiện upload S3
7. **lambda-migration** - Chạy database migration

#### Packages dùng chung

- **types** - Định nghĩa TypeScript dùng chung giữa các apps
- **ui-components** - Components React có thể tái sử dụng
- **database** - Lớp database dựa trên Kysely
- **utils** - Các hàm tiện ích chung
- **constants** - Các hằng số ứng dụng
