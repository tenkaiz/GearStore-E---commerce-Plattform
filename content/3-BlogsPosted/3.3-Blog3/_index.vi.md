---
title: "Blog 3"
date: 2026-07-18
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# How Stratasys built an IoT platform for industrial 3D printers with AWS IoT

Trong những năm gần đây, công nghệ in 3D đã không còn chỉ phục vụ cho việc tạo mẫu sản phẩm mà đã trở thành một phần quan trọng trong nhiều ngành công nghiệp như hàng không, ô tô, y tế và sản xuất hàng tiêu dùng. Tuy nhiên, khi số lượng máy in 3D tăng lên và được triển khai tại nhiều nhà máy khác nhau, doanh nghiệp bắt đầu đối mặt với một bài toán mới: làm thế nào để quản lý, giám sát và khai thác hiệu quả toàn bộ hệ thống máy in theo thời gian thực?

Nếu mỗi máy hoạt động như một hệ thống độc lập, dữ liệu sẽ bị phân tán, việc theo dõi tình trạng thiết bị trở nên khó khăn và quá trình bảo trì chủ yếu dựa trên việc xử lý sự cố sau khi đã xảy ra. Điều này không chỉ làm giảm hiệu suất vận hành mà còn ảnh hưởng trực tiếp đến năng suất sản xuất.

Để giải quyết những thách thức đó, Stratasys đã hợp tác với AWS xây dựng **GrabCAD IoT Platform** – một nền tảng IoT kết nối từ thiết bị biên (Edge) đến đám mây (Cloud). Nền tảng này sử dụng **AWS IoT Core** và **AWS IoT Greengrass** để thu thập, chuẩn hóa và phân tích dữ liệu từ các máy in 3D công nghiệp, tạo nền tảng cho việc tối ưu vận hành cũng như phát triển các tính năng AI trong tương lai.

![Sơ đồ kiến trúc GrabCAD IoT Platform](/images/3-BlogsPosted/blog3.jpg "Sơ đồ kiến trúc kết nối máy in 3D công nghiệp với AWS IoT")

---

### Tại sao nền tảng IoT này lại cần thiết?
Khi doanh nghiệp sở hữu hàng chục hoặc hàng trăm máy in 3D tại nhiều địa điểm khác nhau, việc quản lý thủ công gần như không còn khả thi.

Trước đây, dữ liệu từ từng máy thường được lưu trữ riêng lẻ, khiến doanh nghiệp khó theo dõi tình trạng thiết bị theo thời gian thực hoặc đánh giá hiệu quả vận hành của toàn bộ hệ thống. Đội ngũ kỹ thuật cũng gặp nhiều khó khăn trong việc phát hiện sớm các dấu hiệu bất thường. Phần lớn chỉ có thể xử lý khi máy đã gặp lỗi, làm tăng thời gian ngừng hoạt động và giảm hiệu quả sử dụng thiết bị (Overall Equipment Effectiveness – OEE).

Bên cạnh đó, môi trường sản xuất công nghiệp còn đặt ra những yêu cầu nghiêm ngặt về bảo mật giữa hệ thống công nghệ vận hành (OT) và công nghệ thông tin (IT). Việc kết nối dữ liệu lên đám mây cần đảm bảo an toàn nhưng vẫn đủ linh hoạt để tích hợp với các hệ thống quản lý như MES hoặc ERP.

Chính vì vậy, Stratasys cần một nền tảng IoT vừa có khả năng xử lý dữ liệu tại Edge, vừa đảm bảo kết nối an toàn với AWS Cloud và hỗ trợ mở rộng trong tương lai.

---

### GrabCAD IoT Platform hoạt động như thế nào?
Nền tảng GrabCAD IoT Platform được xây dựng theo mô hình **Edge-to-Cloud**:

- Tại nhà máy, **AWS IoT Greengrass** chạy trên các thiết bị Gateway đặt cạnh máy in 3D. Dịch vụ này giúp xử lý dữ liệu ngay tại Edge trước khi gửi lên đám mây. Việc xử lý cục bộ mang lại nhiều lợi ích như giảm băng thông truyền tải, giảm chi phí và vẫn đảm bảo hệ thống tiếp tục hoạt động ngay cả khi mất kết nối Internet.
- Sau khi được xử lý, dữ liệu sẽ được truyền đến **AWS IoT Core**, đóng vai trò là cổng kết nối bảo mật giữa các thiết bị và hệ thống Cloud. AWS IoT Core hỗ trợ giao tiếp hai chiều theo giao thức MQTT, giúp Stratasys vừa có thể theo dõi tình trạng thiết bị theo thời gian thực, vừa gửi các lệnh điều khiển hoặc cập nhật phần mềm từ xa.
- Một điểm đáng chú ý là nền tảng sử dụng **Device Shadow** để lưu trữ trạng thái số của từng máy in. Nhờ đó, ngay cả khi thiết bị tạm thời ngoại tuyến, hệ thống vẫn có thể duy trì thông tin trạng thái mới nhất và đồng bộ lại khi kết nối được khôi phục.

---

