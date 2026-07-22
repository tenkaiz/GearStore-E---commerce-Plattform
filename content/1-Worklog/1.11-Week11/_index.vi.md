---
title: "Worklog Tuần 11"
date: 2026-07-20
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

# Worklog Tuần 11 (13/07/2026 – 19/07/2026)

#### 1. Mục tiêu công việc
- Cấu hình **maven-shade-plugin** để tối ưu quá trình đóng gói ứng dụng.
- Loại bỏ các thư viện không cần thiết trong gói triển khai.
- Tạo file **backend-0.0.1-SNAPSHOT.jar** tối ưu nhằm giảm thời gian **AWS Lambda Cold Start**.

#### 2. Chi tiết công việc thực hiện trong tuần
Trong tuần này, em tập trung tối ưu quá trình đóng gói ứng dụng Backend GearStore trước khi triển khai lên AWS Lambda. Em cấu hình **maven-shade-plugin** để tạo file JAR thực thi có kích thước nhỏ gọn hơn bằng cách loại bỏ các thư viện không cần thiết và xử lý các tài nguyên bị trùng lặp. Sau khi hoàn thành quá trình đóng gói, em tạo file **backend-0.0.1-SNAPSHOT.jar**, kiểm tra cấu trúc và xác minh toàn bộ dependency đã được tích hợp đầy đủ. Đồng thời, em đánh giá kích thước của file JAR và áp dụng các biện pháp tối ưu nhằm giảm thời gian **Cold Start**, từ đó cải thiện hiệu năng của ứng dụng khi chạy trên AWS Lambda.

#### 3. Bảng phân công & Tiến độ chi tiết

| Thứ | Nội dung công việc thực hiện | Trạng thái | Nguồn tài liệu |
| :---: | :--- | :---: | :--- |
| **Thứ 2** | Cấu hình **maven-shade-plugin** để tối ưu đóng gói | Complete | Apache Maven Documentation |
| **Thứ 3** | Loại bỏ các thư viện dư thừa và tài nguyên trùng lặp | Complete | IntelliJ IDEA |
| **Thứ 4** | Tạo file **backend-0.0.1-SNAPSHOT.jar** | Complete | Maven |
| **Thứ 5** | Kiểm tra kích thước JAR và xác minh các dependency | Complete | Project Source Code |
| **Thứ 6** | Rà soát gói triển khai và đánh giá khả năng tối ưu Cold Start | Complete | AWS Documentation |

#### 4. Kết quả đạt được
- **Hoàn thành**: Cấu hình thành công **maven-shade-plugin**, tạo file **backend-0.0.1-SNAPSHOT.jar** tối ưu, loại bỏ các thư viện không cần thiết và xác minh gói triển khai trước khi đưa lên AWS Lambda.
- **Kỹ năng tích lũy**: Nâng cao kỹ năng tối ưu quá trình đóng gói ứng dụng Java bằng Maven, quản lý dependency hiệu quả, tạo Executable JAR chất lượng và cải thiện hiệu năng triển khai ứng dụng Serverless trên AWS Lambda.