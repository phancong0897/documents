## Tổng quan về mail server

### 1. Mail Server là gì?

- Mail Server hay Email Server là hệ thống máy chủ được cấu hình riêng theo tên miền của doanh nghiệp dùng để gửi và nhận thư điện tử. Bên cạnh tính năng lưu trữ và sắp xếp các Email trên internet, Mail Server là một giao thức chuyên nghiệp để giao tiếp thư tín, quản lý và truyền thông nội bộ, giao dịch thương mại… Không chỉ thao tác với tốc độ nhanh chóng và ổn định, Mail Server còn đảm bảo tính an toàn với khả năng khôi phục dữ liệu cao. 

### 2. Cách thức hoạt động của mailserv

### 2.1 Các thuật ngữ
- Các thuật ngữ sau đây rất quan trọng trong việc tìm hiểu hoạt động của mail server

    - Mail User Agent (MUA): MUA là một thành phần tương tác trực tiếp với người dùng cuối . Ví dụ về MUA là phần mềm Thunderbird, MS Outlook, Zimbra Desktop. Các giao diện web mail như Gmail và Yahoo! cũng là MUA.

    - Mail Transfer Agent (MTA): MTA chịu trách nhiệm chuyển email từ mail server của người gởi thư đến mail server của người nhận thư. Ví dụ về MTA là sendmail và postfix.

    - Mail Delivery Agent (MDA): Trong một mail server nhận thư , local MTA chấp nhận một email đến từ MTA của người gởi . Email sau đó được gửi đến hộp thư của người dùng bởi MDA.

    - POP / IMAP: Giao thức POP và IMAP được sử dụng để tìm nạp email từ hộp thư của máy chủ người nhận tới MUA người nhận.

    - Mail Exchanger Record (MX): MX record có nhiệm vụ là chỉ đường cho email đi đến mail server của bạn ( MX record thường đi kèm theo một A record sẽ trỏ về địa chỉ IP của mail server , và một thông số pref có giá trị số để chỉ ra mức độ ưu tiên của các mail server , giá trị pref càng nhỏ thì mức độ ưu tiên càng cao )

### 2.2 Cách thức hoạt động
<img src="https://i.imgur.com/iB8wuVe.png">
