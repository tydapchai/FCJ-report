---
title: "Proposal"
date: "2025-10-22"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# MAPVIBE - Nền tảng Khám phá địa điểm ăn uống với AI
*(Khám phá các địa điểm ăn uống và các địa điểm khác tại Thành phố Hồ Chí Minh sử dụng các gợi ý ngôn ngữ tự nhiên và thông tin chi tiết theo ngữ cảnh)*

---

## 1. Tóm tắt chung

Chúng tôi là một nhóm gồm 5 sinh viên Công nghệ Thông tin đang thực tập, cùng nhau phát triển một dự án mang tên MapVibe. MapVibe là một nền tảng website sáng tạo, giúp người dùng, đặc biệt là thế hệ **GenZ**, tìm kiếm các địa điểm ăn uống bằng ngôn ngữ tự nhiên, dựa trên **tâm trạng và cảm xúc thật** của họ. Ví dụ, thay vì tìm "quán cà phê", người dùng có thể hỏi "Hôm nay tôi đang buồn, có quán đồ uống nào giúp tôi giải tỏa nỗi buồn không?".

Mục tiêu của dự án là cải tiến phương pháp tìm kiếm truyền thống và tạo ra một trải nghiệm cá nhân hóa, sâu sắc hơn cho người dùng. Chúng tôi lựa chọn AWS làm nền tảng đám mây để tận dụng các dịch vụ mạnh mẽ, linh hoạt và tối ưu chi phí. Điều này giúp đội ngũ tập trung tối đa nguồn lực vào phát triển tính năng cốt lõi, giảm thiểu gánh nặng quản lý hạ tầng, đồng thời giữ cho chi phí vận hành nằm trong **ngân sách 200 đô la từ gói AWS Free Tier**, rất phù hợp với một dự án sinh viên.

Tính năng cốt lõi của MapVibe cho phép người dùng truy vấn bằng ngôn ngữ tự nhiên để tìm kiếm địa điểm phù hợp với tâm trạng hoặc nhu cầu cụ thể của họ. Hệ thống sẽ phân tích và trả về những gợi ý phù hợp nhất, kèm theo các bài đánh giá và thông tin chi tiết.

Để đạt được mục tiêu này, nhóm chúng tôi sẽ chịu trách nhiệm toàn bộ quá trình: từ thiết kế, phát triển website, xây dựng và cấu hình hạ tầng trên AWS (sử dụng các dịch vụ như **Bedrock**, **Lambda**, **RDS**), cho đến việc tự tổng hợp bộ dữ liệu ban đầu về các địa điểm.

---

## 2. Phát biểu Vấn đề

### Vấn đề là gì?

- Các nền tảng bản đồ truyền thống như Google Maps phụ thuộc vào tìm kiếm dựa trên từ khóa và bộ lọc tĩnh, gặp khó khăn trong việc diễn giải các truy vấn tinh tế, giàu ngữ cảnh (ví dụ: "quán cà phê yên tĩnh gần sông có chỗ ngồi ngoài trời").
- Người dùng lãng phí thời gian điều hướng nhiều ứng dụng để tìm địa điểm ăn uống hoặc hoạt động phù hợp.
- Các giải pháp hiện tại thiếu giao diện trò chuyện và không kết hợp được các tín hiệu ngữ cảnh như thời gian, tâm trạng hoặc kích thước nhóm.

### Giải pháp

MapVibe sử dụng **AWS Bedrock (mô hình Titan embedding, mô hình LLM Claude)** để phân tích các gợi ý ngôn ngữ tự nhiên bằng tiếng Việt và tiếng Anh, chuyển đổi chúng thành các truy vấn có cấu trúc. Nó truy xuất và xếp hạng kết quả từ cơ sở dữ liệu nội bộ **RDS (PostgreSQL)** với dữ liệu địa điểm được lập chỉ mục địa lý và các tính năng hỗ trợ vector, cung cấp giao diện kết hợp (tìm kiếm trò chuyện + bộ lọc danh mục). Nội dung do người dùng tạo (đánh giá, gợi ý địa điểm) được kiểm duyệt sử dụng **AWS Rekognition**, đảm bảo an toàn và chất lượng thông qua phân tích driven by AI tiên tiến.

