1. API & RESTful API
   API là giao diện cho phép các hệ thống giao tiếp và trao đổi dữ liệu với nhau.
   REST là kiểu kiến trúc thiết kế dựa trên giao thức HTTP, API tuân thủ chuẩn này gọi là RESTful API.
   Cơ chế hoạt động: Client gửi HTTP Request đến server, server xử lý tài nguyên và trả về HTTP Response.
   Các ràng buộc của REST (Constraints): Stateless, Client-Server, Cacheable, Uniform Interface, Layered System.
   Ưu & Nhược điểm: Dễ mở rộng, linh hoạt, độc lập nền tảng nhưng dễ gặp over/under-fetching dữ liệu.

   // Minh họa định danh tài nguyên chuẩn RESTful:
   GET    /api/v1/users       // Lấy danh sách người dùng
   POST   /api/v1/users       // Tạo mới người dùng
   DELETE /api/v1/users/102   // Xóa người dùng có ID 102


2. Request & Response
   Cấu trúc giao tiếp hai chiều giữa Client và Server:
   HTTP Methods: GET (lấy dữ liệu), POST (tạo mới), PUT/PATCH (cập nhật), DELETE (xóa).
   Resource names & URL: Dùng danh từ số nhiều để định danh tài nguyên (ví dụ: /users, /products).
   Request structure: Gồm URL, Method, Headers (metadata), Params/Body (dữ liệu gửi đi).
   Response structure: Gồm Status code (2xx, 4xx, 5xx), Headers, Response Body (dữ liệu trả về).
   Content types: Định dạng nội dung trao đổi qua header Content-Type (phổ biến nhất là application/json).

   // Minh họa Request - Response:
   // Request: POST /api/v1/users
   // Headers: { "Content-Type": "application/json" }
   // Body: { "name": "Ngọc", "role": "developer" }

   // Response: 201 Created
   // Body: { "id": 1, "name": "Ngọc", "role": "developer" }


3. API Authentication
   Cơ chế định danh và cấp quyền truy cập để bảo vệ tài nguyên API:
   HTTP Basic: Gửi trực tiếp username:password đã mã hóa Base64 qua header (đơn giản, bảo mật thấp).
   JWT (JSON Web Token): Token mã hóa phi trạng thái (Stateless) gồm Header.Payload.Signature, kiểm tra quyền nhanh.
   OAuth (1.0 & 2.0): Giao thức ủy quyền (Authorization) bên thứ ba; OAuth 2.0 dùng Access Token và Refresh Token.

   // Gửi xác thực qua Header Authorization:
   // Basic:  Authorization: Basic dXNlcjpwYXNzd29yZA==
   // JWT:    Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...


4. API Documentation
   Tài liệu kỹ thuật hướng dẫn chi tiết cách thức sử dụng và tích hợp API.
   Thông tin bắt buộc phải có:
     - URL & HTTP Method
     - Request Data (tên trường, kiểu dữ liệu, mô tả bắt buộc/tùy chọn)
     - Authentication (quy định token/header xác thực)
     - Request Headers (ví dụ: Content-Type)
     - Response Example (mẫu dữ liệu trả về và mã trạng thái)
   Lý do cần viết: Tăng độ nhận diện, hỗ trợ người dùng tích hợp nhanh, giảm chi phí hỗ trợ và dễ bảo trì nội bộ.


5. API Tools & Templates
   Các giải pháp chuẩn hóa quy trình phát triển và kiểm thử API:
   API Design Template: Mẫu thiết kế đặc tả API thống nhất quy chuẩn cho toàn đội ngũ phát triển.
   Postman: Công cụ gửi request, kiểm thử API tự động, quản lý biến môi trường và mock data.
   Swagger (OpenAPI): Bộ công cụ định nghĩa đặc tả chuẩn và tự động tạo giao diện tài liệu tương tác trực quan.