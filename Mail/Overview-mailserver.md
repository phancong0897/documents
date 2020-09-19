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
![Imgur](https://i.imgur.com/iB8wuVe.png)

- Khi người gởi nhấp vào nút gởi , SMTP giúp đảm bảo chắc chắn là email được gởi từ server người gởi tới server người nhận . Khi email đến server người nhận MTA của server nhận sẽ tiếp nhận email của người gởi và chuyển nó cho MDA địa phương . MDA sau đó writes email vào mailbox của người nhận . Khi người nhận dùng MUA để kiểm tra email , MUA sẽ dùng giao thức POP hoặc IMAP để lấy mail về

- Sau đây là trình tự hoạt động của mail service trong thực tế :

    - Giả sử rằng userA@exampleA.tst đang cố gắng gửi một email tới userB@exampleB.tst

    - Các sự kiện sau đây sẽ xảy ra tuần tự khi người dùng gởi mail :

    ![Imgur](https://i.imgur.com/Tnb3OOa.png)

    - MUA của người gửi khởi tạo kết nối tới mail server mail.exampleA.tst bằng giao thức SMTP (thường là TCP Port 25).

    - Mail server mail.exampleA.tst nhận email và biết rằng domain đích cần gởi email tới là exampleB.tst . Server mail.exampleA.tst tạo ra một truy vấn đến máy chủ DNS để hỏi về thông tin record MX của domain exampleB.tst. Giả sử rằng không có thông tin về domain exampleB.tst trong bộ nhớ cache của máy chủ DNS .

    - Máy chủ DNS lần lượt tạo ra một truy vấn đệ quy đối với máy chủ DNS có thẩm quyền và tìm hiểu về chi tiết các record MX của domain exampleB.tst. Thông tin này sẽ được trả về cho server mail.exampleA.tst .

    - Bây giờ server mail.exampleA.tst đã có địa chỉ IP của mail server đích , nó sẽ gửi email trực tiếp tới mail server mail.exampleB.tst thông qua Internet. SMTP được sử dụng để liên lạc giữa các mail server nguồn và đích.

    - Email đến được nhận bởi SMTP (MTA) cục bộ trên server mail.exampleB.tst. Sau khi nhận được email, nó được chuyển cho MDA, sau đó gửi thư đến hộp thư của người nhận được lưu trữ trong máy chủ. Máy chủ có các hộp thư riêng biệt cho mỗi người dùng.

    - Khi người nhận kiểm tra email qua giao thức POP hoặc IMAP, email được MUA lấy từ máy chủ về máy tính của user . Tùy thuộc vào cấu hình MUA, email có thể được tải xuống trong máy trạm, bản sao có thể được lưu giữ trong cả máy chủ và máy trạm, hoặc email giữa máy chủ và MUA được đồng bộ hóa , tuỳ thuộc vào bạn chọn giao thức POP hay IMAP .

### 3. Các thuật ngữ thường đi kèm Mail Server

- Có khá nhiều những thuật ngữ đi kèm Mail Server. Dưới đây Mắt Bão sẽ điểm qua khái niệm của một số thuật ngữ thường gặp như:

    - TLS Mail Server : là bảo mật tầng truyền tải (Transport Layer Security). TLS hoạt động cùng với tầng ổ bảo mật SHL (Secure Sockets Layer). Mục đích chính cung cấp phương thức vận chuyển mã hoá cho đăng nhập được chứng thực của SASL.

    - SASL Mail Server: là lớp xác thực và bảo mật đơn giản (Simple Authentication and Security Layer). Để xác thực người dùng. SASL thực hiện xác thực, sau đó TLS cung cấp vận chuyển mã hoá dữ liệu xác thực.

    - Webmail: là email trên nền website. Một số webmail mà các bạn có thường thấy như hotmail, gmail, yahoo mail. Webmail cho phép người dùng truy cập email bất cứ lúc nào.

    - SMTP-IN Queue: Trước khi phân tán thư đến các Local queue hoặc Remote Queue, giao thức SMTP sẽ làm một thao tác sao lưu toàn bộ thư điện tử gửi đi từ email server của doanh nghiệp ở SMTP-IN Queue. Nói cách khác, SMTP-IN Queue chính là kho lưu trữ thông tin thư từ trước khi được gửi đi.

    - Local Queue: Sau khi tiếp nhận thông tin thư từ, hệ thống sẽ tự động điều phối phân loại và xếp thư từ theo thứ tự ngay hàng thẳng lối trước khi chuyến vào hộp thư của người nhận. Việc xếp hàng các bức thư chính là Local Queue.

    Để tăng cường khả năng bảo mật và giữ an toàn cho hệ thống email server, trước khi thư được gửi đến người dùng, local queue và remote queue sẽ tiến hành quét virut. Sau đó kiểm tra spam để chắc chắn về chất lượng thư gửi đi. Tránh trường hợp mail server bị các Blacklist liệt vào danh sách IP spam.

    - Local Mailboxes:  là hộp thư của các account có đăng kí tài khoản mail server của công ty.

    - Email Authentication: là tính năng xác nhận danh tính của các user khi truy cập vào hộp thư email. Tính năng này giúp bạn bảo mật thông tin thư từ của chính mình. Nói cách khác Alternate Email là một dạng email dự phòng. Khi quên mật khẩu của mail server, bạn có thể sử dụng email này để giúp bạn lấy lại mật khẩu một cách nhanh chóng.

    - Mail Exchanger Record (MX): có nhiệm vụ là chỉ đường cho email đi đến mail server của bạn. MX record thường đi kèm theo một A record sẽ trỏ về địa chỉ IP của mail server. Một thông số pref có giá trị số để chỉ ra mức độ ưu tiên của các mail server. Giá trị pref càng nhỏ thì mức độ ưu tiên càng cao.
