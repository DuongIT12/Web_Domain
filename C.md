## C. Cấu hình docker compose:
1. Tạo thư mục: ~/myapp
2. Chuyển vào trong thư mục ~/myapp
3. Tạo thư mục: ./myweb
<img width="630" height="97" alt="image" src="https://github.com/user-attachments/assets/b3c78500-1b6a-4de6-b9f2-4a0440ed4a58" />
4. Tạo file ./myweb/index.html
<img width="1465" height="806" alt="Untitled11" src="https://github.com/user-attachments/assets/70d13ebf-6a3b-42ac-b92e-d54b2a982494" />
5. Tạo file docker-compose.yml để nó sẽ có các dịch vụ sau
s<img width="1465" height="490" alt="Untitled12" src="https://github.com/user-attachments/assets/4a182c5f-ce37-4632-9cee-8670d1a6dafc" />
6. Edit file ./nginx/nginx.conf
- Tạo thư mục nginx: **mkdir ./nginx*
-  Mở file nginx.conf để soạn thảo: **nano ./nginx/nginx.conf*
<img width="644" height="514" alt="image" src="https://github.com/user-attachments/assets/8c456b65-a18e-459d-951b-3be5b5d0d574" />
7. Edit file ./nodered/settings.js để nodered bắt buộc đăng nhập <br>      
 <img width="748" height="144" alt="image" src="https://github.com/user-attachments/assets/2086f047-0b51-4c23-a928-656da689c011" />   
