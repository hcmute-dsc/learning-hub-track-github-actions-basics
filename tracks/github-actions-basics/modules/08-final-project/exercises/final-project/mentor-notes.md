## Khi review bài này

Làm theo thứ tự, ghi chú cho từng tiêu chí của rubric:

1. **Đọc README như người lạ.** Bảng pipeline có khớp với các file trong `.github/workflows/` không. Thiếu mục Bằng chứng thì hỏi trước khi chấm tiếp (có thể thành viên đã gửi riêng).
2. **Xem từng workflow** trong tab **Files changed**. Tìm nhanh các mẫu nguy hiểm: `pull_request_target`, `write-all`, `${{ github.event.` hoặc `${{ github.head_ref` nằm trong `run:`, `echo` có `secrets.`, `set -x`, action bên thứ ba ghi `@main` hoặc tag thay vì SHA.
3. **Kiểm tra SHA** của một vài action đã ghim: `git ls-remote https://github.com/<owner>/<repo> refs/tags/<tag trong chú thích>`.
4. **Chạy actionlint** trên nhánh của PR nếu thành viên không có Docker: clone, `git switch <nhánh>`, rồi lệnh ở chương 1 bài 3. Lỗi `potentially untrusted` là chưa đạt tiêu chí An toàn.
5. **Xem các lần chạy:** có một lần đỏ thật trên PR và lần xanh sau đó; deploy chỉ chạy trên `main` (trên PR phải là skipped hoặc không có).
6. **Ruleset:** nhờ thành viên gửi ảnh chụp, hoặc xem trang PR có dòng "Required" cạnh các check.

## Lỗi hay gặp

- Required check không khớp tên sau khi thêm matrix hoặc reusable workflow (PR treo ở "Expected"). Chỉ cách đọc tên check trên trang PR rồi sửa ruleset.
- Deploy chạy cả trên PR vì thiếu `if`, hoặc vì workflow deploy có `on: pull_request`.
- Job xin `permissions` ở cấp job nhưng quên `contents: read`, rồi thêm `contents: write` cho "chắc ăn". Hỏi vì sao cần quyền ghi.
- Repo private: ruleset và Required reviewers không được áp dụng với tài khoản miễn phí.

## Góp ý nên tránh

- Chấm giao diện trang web hay chất lượng code của project. Track chấm pipeline.
- Đòi công cụ ngoài track (Docker, Kubernetes, deploy lên cloud).
- Viết lại workflow giúp thành viên. Chỉ ra dòng nào, mục nào trong danh sách tự kiểm tra, để họ tự sửa.

## Khi nhận xét

Nêu ít nhất một điểm làm tốt và một điểm nên sửa, gắn với tiêu chí cụ thể. Viết nhận xét ngay trên dòng code trong PR khi có thể. Bài chưa đạt: ghi rõ tiêu chí nào và cách kiểm tra lại, để thành viên sửa trên cùng nhánh và nộp lại.
