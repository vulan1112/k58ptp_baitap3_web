<img width="1657" height="376" alt="image" src="https://github.com/user-attachments/assets/db4786f3-c65f-4490-b4e8-6fdc17691b13" /># k58ptp_baitap3_web
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

 ** 4.1 Web thương mại điện tử.**
 - Tạo web dạng Single Page Application (SPA), chỉ gồm 1 file index.html, toàn bộ giao diện do javascript sinh động.
 - Có tính năng login, lưu phiên đăng nhập vào cookie và session

<img width="1920" height="1073" alt="image" src="https://github.com/user-attachments/assets/43edb7b8-bb44-4320-9cca-de68cf04dae8" />

<img width="1861" height="740" alt="image" src="https://github.com/user-attachments/assets/0fbc978d-ac7e-4ccc-b168-7316799e4ca4" />

 <img width="1920" height="1009" alt="image" src="https://github.com/user-attachments/assets/20948851-3465-47f1-9d73-1d1919faeddc" />

 Thông tin login lưu trong cơ sở dữ liệu của mariadb, được dev quản trị bằng phpmyadmin, yêu cầu sử dụng mã hoá khi gửi login.
 Chỉ cần login 1 lần, bao giờ logout thì mới phải login lại.

  - Có tính năng liệt kê các nhóm sản phẩm

<img width="1214" height="501" alt="image" src="https://github.com/user-attachments/assets/a01fc746-ce95-4292-b2d0-4861ffbffc17" />

<img width="1798" height="666" alt="image" src="https://github.com/user-attachments/assets/505ee993-ae6f-432b-be0d-b7b70367184e" />

- Có tính năng liệt kê các sản phẩm bán chạy ra trang chủ

<img width="1351" height="927" alt="image" src="https://github.com/user-attachments/assets/63047ba0-0c4a-4aa4-816c-cd9fa1ba9cb9" />

<img width="1183" height="550" alt="image" src="https://github.com/user-attachments/assets/94db348a-6fec-4140-bb37-b212ef5a09df" />

- Có tính năng liệt kê sản phẩm theo nhóm

<img width="1099" height="428" alt="image" src="https://github.com/user-attachments/assets/b0c58682-6a70-46a3-8bcf-89ba16b4ab50" />

<img width="1589" height="748" alt="image" src="https://github.com/user-attachments/assets/1fd9f6c2-656a-4dc2-bd58-d0239661985c" />

- Có tính năng tìm kiếm sản phẩm

<img width="1240" height="458" alt="image" src="https://github.com/user-attachments/assets/60f32205-c121-42b6-a13d-720dae157110" />

<img width="1913" height="951" alt="image" src="https://github.com/user-attachments/assets/adf906ce-dc79-4def-a883-b50231706950" />

- Có tính năng chọn sản phẩm (đưa sản phẩm vào giỏ hàng, thay đổi số lượng sản phẩm trong giỏ, cập nhật tổng tiền)

<img width="1292" height="784" alt="image" src="https://github.com/user-attachments/assets/9c80ab1d-936e-4e61-9972-a3a9d306993b" />

<img width="1895" height="540" alt="image" src="https://github.com/user-attachments/assets/732ecbdc-8110-4a80-8992-f1982391686f" />

 - Có tính năng đặt hàng, nhập thông tin giao hàng => được 1 đơn hàng.

<img width="1918" height="1080" alt="image" src="https://github.com/user-attachments/assets/cd10504a-45dc-4018-9971-898d8c0c5588" />

<img width="1911" height="1076" alt="image" src="https://github.com/user-attachments/assets/68f3a4a8-a1d0-411e-aa38-50acc06c0b37" />

<img width="1920" height="1061" alt="image" src="https://github.com/user-attachments/assets/ac0c6051-752d-40c2-a37a-65c3b823a3f6" />

<img width="1903" height="988" alt="image" src="https://github.com/user-attachments/assets/2b03c431-ab7b-47ed-9db3-e82ee244dc35" />

<img width="1886" height="406" alt="image" src="https://github.com/user-attachments/assets/e1053034-f629-4605-8bea-adc372652fbb" />

<img width="1690" height="866" alt="image" src="https://github.com/user-attachments/assets/a19a7f10-5ba4-494b-89c1-581685cef8c2" />

- Có tính năng dành cho admin: Thống kê xem có bao nhiêu đơn hàng, call để xác nhận và cập nhật thông tin đơn hàng. chuyển cho bộ phận đóng gói, gửi bưu điện, cập nhật mã COD, tình trạng giao hàng, huỷ hàng,...

<img width="1897" height="741" alt="image" src="https://github.com/user-attachments/assets/680f59e9-9d13-4c40-a433-f78744b765e3" />

<img width="1329" height="725" alt="image" src="https://github.com/user-attachments/assets/280f7c26-aae4-4532-ae5a-d77ddba31c67" />

- Có tính năng dành cho admin: biểu đồ thống kê số lượng mặt hàng bán được trong từng ngày. (sử dụng grafana)

<img width="1860" height="1080" alt="image" src="https://github.com/user-attachments/assets/21384672-8eff-48fa-9a87-4c447563ead7" />

<img width="1526" height="979" alt="image" src="https://github.com/user-attachments/assets/a14026ee-b2bb-4138-ad64-f261815a929e" />

**5. Nginx làm web-server**

 - Cấu hình nginx để chạy được website qua url http://fullname.com  (thay fullname bằng chuỗi ko dấu viết liền tên của bạn)

<img width="1657" height="376" alt="image" src="https://github.com/user-attachments/assets/44f0d742-611b-4198-a895-7069cdd535fa" />

 - Cấu hình nginx để http://fullname.com/nodered truy cập vào nodered qua cổng 80, (dù nodered đang chạy ở port 1880)

<img width="1872" height="500" alt="image" src="https://github.com/user-attachments/assets/5a3bce85-25e0-4614-9895-bee1c160fbfa" />

 - Cấu hình nginx để http://fullname.com/grafana truy cập vào grafana qua cổng 80, (dù grafana đang chạy ở port 3000)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/25d3a558-63ca-461b-927a-71dda320e10a" />