### Lợi ích và ROI

- **Tốc độ**: Giảm thời gian khám phá địa điểm từ vài phút xuống vài giây.
- **Cá nhân hóa**: Kết quả nhận biết ngữ cảnh dựa trên sở thích và hành vi của người dùng, powered by AI.
- **Tự động hóa**: Loại bỏ bộ lọc thủ công với phân tích ý định driven by AI.
- **Khả năng mở rộng**: Cơ sở hạ tầng AWS toàn cầu đảm bảo độ trễ thấp và khả năng phục hồi.
- **Hiệu quả chi phí**: Tối ưu hóa để phù hợp với ngân sách $200 tín dụng từ AWS Free Tier cho toàn bộ chu kỳ phát triển và triển khai ban đầu.
- **Tiềm năng thương mại**: Cơ hội hợp tác với các doanh nghiệp địa phương hoặc tích hợp với các hệ thống đặt phòng nội bộ.

---

## 3. Kiến trúc Giải pháp

### Tổng quan

Gợi ý Người dùng + Ngữ cảnh → **Mô hình Titan Embedding của Bedrock** → **Truy vấn có Cấu trúc** → **Tìm kiếm RDS (PostgreSQL)** → **Xếp hạng & Bộ nhớ đệm** → **Hiển thị Web UI** → **Vòng lặp Phản hồi Người dùng**.  
![Solution Architecture](/images/2-Proposal/4N1D-Architechture.drawio.png)

### Dịch vụ AWS được sử dụng

| Service                   | Function                              |
|---------------------------|---------------------------------------|
| Amazon Route 53           | Định tuyến tên miền                   |
| AWS Certificate Manager   | Chứng chỉ SSL/TLS                     |
| AWS WAF                   | Tường lửa ứng dụng web                |
| Amazon CloudFront         | CDN toàn cầu cho tài sản tĩnh         |
| Amazon API Gateway        | Điểm cuối API RESTful an toàn         |
| AWS Lambda                | Logic phân tích ý định, tìm kiếm và xếp hạng |
| Amazon RDS (PostgreSQL)   | Dữ liệu địa điểm được lập chỉ mục địa lý và bộ nhớ đệm truy vấn |
| Amazon S3                 | Lưu trữ ảnh, nhật ký và tài sản       |
| Amazon Cognito            | Xác thực và ủy quyền người dùng       |
| Amazon Bedrock            | Mô hình Titan embedding và mô hình LLM Claude để phân tích ý định và tóm tắt    |
| Amazon Rekognition        | Kiểm duyệt nội dung driven by AI cho các tải lên của người dùng |
| Amazon Textract           | Trích xuất văn bản từ hình ảnh và tài liệu (menu, biển hiệu, v.v.) |
| Amazon EventBridge        | Phân tích theo lịch và cập nhật huy hiệu |
| Amazon CloudWatch         | Giám sát và ghi nhật ký               |

### Thiết kế Thành phần

- **Frontend**: Ứng dụng web responsive (Next.js, song ngữ VI/EN, UI tìm kiếm kết hợp).
- **Tiếp nhận Dữ liệu**: Gợi ý và ngữ cảnh được xử lý qua API Gateway; các tải lên của người dùng (đánh giá, ảnh) được kiểm duyệt bởi AI của Rekognition.
- **Lưu trữ Dữ liệu**: RDS (PostgreSQL) cho dữ liệu địa điểm với thiết kế cơ sở dữ liệu quan hệ (ERD), các tính năng hỗ trợ vector và lập chỉ mục để tối ưu hóa tốc độ truy vấn; S3 cho ảnh và nhật ký.
- **Xử lý Dữ liệu**: Microservices Lambda xử lý các cuộc gọi Bedrock (mô hình Titan embedding và mô hình LLM Claude), thực thi truy vấn và xếp hạng kết quả.
- **Quản lý Người dùng**: Cognito cho xác thực dựa trên JWT (đăng nhập email/mạng xã hội); người dùng khách truy cập các tính năng hạn chế.
- **Đầu ra**: Hiển thị thẻ địa điểm với tóm tắt được tạo bởi AI, đánh giá, ảnh và CTA (ví dụ: Chỉ đường, Gọi).

