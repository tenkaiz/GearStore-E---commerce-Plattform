---
title: "Blog 2"
date: 2026-07-18
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Industrial Physical AI on AWS with Galeo Tech and Multiverse Computing

Khi nhắc đến AI, nhiều người thường nghĩ đến việc huấn luyện mô hình với dữ liệu lớn trên đám mây. Tuy nhiên, với các ngành như sản xuất, năng lượng, logistics hay chăm sóc sức khỏe, bài toán thực sự không chỉ nằm ở việc xây dựng một mô hình chính xác mà còn là làm thế nào để triển khai, vận hành và liên tục cập nhật mô hình đó trên hàng trăm hoặc hàng nghìn thiết bị biên (Edge Devices).

Trong môi trường công nghiệp, dữ liệu được tạo ra liên tục từ cảm biến, máy móc và dây chuyền sản xuất. Nếu việc thu thập dữ liệu không ổn định hoặc mô hình AI không thể triển khai hiệu quả trên phần cứng có tài nguyên hạn chế, giá trị của AI sẽ giảm đi đáng kể.

Để giải quyết bài toán này, AWS kết hợp với **Galeo Tech** và **Multiverse Computing** xây dựng một giải pháp AI vật lý (Physical AI) toàn diện. Trong đó, Galeo Tech chịu trách nhiệm xây dựng quy trình thu thập dữ liệu và MLOps từ thiết bị biên lên đám mây, còn Multiverse Computing tối ưu và nén mô hình AI để chúng có thể hoạt động hiệu quả trên các thiết bị công nghiệp.

![Sơ đồ kiến trúc Physical AI](/images/3-BlogsPosted/blog2.jpg "Sơ đồ kiến trúc vòng đời Industrial Physical AI trên AWS")

---

### Tại sao AI vật lý cần nhiều hơn một mô hình AI?
Trong nhiều dự án AI truyền thống, sau khi mô hình được huấn luyện thành công, công việc gần như đã hoàn tất. Tuy nhiên, với AI vật lý, đây mới chỉ là bước khởi đầu.

Các thiết bị công nghiệp thường hoạt động trong nhiều năm với điều kiện mạng không ổn định, tài nguyên phần cứng hạn chế và yêu cầu độ tin cậy rất cao. Điều này khiến việc cập nhật mô hình, quản lý phiên bản và đồng bộ dữ liệu trở thành một thách thức lớn.

Nếu không có quy trình MLOps phù hợp, mỗi lần nâng cấp mô hình đều có thể phải thực hiện thủ công trên từng thiết bị, gây tốn thời gian và tăng nguy cơ xảy ra lỗi. Đó là lý do AWS xây dựng một vòng đời AI khép kín, giúp dữ liệu và mô hình luôn được cập nhật liên tục giữa đám mây và hệ thống Edge.

---

### Galeo Tech giải quyết bài toán thu thập dữ liệu và MLOps như thế nào?
Galeo Tech tập trung vào việc kết nối giữa hệ thống vận hành công nghiệp (Operational Technology - OT) với nền tảng đám mây AWS.

Trong thực tế, dữ liệu có thể đến từ nhiều nguồn khác nhau như PLC, SCADA, OPC UA, MQTT hay Modbus. Những hệ thống này vốn không được thiết kế để phục vụ Machine Learning nên việc chuẩn hóa dữ liệu là bước rất quan trọng.

Thông qua các dịch vụ như **AWS IoT Core**, **AWS IoT Greengrass**, **AWS IoT SiteWise**, **Amazon Kinesis** và **Amazon S3**, dữ liệu từ nhà máy sẽ được thu thập, chuẩn hóa và lưu trữ vào Data Lake trên AWS. Ngay cả khi kết nối Internet bị gián đoạn, các Edge Gateway vẫn có thể lưu trữ dữ liệu cục bộ và tự động đồng bộ khi kết nối được khôi phục.

Ở chiều ngược lại, khi một phiên bản mô hình mới được đưa lên Amazon S3, **AWS Lambda** sẽ tự động xác định nhóm thiết bị cần cập nhật thông qua **Amazon DynamoDB**, đóng gói mô hình thành thành phần AWS IoT Greengrass và triển khai đến đúng nhóm thiết bị. Nhờ đó, doanh nghiệp có thể cập nhật mô hình AI cho hàng trăm hoặc hàng nghìn thiết bị mà không cần thao tác thủ công.

---

### Multiverse Computing giúp mô hình AI nhẹ hơn
Một vấn đề phổ biến của AI hiện nay là các mô hình ngày càng lớn. Trong khi đó, phần lớn thiết bị công nghiệp chỉ có CPU hoặc GPU với tài nguyên giới hạn. Nếu triển khai trực tiếp những mô hình này, tốc độ suy luận sẽ chậm, tiêu tốn nhiều bộ nhớ và điện năng.

