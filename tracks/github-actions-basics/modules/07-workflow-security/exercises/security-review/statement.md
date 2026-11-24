Bạn là người review một pull request thêm workflow dưới đây vào repo của nhóm. **Đừng chép workflow này vào repo nào.** Đọc nó, tìm lỗi, rồi đánh dấu từng mục khi xong.

```yaml
name: PR helper

on: pull_request_target

permissions: write-all

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v7
        with:
          ref: ${{ github.event.pull_request.head.sha }}

      - uses: some-user/setup-tools@main

      - name: Build
        env:
          DEPLOY_TOKEN: ${{ secrets.DEPLOY_TOKEN }}
        run: |
          set -x
          echo "Đang build nhánh ${{ github.head_ref }}"
          npm ci
          npm test
```

Ghi danh sách lỗi ra giấy hoặc một file trên máy, mỗi lỗi một dòng theo mẫu: **dòng nào**, **sai gì**, **kẻ xấu lợi dụng thế nào**, **sửa thế nào**. Dùng danh sách tự kiểm tra ở mục 6 của bài "Script injection" làm khung, và chạy actionlint (bài đó, mục 5) trên bản viết lại của bạn nếu máy có Docker.

Muốn mentor xem danh sách của bạn? Gửi vào kênh Discord của track, hoặc nhắn riêng mentor (tab **Cài đặt** → "Hỏi ở đâu").

<details>
<summary>Gợi ý nếu bị kẹt</summary>

- Workflow mẫu có **6** lỗi, mỗi lỗi ứng với ít nhất một mục trong danh sách tự kiểm tra.
- Đọc từ trên xuống: event, permissions, checkout, action thứ hai, rồi từng dòng trong `run`.
- Với mỗi dòng có `${{ }}`, hỏi: "giá trị này ai đặt?" (bảng ở mục 4 bài "Script injection").
- Với mỗi action, hỏi: "của ai, ghim bằng gì?" (chương 6, bài 3).
- Vẫn kẹt: hỏi mentor. Đọc gợi ý vẫn chưa hiểu thì nhắn mentor, đừng chỉ hỏi AI.

</details>
