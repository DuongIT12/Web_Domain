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