Để giải quyết vấn đề đó, Multiverse Computing phát triển **CompactifAI**, công nghệ nén mô hình lấy cảm hứng từ mạng tensor và điện toán lượng tử. Không giống các phương pháp cắt tỉa hoặc lượng tử hóa truyền thống, CompactifAI phân tích cấu trúc bên trong mạng nơ-ron để loại bỏ những phần dư thừa nhưng vẫn giữ lại các thông tin quan trọng nhất.

Quy trình tối ưu bao gồm ba bước:
1. Phân tích cấu trúc mô hình.
2. Thực hiện nén bằng các thuật toán tối ưu.
3. Huấn luyện lại (healing) để khôi phục độ chính xác.

Theo các kết quả thử nghiệm của Multiverse Computing, CompactifAI có thể **giảm kích thước mô hình tới 80%**, **giảm chi phí suy luận từ 50–80%**, **tăng gấp đôi thông lượng xử lý** và giảm đáng kể mức tiêu thụ điện năng mà vẫn duy trì độ chính xác gần như không thay đổi. Đây là yếu tố rất quan trọng đối với các ứng dụng AI chạy trên robot, drone hay hệ thống sản xuất tự động.

---

### Một vòng đời AI hoàn chỉnh trên AWS
Điểm mình đánh giá cao trong giải pháp này là AWS không chỉ tập trung vào quá trình huấn luyện mô hình mà xây dựng toàn bộ vòng đời AI:

- Quy trình bắt đầu từ việc thu thập dữ liệu tại các thiết bị công nghiệp, sau đó dữ liệu được đưa lên Amazon S3 để phục vụ huấn luyện bằng **Amazon SageMaker**.
- Sau khi mô hình được tạo ra, CompactifAI sẽ tối ưu và nén trước khi lưu phiên bản mới lên Amazon S3.
- Tiếp theo, AWS Lambda, Amazon DynamoDB và AWS IoT Greengrass sẽ tự động triển khai mô hình đến từng nhóm thiết bị theo từng giai đoạn nhằm giảm rủi ro khi cập nhật.
- Cuối cùng, kết quả suy luận và dữ liệu vận hành sẽ tiếp tục được gửi ngược về Data Lake để phục vụ cho lần huấn luyện tiếp theo.

Nhờ vậy, toàn bộ hệ thống tạo thành một vòng lặp AI liên tục, trong đó dữ liệu giúp cải thiện mô hình và mô hình lại tạo ra dữ liệu mới để tiếp tục tối ưu.

---

### Không chỉ dành cho nhà máy sản xuất
Mặc dù ví dụ trong bài chủ yếu hướng đến sản xuất công nghiệp, kiến trúc này còn phù hợp với nhiều lĩnh vực khác như:
- Nhà máy thông minh (Smart Factory).
- Robot tự động.
- Drone công nghiệp.
- Hệ thống giám sát năng lượng.
- Chăm sóc sức khỏe.
- Logistics và kho thông minh.
- Thành phố thông minh (Smart City).

Điểm chung của các lĩnh vực này là đều yêu cầu xử lý dữ liệu ngay tại Edge với độ trễ thấp nhưng vẫn cần khả năng quản lý tập trung trên nền tảng đám mây.

---

### Việc triển khai có đơn giản không?
**Không hoàn toàn.**  
AWS đã cung cấp gần như đầy đủ các dịch vụ cần thiết như IoT Core, Greengrass, SageMaker, Lambda hay DynamoDB. Tuy nhiên, để triển khai thành công trong môi trường công nghiệp, doanh nghiệp vẫn cần giải quyết nhiều bài toán như tích hợp với hệ thống OT hiện có, chuẩn hóa dữ liệu, xây dựng quy trình MLOps và tối ưu mô hình cho từng loại phần cứng.

Đó cũng là lý do vai trò của các đối tác như Galeo Tech và Multiverse Computing trở nên rất quan trọng. Họ không thay thế các dịch vụ AWS mà bổ sung những thành phần chuyên biệt giúp doanh nghiệp rút ngắn thời gian triển khai và giảm đáng kể độ phức tạp của dự án.

---

### Góc nhìn cá nhân & Kết luận
Theo mình, điểm đáng chú ý nhất của giải pháp này không nằm ở một dịch vụ AWS riêng lẻ mà ở cách AWS kết nối toàn bộ vòng đời của AI vật lý thành một quy trình khép kín.

Trước đây, nhiều doanh nghiệp có thể xây dựng được mô hình AI tốt nhưng gặp khó khăn trong việc triển khai, cập nhật và vận hành trên hàng loạt thiết bị công nghiệp. Với kiến trúc này, AWS cùng các đối tác đã giúp tự động hóa gần như toàn bộ quá trình từ thu thập dữ liệu, huấn luyện, tối ưu mô hình cho đến triển khai và giám sát.

* **Link bài viết trên Facebook nhóm AWS Study Group VN:** [Xem bài viết trên Facebook](https://www.facebook.com/share/p/1Eat9Gbha2/)