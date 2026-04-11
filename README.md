# Web_Domain
## A. Đăng ký tên miền cho cá nhân:
### B1. Mua tên miền trên *mắt bão*:###   
- Truy cập trang https://www.matbao.net/   
  *Chọn Sản phẩm---> Tên miền---> Tên miền miễn phí*
<img width="1908" height="1026" alt="Screenshot 2026-01-29 104336" src="https://github.com/user-attachments/assets/c6fff26e-2b1a-4feb-af5c-cebe8d3e3ca1" />         
  <img width="1913" height="977" alt="Untitled" src="https://github.com/user-attachments/assets/e3d88b42-5174-43f4-bcf7-22707b7c158d" />
*Xác thực thông tin cá nhân*  
<img width="740" height="782" alt="image" src="https://github.com/user-attachments/assets/02c780e6-bc68-4847-9ca6-28aa2653ede9" />
*Hoàn thành mua tên miền*  
<img width="1552" height="792" alt="Untitled1" src="https://github.com/user-attachments/assets/e78bbd1b-7e89-4043-9158-b3163631404a" />


### B2. Đăng ký tài khoản **Cloudflare**   
- Truy cập trang: https://dash.cloudflare.com/login  
  *Login--->xác thực---> Done*     
<img width="1913" height="970" alt="Untitled3" src="https://github.com/user-attachments/assets/46ad0b06-17ea-4898-a4e0-35d08ce5dc3b" />


### B3. Thêm domain đã đăng ký vào trong **cloudflare** : Nhận 2 dòng namespace <br>
**Bước 1: Thêm tên miền vào Cloudflare** <br>
1. Đăng nhập vào tài khoản [Cloudflare](https://www.cloudflare.com/).
2. Nhấn nút **Add a Site.**<br>
<img width="1929" height="976" alt="Untitled4" src="https://github.com/user-attachments/assets/ff5a5b6b-e37c-45a5-847d-2c612f67012e" />

4. Nhập tên miền của bạn *(ví dụ: tenmien.com)* và nhấn **Continue.** <br>
5. Chọn gói dịch vụ (chọn gói **Free** ở dưới cùng nếu bạn muốn dùng miễn phí) rồi nhấn **Continue.**<br>
6. Cloudflare sẽ tự động quét các bản ghi DNS hiện tại. Sau khi quét xong, nhấn **Continue.** <br>

**Bước 2: Lấy 2 dòng Nameservers** <br>
Sau bước trên, Cloudflare sẽ hiển thị mục Change your nameservers. Tại đây, bạn sẽ thấy 2 dòng Nameservers mới (thường có dạng ***.ns.cloudflare.com*).<br>
Hãy sao chép (copy) 2 dòng này để chuẩn bị dán vào trang quản lý tên miền.<br>
<img width="1929" height="552" alt="Untitled5" src="https://github.com/user-attachments/assets/46fbbd34-9e39-481f-9a3d-42390857924f" />
**Bước 3: Cập nhật Nameservers tại trang quản trị (vd: Mắt Bão)** <br>
### B4. Nhập 2 dòng namespace của cloudflare vào trong trang quản lý DNS record của tên miền đăng ký (vd trên mắt bão)
1. Tìm mục có tên là Quản lý DNS hoặc Thay đổi Nameserver.
2. Tại đây, bạn sẽ thấy các dòng Nameserver mặc định của Mắt Bão (thường là ns1.matbao.com, ns2.matbao.com).
3. Chọn tùy chọn: Sử dụng Nameserver khác (hoặc Nameserver tùy chỉnh).
4. Bạn xóa trắng các dòng cũ và dán 2 dòng từ Cloudflare vào:
Nameserver 1: itzel.ns.cloudflare.com
Nameserver 2: (Dòng thứ 2 trong ảnh Cloudflare của bạn, ví dụ: olga.ns.cloudflare.com)
5. Nhấn Cập nhật hoặc Lưu.
<img width="1916" height="1039" alt="Untitled6" src="https://github.com/user-attachments/assets/b87f66c4-148a-4a98-b82e-ffac4fa96610" />

## B. Cài đặt Ubuntu + Docker




 








