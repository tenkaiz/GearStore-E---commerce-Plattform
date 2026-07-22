---
title: "Worklog Tuần 6"
date: 2026-07-20
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

# Worklog Tuần 6 (08/06/2026 – 14/06/2026)

#### 1. Mục tiêu công việc
- Nghiên cứu AWS Serverless Java Container.
- Tìm hiểu cơ chế Request/Response Mapping giữa Spring Boot và AWS Lambda.
- Phân tích quy trình xử lý của ứng dụng Serverless.

#### 2. Chi tiết công việc thực hiện trong tuần
Trong tuần này, em tập trung nghiên cứu thư viện **AWS Serverless Java Container**, một thành phần quan trọng giúp tích hợp ứng dụng **Spring Boot** với **AWS Lambda**. Em tìm hiểu cách các yêu cầu HTTP từ **Amazon API Gateway** được chuyển đổi thành **Servlet Request** để Spring Boot có thể xử lý như một ứng dụng web thông thường. Đồng thời, em phân tích cơ chế **Request/Response Mapping**, quá trình khởi tạo **Application Context** của Spring Boot và luồng xử lý yêu cầu từ AWS Lambda đến các Controller của ứng dụng. Bên cạnh đó, em thực hành phân tích kiến trúc và vòng đời hoạt động của ứng dụng Java theo mô hình Serverless.

#### 3. Bảng phân công & Tiến độ chi tiết

| Thứ | Nội dung công việc thực hiện | Trạng thái | Nguồn tài liệu |
| :---: | :--- | :---: | :--- |
| **Thứ 2** | Nghiên cứu kiến trúc AWS Serverless Java Container | Complete | AWS Documentation |
| **Thứ 3** | Tìm hiểu cơ chế Request/Response Mapping giữa API Gateway và Spring Boot | Complete | AWS Serverless Java Container Documentation |
| **Thứ 4** | Phân tích quá trình khởi tạo Spring Boot trên AWS Lambda | Complete | Spring Boot Documentation |
| **Thứ 5** | Nghiên cứu luồng xử lý yêu cầu trong ứng dụng Serverless | Complete | Project Source Code |
| **Thứ 6** | Ôn tập kiến trúc và hoàn thành các bài thực hành | Complete | AWS Academy Lab |

#### 4. Kết quả đạt được
- **Hoàn thành**: Nắm vững kiến trúc AWS Serverless Java Container, cơ chế Request/Response Mapping và quy trình tích hợp giữa AWS Lambda với Spring Boot.
- **Kỹ năng tích lũy**: Nâng cao kiến thức về kiến trúc Java Serverless, cơ chế hoạt động của API Gateway, quy trình khởi tạo Spring Boot trên AWS Lambda và luồng xử lý yêu cầu trong ứng dụng Serverless.