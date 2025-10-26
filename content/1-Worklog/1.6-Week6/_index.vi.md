---
title: "Worklog Tuần 6"
date: "2025-09-11"
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 6:

* Hoàn thành khóa học AWS Security and Cost Management trên DataCamp.
* Hiểu AWS Shared Responsibility Model và tầm quan trọng của bảo mật cloud.
* Tìm hiểu về governance, compliance và yêu cầu pháp lý.
* Khám phá các công cụ tự động hóa bảo mật và compliance của AWS (Security Hub, Trusted Advisor, GuardDuty).
* Áp dụng nguyên tắc least privilege cho IAM users, groups và roles.
* Bảo mật mạng sử dụng VPC, NACLs, security groups và AWS WAF.
* Triển khai bảo mật compute và data với encryption, Security Groups và quản lý credentials.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 1   | - Hoàn thành Chương 1: Foundation Security & Governance <br>&emsp; + AWS Shared Responsibility Model <br>&emsp; + Tại sao bảo mật cloud quan trọng <br>&emsp; + Trách nhiệm của khách hàng vs AWS | 13/10/2025   | 13/10/2025      | DataCamp - Khóa học AWS Security |
| 2   | - Tiếp tục Chương 1: <br>&emsp; + Compliance và governance <br>&emsp; + Các quy định (Sarbanes-Oxley, GDPR) <br>&emsp; + Các chức năng governance (identify, detect, protect, respond, recover) | 13/10/2025   | 13/10/2025      | DataCamp - Khóa học AWS Security |
| 3   | - Tiếp tục Chương 1: <br>&emsp; + Tổng quan AWS Security Hub <br>&emsp; + AWS Trusted Advisor <br>&emsp; + Phát hiện mối đe dọa GuardDuty <br>&emsp; + So sánh các công cụ tự động hóa bảo mật | 14/10/2025   | 14/10/2025      | DataCamp - Khóa học AWS Security |
| 4   | - Hoàn thành Chương 2: Identity and Access Management <br>&emsp; + Nguyên tắc least privilege (5 bước) <br>&emsp; + Bảo vệ root user, MFA <br>&emsp; + Bảo mật user và group <br>&emsp; + Quản lý credentials (Secrets Manager) | 14/10/2025   | 14/10/2025      | DataCamp - Khóa học AWS Security |
| 5   | - Tiếp tục Chương 2: <br>&emsp; + IAM users vs roles (ai, gì, ở đâu) <br>&emsp; + Policies và permissions <br>&emsp; + IAM Identity Center <br>&emsp; + Gán roles cho tài nguyên compute | 15/10/2025   | 15/10/2025      | DataCamp - Khóa học AWS Security |
| 6   | - Hoàn thành Chương 3: Network Security <br>&emsp; + Cơ bản về networking (subnets, networks, routers) <br>&emsp; + Virtual Private Cloud (VPC) <br>&emsp; + Bảo mật VPC (5 bước) <br>&emsp; + So sánh NACL vs Security Group vs AWS WAF | 15/10/2025   | 15/10/2025      | DataCamp - Khóa học AWS Security |
| 7   | - Tiếp tục Chương 3: <br>&emsp; + AWS Marketplace cho các giải pháp bảo mật <br>&emsp; + AWS Firewall Manager <br>&emsp; + VPC flow logs | 16/10/2025   | 16/10/2025      | DataCamp - Khóa học AWS Security |
| 8   | - Hoàn thành Chương 4: Compute and Data Security <br>&emsp; + Bảo mật EC2 (SSH keys, patches, security groups) <br>&emsp; + Security Groups vs NACLs <br>&emsp; + Mã hóa data at-rest (S3, EBS) <br>&emsp; + Bảo vệ S3 public access | 16/10/2025   | 16/10/2025      | DataCamp - Khóa học AWS Security |
| 9   | - Tiếp tục Chương 4 và Cost Optimization: <br>&emsp; + AWS KMS để quản lý encryption keys <br>&emsp; + Glacier cho archival storage <br>&emsp; + Disaster recovery (versioning, replication) <br>&emsp; + Trusted Advisor recommendations để tối ưu chi phí | 17/10/2025   | 17/10/2025      | DataCamp - Khóa học AWS Security |
| 10  | - Thực hành với AWS Sandbox: <br>&emsp; + Kích hoạt Security Hub và xem security findings <br>&emsp; + Cấu hình IAM users và groups với least privilege <br>&emsp; + Tạo và gắn IAM roles cho EC2 instances <br>&emsp; + Xem Trusted Advisor recommendations | 18/10/2025   | 18/10/2025      | AWS Sandbox Account |


