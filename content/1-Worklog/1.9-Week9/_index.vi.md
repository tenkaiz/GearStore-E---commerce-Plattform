---
title: "Worklog Tuần 9"
date: 2026-07-20
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

# Worklog Tuần 9 (29/06/2026 – 05/07/2026)

#### 1. Mục tiêu công việc
- Tích hợp thư viện **aws-serverless-java-container-springboot3**.
- Cấu hình dự án Maven phục vụ triển khai Serverless.
- Kiểm tra khả năng tương thích giữa Spring Boot 3 và AWS Lambda.

#### 2. Chi tiết công việc thực hiện trong tuần
Trong tuần này, em tập trung tích hợp thư viện **aws-serverless-java-container-springboot3** vào dự án Backend GearStore nhằm hỗ trợ triển khai ứng dụng Spring Boot trên AWS Lambda. Em tiến hành cấu hình các dependency cần thiết trong tệp **pom.xml**, đồng thời thiết lập môi trường để AWS Lambda có thể tiếp nhận và chuyển tiếp yêu cầu đến ứng dụng Spring Boot. Bên cạnh đó, em kiểm tra khả năng tương thích giữa Spring Boot 3 và AWS Lambda, đánh giá quá trình chuyển đổi Request/Response và đảm bảo ứng dụng có thể được đóng gói chính xác để triển khai theo kiến trúc Serverless.

#### 3. Bảng phân công & Tiến độ chi tiết

| Thứ | Nội dung công việc thực hiện | Trạng thái | Nguồn tài liệu |
| :---: | :--- | :---: | :--- |
| **Thứ 2** | Tích hợp thư viện **aws-serverless-java-container-springboot3** | Complete | AWS Documentation |
| **Thứ 3** | Cấu hình các dependency trong **pom.xml** | Complete | Apache Maven Documentation |
| **Thứ 4** | Thiết lập môi trường cho ứng dụng Serverless | Complete | IntelliJ IDEA |
| **Thứ 5** | Kiểm tra khả năng tương thích giữa Spring Boot 3 và AWS Lambda | Complete | AWS Lambda |
| **Thứ 6** | Rà soát kết quả tích hợp và chuẩn bị xây dựng Lambda Handler | Complete | Project Source Code |

#### 4. Kết quả đạt được
- **Hoàn thành**: Tích hợp thành công thư viện **aws-serverless-java-container-springboot3**, cấu hình đầy đủ các dependency cần thiết và xác minh khả năng tương thích giữa Spring Boot 3 với AWS Lambda.
- **Kỹ năng tích lũy**: Nâng cao kỹ năng tích hợp ứng dụng Java theo kiến trúc Serverless, quản lý dependency bằng Maven, triển khai Spring Boot trên AWS Lambda và đánh giá tính tương thích của hệ thống trước khi đưa vào vận hành.