---

## 4. Triển khai Kỹ thuật

### Các giai đoạn Triển khai

| Phase | Description                                          | Duration   |
|-------|------------------------------------------------------|------------|
| 1     | Xác định kiến trúc, schema Titan embedding của Bedrock và schema RDS (PostgreSQL) với thiết kế ERD | 2 tuần |
| 2     | Ước tính chi phí và tối ưu hóa chiến lược bộ nhớ đệm  | 1 tuần |
| 3     | Xây dựng backend (Lambda, RDS PostgreSQL, Bedrock Titan embedding, Rekognition)| 3 tuần |
| 4     | Phát triển frontend (Next.js, song ngữ, UI responsive)  | 3 tuần |
| 5     | Kiểm tra và tối ưu hóa cho độ trễ <10s và khả năng mở rộng | 2 tuần |
| 6     | Ra mắt MVP, triển khai qua CI/CD (Terraform, GitLab), thu thập phản hồi    | 2 tuần |

### Yêu cầu Kỹ thuật

- **Thiết bị Edge**: Trình duyệt hiện đại (Chrome, Safari, Firefox) với UI responsive sẵn sàng PWA.
- **Cloud**: AWS Route 53, ACM, WAF, CloudFront, API Gateway, Lambda, RDS (PostgreSQL với hỗ trợ vector), S3, Cognito, Bedrock (Titan embedding, Claude LLM), Rekognition, Textract, EventBridge, CloudWatch.
- **Công cụ & Framework**: Next.js (App Router), TypeScript, Terraform cho infrastructure-as-code, GitLab cho CI/CD.

---

## 5. Lịch trình & Cột mốc

| Period              | Activities                                                  |
|---------------------|-------------------------------------------------------------|
| Trước khi Phát triển (Tháng 0 - 9/2025) | Nghiên cứu các bộ dữ liệu địa điểm tại Thành phố Hồ Chí Minh cho RDS (PostgreSQL) |
| Tháng 1 (10/2025) | Xây dựng backend MVP với mô hình Titan embedding của Bedrock và RDS (PostgreSQL)            |
| Tháng 2 (11/2025)  | Triển khai bộ nhớ đệm, phát triển tích hợp frontend            |
| Tháng 3 (11/2025)  | Ra mắt beta công khai, tối ưu hóa hiệu suất, thu thập phản hồi  |
| Sau khi Ra mắt (12/2025) | Thêm các tính năng nâng cao (ví dụ: xếp hạng dựa trên ML, chế độ ngoại tuyến)|

---

## 6. Ước tính Ngân sách

### Ước tính Thời gian Đầu tư theo Giai đoạn

Chúng tôi ước tính mỗi thành viên sẽ đóng góp khoảng 20 giờ mỗi tuần cho dự án. Với mỗi giai đoạn kéo dài 2 tuần, tổng thời gian đầu tư được ước tính như sau:

| Giai đoạn dự án | Tổng số giờ ước tính |
|:--:|:--:|
| Giai đoạn 1: Thiết lập nền tảng | 200 giờ (5 người * 20 giờ/tuần * 2 tuần) |
| Giai đoạn 2: Xây dựng tính năng lõi | 200 giờ (5 người * 20 giờ/tuần * 2 tuần) |
| Giai đoạn 3: Hoàn thiện và Triển khai | 200 giờ (5 người * 20 giờ/tuần * 2 tuần) |
| **Tổng số giờ** | **600 giờ** |
| **Tổng chi phí tài chính** | **$0** |

