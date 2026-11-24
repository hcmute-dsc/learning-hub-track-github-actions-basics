Dựng pipeline CI/CD hoàn chỉnh cho **một repo public của bạn**, theo bài "Hướng dẫn dự án cuối".

## Yêu cầu

- **CI** chạy trên `pull_request` và `push` lên `main`, làm một việc kiểm tra thật (test, hoặc kiểm tra link) và đỏ khi có lỗi.
- **Ruleset** cho `main`: bắt buộc PR, bắt buộc các check của CI.
- **Deploy** chỉ từ `main`, có `needs` tới một job test **trong cùng file workflow** (`needs` không nối được sang file khác: cho `deploy.yml` tự có job test gọi reusable workflow, hoặc đặt job deploy trong `ci.yml` với `if: github.event_name == 'push'`), qua một `environment` có luật bảo vệ. Pages: environment `github-pages`. Không có chỗ deploy thật: deploy giả lập bằng `echo` như chương 4, environment `production` có Required reviewers.
- **Ít nhất một** trong: matrix, cache, artifact.
- **Ít nhất một** trong: reusable workflow, composite action.
- **An toàn:** đạt danh sách tự kiểm tra ở mục 6 bài "Script injection"; action bên thứ ba ghim SHA kèm chú thích; có `.github/dependabot.yml`.
- **README:** badge CI, bảng pipeline, đoạn bảo mật, mục **Bằng chứng**.

## Nộp bài

Làm trên một nhánh, mở **một pull request** vào `main` của repo đó, và nộp **link PR**. Trong README (hoặc mô tả PR), mục **Bằng chứng** gồm:

- link một lần chạy CI **đỏ** trên PR (cố tình làm hỏng một lần) và lần chạy xanh sau khi sửa;
- link lần chạy deploy trên `main` (với deploy giả lập: thấy job chờ duyệt rồi chạy). Nếu PR nộp bài chưa merge, dùng lần chạy từ các bài trước hoặc merge một PR nhỏ khác để có bằng chứng;
- một câu cho mỗi mục trong danh sách tự kiểm tra bảo mật: repo đáp ứng ở file nào, dòng nào.

Ảnh chụp không được có email hay thông tin cá nhân. Không muốn để bằng chứng công khai thì gửi riêng cho mentor (tab **Cài đặt** → "Hỏi ở đâu"), và ghi trong PR "đã gửi bằng chứng cho mentor".

Khuyến khích: review PR dự án cuối của một bạn khác trong track và để lại ít nhất một bình luận có ích.

## Tiêu chí chấm

Mentor đọc README, xem các workflow và các lần chạy, rồi chấm theo rubric trong bài tập:

| Tiêu chí | Đạt khi |
| --- | --- |
| CI và required checks | PR đỏ thì không merge được; tên check trong ruleset khớp |
| Deploy | Không chạy trên PR; có `needs` tới job test cùng file và `environment` có luật |
| Matrix, cache hoặc artifact | Dùng đúng, có tác dụng thấy được trong log |
| Tái sử dụng | Bớt được đoạn lặp, gọi đúng cấp (job hoặc step) |
| An toàn | Đạt mọi mục của danh sách tự kiểm tra |
| README | Người chưa biết gì về repo hiểu pipeline chạy thế nào |
| Quy trình | Nộp bằng PR, trả lời nhận xét trên cùng nhánh |

Kẹt ở đâu, hỏi trong kênh Discord của track hoặc nhắn riêng mentor. Hỏi giữa chừng là bình thường, không cần đợi làm xong mới hỏi.
