Làm lại ba workflow của chương 4 trong repo `diem-trung-binh`: `env-demo.yml`, `secret-demo.yml`, `deploy-demo.yml`. Đánh dấu từng mục khi xong.

Vì ruleset ở chương 3, mỗi workflow mới phải vào `main` qua pull request. Gộp cả ba vào một PR cũng được.

**Chỉ dùng giá trị giả** cho mọi secret trong bài này (`gia-tri-gia-123456`, `token-gia-cho-prod`). Không bao giờ thử masking với token thật.

<details>
<summary>Gợi ý nếu bị lỗi</summary>

- Biến in ra rỗng: so tên từng chữ, phân biệt hoa thường; xem biến khai báo ở cấp workflow, job hay step.
- `Độ dài token: 0`: secret sai tên, hoặc `DEPLOY_TOKEN` được tạo ở **Repository secrets** thay vì **Environment secrets** của `production`.
- Không thấy nút Approve: thêm chính bạn vào Required reviewers và tắt **Prevent self-review**.
- Repo private: Required reviewers với repo private cần gói GitHub Enterprise. Chuyển repo sang public.
- Vẫn kẹt: hỏi trong kênh Discord của track hoặc nhắn riêng mentor, gửi kèm link lần chạy.

</details>
