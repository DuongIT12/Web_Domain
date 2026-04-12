## G. Triển khai ứng dụng đến End-user
### 1. Trong Cloudflare: Tạo tunnel (đường hầm), chọn loại triển khai cho docker
B1: Tạo Tunnel (Đường hầm kết nối)
1.Truy cập Zero Trust -> Networks -> Tunnels.  
<img width="1881" height="921" alt="Untitled13" src="https://github.com/user-attachments/assets/137d60ce-71c5-4363-818a-0d54a0ae7ea0" />

2. Chọn Create a Tunnel, đặt tên là myapp-tunnel.<br>
<img width="1906" height="911" alt="Untitled14" src="https://github.com/user-attachments/assets/8d4924ac-a4db-474d-ae1b-8c854bf09216" />

3. Tại phần Install connector, chọn tab Docker. Copy đoạn mã hiện ra, bạn sẽ thấy một dãy ký tự dài (đó chính là TOKEN).  
<img width="523" height="104" alt="image" src="https://github.com/user-attachments/assets/16a205c4-f232-4260-ad32-fe29a4617a3e" />

4. Chạy lại docker compose     
<img width="1482" height="256" alt="image" src="https://github.com/user-attachments/assets/276790ec-ba25-4b97-873c-90e23c2058a3" />

5. Public ứng dụng bằng cách thêm 1 router trỏ tới container đang chạy trong docker, dữ liệu sẽ đi qua tunnel, url dạng sub-domain

6. Kiểm tra url sub-domain đã hoạt động public cho mọi end-user
- Kết quả thực tế:     
    - Tên miền truy cập: https://wapvip.io.vn   
- Trạng thái: Hoạt động công khai (Public).  
- Bảo mật: Đã cấu hình SSL/TLS thành công qua Cloudflare Tunnel   .
<img width="1911" height="1024" alt="image" src="https://github.com/user-attachments/assets/be628b31-8657-49a8-8ff5-c2e9a8ccbbaa" />


7. Tất cả hoàn thành đã sử dụng được domain: *www.wapvip.io.vn*  
## Test *Funnny*   
<img width="1917" height="1026" alt="image" src="https://github.com/user-attachments/assets/231800c5-dc52-4040-8b72-2e0ce0e20be8" />

# CÂU HỎI VỀ BÀI LÀM (Q&A)
## 1. Tại sao phải dùng Nginx làm Reverse Proxy mà không trỏ thẳng Tunnel vào Node-RED?
- **Quản lý tập trung**: Nginx đóng vai trò là "cổng vào" duy nhất, giúp điều phối (Routing) yêu cầu đến đúng dịch vụ (ví dụ: `/` vào Web tĩnh, `/api` vào Node-RED).
- **Hiệu suất**: Nginx xử lý các file tĩnh (HTML/CSS) nhanh hơn Node-RED, giúp tối ưu tài nguyên server.
- **Bảo mật**: Tạo thêm một lớp đệm ngăn chặn các yêu cầu độc hại trực tiếp chạm vào logic Backend.

---
## 2. Sự khác biệt giữa việc Mount file và Mount thư mục trong Docker là gì?
- **Mount file**: Chỉ gắn kết một file duy nhất. Thường dùng cho các file cấu hình cố định như `nginx.conf`.
- **Mount thư mục**: Gắn kết toàn bộ thư mục. Mọi thay đổi về file bên trong thư mục ở máy host (Ubuntu) sẽ ngay lập tức cập nhật vào container. Phù hợp cho thư mục chứa mã nguồn web.

---
## 3. Nếu thay đổi file index.html ở máy Ubuntu, nội dung trên web có thay đổi ngay không? Tại sao?
- **Trả lời**: Có thay đổi ngay lập tức.  
- **Giải thích**: Vì chúng ta sử dụng cơ chế **Bind Mount**. Container Nginx đọc trực tiếp dữ liệu từ thư mục trên máy Ubuntu, nên khi file được lưu, Nginx sẽ phục vụ ngay nội dung mới mà không cần khởi động lại container.

---
## 4. Ý nghĩa của `restart: always` và `restart: unless-stopped`?
- **always**: Container tự động khởi động lại trong mọi tình huống (lỗi, reboot máy ảo, restart Docker).
- **unless-stopped**: Tương tự như `always`, nhưng nếu người dùng chủ động tắt bằng lệnh `docker stop`, nó sẽ không tự bật lại cho đến khi được Start thủ công.

---
# CÂU HỎI VỀ BÀI LÀM (Q&A)

## 5. Khai báo dùng chung 1 network & Lợi ích?
- **Cách khai báo**: Thêm mục `networks:` ở cuối file và trong từng service.
- **Lợi ích**: Các container có thể "gọi tên" nhau (ví dụ Nginx gọi `http://nodered:1880`) một cách bảo mật mà không cần dùng địa chỉ IP hay mở cổng ra ngoài Internet.
### Sửa đổi file mẫu:
yaml
services:
  nginx:
    networks:
      - my_bridge
  nodered:
    networks:
      - my_bridge
networks:
  my_bridge:
    driver: bridge 


## 6. Đưa Token vào .env và .gitignore? Tại sao quan trọng?
- **Cách làm**:  
  - Tạo file `.env` chứa `CF_TOKEN=....`  
  - Trong `docker-compose.yml` dùng `${CF_TOKEN}`  
  - Thêm `.env` vào `.gitignore`
- **Tầm quan trọng**:  
  Tránh lộ thông tin nhạy cảm. Nếu bạn đẩy Token lên GitHub, bất kỳ ai cũng có thể điều khiển Tunnel của bạn, truy cập trái phép vào server hoặc đánh cắp dữ liệu.

---

## 7. Tại sao nên thêm hậu tố `:ro` khi mount file cấu hình Nginx?
- **`:ro` (Read-Only)**: Nghĩa là "Chỉ đọc".
- **Lý do**:  
  Đảm bảo container Nginx không bao giờ có quyền sửa đổi file gốc trên máy Ubuntu.  
  Điều này ngăn chặn hacker nếu chiếm được container cũng không thể ghi đè mã độc vào file cấu hình gốc của bạn.

---
## 8. Khi dùng Cloudflare Tunnel, có cần thiết phải mở cổng cho các service nữa không?
- **Trả lời**: Không cần thiết.
- **Lý do**:  
  Tunnel tạo một kết nối "đi ra" (outbound) từ máy ảo tới Cloudflare. Người dùng đi vào qua đường hầm này.  
  Bạn có thể đóng hết các cổng (80, 1880) trên Firewall của máy ảo, hệ thống vẫn chạy tốt và cực kỳ an toàn vì không có "cửa hở" nào từ Internet vào thẳng máy ảo của bạn.








