# Báo cáo Lab 7 - Thực hành Kiểm thử API với Postman

**Thông tin sinh viên:**
* **Họ và tên:** Nguyễn Đình Đạt
* **Mã sinh viên:** 23010282
* **Môn học:** Đánh giá và kiểm thử chất lượng phần mềm

---

## 1. Mục tiêu của bài Lab
* Làm quen và thực hành sử dụng công cụ Postman để gửi các HTTP Requests.
* Nắm vững cách cấu hình URL, Headers, và dữ liệu Body dạng JSON.
* Viết các Test Scripts tự động bằng JavaScript để kiểm chứng kết quả trả về từ Server (Status Code, nội dung Response).

## 2. Môi trường kiểm thử
* **Công cụ sử dụng:** Postman Desktop App
* **Đối tượng kiểm thử:** RESTful API mô phỏng từ `https://reqres.in/`

---

## 3. Kịch bản kiểm thử (Test Cases) & Kết quả

### Test Case 1: Lấy danh sách người dùng (GET Request)
* **Mô tả:** Kiểm tra API lấy danh sách người dùng ở trang số 2 xem có hoạt động đúng và trả về dữ liệu hợp lệ hay không.
* **API EndPoint:** `GET https://reqres.in/api/users?page=2`
* **Test Scripts thiết lập:**
  * Kiểm tra mã trạng thái trả về có đúng là `200 OK`.
  * Kiểm tra nội dung body có tồn tại (không rỗng).
  * Kiểm tra trường `page` trong cục JSON trả về có đúng giá trị là `2`.
* **Kết quả thực tế:** **PASS 100%**. Hệ thống xác thực API Key thành công và trả về dữ liệu đúng như mong đợi.
* **Hình ảnh minh họa:**
* <img width="1144" height="901" alt="image" src="https://github.com/user-attachments/assets/2d4a22fa-50cb-4d93-a6dc-4357290f77e7" />


  ![Minh chứng Test Case GET](./images/get-test.png)
  *(Lưu ý: Thay `get-test.png` bằng tên file ảnh chụp màn hình Postman lúc ra 200 OK của bạn)*

### Test Case 2: Thêm người dùng mới (POST Request)
* **Mô tả:** Kiểm tra API tạo mới người dùng xem server có tiếp nhận dữ liệu từ body và tạo thành công tài nguyên mới hay không.
* **API EndPoint:** `POST https://reqres.in/api/users`
* **Dữ liệu gửi đi (Body - JSON):**
  ```json
  {
      "name": "Nguyen Dinh Dat",
      "job": "Backend Developer"
  }

 <img width="1144" height="901" alt="image" src="https://github.com/user-attachments/assets/06d6f160-fd0c-41e4-bbdb-75836621a72f" />


## 4. Kết luận & Đánh giá

Qua quá trình thực hiện Lab 7, em đã rút ra được những kết quả và kinh nghiệm sau:

* **Về mặt công cụ:** Nắm vững và thao tác thành thạo trên giao diện của Postman. Hiểu rõ cách thiết lập các HTTP Methods (GET, POST), phân biệt được vai trò của URL parameters, cách truyền dữ liệu vào Body (định dạng JSON), và đặc biệt là cách cấu hình Headers để xử lý xác thực (Authentication) bằng API Key.
* **Về mặt kiểm thử tự động:** Bước đầu hình thành tư duy viết test script tự động bằng JavaScript trong Postman (`pm.test`, `pm.expect`). Kỹ năng này giúp thay thế việc kiểm tra dữ liệu bằng mắt thường, tự động hóa quá trình xác thực HTTP Status Code (200, 201, 401, 403) và độ chính xác của cấu trúc JSON trả về.
* **Định hướng ứng dụng:** Nhận thức được tầm quan trọng của việc kiểm thử API độc lập. Trong thực tế phát triển phần mềm, khi xây dựng các RESTful API phức tạp ở phía backend — chẳng hạn như thiết kế API quản lý giỏ hàng (xử lý logic cho phép người dùng linh hoạt thêm hoặc xóa các sản phẩm không mong muốn ra khỏi giỏ trước khi tiến hành chốt đơn đặt hàng) — việc dùng Postman để chạy các kịch bản test sẽ giúp phát hiện và ngăn chặn sớm các lỗi sai logic dữ liệu trước khi tích hợp vào giao diện frontend.