### Kết quả đạt được tuần 6:

* Hiểu tại sao bảo mật cloud quan trọng:
  * Vi phạm dữ liệu gây mất lòng tin khách hàng, thu hồi giấy phép trong các ngành được quy định, và hậu quả tài chính
  * Từ 2018-2022, FBI nhận khiếu nại tội phạm mạng với tổng thiệt hại 27,6 tỷ USD tại Mỹ
  * Các công ty lớn lưu trữ dữ liệu nhạy cảm của khách hàng (dữ liệu tài chính, sức khỏe) cần kiểm soát truy cập phù hợp

* AWS Shared Responsibility Model và governance:
  * Bảo mật cloud là trách nhiệm chung giữa AWS và khách hàng (tương tự mối quan hệ chủ nhà-người thuê)
  * Trách nhiệm AWS: an ninh vật lý data centers, thiết bị, networking, nguồn dự phòng, phần mềm hạ tầng, redundancy
  * Trách nhiệm khách hàng cho dịch vụ hạ tầng: operating systems, security ứng dụng, mã hóa dữ liệu, kiểm soát truy cập, cập nhật server
  * Trách nhiệm thay đổi theo loại dịch vụ: serverless services (Lambda, Glue) chuyển nhiều trách nhiệm hơn sang AWS
  * Framework cloud governance bao gồm: Identify tài nguyên quan trọng, Detect các bất thường, Protect tài nguyên quan trọng, Lập kế hoạch phản hồi sự cố, Quy trình phục hồi

* AWS compliance và quy định:
  * Governance đảm bảo chiến lược doanh nghiệp, hành vi đạo đức, quản lý rủi ro và compliance
  * Quy định toàn cầu: Sarbanes-Oxley (công ty công khai ở Mỹ), GDPR (bảo vệ dữ liệu người tiêu dùng ở Châu Âu)
  * Security Hub: tự động kiểm tra tài nguyên AWS theo best practices bảo mật, tìm cấu hình sai, findings định dạng chuẩn
  * AWS Shield: bảo vệ khỏi các cuộc tấn công DDoS
  * CloudWatch: cho phép giám sát liên tục tự động cho các hoạt động bất thường và độc hại

* Các công cụ tự động hóa bảo mật và compliance AWS:
  * Security Hub: dashboard tập trung về security posture, tổng hợp alerts từ 60+ dịch vụ bảo mật AWS, hỗ trợ remediation qua Lambda
  * Trusted Advisor: giám sát best practices cho tối ưu chi phí, hiệu suất hệ thống, độ tin cậy và lỗ hổng bảo mật
  * GuardDuty: dịch vụ phát hiện mối đe dọa theo dõi hoạt động độc hại (hoạt động độc lập, không ảnh hưởng hiệu suất tài nguyên)
  * Inspector: quản lý vulnerability tự động, liên tục quét AWS workloads để tìm software vulnerabilities
  * CloudTrail: cho phép auditing, security monitoring và troubleshooting vận hành bằng cách theo dõi user activity và API usage

