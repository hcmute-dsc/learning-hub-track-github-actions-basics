Nâng cấp `ci.yml` của repo `diem-trung-binh` bằng ba thứ của chương 5. Làm trên một nhánh, mở PR, đánh dấu từng mục khi xong.

1. **Matrix** Node 22, 24, 26 với `fail-fast: false` (bài "Matrix").
2. **Cache** npm bằng `cache: npm` của `setup-node` (bài "Cache"). Chạy lại lần thứ hai (push thêm một commit, hoặc **Re-run jobs**) để thấy cache hit.
3. **Artifact**: đổi step test thành `npm test 2>&1 | tee test-report.txt`, rồi upload `test-report.txt` với `if: always()` và tên có `${{ matrix.node-version }}` (bài "Artifact", mục 2 và 4).

Nhớ sửa ruleset trước khi merge (bài "Matrix", mục 5), nếu không PR sẽ treo.

<details>
<summary>Gợi ý nếu bị lỗi</summary>

- Chỉ có 1 check: `matrix` phải nằm trong `strategy`, và `strategy` ngang hàng với `runs-on`.
- `Conflict: an artifact with this name already exists`: tên artifact chưa có giá trị matrix.
- Lần hai vẫn không thấy `Cache restored`: lần đầu phải **xanh** thì cache mới được lưu; cache lưu trên nhánh PR chỉ dùng được cho chính nhánh đó.
- Vẫn kẹt: gửi link lần chạy vào kênh Discord của track, hoặc nhắn riêng mentor.

</details>
