# BÁO CÁO THỰC HÀNH KIỂM THỬ API BẰNG POSTMAN

## 1. Thông tin sinh viên

* **Họ và tên:** Huu Nguyen Danh
* **Môn học:** Software Testing
* **Công cụ:** Postman
* **Chủ đề:** Thực hành kiểm thử API

## 2. Mục tiêu

* Làm quen với giao diện và các chức năng cơ bản của Postman.
* Thực hiện gửi HTTP request bằng phương thức GET và POST.
* Kiểm tra dữ liệu phản hồi từ API.
* Viết các câu lệnh kiểm thử tự động bằng JavaScript.
* Đánh giá kết quả kiểm thử thông qua Test Results.

## 3. Môi trường thực hành

* Công cụ: Postman Desktop
* API sử dụng: Postman Echo
* GET endpoint: `https://postman-echo.com/get`
* POST endpoint: `https://postman-echo.com/post`

Postman Echo là dịch vụ phản hồi lại thông tin của request để hỗ trợ thực hành và kiểm thử API.

## 4. Thực hành kiểm thử API GET

### 4.1. Các bước thực hiện

1. Tạo request mới trong Postman.
2. Chọn phương thức GET.
3. Nhập URL `https://postman-echo.com/get`.
4. Nhấn Send.
5. Quan sát phần Response.

### 4.2. Kết quả

API trả về dữ liệu JSON bao gồm các thông tin như `args`, `headers` và `url`.

Mã trạng thái nhận được: **200 OK**.

Kết quả cho thấy request GET được gửi thành công và máy chủ đã phản hồi.

**Hình 1: Kết quả thực hiện request GET**

<!-- Chèn ảnh chụp kết quả GET tại đây -->

## 5. Thực hành kiểm thử API POST

### 5.1. Các bước thực hiện

1. Tạo request POST mới.
2. Nhập URL `https://postman-echo.com/post`.
3. Chọn Body → raw → JSON.
4. Nhập dữ liệu JSON:

```json
{
  "name": "Huu Nguyen Danh",
  "subject": "Software Testing",
  "tool": "Postman"
}
```

5. Nhấn Send.
6. Kiểm tra dữ liệu trong Response.

### 5.2. Kết quả

API trả về mã trạng thái **200 OK**.

Trong phần phản hồi, dữ liệu gửi lên được trả về trong trường `json`, bao gồm:

* `name`: Huu Nguyen Danh
* `subject`: Software Testing
* `tool`: Postman

Kết quả cho thấy dữ liệu JSON đã được gửi và phản hồi đúng như mong đợi.

**Hình 2: Kết quả thực hiện request POST**

<!-- Chèn ảnh chụp kết quả POST tại đây -->

## 6. Viết kiểm thử tự động bằng JavaScript

Tại request POST, chọn Scripts → After response và nhập đoạn mã sau:

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response contains correct name", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.json.name).to.eql("Huu Nguyen Danh");
});

pm.test("Response contains correct subject", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.json.subject).to.eql("Software Testing");
});

pm.test("Response contains correct tool", function () {
    const jsonData = pm.response.json();
    pm.expect(jsonData.json.tool).to.eql("Postman");
});
```

### 6.1. Giải thích

* **Test 1:** Kiểm tra mã trạng thái HTTP có bằng 200 hay không.
* **Test 2:** Kiểm tra tên trong phản hồi có chính xác hay không.
* **Test 3:** Kiểm tra tên môn học trong phản hồi.
* **Test 4:** Kiểm tra tên công cụ trong phản hồi.

Các bài kiểm thử được chạy tự động mỗi khi gửi request.

### 6.2. Kết quả kiểm thử

| Nội dung kiểm thử                 | Kết quả |
| --------------------------------- | ------- |
| Status code is 200                | Passed  |
| Response contains correct name    | Passed  |
| Response contains correct subject | Passed  |
| Response contains correct tool    | Passed  |

**Tổng kết: 4 bài kiểm thử Passed, 0 bài kiểm thử Failed.**

**Hình 3: Kết quả Test Results trên Postman**

<!-- Chèn ảnh chụp màn hình thể hiện 4 tests passed tại đây -->

## 7. Nhận xét và kết luận

Qua bài thực hành, em đã làm quen với Postman và biết cách gửi các request GET, POST để kiểm thử API. Em cũng đã thực hành gửi dữ liệu JSON, đọc phản hồi từ máy chủ và viết các bài kiểm thử tự động bằng JavaScript.

Kết quả thực hành cho thấy cả bốn kiểm thử đều thành công với dữ liệu đã thiết lập. Qua đó, em hiểu rõ hơn cách kiểm tra mã trạng thái HTTP và xác minh dữ liệu phản hồi của API.

## 8. Tài liệu tham khảo

* Postman Documentation: https://learning.postman.com/docs/
* Postman Echo: https://www.postman-echo.com/
* Video hướng dẫn được cung cấp trong bài tập: https://www.youtube.com/watch?v=MFxk5BZulVU
