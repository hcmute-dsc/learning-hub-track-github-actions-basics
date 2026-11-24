Repo `diem-trung-binh` giờ có nhiều workflow lặp lại cùng một đoạn. Dọn nó theo chương 6, làm trên một nhánh và nộp bằng **một pull request**.

## Yêu cầu

1. **Composite action** `.github/actions/setup-project/action.yml` như bài "Composite action": cài Node (có cache npm) và chạy `npm ci`.
2. **Reusable workflow** `.github/workflows/node-test.yml` như bài "Reusable workflow", dùng composite action ở trên thay cho step setup-node và `npm ci`.
3. **Gọi lại ở hai nơi:**
   - `ci.yml`: job `test` gọi `node-test.yml` trong matrix Node 22, 24, 26;
   - `deploy-demo.yml` (chương 4): thay job `test` tự viết bằng job gọi `node-test.yml` với `node-version: "24"`; job `deploy` giữ `needs: test` và `environment: production`.
4. **Ghim SHA** cho mọi action **không** thuộc `actions/` mà repo đang dùng (nếu repo có `pages.yml` với `lycheeverse/lychee-action`, đó là một ví dụ), kèm chú thích phiên bản. Ghim thêm `actions/` cũng được, không bắt buộc.
5. **Dependabot:** `.github/dependabot.yml` cho `github-actions` và `npm`.
6. **Ruleset:** sửa required checks theo tên check mới (dạng `test (22) / run-tests`).

## Nộp bài

Nộp **link pull request**. Trong mô tả PR, ghi:

- danh sách file thêm/sửa, mỗi file một dòng nói nó làm gì;
- với mỗi action đã ghim SHA: lệnh bạn dùng để tìm SHA (ví dụ `git ls-remote ...`);
- trước và sau: số dòng YAML bị lặp lại đã bỏ được (ước lượng là đủ).

Nếu repo của bạn không có action bên thứ ba nào, ghi rõ điều đó trong PR và ghim SHA cho `actions/checkout` để mentor chấm tiêu chí ghim.

## Tiêu chí chấm

Mentor chấm theo rubric trong bài tập:

| Tiêu chí | Đạt khi |
| --- | --- |
| Composite action | Input có `default`, có `cache: npm`, mọi `run` có `shell` |
| Reusable workflow | `on: workflow_call`, input `required`; được gọi ở cấp job từ cả `ci.yml` và `deploy-demo.yml` |
| Không lặp lại | Đoạn setup-node + `npm ci` chỉ còn ở composite action |
| Ghim SHA | 40 ký tự, có chú thích, SHA đúng là của tag được ghi |
| Dependabot và ruleset | File đúng chỗ; check bắt buộc khớp tên mới; PR xanh |

Kẹt ở đâu, hỏi trong kênh Discord của track hoặc nhắn riêng mentor (tab **Cài đặt** → "Hỏi ở đâu").