### Phân bố Đóng góp cho Dự án

Chi phí tài chính trực tiếp của dự án là không đáng kể và được trang trải hoàn toàn bởi các khoản tín dụng. Sự đóng góp chính đến từ thời gian của đội ngũ và sự hỗ trợ từ AWS.

| Bên tham gia | Đóng góp | % Đóng góp (Tổng giá trị) |
|:--|:--|:--|
| Khách hàng (Chương trình thực tập) | - Cơ hội học tập và kinh nghiệm thực tế. | - |
| Đối tác (Nhóm sinh viên) | - Thời gian và công sức (ước tính 600 giờ). | - |
| AWS | - $200 tín dụng (credit). <br> - Các dịch vụ trong Gói Miễn phí (Free Tier). | 100% (chi phí tài chính) |

### Biện pháp Tối ưu hóa Chi phí
- **Sử dụng Free-Tier**: Tận dụng các miễn phí của AWS cho Lambda, RDS, S3, CloudFront, Rekognition và Cognito để giảm thiểu chi phí.
- **Bộ nhớ đệm Aggressive cho Bedrock**: Đạt tỷ lệ truy cập bộ nhớ đệm cao để giảm chi phí token AI.
- **Xử lý Batch Rekognition**: Các kiểm tra hình ảnh không theo thời gian thực để tiết kiệm chi phí.
- **Sử dụng RDS Tối ưu**: Sử dụng PostgreSQL với lập chỉ mục phù hợp để giảm thiểu chi phí truy vấn.
- **Bộ nhớ đệm Tài sản Tĩnh**: Tối thiểu hóa chi phí truyền dữ liệu đi ra thông qua CloudFront.

### Kiểm soát Ngân sách
- Toàn bộ dự án hoạt động trong phạm vi **$200 tín dụng từ AWS Free Tier**.
- Tất cả chi phí cơ sở hạ tầng được trang trải bởi tín dụng AWS và các dịch vụ free tier.
- Không có chi phí tài chính trực tiếp nào được phát sinh bởi nhóm.

---

## 7. Đánh giá Rủi ro

| Risk                            | Impact | Probability | Mitigation                              |
|---------------------------------|--------|-------------|----------------------------------------|
| Dữ liệu RDS không nhất quán      | High   | Medium      | Xác thực và sao lưu dữ liệu thường xuyên    |
| Phân tích Titan embedding không chính xác (VN/EN)  | Medium | Low         | Mẫu gợi ý được xác định trước, xác thực |
| Khả năng mở rộng dưới tải cao     | Medium | Medium      | Tự động mở rộng serverless, bộ nhớ đệm       |
| Mối quan tâm về quyền riêng tư (dữ liệu vị trí)| High   | Low         | Sự đồng ý rõ ràng của người dùng, các truy vấn ẩn danh |
| Vượt quá ngân sách               | High   | Medium      | Giám sát chặt chẽ, sử dụng free tiers, cảnh báo chi phí |
| Phụ thuộc vào dịch vụ AWS Bedrock (Titan, Claude)  | High   | Low         | Cơ chế dự phòng thay thế, kết quả được bộ nhớ đệm |
| Phụ thuộc vào nền tảng GitLab    | Medium | Low         | Sao lưu thường xuyên, tùy chọn repository thay thế |
| Chất lượng dữ liệu ban đầu       | Medium | Medium      | Quy trình xác thực dữ liệu, tích hợp phản hồi người dùng |

**Kế hoạch dự phòng**: Sử dụng kết quả RDS được bộ nhớ đệm hoặc dự phòng JSON cục bộ cho các demo. Triển khai giới hạn tốc độ dựa trên IP cho người dùng chưa xác thực. Giám sát chi phí AWS hàng tuần để ngăn chặn vượt quá ngân sách.

---

## 8. Kết quả Dự kiến

### Tiêu chí Thành công Dự án

