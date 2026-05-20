## 1. REST yêu cầu dùng danh từ cho URL

Đúng. REST khuyến khích dùng danh từ (thường ở dạng số nhiều) cho URL, không dùng động từ.

### Ví dụ đúng

```text
/students
/students/1
```

### Ví dụ sai

```text
/getStudents
/deleteStudent
```

---

## 2. Ví dụ API quản lý sinh viên

### 2 ví dụ đúng

```text
GET /students
DELETE /students/5
```

### 2 ví dụ sai

```text
GET /getAllStudents
POST /createStudent
```

---

## 3. Các phương thức HTTP

| Method | Mục đích chính | Có body không? (thường) |
|---|---|---|
| GET | Lấy dữ liệu | Không |
| POST | Tạo mới dữ liệu | Có |
| PUT | Cập nhật toàn bộ dữ liệu | Có |
| PATCH | Cập nhật một phần dữ liệu | Có |
| DELETE | Xóa dữ liệu | Không |

---

## 4. Phân biệt PUT và PATCH

Sản phẩm ban đầu:

```json
{
  "id": 1,
  "name": "Bút bi",
  "price": 5000
}
```

### Dùng PUT

```http
PUT /products/1
```

Body:

```json
{
  "name": "Bút mực"
}
```

Kết quả:

```json
{
  "id": 1,
  "name": "Bút mực",
  "price": null
}
```

PUT thường thay thế toàn bộ dữ liệu nên các trường không gửi lên có thể bị mất.

---

### Dùng PATCH

```http
PATCH /products/1
```

Body:

```json
{
  "name": "Bút mực"
}
```

Kết quả:

```json
{
  "id": 1,
  "name": "Bút mực",
  "price": 5000
}
```

PATCH chỉ cập nhật phần dữ liệu được gửi lên.

---

## 5. HTTP Status Codes

| Mã | Ý nghĩa | Tình huống ví dụ |
|---|---|---|
| 200 | OK | Lấy danh sách sinh viên thành công |
| 201 | Created | Thêm sinh viên mới thành công |
| 204 | No Content | Xóa dữ liệu thành công |
| 400 | Bad Request | Thiếu dữ liệu hoặc sai dữ liệu |
| 404 | Not Found | Không tìm thấy sinh viên |
| 500 | Internal Server Error | Lỗi phía server |