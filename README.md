# k58ptp_baitap3_web
VU LAN_K225480106036_môn Phát triển ứng dụng trên nền web
Bài tập 3   : môn Phát triển ứng dụng trên nền web
Giảng viên  : Đỗ Duy Cốp
Lớp học phần: 58KTPM
Ngày giao   : 2025-10-24 13:50
Hạn nộp     : 2025-11-05 00:00
--------------------------------------------------
Yêu cầu     : LẬP TRÌNH ỨNG DỤNG WEB trên nền linux
1. Cài đặt môi trường linux: SV chọn 1 trong các phương án
 - enable wsl: cài đặt docker desktop
 - enable wsl: cài đặt ubuntu
 - sử dụng Hyper-V: cài đặt ubuntu
 - sử dụng VMware : cài đặt ubuntu
 - sử dụng Virtual Box: cài đặt ubuntu
2. Cài đặt Docker (nếu dùng docker desktop trên windows thì nó có ngay)
3. Sử dụng 1 file docker-compose.yml để cài đặt các docker container sau: 
   mariadb (3306), phpmyadmin (8080), nodered/node-red (1880), influxdb (8086), grafana/grafana (3000), nginx (80,443)
4. Lập trình web frontend+backend:
 SV chọn 1 trong các web sau:
 4.1 Web thương mại điện tử
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
 - Có tính năng liệt kê các sản phẩm bán chạy ra trang chủ
 - Có tính năng liệt kê các nhóm sản phẩm
 - Có tính năng liệt kê sản phẩm theo nhóm
 - Có tính năng tìm kiếm sản phẩm
 - Có tính năng chọn sản phẩm (đưa sản phẩm vào giỏ hàng, thay đổi số lượng sản phẩm trong giỏ, cập nhật tổng tiền)
 - Có tính năng đặt hàng, nhập thông tin giao hàng => được 1 đơn hàng.
 - Có tính năng dành cho admin: Thống kê xem có bao nhiêu đơn hàng, call để xác nhận và cập nhật thông tin đơn hàng. chuyển cho bộ phận đóng gói, gửi bưu điện, cập nhật mã COD, tình trạng giao hàng, huỷ hàng,...
 - Có tính năng dành cho admin: biểu đồ thống kê số lượng mặt hàng bán được trong từng ngày. (sử dụng grafana)
 - backend: sử dụng nodered xử lý request gửi lên từ javascript, phản hồi về json.
 4.2 Web IOT: Giám sát dữ liệu IOT.
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session
   Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
   Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.
 - hiển thị giá trị mới nhất của các thông số đang giám sát, khi click vào thì hiển thị đồ thị lịch sử quá trình thay đổi (gọi grafana iframe để hiển thị)
 - backend: Sử dụng nodered để đọc dữ liệu từ các cảm biến (có thể dùng api online để lấy dữ liệu theo giời gian thực), 
   nodered sẽ lưu dữ liệu mới nhất (dạng update) vào cơ sở dữ liệu mariadb (sử dụng phpmyadmin để tạp table và quản trị lần đầu)
   nodered sẽ lưu dữ liệu (insert) vào influxdb để lưu giá trị lịch sử, để cho grafana dùng để hiển thị biểu đồ.
5. Nginx làm web-server
 - Cấu hình nginx để chạy được website qua url http://fullname.com  (thay fullname bằng chuỗi ko dấu viết liền tên của bạn)
 - Cấu hình nginx để http://fullname.com/nodered truy cập vào nodered qua cổng 80, (dù nodered đang chạy ở port 1880)
 - Cấu hình nginx để http://fullname.com/grafana truy cập vào grafana qua cổng 80, (dù grafana đang chạy ở port 3000)

## BÀI LÀM

# 1.Cài đặt môi trường linux: enable wsl: cài đặt docker desktop

<img width="1919" height="1080" alt="image" src="https://github.com/user-attachments/assets/fac15cad-81c1-4b02-a3ae-e83f06d3bdb2" />

# 2. Cài đặt Docker (nếu dùng docker desktop trên windows thì nó có ngay)
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6f9cc01d-5a10-412c-b242-78bdb8b76d8e" />

# 3. Sử dụng 1 file docker-compose.yml để cài đặt các docker container sau: 
   mariadb (3306), phpmyadmin (8080), nodered/node-red (1880), influxdb (8086), grafana/grafana (3000), nginx (80,443)

<img width="1713" height="676" alt="image" src="https://github.com/user-attachments/assets/58c7b81a-f204-4d7a-b484-0f154b1f28ef" />

*nginx (80,443)*
<img width="1915" height="1080" alt="image" src="https://github.com/user-attachments/assets/df2b743d-8f43-4ae7-87cd-d168a5f0e5ee" />

*grafana/grafana (3000)*
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/264b020e-3e82-4f19-8208-bccb6265cd2f" />

 *mariadb (3306)*
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6d5afbf1-9a27-4373-a5a4-447a11aa2fa2" />

*influxdb (8086)*
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bc5ed0f4-78ba-4021-99a8-70c3f4d4e42e" />

*nodered/node-red (1880)*
<img width="1920" height="1078" alt="image" src="https://github.com/user-attachments/assets/79b376a6-7732-4c38-9813-2d0c50964073" />

# 4. Lập trình web frontend+backend:

 **4.2 Web IOT: Giám sát dữ liệu IOT.**
   Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
   
