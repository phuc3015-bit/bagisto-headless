# BÁO CÁO THỰC HÀNH: THIẾT LẬP BAGISTO HEADLESS COMMERCE

**Sinh viên:** Nguyễn Trọng Phúc  
**MSSV:** 23810310391

---

## I. MỤC TIÊU BÀI LÀM
* Nắm vững kiến trúc Headless Commerce: Tách biệt hoàn toàn Back-end (Bagisto) và Front-end (HTML/JS).
* Triển khai thành công API để truy xuất dữ liệu sản phẩm.
* Xây dựng giao diện hiển thị sản phẩm thực tế từ API.

---

## II. NỘI DUNG THỰC HIỆN

### 1. Cài đặt hệ thống & Dữ liệu mẫu
* Sử dụng **Bagisto phiên bản 2.3** trên nền tảng XAMPP.
* Đã cấu hình Database và cài đặt thành công gói `bagisto/rest-api` để phục vụ kiến trúc Headless.
* Đã thêm mới 03 sản phẩm mẫu với tiền tố **Phuc_** theo đúng yêu cầu:
  1. `Phuc-Laptop Gigabyte G5RD`
  2. `Phuc-Laptop Lenovo loq`
  3. `Phuc-Smart phone Vivo iqoo neo 3`

> **Minh chứng Admin:** <img width="1920" height="1020" alt="Screenshot 2026-04-03 205618" src="https://github.com/user-attachments/assets/4bedee70-a460-4666-a53e-662924558820" />


### 2. Khai thác API (Phần 2)
Do phiên bản Bagisto 2.3 gặp xung đột với extension GraphQL cũ, em đã chủ động sử dụng **REST API** để thực hiện truy vấn. Kết quả trả về định dạng JSON chính xác.
* **Endpoint:** `http://localhost/bagisto-headless/public/api/products?name=Phuc`

> **Minh chứng API:** <img width="1920" height="1020" alt="Screenshot 2026-04-03 205600" src="https://github.com/user-attachments/assets/e0693123-8157-4951-8fc5-6ccfa9fe40a1" />


### 3. Xây dựng Frontend (Phần 3)
* Sử dụng **HTML5, CSS3 và Vanilla JavaScript (Fetch API)**.
* Giao diện được thiết kế dạng Card, tự động gọi dữ liệu từ Back-end khi tải trang.
* Mã nguồn có comment giải thích chi tiết các hàm xử lý dữ liệu.

> **Minh chứng Frontend:** <img width="1920" height="1020" alt="Screenshot 2026-04-03 210513" src="https://github.com/user-attachments/assets/92ac789b-b2d9-4568-9fd0-c0d5f37a6986" />


---

## III. CÂU HỎI BẮT BUỘC

**1. So sánh sự khác biệt về lưu lượng dữ liệu (Payload) giữa REST API và GraphQL?**
* **REST API:** Trong bài làm của em, REST API trả về toàn bộ cấu hình sản phẩm (mô tả, các loại link ảnh, metadata dư thừa...), dẫn đến Payload nặng hơn (vài chục KB).
* **GraphQL:** Cho phép người dùng chỉ định chính xác trường cần lấy (ví dụ chỉ lấy `name` và `price`), giúp giảm dung lượng Payload xuống mức tối thiểu, tối ưu tốc độ cho ứng dụng.

**2. Thay đổi giá sản phẩm qua API dùng Query hay Mutation? Giải thích.**
* Em sẽ sử dụng **Mutation**.
* **Giải thích:** Trong quy chuẩn GraphQL, Query chỉ dùng để đọc dữ liệu (Read). Các hành động làm thay đổi dữ liệu trên Server (Thêm, Sửa, Xóa) như cập nhật giá sản phẩm phải sử dụng Mutation để đảm bảo tính an toàn và đúng chuẩn kiến trúc API.


*(Trong video em thực hiện thao tác Refresh trang để chứng minh dữ liệu được load thực tế từ API).*
