---
title: "Event 1"
date: 2026-05-23
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Bài Thu Hoạch Workshop: "Context Is Everything: Making AI Actually Work for You"

### 1. Thông Tin Tổng Quan Sự Kiện
- **Tên chủ đề**: *Context Is Everything: Making AI Actually Work for You* (Ngữ cảnh là tất cả: Làm sao để AI làm việc hiệu quả cho bạn).
- **Thời gian tổ chức**: Ngày 23/05/2026.
- **Diễn giả chính**: **Anh Tính Trương** - Platform Engineer tại **GoTymeX** (Đồng tổ chức bởi AWS Vietnam & AWS Study Group).
- **Đối tượng tham dự**: Hơn 200 sinh viên chuyên ngành Công nghệ Thông tin, Kỹ thuật Phần mềm và Đám mây từ các trường Đại học trên địa bàn TP.HCM (HUTECH, ĐH KHTN, Bách Khoa...).

---

### 2. Tóm Tắt Nội Dung Chuyên Môn

#### A. Bản chất của "Context" trong lập trình cùng AI
- **Nguyên nhân chính khiến AI phản hồi sai/lệch hướng**: Không phải do mô hình AI kém, mà do đầu vào (Prompt) bị **thiếu ngữ cảnh nền tảng**. AI giống như một lập trình viên mới gia nhập dự án — nếu không cung cấp tài liệu kiến trúc, nó sẽ tự suy đoán và dẫn đến hiện tượng "ảo tưởng" (Hallucination).
- **Công thức ngữ cảnh đầy đủ**:  
  $$\text{Context} = \text{Goal} + \text{Architecture Situation} + \text{Tech Constraints} + \text{Code Evidence}$$

#### B. Áp dụng Bộ khung Context Đơn giản (Simple Context Framework)
Diễn giả hướng dẫn cấu trúc thông tin 4 lề trước khi gửi yêu cầu cho AI:
1. **Goal (Mục tiêu)**: Nêu rõ kết quả mong muốn (VD: *Viết REST Controller xử lý upload ảnh sản phẩm lên AWS S3*).
2. **Relevant Info (Thông tin liên quan)**: Cung cấp đúng đoạn code DTO, DynamoDB Entity hoặc cấu hình `pom.xml`, lọc bỏ thông tin thừa.
3. **Constraints (Ràng buộc kỹ thuật)**: Quy định chặt chẽ phiên bản (Java 21, Spring Boot 3.3.0), thư viện (`software.amazon.awssdk:s3`), không thêm dependency gây nặng dung lượng file `.jar`.
4. **Success Criteria (Tiêu chí thành công)**: Kết quả mã nguồn phải đạt chuẩn Clean Code, bắt ngoại lệ `S3Exception` và có log rõ ràng.

#### C. Định hướng 4 Hướng Dự án AI thực tế cho Sinh viên
- **AI Code Reviewer**: Phân tích lỗi bảo mật, phát hiện memory leak và đề xuất refactor code backend.
- **RAG Document Q&A App**: Hỏi đáp thông tin dựa trên file tài liệu PDF giáo trình học tập.
- **Personal Knowledge Hub**: Hệ thống hóa ghi chú cá nhân và tra cứu nhanh tri thức lập trình.
- **Automated Test Generator**: Tự động sinh ra các kịch bản Unit Test cho REST API.

---

### 3. Góc Nhìn & Đánh Giá Cá Nhân

#### 💡 Thay đổi tư duy từ "Code Generator" sang "Context Engine"
- Trải nghiệm thực tế khi làm dự án **GearStore E-Commerce**: Trước khi tham gia sự kiện, em thường yêu cầu AI viết code một cách chung chung, dẫn đến việc mã nguồn sinh ra dùng AWS SDK v1 cũ hoặc dùng phiên bản Java 8 không tương thích với dự án Java 21 / Spring Boot 3 của em.
- Sau workshop, em nhận ra rằng **kỹ năng quản trị ngữ cảnh (Context Engineering)** chính là năng lực cốt lõi của kỹ sư Cloud tương lai. Việc làm chủ kiến trúc nền tảng (Spring Boot, DynamoDB, S3) mới giúp mình làm chủ được AI, tránh phụ thuộc thụ động.

---

### 4. Trải Nghiệm Thực Tế & Cảm Nhận Sự Kiện

- **Bầu không khí sự kiện**: Buổi workshop diễn ra vô cùng sôi nổi và hào hứng tại văn phòng AWS Vietnam. Không gian hiện đại, chuyên nghiệp cùng sự đón tiếp nhiệt tình từ Ban tổ chức FCAJ.
- **Kết quả thu hoạch**: Chuyến đi không chỉ mang lại kiến thức công nghệ mới mà còn giúp em mở rộng mạng lưới kết nối với các bạn sinh viên cùng đam mê Cloud & AI, đồng thời nhận được phần quà kỷ niệm ý nghĩa từ AWS Vietnam.

---

#### Hình ảnh tham gia sự kiện

![Sinh viên Vũ Hoàng Gia Huy tham dự sự kiện AWS]
