## B. Cài đặt Ubuntu + Docker
### 1. Cài đặt hệ điều hành Ubuntu 24.04.4 LTS
- Cách cài đặt + sử dụng VirutualBox
  ### 🔽 Bước 1: Tải VirtualBox
- Truy cập trang chính thức: [https://www.virtualbox.org](https://www.virtualbox.org)
- Nhấn **Download**
- Chọn bản phù hợp:
  - **Windows hosts**
👉 File tải về dạng `.exe`
### ⚙️ Bước 2: Cài đặt VirtualBox
- Mở file vừa tải (double click)
- Nhấn **Next**
- Giữ mặc định các tùy chọn → **Next**
- Có thể hiện cảnh báo mạng → chọn **Yes**
- Nhấn **Install**
- Đợi cài xong → **Finish**
### 🔌 Bước 3: Cài Extension Pack (rất quan trọng)
👉 Giúp dùng USB, full màn hình, tăng hiệu năng
- Tải **VirtualBox Extension Pack** (cùng version)
- Mở VirtualBox → vào:
  - **File → Preferences → Extensions**
- Nhấn dấu ➕ → chọn file Extension Pack
- Nhấn **Install**
<img width="1904" height="987" alt="Untitled7" src="https://github.com/user-attachments/assets/02438053-eedf-48f1-afc8-5e711f44b2eb" />
🔹 Profile (tạo user giống đề)
👉 Nhập:
Your name: admin
Server name: ubuntu
Username: admin
Password: 123456 (hoặc tuỳ)
👉 Done
<img width="1278" height="840" alt="image" src="https://github.com/user-attachments/assets/a890be29-a702-471d-8765-2a9af46d963f" />
⏳ 4. Đợi cài
👉 Khoảng 10–15 phút
<img width="1288" height="818" alt="image" src="https://github.com/user-attachments/assets/1c51550b-6e65-45d5-b93e-47001e9d7af9" />
🔁 5. Khi xong
👉 Chọn:
Reboot Now
<img width="1286" height="792" alt="Untitled8" src="https://github.com/user-attachments/assets/f710a468-8a7d-4c45-8b78-0eccbf37ec68" />

🎯 Kết quả cần đạt
👉 Sau reboot sẽ thấy:
login:
👉 Đăng nhập:
user: admin
pass: đã đặt
<img width="1290" height="806" alt="Untitled9" src="https://github.com/user-attachments/assets/0d06bf38-1648-4506-9eb0-6196c6f4ba55" />
*sh tới ubuntu ở ip 192.168.1.19 - Login succes*
<img width="1290" height="806" alt="Untitled10" src="https://github.com/user-attachments/assets/b7c1f179-762e-43da-bdcb-83e0efdfcd06" />


### 2. Tìm hiểu các lệnh cơ bản của ubuntu
Dưới đây là giải thích chức năng của các lệnh Linux cơ bản được sử dụng thường xuyên trong quá trình quản trị máy chủ Ubuntu:
* **`ls`**: Liệt kê danh sách các tập tin (file) và thư mục con nằm trong thư mục làm việc hiện tại.
* **`mkdir nameFolder`**: Tạo một thư mục mới có tên là `nameFolder` tại vị trí hiện tại.
* **`cd path`**: Chuyển đổi thư mục làm việc (Change Directory). Di chuyển từ thư mục hiện tại sang thư mục đích được chỉ định trong `path`.
* **`cp file_nguồn path/file_đích`**: Sao chép (Copy) tập tin từ vị trí nguồn sang vị trí đích. Có thể đổi tên file trong lúc sao chép.
* **`sudo chmod xxx filename`**: Thay đổi quyền hạn (đọc, ghi, thực thi) của file hoặc thư mục (ví dụ: `chmod 777` cấp toàn quyền). Cần dùng `sudo` để chạy với quyền quản trị cao nhất.
* **`sudo nano tenfile`**: Mở tập tin bằng trình soạn thảo văn bản `nano` trực tiếp trên giao diện dòng lệnh Terminal với quyền quản trị.
  * `CTRL+O`: Lưu nội dung sau khi chỉnh sửa (nhấn Enter để xác nhận tên file).
  * `CTRL+X`: Thoát khỏi trình soạn thảo `nano` để quay lại Terminal.
* **`ip -4 addr`**: Hiển thị thông tin các card mạng và địa chỉ IPv4 tương ứng của máy. Dùng để xác định IP của máy ảo phục vụ cho việc kết nối SSH.

### 3. Cài đặt docker cho Ubuntu
- Chạy lệnh  dưới đây để cập nhật hệ thống và cài đặt: <br>
*Bash*: 
**sudo apt update && sudo apt install docker.io docker-compose -y**
<img width="1168" height="383" alt="image" src="https://github.com/user-attachments/assets/3063a7d3-0465-46e1-9357-741431fba405" />

### 4. Kiểm tra phiên bản docker vừa cài đặt, kiểm tra phiên bản của docker compose
- Chạy lệnh :
    **- docker --version*
   * - docker-compose --version**
 <img width="656" height="96" alt="image" src="https://github.com/user-attachments/assets/222ea0d2-f4e6-41b3-8df1-093639586fc7" />

### 5. Cấu hình để docker chạy mà không cần tiền tố sudo
- Chạy lần lượt 3 lệnh này để cấp quyền cho user :
  *1. sudo groupadd docker*
   *2. sudo usermod -aG docker* **$USER**
   *3. newgrp docker*
### 6. Tìm hiểu tập lệnh của docker và docker compose
Docker và Docker Compose cung cấp các tập lệnh giúp quản lý container và các dịch vụ mạng một cách nhanh chóng. Dưới đây là các lệnh quan trọng nhất:
#### a. Tập lệnh cơ bản của Docker:
* **`docker ps`**: Hiển thị danh sách các container đang chạy.
* **`docker ps -a`**: Hiển thị danh sách tất cả các container (bao gồm cả những container đã dừng/tắt).
* **`docker images`**: Liệt kê danh sách các images (bản ảnh) đã được tải về máy chủ.
* **`docker stop <container_id_hoặc_tên>`**: Dừng một container đang chạy một cách an toàn.
* **`docker rm <container_id_hoặc_tên>`**: Xóa bỏ một container đã dừng.
* **`docker rmi <image_id>`**: Xóa một image khỏi hệ thống để giải phóng dung lượng.
#### b. Tập lệnh cơ bản của Docker Compose:
*(Thường chạy tại thư mục có chứa file `docker-compose.yml`)*
* **`docker-compose up -d`**: Đọc file cấu hình và khởi chạy toàn bộ các dịch vụ (container) ở chế độ ngầm (detached mode), giúp trả lại giao diện Terminal để gõ lệnh khác.
* **`docker-compose down`**: Dừng và xóa toàn bộ các container, mạng (network) đã được tạo ra bởi lệnh `up`.
* **`docker-compose logs -f`**: Xem luồng log (nhật ký hoạt động) trực tiếp của các dịch vụ để kiểm tra lỗi hoặc trạng thái chạy.

### 7. Đảm bảo tường lửa trên Ubuntu đã cho phép các cổng 80, 1880, 9630 (Lệnh: sudo ufw allow ...)
- Mở các cổng: <br>
  *sudo ufw allow 80 
  sudo ufw allow 1880 
  sudo ufw allow 9630 
  sudo ufw allow 22*
  <img width="960" height="358" alt="image" src="https://github.com/user-attachments/assets/2d3b4c1a-f64c-4f8e-baa4-fbb3eca27395" />
- Kích hoạt tường lửa:  
  *sudo ufw enable*   










   
