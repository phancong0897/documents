# Tổng quan về POP. IMAP, SMTP

### 1. POP Post Office Porotocol version 3
### Cách thức hoạt động của POP:
- Kết nối với máy chủ ( server )
- Lấy lại được tất cả các mail
- Lưu trữ cục bộ dưới dạng mail mới
- Xóa mail khỏi máy chủ (server)
- Ngắt kết nối.
### Ưu nhược điểm của POP
- Nhược điểm : Mỗi lần nhận mail, POP sẽ tải lá mail đó về máy tính cục bộ của người dùng (và mặc định xóa mail đó trên máy chủ ), và giao thức này hoạt động hoàn toàn độc lập nên bạn sẽ không thể sử dụng nhiều thiết bị để quản lý cùng một tài khoản email qua giao thức POP
- Ưu điểm : POP có những ưu điểm như sau :
    - Mail lưu trữ cục bộ, tức là có thể truy cập bất cứ lúc nào ngay cả khi không có kết nối Internet.
	- Kết nối Internet chỉ dùng để gửi và nhận mail.
	- Tiết kiệm không gian lưu trữ trên server.
	- Được lựa chọn để lại bản sao mail trên server.
	- Hợp nhất nhiều tài khoản email và nhiều server vào một hộp thư đến
- Mặc định, port POP3 là:
	- Port 110 – port không mã hóa
	- Port 995 – SSL/TLS port, cũng có thể được gọi là POP3S
	
### 2. IMAP Internet Message Access Protocol
### Cách thức hoạt động của IMAP:
- Kết nối với máy chủ (server).
- Đồng bộ với máy chủ, lấy nội dung được yêu cầu từ người dùng và lưu đệm cục bộ (chẳng hạn như danh sách mail mới, tổng kết tin nhắn hay nội dung của những email được chọn lựa kỹ càng)
- Xử lý các thao tác của người dùng, chẳng hạn như đánh dấu email đã đọc, xóa email,…
- Ngắt kết nối.
### Ưu nhược điểm của IMAP
- Nhược điểm : Vì IMAP lưu các email trên mail server, nên dung lượng hòm thư của bạn sẽ bị giới hạn bởi các nhà cung cấp dịch vụ mail. Nếu bạn có một lượng lớn email cần lưu trữ, bạn sẽ gặp nhiều vấn đề khi gửi nhận mail khi hòm thư bị đầy. IMAP sẽ không thể lưu trữ dữ liệu của bạn trên máy tính cục bộ. Ngoài ra, nếu sử dụng IMAP thì bạn cần phải có kết nối Internet nếu muốn truy cập email.
- Ưu điểm : IMAP có những ưu điểm sau :
	- IMAP được tao ra để cho phép người dùng truy cập từ xa email lưu trữ trên một server.
	- Cho phép nhiều máy khách hay người dùng quản lý cùng một hộp thư đến.
	- Vì vậy, khi đăng nhập máy tính công ty, cá nhân, thiết bị di động sẽ luôn thấy cùng email và cấu trúc thư mục do chúng được lưu trên server và tất cả những thay đổi bạn tạo ra với các bản sao cục bộ ngay lập tức được đồng bộ với server.
	- Xem nhanh hơn khi chỉ có các tiêu đề mail được tải về đến khi nội dung được yêu cầu rõ ràng.
	- Mail được dự phòng tự động trên server.
	- Tiết kiệm không gian lưu trữ cục bộ.
- Port IMAP mặc định:
	- Port 143 – port không mã hóa
	- Port 993 – SSL/TLS port, cũng có thể được gọi là IMAPS

### SMTP Simple Mail Transfer Porotocol
- SMTP (Simple Mail Transfer Protocol) là giao thức chuẩn TCP/IP được dùng để truyền tải thư điện tử (e-mail) trên mạng internet.
- Các port mặc định của SMTP:
	- Port 25 – port không mã hóa
	- Port 465/587 – SSL/TLS port, cũng có thể được gọi là SMTPS.