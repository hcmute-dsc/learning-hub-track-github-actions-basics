Đưa portfolio của bạn lên GitHub Pages bằng workflow ở chương này, có job kiểm tra link chạy trước job deploy. Đánh dấu từng mục khi xong.

Chưa có portfolio? Một file `index.html` có tên bạn, một file `style.css` và một ảnh là đủ cho chương này. Track chấm workflow, không chấm giao diện.

Gửi link trang Pages của bạn vào kênh Discord của track để mentor biết bạn đã xong phần này. Không muốn đăng công khai thì nhắn riêng cho mentor (tab **Cài đặt** → "Hỏi ở đâu").

<details>
<summary>Gợi ý nếu bị lỗi</summary>

- `configure-pages` báo `Not Found`: vào **Settings** → **Pages**, chọn **Source: GitHub Actions**.
- Trang trắng hoặc 404: phải có `index.html` ở đúng thư mục `path` của `upload-pages-artifact`.
- Mất CSS: link bắt đầu bằng `/` hoặc sai hoa thường tên file.
- `deploy` báo nhánh không được phép: bạn đang chạy từ nhánh khác `main`; merge PR trước.

</details>
