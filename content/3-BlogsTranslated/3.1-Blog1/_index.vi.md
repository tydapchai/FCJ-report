---
title: "Blog 1"
date: "2024-09-30"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---


# Mở Khóa Các Mô Hình AI Thương Mại trong AWS GovCloud (US): Truy Cập Bảo Mật Xuyên Phân Vùng với Amazon Bedrock

**Tác giả:** Tyler Replogle, Doug Hairfield, Michael Pitcher, và Vin Minichino | **Ngày đăng:** 30/09/2025

**Chủ đề:** [Amazon Bedrock](https://aws.amazon.com/bedrock/), [Artificial Intelligence](https://aws.amazon.com/blogs/publicsector/category/artificial-intelligence/), [AWS GovCloud (US)](https://aws.amazon.com/govcloud-us/), [Generative AI](https://aws.amazon.com/generative-ai/)

**Nguồn:** [AWS Public Sector Blog](https://aws.amazon.com/blogs/publicsector/unlocking-commercial-ai-models-in-aws-govcloud-us-secure-cross-partition-access-with-amazon-bedrock/)

---

![Header](https://d2908q01vomqb2.cloudfront.net/9e6a55b6b4563e652a23be9d623ca5055c356940/2025/09/23/AWS-Public-Sector-Blog-Featured-Images-Blog-Header-static-template-Autosaved-22.png)

Trong bài đăng này, chúng tôi sẽ trình bày **ba giải pháp** cho phép các workload trong [AWS GovCloud (US)](https://aws.amazon.com/govcloud-us/) kết nối an toàn vào phân vùng thương mại của [Amazon Web Services (AWS)](https://aws.amazon.com/) để thực hiện suy luận với [Amazon Bedrock](https://aws.amazon.com/bedrock/). Mỗi phương pháp có những điểm mạnh, yếu riêng và đến cuối bài bạn sẽ xác định được lựa chọn phù hợp nhất cho tổ chức của mình.

[Generative AI](https://aws.amazon.com/generative-ai/) đang phát triển rất nhanh, với các [foundation models (FMs)](https://aws.amazon.com/what-is/foundation-models/) và tính năng mới được cập nhật liên tục. Những khả năng này được giới thiệu đầu tiên ở phân vùng AWS thương mại. Với những tổ chức trong môi trường nhạy cảm, chịu sự quản lý nghiêm ngặt, thách thức là làm sao bắt kịp đổi mới này và cùng lúc thử nghiệm nhanh, thu thập phản hồi khách hàng, hoàn thiện chức năng mới thành các giải pháp sẵn sàng cho nhiệm vụ thực tế.

---

## Cách Hoạt Động của Truy Cập Xuyên Phân Vùng

Các workload trong AWS GovCloud (US) gọi Amazon Bedrock bằng cách gửi request tới API dịch vụ trong phân vùng thương mại. Thay vì gọi endpoint Amazon Bedrock trong AWS GovCloud (US), ứng dụng sẽ chuyển request qua kết nối mạng đã chọn vào phân vùng thương mại nơi Amazon Bedrock lưu trú.

Do AWS GovCloud (US) và thương mại không có kết nối nội bộ tự nhiên, hai phân vùng này được **cô lập về mặt logic và vật lý**. Để giao tiếp, tổ chức phải dùng đường kết nối như:
- Endpoint công khai
- [AWS Site-to-Site VPN](https://aws.amazon.com/vpn/site-to-site-vpn/)
- [AWS Direct Connect](https://aws.amazon.com/directconnect/)

Khi lưu lượng truyền giữa AWS GovCloud (US) và thương mại, nó thường đi qua backbone của AWS. Như [Amazon VPC FAQ](https://aws.amazon.com/vpc/faqs/#topic-2) giải thích: *"Các gói tin xuất phát từ mạng AWS có đích đến cũng thuộc mạng AWS sẽ luôn lưu thông trên mạng toàn cầu AWS, trừ trường hợp sang khu vực Trung Quốc."* Để tìm hiểu kỹ hơn, xem bài [Introduction to Network Transformation on AWS](https://aws.amazon.com/blogs/networking-and-content-delivery/introduction-to-network-transformation-on-aws-part-1/).

Amazon Bedrock sử dụng API dịch vụ qua **HTTPS**, mã hóa các request với TLS từ AWS GovCloud (US) sang phân vùng thương mại. Điều này đảm bảo luôn mã hóa cho giao tiếp xuyên phân vùng, bất kể cách kết nối. Đối với workload yêu cầu module mật mã đạt chuẩn FIPS 140, Bedrock cung cấp endpoint FIPS như tài liệu [AWS General Reference for Amazon Bedrock](https://docs.aws.amazon.com/general/latest/gr/bedrock.html).

### Kiến trúc ứng dụng

Logic ứng dụng luôn nằm hoàn toàn trong AWS GovCloud (US):
- [Amazon API Gateway](https://aws.amazon.com/api-gateway/) - lộ endpoint tới workload
- [AWS Lambda](https://aws.amazon.com/lambda/) - xử lý request, lấy khóa API từ Secrets Manager
- [AWS Secrets Manager](https://aws.amazon.com/secrets-manager/) - lưu trữ an toàn khóa API Bedrock
- [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) - ghi log để theo dõi hiệu suất
- **AWS CloudTrail** - cung cấp nhật ký audit các API call tới Bedrock

---

## Ba Lựa Chọn Kết Nối

Có ba cách kết nối từ AWS GovCloud (US) tới phân vùng thương mại. Chọn tùy theo yêu cầu bảo mật, hiệu năng và vận hành.

### Thiết lập xác thực

Trước khi chọn phương án kết nối, cần thiết lập xác thực bằng khóa API Amazon Bedrock ở tài khoản phân vùng thương mại. Xem hướng dẫn tại [Accelerate AI development with Amazon Bedrock API keys](https://aws.amazon.com/blogs/machine-learning/accelerate-ai-development-with-amazon-bedrock-api-keys/).

Ngoài khóa API, cần:
- Bật quyền truy cập model trên Bedrock commercial cho từng foundation model
- Cấu hình inference profile nếu cần (như [Anthropic's Claude 4](https://aws.amazon.com/bedrock/anthropic/))

Với VPN và Direct Connect, cần lập các **VPC endpoint** trong VPC thương mại cho Amazon Bedrock và các dịch vụ phụ trợ như [CloudWatch Logs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html), Secrets Manager. Xem thêm tại [Amazon VPC endpoints documentation](https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html).

---

## Lựa chọn 1: Endpoint Công Khai

Cách đơn giản nhất dùng backbone AWS để nối GovCloud (US) đến phân vùng thương mại. Ứng dụng GovCloud (US) gửi HTTPS tới API Gateway. TLS mã hóa truyền tải; IAM và Secrets Manager điều khiển xác thực.

**Yêu cầu ở phân vùng thương mại:**
- Khóa API Amazon Bedrock xác thực
- Đã bật quyền truy cập model cho từng FM muốn dùng
- Inference profile cho các model yêu cầu (như Claude 4)

**Phù hợp cho:** proof-of-concept hoặc dự án thử nghiệm cần triển khai nhanh, có thể xong trong vài tuần với hạ tầng tối thiểu.

**Đánh đổi:** lưu lượng đi ra internet nên không đạt mức độ bảo mật cao nhất.

![Kiến trúc Public Endpoint](https://d2908q01vomqb2.cloudfront.net/9e6a55b6b4563e652a23be9d623ca5055c356940/2025/09/26/cross-partition-inference-architecture-public-endpoint.png)

*Hình 1: Kiến trúc tổng quan tùy chọn endpoint công khai - ứng dụng GovCloud (US) gọi trực tiếp Bedrock ở phân vùng thương mại qua HTTPS*

---

## Lựa chọn 2: AWS Site-to-Site VPN với Endpoint Riêng Tư

Dành cho tổ chức muốn bảo mật cao hơn, tránh internet công khai, dùng [AWS Site-to-Site VPN](https://aws.amazon.com/vpn/site-to-site-vpn/) lập "đường hầm" mã hóa giữa VPC GovCloud (US) và thương mại.

**Yêu cầu ở phân vùng thương mại:**
- Mọi thứ ở lựa chọn 1
- Đã cấu hình VPN gateway nối GovCloud (US)
- Đã tạo các VPC endpoint để dùng dịch vụ AWS mà không đi qua internet

**Phù hợp cho:** môi trường triển khai thực tế, tuân thủ quy định tốt hơn, bảo mật cao hơn.

**Đánh đổi:** phức tạp hơn và tốn thời gian triển khai.

Xem hướng dẫn setup chi tiết tại [Get started with AWS Site-to-Site VPN](https://docs.aws.amazon.com/vpn/latest/s2svpn/SetUpVPNConnections.html).

![Kiến trúc VPN](https://d2908q01vomqb2.cloudfront.net/9e6a55b6b4563e652a23be9d623ca5055c356940/2025/09/26/cross-partition-inference-architecture-vpn.drawio-2.png)

*Hình 2: Kiến trúc tổng quan tùy chọn kết nối VPN - GovCloud (US) và thương mại kết nối qua đường hầm VPN mã hóa*

---

## Lựa chọn 3: AWS Direct Connect

Lựa chọn này sử dụng [AWS Direct Connect](https://aws.amazon.com/directconnect/) tạo đường kết nối riêng tư giữa GovCloud (US) và phân vùng thương mại, cho **thông lượng cao nhất, độ trễ thấp nhất**.

**Lưu ý quan trọng:** Direct Connect không cung cấp đường riêng nội bộ từ GovCloud (US) sang thương mại, mà sẽ kết nối từng phân vùng tới mạng riêng của khách hàng, sau đó định tuyến giữa hai đầu ở đây.

**Yêu cầu ở phân vùng thương mại:**
- Mọi thứ ở lựa chọn 1
- Direct Connect gateway, đa kết nối từ từng phân vùng về mạng khách hàng để định tuyến
- VPC endpoint để truy cập AWS mà không qua internet

**Phù hợp cho:** workload AI trọng yếu hoặc khối lượng lớn, khi workload đã ổn định và có nhu cầu hiệu năng lớn.

**Đánh đổi:** phải triển khai hạ tầng mạng phức tạp, tốn nhiều tuần/tháng.

Xem thêm blog về kết nối tại [Hybrid connectivity to AWS GovCloud (US) and commercial Regions using AWS Direct Connect](https://aws.amazon.com/blogs/publicsector/aws-hybrid-connectivity-sharing-aws-direct-connect-aws-govcloud-us-commercial-regions/).

![Kiến trúc Direct Connect](https://d2908q01vomqb2.cloudfront.net/9e6a55b6b4563e652a23be9d623ca5055c356940/2025/09/26/cross-partition-inference-architecture-direct-connect.drawio-5.png)

*Hình 3: Kiến trúc tổng quan tùy chọn Direct Connect - từng phân vùng nối Direct Connect về mạng khách hàng, nơi định tuyến tới Bedrock ở phân vùng thương mại*

---

## Chọn Kết Nối Phù Hợp

| Tiêu chí | Public Endpoint | Site-to-Site VPN | Direct Connect |
|----------|-----------------|------------------|----------------|
| **Thời gian triển khai** | Vài tuần | Vài tuần (IaC) | Vài tuần/tháng |
| **Độ phức tạp** | Thấp | Trung bình | Cao |
| **Bảo mật** | TLS qua internet | VPN mã hóa | Đường riêng tư |
| **Hiệu năng** | Tốt | Tốt | Cao nhất (SLA) |
| **Chi phí** | Thấp | Trung bình | Cao |

### Lưu ý quan trọng

1. **Dữ liệu đi kèm prompt** sẽ truyền tới dịch vụ Amazon Bedrock ở phân vùng thương mại — nghĩa là dữ liệu và ngữ cảnh đi ra khỏi GovCloud (US). Các tổ chức phải kiểm tra quy trình phù hợp quy định bảo mật.

2. **Chi phí truyền dữ liệu:** lưu lượng đi qua phân vùng sẽ tính phí egress ở cả tài khoản GovCloud (US) lẫn thương mại.

3. **Chọn đường kết nối** không phải là bắt đầu đơn giản rồi nâng cấp, mà nên chọn khớp với chính sách bảo mật và loại dữ liệu gửi sang Bedrock ngay từ đầu.

---

## Kết luận

Suy luận xuyên phân vùng là giải pháp **an toàn và mở rộng** cho khách hàng AWS GovCloud (US) tận dụng ngay các mô hình AI mới nhất ở phân vùng thương mại. Bằng cách kết hợp mạng qua internet, VPN hoặc Direct Connect, tổ chức có thể dùng Bedrock ở phân vùng thương mại từ GovCloud (US) nếu hợp quy định và kiểm soát rủi ro.

Kiến trúc này cho phép các tổ chức vận hành trên GovCloud (US) với dữ liệu nhạy cảm vẫn có thể thử nghiệm, đổi mới với AI hiện đại ngay khi vừa ra mắt ở phân vùng thương mại — **cân bằng giữa đổi mới và kiểm soát an toàn, tuân thủ nghiêm ngặt.**



**TAGS:** [Artificial Intelligence](https://aws.amazon.com/blogs/publicsector/tag/artificial-intelligence/), [AWS GovCloud (US)](https://aws.amazon.com/blogs/publicsector/tag/aws-govcloud-us/), [AWS Public Sector](https://aws.amazon.com/blogs/publicsector/tag/aws-public-sector/), [Government](https://aws.amazon.com/blogs/publicsector/tag/government/), [Technical How-to](https://aws.amazon.com/blogs/publicsector/tag/technical-how-to/)
