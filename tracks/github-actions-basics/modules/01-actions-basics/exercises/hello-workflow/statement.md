Thêm workflow `hello.yml` (bài "Viết workflow đầu tiên") vào repo portfolio của bạn, làm nó đỏ một lần rồi sửa cho xanh lại (bài "Khi workflow bị đỏ"). Đánh dấu từng mục khi xong.

Với mục cuối: thêm `workflow_dispatch:` vào `on:` như mục "Chọn event" của bài "Viết workflow đầu tiên". Khi có hơn một event, `on:` phải viết dạng nhiều dòng:

```yaml
on:
  push:
  workflow_dispatch:
```

Sau khi push, nút **Run workflow** xuất hiện ở tab **Actions** khi bạn chọn workflow **Hello** ở cột trái.

<details>
<summary>Gợi ý nếu bị lỗi</summary>

- Không thấy lần chạy nào: kiểm tra đường dẫn `.github/workflows/hello.yml` (có dấu chấm ở đầu `.github`, có chữ `s` ở `workflows`).
- `Invalid workflow file`: mở file trên GitHub, dòng lỗi được tô đỏ. Thường là thụt lề bằng Tab.
- Không thấy nút **Run workflow**: `workflow_dispatch` chỉ có hiệu lực khi file đã nằm trên nhánh mặc định (`main`).
- Vẫn kẹt: gửi link lần chạy vào kênh Discord của track, hoặc nhắn riêng mentor.

</details>
