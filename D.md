1. Tạo thư mục ./myapi
2. Tạo file ./myapi/app.py sử dụng Python + Flask để làm gì đó funny
<img width="1483" height="488" alt="image" src="https://github.com/user-attachments/assets/f0a8bcc8-33b3-4430-903c-7ae608e0243e" />
- Tạo file package.json (Khai báo thư viện):
<img width="1465" height="243" alt="image" src="https://github.com/user-attachments/assets/94c39bf1-fc1b-4303-8d96-b9aa42761f84" />


3. Tạo file ./myapi/requirements.txt chứa các thư viện mà app.py sử dụng (theo như app.py ví dụ thì requirements.txt chỉ cần có nội dung: flask)
4. Tạo file Dockerfile:
- nano ./myapi/Dockerfile

5. Bước 2: Bổ sung API vào Docker Compose (Mục 5)
- Mở file docker-compose.yml:
  <img width="1269" height="686" alt="image" src="https://github.com/user-attachments/assets/9fddf247-6a72-49b4-93c2-1a2613d26c9a" />
6. Sửa đổi nginx/nginx.conf để /api trỏ tới service myapp cổng 9630
  - Mở file cấu hình Nginx:  *nano ~/myapp/nginx/nginx.conf*
  - <img width="769" height="485" alt="image" src="https://github.com/user-attachments/assets/5c724022-df60-4720-a0fc-784c274d225f" />
