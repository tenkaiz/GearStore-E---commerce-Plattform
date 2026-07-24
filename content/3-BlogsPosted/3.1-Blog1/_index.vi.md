---
title: "Blog 1"
date: 2026-07-09
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Tìm hiểu chuyển đổi dự phòng thông minh với AWS Lambda@Edge và Amazon DynamoDB: Giữ ứng dụng luôn sẵn sàng khi sự cố xảy ra

Trong quá trình tìm hiểu về các dịch vụ bảo mật trên AWS, mình đã đọc bài viết *"Intelligent failover using AWS Lambda@Edge and Amazon DynamoDB"*.

Khi xây dựng các ứng dụng hiện đại trên AWS, chúng ta thường quan tâm đến hiệu năng, khả năng mở rộng và bảo mật. Tuy nhiên, một câu hỏi quan trọng không kém là: **điều gì sẽ xảy ra nếu Region hoặc một cụm dịch vụ mà ứng dụng đang sử dụng bất ngờ gặp sự cố?**

Trong nhiều hệ thống, đặc biệt là thương mại điện tử, ngân hàng, SaaS hay chăm sóc sức khỏe, việc người dùng không thể truy cập dịch vụ chỉ trong vài phút cũng có thể gây ra thiệt hại lớn. Không chỉ vậy, nếu người dùng bị chuyển sang Region khác nhưng mất phiên đăng nhập hoặc bị điều hướng không nhất quán, trải nghiệm sử dụng sẽ bị ảnh hưởng đáng kể.

Để giải quyết bài toán này, AWS giới thiệu một kiến trúc kết hợp giữa **AWS Lambda@Edge** và **Amazon DynamoDB**, cho phép định tuyến người dùng thông minh ngay tại Edge, duy trì mối liên kết giữa người dùng và Region đang phục vụ, đồng thời hỗ trợ chuyển đổi dự phòng (Failover) nhanh chóng khi xảy ra sự cố.

![Sơ đồ kiến trúc Intelligent Failover](/images/3-BlogsPosted/blog1.jpg "Sơ đồ kiến trúc chuyển đổi dự phòng thông minh với AWS Lambda@Edge và Amazon DynamoDB")

---

### Tại sao giải pháp này lại cần thiết?
Trong các kiến trúc Multi-Region truyền thống, doanh nghiệp thường sử dụng DNS hoặc Amazon Route 53 để chuyển hướng lưu lượng khi một Region gặp sự cố. Tuy nhiên, cách tiếp cận này vẫn còn nhiều hạn chế.

Ví dụ, người dùng có thể bị chuyển sang Region mới nhưng mất thông tin phiên, phải đăng nhập lại hoặc bị định tuyến đến một máy chủ khác trong mỗi lần gửi yêu cầu. Điều này đặc biệt bất lợi đối với những ứng dụng cần duy trì tính liên tục của phiên làm việc.

Để khắc phục vấn đề này, doanh nghiệp thường phải tự xây dựng cơ chế lưu trữ phiên, đồng bộ dữ liệu giữa các Region và phát triển hệ thống định tuyến riêng. Đây là quá trình khá phức tạp, tốn nhiều chi phí vận hành và khó đảm bảo tính nhất quán khi hệ thống mở rộng.

Chính vì vậy, AWS đề xuất kết hợp **Lambda@Edge** và **DynamoDB** để xử lý việc định tuyến ngay tại Edge, giúp giảm độ trễ và đơn giản hóa kiến trúc.

---

### Giải pháp hoạt động như thế nào?
Kiến trúc này tận dụng **Amazon CloudFront** làm lớp tiếp nhận mọi yêu cầu từ người dùng trên toàn cầu.

1. Khi một yêu cầu được gửi đến CloudFront, hàm **Lambda@Edge** sẽ được kích hoạt tại Regional Edge Cache gần người dùng nhất để kiểm tra thông tin phiên hoặc cookie.
2. Nếu người dùng đã được gắn với một Region trước đó, yêu cầu sẽ tiếp tục được chuyển đến đúng Region đó nhằm đảm bảo tính nhất quán trong suốt phiên làm việc.
3. Ngược lại, nếu đây là lần truy cập đầu tiên, Lambda@Edge sẽ lựa chọn một Region phù hợp theo chiến lược định tuyến đã cấu hình (có thể là ngẫu nhiên hoặc theo thuật toán riêng). Sau khi phản hồi từ ứng dụng được trả về, hệ thống sẽ tạo hoặc cập nhật Session ID, lưu thông tin Region tương ứng vào cookie của trình duyệt và đồng thời ghi dữ liệu này vào Amazon DynamoDB.

Nhờ đó, trong các lần truy cập tiếp theo, người dùng luôn được định tuyến đến đúng Region đã được gán mà không cần thực hiện thêm các thao tác xử lý phức tạp.

---

### DynamoDB đóng vai trò gì?
Một điểm quan trọng của giải pháp là sử dụng **Amazon DynamoDB** làm kho lưu trữ trạng thái định tuyến. DynamoDB lưu các thông tin như:
- Session ID hoặc User ID.
- Region hoặc Endpoint đã được gán.
- Trạng thái định tuyến của người dùng.
- Cấu hình Endpoint phục vụ.

