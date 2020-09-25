# Tài liệu hướng dẫn cài đặt mail kerio trên cụm OPVZ

- Login vào control bằng đường link: https://103.28.37.228:5656/admincp

- Giao diện control

    ![Imgur](https://imgur.com/532Dioq.png)

- Chọn Add Virtual Server

    ![Imgur](https://imgur.com/10rElEV.png)

- Chọn OpenVZ

    ![Imgur](https://imgur.com/xo4hyby.png)

- Chọn node và plan, sau đó click vào tiếp tục

    ![Imgur](https://imgur.com/0tEwWpo.png)

- Chọn host name, temp, và IP cho mail kerio

    ![Imgur](https://imgur.com/LdU2dT2.png)

- Chọn các thông số cho mail kerio

    ![Imgur](https://imgur.com/e69cfOJ.png)

- Click chọn Create Virtual Server

    ![Imgur](https://imgur.com/csPVO3K.png)

- Sau khi Create, hệ thống sẽ tự động chuyển trang và trả về các thông tin quản trị

    ![Imgur](https://imgur.com/7YHz1fn.png)

- Đợi một lúc để hệ thống setup, sau đó SSH vào mail kerio vừa tạo, tắt một số dịch vụ bằng các câu lệnh:

    ```
    service iptables stop
    
    service httpd stop
    
    systemctl disable httpd
    
    service sendmail stop
    
    systemctl disable sendmail

    ```

-  Truy cập mail kerio bằng đường link: http://IP:4040 để tiến hành setup mail.

    ![Imgur](https://imgur.com/HUZ1yD4.png)

- ![Imgur](https://imgur.com/goCrfvW.png)

- ![Imgur](https://imgur.com/5DSfrdO.png)

Ở bước này các bạn lưu ý, hostname sẽ là mail.domain, email domain sẽ là domain.

- ![Imgur](https://imgur.com/CbvBhNA.png)

- ![Imgur](https://imgur.com/caEeFx3.png)

- ![Imgur](https://imgur.com/ZXB6EBN.png)

- ![Imgur](https://imgur.com/rUjSC6J.png)

- ![Imgur](https://imgur.com/5REDqs3.png)

- ![Imgur](https://imgur.com/bYuo795.png)

- ![Imgur](https://imgur.com/GELkZrB.png)

- ![Imgur](https://imgur.com/WCtvSJi.png)