* Triển khai nguyên tắc least privilege:
  * Nguyên tắc cốt lõi: cấp cho users và systems bộ quyền hẹp nhất để hoàn thành nhiệm vụ được yêu cầu
  * Chiến lược năm bước:
    1. Bắt đầu với điều khiển bảo mật coarse-grained (chặn public access ở cấp Organization)
    2. Áp dụng điều khiển fine-grained cho nhu cầu truy cập cụ thể
    3. Sử dụng accounts như boundaries cho security administration
    4. Ưu tiên short-term credentials qua AWS Security Token Service (STS)
    5. Thực thi invariants rộng (ví dụ: hạn chế khu vực cho hoạt động kinh doanh)
  * Cân bằng: ngăn chặn hành động nguy hiểm trong khi cho phép đổi mới và tốc độ

* Framework bảo mật tài khoản:
  * Bảo mật root user: mật khẩu mạnh, xác thực đa yếu tố, tránh tạo access keys, email nhóm, phê duyệt nhiều người
  * Users & groups: bật MFA cho tất cả IAM users, sử dụng groups cho permissions nhất quán, xoay passwords và access keys thường xuyên
  * Tài nguyên computing: sử dụng IAM roles cho virtual machines, Systems Manager cho cấu hình và quản lý patch
  * Bảo mật credentials: sử dụng AWS Secrets Manager cho database credentials và API keys với automatic rotation, tích hợp với các dịch vụ AWS khác

* Nền tảng Identity and Access Management (IAM):
  * Ai: Principals (users với long-term credentials HOẶC roles với short-term credentials qua STS)
  * Gì: Policies (tài liệu văn bản chỉ định principals và resources được ủy quyền)
  * Ở đâu: AWS Organizations (các đơn vị tổ chức như production, development, test)
  * IAM Identity Center: tạo hoặc kết nối workforce users, quản lý tập trung quyền truy cập vào nhiều AWS accounts
  * Hỗ trợ single sign-on cho Office 365 và các work accounts khác

* Bảo mật mạng trong AWS:
  * Cơ bản networking: subnets (máy tính kết nối), networks (subnets kết nối), routers (định tuyến traffic), route tables (ánh xạ địa chỉ)
  * Virtual Private Cloud (VPC): mạng ảo với subnets, route tables, firewall, DNS
  * Năm bước để bảo mật VPC: loại subnet phù hợp, tách biệt môi trường, tạo NACLs, tạo firewall/AWS WAF, tạo VPC flow logs
  * So sánh NACL vs Security Group vs AWS WAF: NACL (stateless, cấp subnet, miễn phí), Security Groups (stateful, cấp instance, miễn phí), WAF (stateful, cấp application, trả phí)
  * AWS Marketplace: tìm, mua, triển khai phần mềm bảo mật của bên thứ ba (ví dụ: Cisco, Juniper Networks)

* Bảo mật compute và data:
  * Bảo mật data in-transit (mạng) và data at-rest (ổ cứng)
  * Bảo mật EC2: sử dụng SSH keys thay vì passwords, cập nhật OS với patches mới nhất, điều khiển traffic với security groups, gán IAM roles để loại bỏ lưu trữ credentials
  * Security Groups: virtual firewall cho EC2 instances, stateful (ghi nhớ trạng thái kết nối), cho phép outbound theo mặc định
  * Security Groups vs NACLs: Security Groups cho phép fine-grained traffic đến các máy chủ riêng lẻ, stateful và cho phép outbound theo mặc định; NACLs áp dụng cho toàn bộ subnets và stateless
  * Encryption data at-rest: sử dụng AWS Key Management Service (KMS), hỗ trợ S3 và EBS
  * Bảo mật S3: tắt public access, sử dụng versioning, Glacier cho archival storage, replication cho disaster recovery
  * Glacier: lưu trữ archive được xây dựng trên S3, tối ưu hóa cho khối lượng lớn và thời gian truy xuất không thường xuyên/chậm hơn
  * AWS Knowledge Center: câu trả lời cho các câu hỏi thường gặp của khách hàng
  * Security blog: deep-dives vào best practices, tính năng mới, hướng dẫn cách sử dụng