Đặc biệt, khi sử dụng **DynamoDB Global Tables**, dữ liệu sẽ được đồng bộ giữa nhiều AWS Region. Điều này đồng nghĩa với việc nếu Region chính gặp sự cố, Lambda@Edge ở bất kỳ vị trí nào cũng có thể truy cập bản sao dữ liệu gần nhất để xác định Region dự phòng phù hợp mà không cần sử dụng các cơ chế đồng bộ dữ liệu riêng.

---

### Chuyển đổi dự phòng diễn ra như thế nào?
Một trong những điểm nổi bật của kiến trúc này là khả năng xử lý sự cố gần như theo thời gian thực.

- Khi hệ thống phát hiện Region đang phục vụ người dùng không còn khả dụng, Lambda@Edge sẽ kiểm tra dữ liệu trong DynamoDB để tìm Endpoint hoặc Region còn hoạt động.
- Sau đó, yêu cầu sẽ được chuyển hướng sang Region mới mà không cần thay đổi ứng dụng phía người dùng.
- Toàn bộ quá trình diễn ra chỉ trong vài mili giây nhờ việc Lambda@Edge thực thi ngay tại Edge và dữ liệu định tuyến đã được đồng bộ sẵn trên DynamoDB.

Điều mình đánh giá cao là việc chuyển đổi này diễn ra rất mượt mà. Người dùng hầu như không nhận thấy hệ thống đã chuyển sang một Region khác, giúp giảm tối đa gián đoạn trong quá trình sử dụng.

---

### Không chỉ phục vụ Failover
Mặc dù mục tiêu chính là tăng khả năng phục hồi của hệ thống, kiến trúc này còn phù hợp với nhiều kịch bản khác:
- Thực hiện **A/B Testing** bằng cách định tuyến một nhóm người dùng đến Region hoặc Endpoint riêng.
- Triển khai kiến trúc **Cell-Based Architecture** để phân tách lưu lượng giữa các cụm dịch vụ.
- Duy trì **Session Affinity** cho các ứng dụng yêu cầu người dùng luôn làm việc với cùng một máy chủ hoặc cùng một Region.
- Phân phối lưu lượng theo nhiều chiến lược khác nhau tùy vào nhu cầu doanh nghiệp.

Nhờ việc toàn bộ logic được xử lý tại Edge, các thay đổi về định tuyến có thể được áp dụng rất nhanh mà không ảnh hưởng đến ứng dụng phía sau.

---

### Hiệu năng và khả năng mở rộng
Một ưu điểm đáng chú ý là Lambda@Edge thực thi ngay tại các Regional Edge Cache của CloudFront thay vì chuyển toàn bộ yêu cầu về Region gốc, giúp giảm đáng kể độ trễ khi xử lý.

Ngoài ra, Lambda@Edge chỉ được kích hoạt đối với các yêu cầu cần xử lý động, chẳng hạn như kiểm tra phiên hoặc xác thực người dùng. Các tài nguyên tĩnh như hình ảnh, CSS hay JavaScript vẫn được CloudFront phục vụ trực tiếp từ bộ nhớ đệm, giúp tối ưu chi phí và hiệu năng.

Trong khi đó, DynamoDB được thiết kế để cung cấp thời gian phản hồi chỉ vài mili giây ngay cả khi xử lý lượng truy cập rất lớn, phù hợp với các ứng dụng có hàng triệu người dùng.

---

### Việc triển khai có hoàn toàn tự động?
**Không hoàn toàn.**  
AWS cung cấp sẵn các dịch vụ nền tảng như CloudFront, Lambda@Edge và DynamoDB, nhưng doanh nghiệp vẫn cần tự xây dựng logic định tuyến phù hợp với hệ thống của mình.

Ngoài ra, nhóm kỹ thuật cũng cần chuẩn bị:
- Chiến lược xác định Region hoặc Endpoint phù hợp.
- Health Check để phát hiện Region gặp sự cố.
- Cơ chế giám sát trạng thái dịch vụ.
- Quy tắc chuyển đổi dự phòng.
- Triển khai ứng dụng trên nhiều Region nếu muốn đảm bảo khả năng sẵn sàng cao.

---

### Góc nhìn cá nhân & Kết luận
Theo mình, đây là một kiến trúc rất đáng tham khảo đối với các hệ thống yêu cầu tính sẵn sàng cao và phục vụ người dùng trên phạm vi toàn cầu.

Điều mình thích ở giải pháp này là AWS không cố gắng xây dựng một cơ chế định tuyến "đóng", mà cung cấp các thành phần linh hoạt để doanh nghiệp có thể tự thiết kế chiến lược phù hợp với nhu cầu của mình. Việc kết hợp Lambda@Edge với DynamoDB cũng cho thấy lợi thế của mô hình serverless. Thay vì phải vận hành các máy chủ chuyên trách cho việc định tuyến hoặc quản lý phiên, toàn bộ logic có thể được triển khai dưới dạng dịch vụ được quản lý, vừa giảm chi phí vận hành vừa tăng khả năng mở rộng.

* **Link bài viết trên Facebook nhóm AWS Study Group VN:** [Xem bài viết trên Facebook](https://www.facebook.com/share/p/1DAnbdHiR8/)