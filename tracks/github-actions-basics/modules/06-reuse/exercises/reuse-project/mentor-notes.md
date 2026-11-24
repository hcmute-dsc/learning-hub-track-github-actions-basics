## Khi review bài này

1. Mở tab **Files changed**. Tìm `setup-node` và `npm ci` trong mọi file: chỉ được còn trong `.github/actions/setup-project/action.yml`.
2. `node-test.yml`: có `on: workflow_call`, input `node-version` có `required: true`, dùng `uses: ./.github/actions/setup-project` **sau** checkout. Step test dùng `tee` phải có `shell: bash` (không có thì test trượt mà step vẫn xanh); upload artifact có `if: always()` và tên chứa `inputs.node-version` (dùng `matrix.` trong workflow được gọi là sai). `report.yml` đã xóa hoặc cũng gọi `node-test.yml`.
3. `ci.yml` và `deploy-demo.yml`: job gọi có `uses:` ở cấp job, không có `runs-on`/`steps`; `deploy` vẫn có `needs: test` và `environment: production`.
4. Kiểm tra SHA: với mỗi action ghim SHA, chạy `git ls-remote https://github.com/<owner>/<repo> "refs/tags/<tag>" "refs/tags/<tag>^{}"` (tag lấy từ chú thích) và so với SHA trong file: có dòng `^{}` thì SHA đúng là của dòng đó. Lệch là chưa đạt tiêu chí ghim, kể cả khi workflow vẫn chạy.
5. Xem tab **Checks** của PR: các check dạng `test (22) / run-tests` xanh; PR không treo ở "Expected".

## Lỗi hay gặp

- `uses: ./.github/actions/setup-project` đặt trước checkout: lỗi `Can't find 'action.yml'`.
- Quên `shell: bash` trong composite action.
- Chú thích phiên bản không khớp SHA (chép SHA của `v7` nhưng ghi `# v7.0.0`). Hỏi thành viên đã tìm SHA bằng lệnh nào.
- `deploy-demo.yml` gọi reusable workflow nhưng truyền `node-version: 24` không có nháy: vẫn chạy được, không trừ điểm.

## Góp ý nên tránh

- Đòi tách action ra repo riêng hay tạo release: ngoài phạm vi chương.
- Trừ điểm vì không ghim SHA cho `actions/`: bài chỉ bắt buộc với action bên thứ ba.

## Khi nhận xét

Nêu ít nhất một điểm làm tốt và một điểm nên sửa, gắn với tiêu chí cụ thể. Bài chưa đạt: ghi rõ tiêu chí nào và cách kiểm tra lại, để thành viên sửa và nộp lại.