* Thực hành với AWS Sandbox:
  * Kích hoạt Security Hub và xem security findings
  * Tạo IAM users và groups với permissions least privilege
  * Tạo và gắn IAM roles cho EC2 instances
  * Xem Trusted Advisor recommendations để tối ưu chi phí

### Tóm tắt / Ghi chú

Tuần này hoàn thành khóa học AWS Security and Cost Management toàn diện trên DataCamp. Khóa học cung cấp hiểu biết sâu sắc về nền tảng bảo mật cloud, governance và best practices:

**Điểm chính:**

1. **Bảo mật Cloud là quan trọng**: Vi phạm dữ liệu có thể gây mất lòng tin khách hàng, thu hồi giấy phép và thiệt hại tài chính. FBI báo cáo tổn thất liên quan đến tội phạm mạng là 27,6 tỷ USD từ 2018-2022 chỉ riêng tại Mỹ.

2. **Shared Responsibility Model**: Bảo mật là trách nhiệm chung. AWS quản lý hardware, infrastructure và data centers ("Security OF the cloud"). Khách hàng quản lý operating systems, applications, data encryption và access controls ("Security IN the cloud"). Phân chia này giống như mối quan hệ chủ nhà-người thuê.

3. **Framework Governance**: Cloud governance đảm bảo chiến lược doanh nghiệp, hành vi đạo đức, quản lý rủi ro và compliance. Năm chức năng: Identify, Detect, Protect, Respond và Recover. Quy định quan trọng bao gồm Sarbanes-Oxley (Mỹ) và GDPR (Châu Âu).

4. **Security Automation Tools**: AWS cung cấp nhiều công cụ chuyên biệt. Security Hub cung cấp dashboard tập trung tổng hợp alerts từ 60+ services. Trusted Advisor giám sát cost, performance và security. GuardDuty phát hiện mối đe dọa. Inspector quét tìm vulnerabilities. CloudTrail theo dõi user activity để auditing.

5. **Nguyên tắc Least Privilege**: Cấp bộ quyền hẹp nhất cần thiết cho công việc. Năm bước: coarse-grained controls, fine-grained exceptions, account boundaries, short-lived credentials (STS) và enforce invariants.

6. **Account Security**: Bảo vệ root user bằng MFA và mật khẩu mạnh. Bật MFA cho tất cả IAM users. Sử dụng groups cho permissions. Ưu tiên roles hơn long-term credentials cho computing resources. Sử dụng Secrets Manager để quản lý credentials an toàn.

7. **Network Security**: Hiểu các thành phần VPC (subnets, route tables, firewalls, DNS). Triển khai bảo mật VPC thông qua loại subnet phù hợp, tách biệt môi trường, NACLs, firewalls/WAF và flow logs. So sánh NACLs (stateless, subnet-level, miễn phí) vs Security Groups (stateful, instance-level, miễn phí) vs WAF (application-level, trả phí).

8. **Compute and Data Security**: Bảo mật EC2 với SSH keys, OS patches và Security Groups. Sử dụng encryption at-rest với KMS cho keys. Bảo vệ S3 buckets bằng cách tắt public access. Triển khai disaster recovery với versioning, Glacier cho archival và replication.

**Ứng dụng thực tế**: 
Thực hành với tài khoản AWS Sandbox để kích hoạt Security Hub, cấu hình IAM với least privilege, gắn roles cho EC2 instances và xem Trusted Advisor recommendations để tối ưu chi phí (xác định idle load balancers và tài nguyên không sử dụng).

**Giảng viên khóa học**: Dev Bhosale (Cloud & Data Professional, DataCamp Instructor)

Tài liệu tham khảo:
- DataCamp: Khóa học AWS Security and Cost Management
- AWS Security Hub Documentation
- AWS Trusted Advisor Documentation
- AWS IAM Documentation
- AWS VPC Documentation