Để đảm bảo dự án MapVibe thành công, chúng tôi đặt ra các tiêu chí thành công cụ thể, có thể đo lường được như sau:

- **Hoàn thành triển khai hạ tầng**: Triển khai thành công và an toàn toàn bộ kiến trúc hệ thống lên AWS, bao gồm các dịch vụ đã định sẵn như VPC, Subnet, RDS, Lambda, S3, CloudFront, API Gateway, và Cognito.
- **Tính năng tìm kiếm cốt lõi hoạt động hiệu quả**: Tính năng tìm kiếm bằng ngôn ngữ tự nhiên sử dụng AWS Bedrock (mô hình Titan embedding, mô hình LLM Claude) và RDS PostgreSQL phải có khả năng hiểu và trả về kết quả phù hợp, có ý nghĩa cho ít nhất **90%** các câu truy vấn thông thường từ người dùng.
- **Tối ưu chi phí**: Toàn bộ chi phí sử dụng dịch vụ AWS trong suốt quá trình phát triển và triển khai ban đầu không vượt quá 200 đô la tín dụng từ gói AWS Free Tier.
- **Ra mắt sản phẩm (MVP)**: Hoàn thiện và cho ra mắt phiên bản sản phẩm khả dụng tối thiểu (MVP) của website MapVibe cho nhóm người dùng mục tiêu (GenZ) trên cả **desktop và nền tảng iOS, Android**. Ngoài ra, còn có **trang tổng quan (Dashboard) dành cho quản trị viên** để quản lý nội dung và người dùng.
- **Thu thập phản hồi tích cực**: Sau khi ra mắt, thu thập được ít nhất 50 đề xuất địa điểm mới từ người dùng trong tháng đầu tiên, cho thấy sự tương tác và hưởng ứng của cộng đồng.

### Cải tiến Kỹ thuật
- **Tìm kiếm Trò chuyện dựa trên Tâm trạng**: Hỗ trợ ngôn ngữ tự nhiên cho tiếng Việt và tiếng Anh với độ trễ <10s, powered by Bedrock (mô hình Titan embedding và mô hình LLM Claude), hiểu được cảm xúc và tâm trạng của người dùng.
- **Tóm tắt AI**: Tổng quan địa điểm được tạo bởi Bedrock, làm mới mỗi 7 ngày hoặc sau 10 đánh giá mới.
- **Khả năng mở rộng**: Kiến trúc serverless với phân phối CDN toàn cầu qua CloudFront.
- **Kiểm duyệt**: AI của Rekognition đảm bảo nội dung do người dùng tạo an toàn (đánh giá, ảnh).
- **Cơ sở dữ liệu Quan hệ**: PostgreSQL với lập chỉ mục được tối ưu hóa cho hiệu suất truy vấn nhanh.

### Giá trị Dài hạn
- **Cá nhân hóa**: Xếp hạng lại dựa trên ML và phân tích hành vi người dùng dựa trên tâm trạng và sở thích.
- **Hỗ trợ Ngoại tuyến**: PWA để liệt kê các địa điểm ngoại tuyến.
- **Khả năng mở rộng**: Tiềm năng tích hợp với các hệ thống đặt phòng nội bộ.
- **Mở rộng Ngữ cảnh**: Đề xuất dựa trên thời tiết, sự kiện, xu hướng xã hội và cảm xúc người dùng.

---

### Tài liệu đính kèm / Tham khảo
- [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=b574c31813807522d949cf5adca64b41612e12c7)
- [GitLab Repository](https://gitlab.com/4n1d/mapvibe)

## 9. QUAN TRỌNG: Proposal bản docs
- [Proposal Docs Version](https://docs.google.com/document/d/1-wM11mgTNaL8gvbMjAmukW9ZKzqGtHMp/edit)
- [Related Documents](https://drive.google.com/drive/u/0/folders/1cdBYgwzBA4Vl9ww_fCPXmbsKToTKgH4L)