### Chuẩn hóa dữ liệu để tạo nền tảng cho AI
Để dữ liệu từ nhiều dòng máy khác nhau có thể được phân tích thống nhất, Stratasys sử dụng chuẩn công nghiệp **MTConnect**. Thông qua chuẩn này, các thông tin như trạng thái máy, dữ liệu cảm biến, mã lỗi và mức độ sử dụng thiết bị đều được chuẩn hóa trước khi lưu trữ.

Sau đó, dữ liệu được chuyển vào **Amazon S3 Data Lake** thông qua các dịch vụ AWS, tạo nền tảng cho nhiều mục đích khác nhau như:
- Theo dõi hiệu suất thiết bị.
- Phân tích hoạt động sản xuất.
- Đáp ứng yêu cầu kiểm toán.
- Huấn luyện các mô hình Machine Learning trong tương lai.

Việc chuẩn hóa dữ liệu ngay từ đầu giúp doanh nghiệp dễ dàng tích hợp với các hệ thống MES, ERP hoặc các công cụ phân tích dữ liệu khác.

---

### Những lợi ích mà nền tảng mang lại
Đối với khách hàng sử dụng máy in Stratasys, nền tảng GrabCAD IoT Platform mang lại nhiều cải thiện đáng kể:
- Nhờ khả năng giám sát theo thời gian thực, doanh nghiệp có thể nhanh chóng phát hiện các dấu hiệu bất thường, giảm thời gian ngừng hoạt động và nâng cao hiệu quả sử dụng thiết bị (OEE).
- Dịch vụ giám sát từ xa **ARMS** cũng giúp phát hiện lỗi trước khi chúng gây ảnh hưởng đến sản xuất, đồng thời **rút ngắn khoảng 38% thời gian xử lý sự cố** so với phương pháp hỗ trợ truyền thống.
- Bên cạnh đó, việc hỗ trợ cập nhật phần mềm OTA (Over-the-Air) giúp các bản vá bảo mật và tính năng mới được triển khai nhanh chóng mà không cần kỹ sư đến trực tiếp nhà máy.

Đối với Stratasys, việc thu thập dữ liệu từ toàn bộ hệ thống máy in còn giúp hãng hiểu rõ hơn cách khách hàng sử dụng sản phẩm trong thực tế. Các dữ liệu đã được ẩn danh sẽ được sử dụng để cải tiến phần cứng, phần mềm và phát triển những tính năng mới phù hợp hơn với nhu cầu của doanh nghiệp.

---

### Không chỉ là giám sát thiết bị
Điều mình đánh giá cao là GrabCAD IoT Platform không chỉ dừng lại ở việc kết nối máy in với Cloud. Nền tảng này còn được xây dựng như một cơ sở hạ tầng dữ liệu phục vụ cho các ứng dụng AI trong tương lai.

Theo kế hoạch của Stratasys, các tính năng đang được phát triển bao gồm:
- Bộ lập lịch in thông minh sử dụng AI.
- Thị giác máy tính để kiểm tra chất lượng sản phẩm theo thời gian thực.
- Bảo trì dự đoán (Predictive Maintenance).
- Phân tích nguyên nhân lỗi tự động.
- Quản lý vật tư và linh kiện bằng AI.
- Điều khiển quy trình in theo vòng lặp khép kín (Closed-loop Process Control).

Những tính năng này sẽ giúp hệ thống không chỉ thu thập dữ liệu mà còn có khả năng tự tối ưu hoạt động và đưa ra quyết định gần như theo thời gian thực.

---

### Việc triển khai có đơn giản không?
**Không hoàn toàn.**  
AWS đã cung cấp đầy đủ các thành phần quan trọng như AWS IoT Core, AWS IoT Greengrass và Amazon S3. Tuy nhiên, để xây dựng được một nền tảng IoT công nghiệp hoàn chỉnh, doanh nghiệp vẫn cần chuẩn hóa dữ liệu từ thiết bị, thiết kế kiến trúc Edge phù hợp, đảm bảo an toàn giữa hệ thống OT và IT, cũng như tích hợp với các hệ thống quản lý hiện có.

Đây là lý do Stratasys hợp tác với **GreenCustard** – đối tác AWS chuyên về các giải pháp IoT – nhằm đảm bảo quá trình triển khai diễn ra an toàn và hiệu quả.

---

### Góc nhìn cá nhân & Kết luận
Theo mình, giá trị lớn nhất của GrabCAD IoT Platform không nằm ở việc kết nối máy in với Internet mà ở việc biến dữ liệu vận hành thành tài sản chiến lược của doanh nghiệp.

Khi toàn bộ dữ liệu từ các máy in được chuẩn hóa và tập trung trên một nền tảng duy nhất, doanh nghiệp có thể dễ dàng phân tích hiệu suất, phát hiện xu hướng và xây dựng các ứng dụng AI nhằm tối ưu quy trình sản xuất. Điều mình thích ở kiến trúc này là AWS không chỉ cung cấp hạ tầng Cloud mà còn mang đến một hệ sinh thái IoT hoàn chỉnh, từ xử lý tại Edge, truyền dữ liệu bảo mật đến lưu trữ và phân tích trên đám mây.

* **Link bài viết trên Facebook nhóm AWS Study Group VN:** [Xem bài viết trên Facebook](https://www.facebook.com/share/p/19E1XeurX2/)