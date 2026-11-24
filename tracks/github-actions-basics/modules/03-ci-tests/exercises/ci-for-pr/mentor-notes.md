## Khi review bài này

1. Mở PR, xem danh sách commit và tab **Checks**: phải thấy ít nhất một commit có check `test` đỏ và commit sau xanh. Không có lần đỏ thì chưa đạt tiêu chí "Lịch sử PR".
2. Mở `ci.yml`: event `pull_request` và `push` lên `main`, có `node-version`, dùng `npm ci` (không phải `npm install`), có `permissions: contents: read`, mọi action có phiên bản.
3. Mở test của `isPassed`: có ca đúng mốc 5 không. Đây là ý chính của bài (mốc biên).
4. Ruleset: xem ảnh chụp, hoặc nhờ thành viên thử push thẳng lên `main` và gửi lại thông báo `GH013`.
5. Xem repo có `node_modules/` bị commit không, có `package-lock.json` không.

## Lỗi hay gặp

- Required check chọn sai tên (gõ `CI` hoặc `ci.yml` thay vì tên job `test`), nên PR treo ở trạng thái "Expected, Waiting for status". Hướng dẫn sửa tên trong ruleset.
- Quên thêm `isPassed` vào `module.exports`: log báo `isPassed is not a function`. Lỗi tốt để hỏi thành viên đọc log thế nào.
- Repo private trên tài khoản miễn phí: ruleset không được áp dụng. Nhắc chuyển repo sang public.

## Góp ý nên tránh

- Đòi dùng test framework khác (Jest, Vitest). Track dùng `node --test` có sẵn cho đơn giản.
- Chấm phong cách JavaScript. Bài chấm quy trình CI, không chấm code.

## Khi nhận xét

Nêu ít nhất một điểm làm tốt và một điểm nên sửa, gắn với tiêu chí cụ thể. Bài chưa đạt: ghi rõ tiêu chí nào và cách kiểm tra lại, để thành viên sửa và nộp lại.
