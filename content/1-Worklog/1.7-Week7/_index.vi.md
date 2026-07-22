---
title: "Worklog Tuần 7"
date: 2026-07-20
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

# Worklog Tuần 7 (15/06/2026 – 21/06/2026)

#### 1. Mục tiêu công việc
- Thực hành quy trình Build và Package ứng dụng bằng Maven.
- Cấu hình **maven-shade-plugin** để đóng gói toàn bộ thư viện phụ thuộc.
- Tạo file JAR phục vụ triển khai trên AWS Lambda.

#### 2. Chi tiết công việc thực hiện trong tuần
Trong tuần này, em tập trung nghiên cứu quy trình **Build** và **Package** ứng dụng Java bằng **Apache Maven**. Em tìm hiểu vòng đời (Lifecycle) của Maven bao gồm các giai đoạn **Compile**, **Test**, **Package** và **Install**. Đồng thời, em thực hành cấu hình **maven-shade-plugin** để đóng gói toàn bộ các thư viện phụ thuộc vào một file **Executable JAR**, đáp ứng yêu cầu triển khai trên AWS Lambda. Sau khi hoàn tất quá trình Build, em kiểm tra cấu trúc của file JAR, xác minh các thư viện đã được đóng gói đầy đủ và đảm bảo ứng dụng có thể sẵn sàng cho môi trường Serverless.

#### 3. Bảng phân công & Tiến độ chi tiết

| Thứ | Nội dung công việc thực hiện | Trạng thái | Nguồn tài liệu |
| :---: | :--- | :---: | :--- |
| **Thứ 2** | Nghiên cứu vòng đời Build và Package của Maven | Complete | Apache Maven Documentation |
| **Thứ 3** | Cấu hình **maven-shade-plugin** | Complete | Maven Plugin Documentation |
| **Thứ 4** | Build ứng dụng Spring Boot và tạo file Executable JAR | Complete | IntelliJ IDEA / Maven |
| **Thứ 5** | Kiểm tra các thư viện được đóng gói trong file JAR | Complete | Project Source Code |
| **Thứ 6** | Rà soát kết quả đóng gói và chuẩn bị triển khai AWS Lambda | Complete | AWS Documentation |

#### 4. Kết quả đạt được
- **Hoàn thành**: Cấu hình thành công **maven-shade-plugin**, tạo file Executable JAR và xác minh đầy đủ các thư viện cần thiết cho quá trình triển khai trên AWS Lambda.
- **Kỹ năng tích lũy**: Nâng cao kỹ năng sử dụng Apache Maven, quản lý Dependency, đóng gói ứng dụng Java thành Executable JAR và chuẩn bị môi trường triển khai theo kiến trúc Serverless trên AWS Lambda.