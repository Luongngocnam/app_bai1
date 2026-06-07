# BÁO CÁO BÀI TẬP LỚN: PHÁT TRIỂN ỨNG DỤNG TRÊN MIT APP INVENTOR

## I. QUY TRÌNH PHÁT TRIỂN ỨNG DỤNG
Quy trình xây dựng ứng dụng trên MIT App Inventor tuân thủ chặt chẽ theo 2 giai đoạn cốt lõi:
1. **Giao diện Designer (Thiết kế):** Thực hiện kéo thả các thành phần giao diện (UI) từ thanh công cụ (Palette) vào màn hình mô phỏng (Viewer) và cấu hình các thuộc tính (Properties) như kích thước, màu sắc, phông chữ.
2. **Giao diện Blocks (Lập trình logic):** Thực hiện lắp ghép các khối lệnh trực quan để định nghĩa hành vi xử lý sự kiện cho các thành phần UI đã tạo.

---

## II. HƯỚNG DẪN CHI TIẾT CÁC BƯỚC THỰC HIỆN (STEP-BY-STEP)

### BƯỚC 1: KHỞI TẠO DỰ ÁN VÀ CẤU TRÚC MÀN HÌNH
1. Truy cập vào trang web [appinventor.mit.edu](https://appinventor.mit.edu), chọn **Create Apps!** và đăng nhập bằng tài khoản Google.
2. Chọn **Projects** $\rightarrow$ **Start new project**, đặt tên dự án là `BaiTapLon_MIT`.
3. Mặc định hệ thống sẽ tạo sẵn màn hình đầu tiên là **Screen1**. Để tạo thêm các màn hình theo yêu cầu đề bài, nhấn nút **Add Screen** ở thanh công cụ phía trên:
   * Tạo thêm **Screen2** (Màn hình giải toán).
   * Tạo thêm **Screen3** (Màn hình hiển thị Web).

---

### BƯỚC 2: THIẾT KẾ GIAO DIỆN (DESIGNER MODE)

#### 1. Cấu hình Screen1: Giao diện Giới thiệu bản thân (About Me)
* **Thành phần kéo thả:**
  * Từ mục *User Interface*, kéo 1 `Label` vào màn hình. Sửa thuộc tính `Text` tại bảng Properties bên phải thành: `"Họ và tên: Luông Ngọc Nam - MSV: ... - Chuyên ngành: Kỹ thuật Máy tính"`.
  * Từ mục *Layout*, kéo 1 `HorizontalArrangement` (Khung ngang) vào để chứa các nút bấm nằm kề nhau.
  * Kéo 2 `Button` đặt vào bên trong khung ngang vừa tạo.
* **Thay đổi thuộc tính (Properties):**
  * Chọn Button thứ nhất: Đổi tên thành `btnGoToMath` (bằng nút *Rename* phía dưới bảng Components). Sửa thuộc tính `Text` thành `"Giải Toán"`, thuộc tính `BackgroundColor` thành màu Xanh.
  * Chọn Button thứ hai: Đổi tên thành `btnGoToWeb`. Sửa thuộc tính `Text` thành `"Xem Web"`, thuộc tính `BackgroundColor` thành màu Đỏ.

#### 2. Cấu hình Screen2: Giao diện Giải toán đơn giản ($ax + b = 0$)
* Chuyển sang chọn **Screen2** ở hộp thoại thả xuống phía trên màn hình Viewer.
* **Thành phần kéo thả:**
  * Kéo 2 thành phần `TextBox` từ mục *User Interface* vào màn hình để người dùng nhập hệ số.
  * Kéo 1 `Button` dùng để kích hoạt lệnh tính toán.
  * Kéo 1 `Label` dùng để hiển thị kết quả đầu ra.
* **Thay đổi thuộc tính (Properties):**
  * `TextBox1`: Đổi tên thành `txtA`. Sửa thuộc tính `Hint` thành `"Nhập hệ số a"`. Tích chọn thuộc tính `NumbersOnly` (Chỉ cho nhập số).
  * `TextBox2`: Đổi tên thành `txtB`. Sửa thuộc tính `Hint` thành `"Nhập hệ số b"`. Tích chọn thuộc tính `NumbersOnly`.
  * `Button1`: Đổi tên thành `btnSolve`. Sửa thuộc tính `Text` thành `"Tính Nghiệm X"`.
  * `Label1`: Đổi tên thành `lblResult`. Sửa thuộc tính `Text` thành `"Kết quả: "` và tăng `FontSize` lên `18`.

#### 3. Cấu hình Screen3: Giao diện Web-View
* Chuyển sang chọn **Screen3**.
* **Thành phần kéo thả:**
  * Từ mục *User Interface*, tìm đến thành phần `WebViewer`, kéo và thả trực tiếp vào màn hình Viewer.
* **Thay đổi thuộc tính (Properties):**
  * Thành phần `WebViewer1` mặc định sẽ chiếm toàn bộ chiều rộng (`Width` = Fill parent) và chiều cao (`Height` = Fill parent) để hiển thị tối ưu giao diện điện thoại.

---

### BƯỚC 3: LẬP TRÌNH LOGIC XỬ LÝ (BLOCKS MODE)

Ấn nút **Blocks** ở góc trên bên phải để chuyển sang màn hình lập trình ghép khối:

#### 1. Viết mã xử lý cho Screen1 (Chuyển đổi màn hình)
* Chọn nhóm lệnh `btnGoToMath` ở cột bên trái $\rightarrow$ Kéo khối sự kiện `when btnGoToMath.Click do` ra màn hình.
* Chọn nhóm lệnh **Built-in** $\rightarrow$ **Control** $\rightarrow$ Kéo khối `open another screen screenName` gắn vào bên trong khối `do`.
* Chọn nhóm **Built-in** $\rightarrow$ **Text** $\rightarrow$ Kéo khối chuỗi rỗng `""` gắn vào đuôi `screenName` và gõ chữ `Screen2`.
* *Thực hiện tương tự cho nút bấm thứ hai để gọi sang Screen3.*

#### 2. Viết mã thuật toán cho Screen2 (Giải phương trình $ax+b=0$)
* Kéo khối sự kiện `when btnSolve.Click do` từ mục `btnSolve`.
* Sử dụng cấu trúc điều khiển rẽ nhánh bằng cách vào **Control** $\rightarrow$ Kéo khối `if - then - else` lồng vào trong.
* Thiết lập các điều kiện logic toán học dựa trên các khối tại mục **Math**:
  * **Nếu (If)** `txtA.Text = 0` và `txtB.Text = 0`: 
    * Gọi lệnh `set lblResult.Text to` $\rightarrow$ Ghép chuỗi văn bản `"Phương trình vô số nghiệm"`.
  * **Ngược lại nếu (Else if)** `txtA.Text = 0` và `txtB.Text != 0`:
    * Gọi lệnh `set lblResult.Text to` $\rightarrow$ Ghép chuỗi văn bản `"Phương trình vô nghiệm"`.
  * **Ngược lại (Else)** (Trường hợp $a \\neq 0$):
    * Gọi lệnh `set lblResult.Text to` $\rightarrow$ Ghép với khối phép tính toán học: `( 0 - txtB.Text ) / txtA.Text` (tương đương công thức $x = -b/a$).

#### 3. Viết mã xử lý cho Screen3 (Tải trang Web tự động)
* Chọn nhóm `Screen3` ở cột bên trái $\rightarrow$ Kéo khối sự kiện khởi tạo màn hình: `when Screen3.Initialize do`.
* Chọn nhóm `WebViewer1` $\rightarrow$ Kéo khối hàm hành động: `call WebViewer1.GoToUrl`.
* Chọn nhóm **Text** $\rightarrow$ Kéo khối chuỗi `""`, điền chính xác địa chỉ URL theo yêu cầu: `https://k58kmt.tdh.io.vn?masv=MÃ_SỐ_SV_CỦA_BẠN` để gắn vào tham số `url`.

---

## III. ĐÁNH GIÁ VỀ CÔNG CỤ LẬP TRÌNH BLOCK-BASED
Qua quá trình thực hiện phần mềm trên công cụ MIT App Inventor, bản chất và đặc điểm của phương pháp lập trình kéo thả khối được đúc kết như sau:

* **Bản chất:** Là việc trực quan hóa các cú pháp mã nguồn (Syntax) khô khan thành các mảnh ghép hình học. Lập trình viên không cần gõ mã code, thay vào đó tư duy logic được thể hiện bằng cách kết nối các khối lệnh khớp nhau về mặt cấu trúc và kiểu dữ liệu.
* **Ưu điểm so với viết code:**
  * Loại bỏ hoàn toàn các lỗi cú pháp (Syntax errors) phổ biến khi viết code tay như thiếu dấu chấm phẩy `;`, đặt sai dấu ngoặc `{}` hay viết sai chính tả từ khóa.
  * Mô hình hóa các sự kiện tương tác (`Event-driven`) một cách trực quan, giúp người học dễ dàng tiếp cận và nắm bắt luồng dữ liệu của ứng dụng.
* **Nhược điểm:**
  * Khi logic ứng dụng trở nên quá lớn và phức tạp, số lượng khối lệnh tăng lên sẽ gây ra hiện tượng rối mắt, rất khó quản lý, theo dõi và bảo trì.
  * Hạn chế khả năng can thiệp sâu vào các tài nguyên phần cứng chuyên sâu hoặc tối ưu hóa hiệu năng hệ thống của thiết bị.
* **Tính năng Balo (Backpack):** Tính năng này đóng vai trò như một bộ nhớ tạm (Clipboard) nâng cao. Nó cho phép người phát triển kéo các khối lệnh phức tạp đã xây dựng ở màn hình này (hoặc dự án này) thả vào Balo, sau đó chuyển sang một màn hình khác để lấy ra tái sử dụng, giúp tiết kiệm đáng kể thời gian lập trình lại từ đầu.
