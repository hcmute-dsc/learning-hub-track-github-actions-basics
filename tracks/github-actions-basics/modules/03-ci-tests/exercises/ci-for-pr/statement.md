Hoàn thiện repo `diem-trung-binh` (chương 3) thành một repo có CI chặn merge, đúng như cách các nhóm làm ở công ty.

## Yêu cầu

1. **CI:** `.github/workflows/ci.yml` như bài "Workflow CI", chạy trên `pull_request` và `push` lên `main`.
2. **Ruleset:** bật ruleset cho nhánh mặc định như bài "Status check và required check": bắt buộc PR, bắt buộc check `test`.
3. **Tính năng mới qua PR.** Tạo nhánh `them-isPassed`, thêm hàm sau vào `src/grade.js`, và thêm `isPassed` vào `module.exports`:

   ```js
   // Đậu khi điểm trung bình từ 5 trở lên
   function isPassed(avg) {
     return avg >= 5;
   }
   ```

   Rồi tự viết một `test(...)` mới trong `test/grade.test.js` cho `isPassed`, dùng `assert.equal` như các test có sẵn. Cần ít nhất 3 ca: một điểm đậu rõ ràng, một điểm trượt rõ ràng, và **đúng mốc 5**.
4. **Thấy đỏ một lần.** Cố tình push một commit làm test đỏ (ví dụ đổi `>=` thành `>` trong `isPassed`), xem PR bị **Merging is blocked**. Sau đó sửa lại và push để PR xanh.
5. **Mô tả PR:** 2–4 câu: PR thêm gì, lần đỏ là do đâu (trích dòng actual/expected trong log), đã sửa thế nào.
6. **README:** thêm badge CI.

## Nộp bài

Nộp **link pull request** (chưa merge cũng được, mentor cần xem lịch sử check). Trong mô tả PR, thêm ảnh chụp trang PR lúc **Merging is blocked**, hoặc ảnh chụp trang ruleset. Ảnh không được có email hay thông tin cá nhân khác; ngại đăng thì gửi riêng ảnh cho mentor.

## Tiêu chí chấm

Mentor chấm theo rubric trong bài tập:

| Tiêu chí | Đạt khi |
| --- | --- |
| Workflow CI | Đúng event, có `node-version`, `npm ci` rồi `npm test`, `permissions: contents: read` |
| Test cho `isPassed` | Có ít nhất 3 ca, có mốc 5; lockfile đã commit, không có `node_modules/` |
| Lịch sử PR | Thấy một lần check `test` đỏ và lần sau xanh; mô tả giải thích lần đỏ |
| Ruleset | Active, bắt buộc PR và check `test` |
| Badge | Hiện đúng trạng thái của `ci.yml` |

Kẹt ở đâu, hỏi trong kênh Discord của track hoặc nhắn riêng mentor (tab **Cài đặt** → "Hỏi ở đâu").
