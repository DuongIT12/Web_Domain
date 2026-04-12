## Triển khai (level test) ứng dụng
1. Chuyển vào trong thư mục ~/myapp <br>
<img width="602" height="110" alt="image" src="https://github.com/user-attachments/assets/88bbbba1-dd7b-4f75-9377-b29c6f327e30" />
<img width="1464" height="160" alt="image" src="https://github.com/user-attachments/assets/499243c2-66f3-4020-8964-6829ce2b9a52" />
2. Gõ lệnh để docker compose chạy: sẽ run tất cả các service khai báo trong file docker-compose.yml
- Lợi ích: Chỉ cần docker-compose up -d là toàn bộ hệ thống (Web + Node-RED + Tunnel) tự chạy,
3.  Kiểm tra các container đang chạy trong docker, nếu có cái nào bị restart cần tìm lỗi rồi edit lại docker-compose.yml  
 Sau khi chạy lệnh khởi động, cần xác nhận các dịch vụ đang hoạt động ổn định.<br>
*Xem danh sách các container đang chạy*: **sudo docker ps**

4. Kiểm tra kiểm thử các service đang chạy độc lập thông qua ip và port của nó: ví dụ mở trình duyệt ip_ubuntu:1880 để check nodered đã chạy chưa   
- Kiểm tra Node-RED: Truy cập địa chỉ:*(http://192.168.1.9:1880/#flow/75ebc46a106624f5)*.<br>
<img width="1901" height="1037" alt="image" src="https://github.com/user-attachments/assets/340c4eae-110f-428f-8350-00035993faf0" />

- Kiểm tra Web Server: Truy cập địa chỉ:http: *//192.168.1.9/* <br>
  <img width="1894" height="1031" alt="image" src="https://github.com/user-attachments/assets/e5394503-d694-419c-bd50-b3ebfc63621a" />

5. Sử dụng nodered: kéo nodered http_in , http_response, function : để tạo api get đơn giản (dùng cho /api proxy_pass của nginx)<br>
- Deloy Succese
<img width="1899" height="955" alt="image" src="https://github.com/user-attachments/assets/04b09581-024a-4fbf-b636-b56e9b15e902" />


6. Sửa file ./myweb/index.html : thêm code html+js để sử dụng được api đã khai báo proxy_pass (thực ra là sử dụng nodered http_in hoặc sử dụng service myapi)
<img width="848" height="525" alt="image" src="https://github.com/user-attachments/assets/b03b063c-fe4d-4770-b508-351818e4e33a" />










