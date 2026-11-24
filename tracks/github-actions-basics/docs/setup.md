Làm các bước dưới đây **một lần**, trước bài học đầu tiên. Mất khoảng 20–30 phút. Chương 1–2 chỉ cần mục 1 và VS Code; Node.js cần từ chương 3.

## 1. Chuẩn bị chung

**Terminal.** Trên Windows, track này dùng **PowerShell** (mở Start, gõ "PowerShell"). macOS và Linux dùng **Terminal**. Lệnh nào khác nhau giữa hai loại, bài học sẽ ghi cả hai.

**Git.**

- **Windows**: tải [Git for Windows](https://git-scm.com/download/win), giữ các lựa chọn mặc định.
- **macOS**: chạy `xcode-select --install` trong Terminal.
- **Ubuntu**: `sudo apt install git`.

Rồi khai báo tên và email. Git ghi chúng vào mỗi commit; thiếu thì commit báo lỗi `Author identity unknown`. Dùng email của tài khoản GitHub:

```bash
git config --global user.name "Tên của bạn"
git config --global user.email "email-github-cua-ban@example.com"
```

**Tài khoản GitHub** ([đăng ký](https://github.com/signup)), và tham gia **Discord của HCMUTE DSC** để hỏi bài. Track này cần bạn đã biết commit, push, tạo nhánh và mở pull request (track Git/GitHub của CLB).

**Repo public.** Mọi bài thực hành dùng repo **public** trên tài khoản của bạn: GitHub Actions chạy miễn phí không giới hạn phút, và các tính năng ở chương 3–4 chỉ dùng được với tài khoản miễn phí khi repo là public (ruleset được áp dụng; required reviewers của environment với repo private còn cần gói GitHub Enterprise). Vì repo public ai cũng đọc được, **không bao giờ** để token, mật khẩu hay thông tin cá nhân trong repo; chương 4 dạy chỗ cất đúng.

**Mấy lệnh khác nhau trên Windows** (gặp trong bài thì quay lại đây):

| Việc | macOS / Linux | Windows PowerShell |
| --- | --- | --- |
| xem exit code của lệnh vừa chạy | `echo $?` | `echo $LASTEXITCODE` |
| đọc biến môi trường | `echo $HOME` | `echo $env:USERPROFILE` |
| đặt biến môi trường | `export X=1` | `$env:X = "1"` |
| thư mục hiện tại trong lệnh `docker -v` | `"$(pwd):/repo"` | `"${PWD}:/repo"` |
| gọi HTTP | `curl` | `curl.exe` (gõ `curl` sẽ ra lệnh khác) |

Lệnh trong khối `yaml` của bài học chạy trên **runner Linux** của GitHub, không chạy trên máy bạn, nên luôn viết kiểu bash, kể cả khi bạn dùng Windows.

## 2. Cài công cụ của track

### VS Code và extension GitHub Actions (từ chương 1)

1. Cài [Visual Studio Code](https://code.visualstudio.com/).
2. Mở VS Code → biểu tượng **Extensions** ở cột trái (hoặc `Ctrl+Shift+X`, macOS `Cmd+Shift+X`) → tìm **GitHub Actions** → chọn extension của nhà phát hành **GitHub** → **Install**.

Extension tô màu file workflow, gợi ý khóa, và gạch đỏ chỗ sai cú pháp ngay khi gõ. Khi được hỏi, đăng nhập GitHub để nó xem được các lần chạy.

### Node.js (từ chương 3)

Cài bản **LTS** (số chẵn, 22 trở lên). `npm` đi kèm Node.js.

- **Windows**: tải bản LTS ở [nodejs.org](https://nodejs.org/), chạy file `.msi`, giữ lựa chọn mặc định. Hoặc trong PowerShell: `winget install OpenJS.NodeJS.LTS`.
- **macOS**: tải bản LTS ở [nodejs.org](https://nodejs.org/) (file `.pkg`), giữ lựa chọn mặc định. Dùng Homebrew thì `brew install node@24` **chưa đủ**: bản có số phiên bản được cài "keg-only", tức không tự thêm vào `PATH`, nên gõ `node` vẫn báo không có. Chạy thêm `brew link --overwrite node@24`, hoặc dùng [nvm](https://github.com/nvm-sh/nvm) như Ubuntu.
- **Ubuntu**: gói `nodejs` của `apt` thường quá cũ. Dùng [nvm](https://github.com/nvm-sh/nvm) theo hướng dẫn trên trang đó, rồi `nvm install --lts`.

Cài xong, **đóng terminal và mở lại** để terminal thấy lệnh mới.

### Docker (không bắt buộc)

Chỉ dùng để chạy **actionlint** (chương 1, bài 3 và chương 7) trên máy. Không có Docker thì bỏ qua: extension VS Code đủ cho track, và mentor có thể chạy actionlint giúp bạn. Đã có Docker Desktop (ví dụ từ track Docker của CLB) thì dùng luôn.

## 3. Tự kiểm tra

```bash
git --version
git config --global user.name
node --version
npm --version
```

Kết quả mong đợi:

- `git version 2.x` và tên của bạn;
- `v22.x`, `v24.x` hoặc mới hơn (số đầu là số chẵn từ 22 trở lên);
- một số phiên bản npm, ví dụ `10.x` hoặc `11.x`.

Thấy đủ là xong. Chưa tới chương 3 thì chưa cần Node.js.

## 4. Khi bị lỗi

| Lỗi | Cách sửa |
| --- | --- |
| `git: command not found` | Mở lại terminal sau khi cài; trên Windows, chọn "Git from the command line" khi cài |
| `Author identity unknown` khi commit | Chạy hai lệnh `git config` ở mục 1 |
| `node`/`npm` không được nhận ra (`is not recognized`, `command not found`) | Đóng hết terminal và VS Code, mở lại. Vẫn lỗi trên Windows thì đăng xuất rồi đăng nhập lại |
| `node --version` ra số lẻ (23, 25) hoặc dưới 22 | Cài lại bản LTS |
| PowerShell báo `running scripts is disabled on this system` khi chạy `npm` | Chạy `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` một lần, chọn `Y` |
| `git push` bị từ chối với `GH013` (từ chương 3) | Repo có ruleset bắt buộc PR: tạo nhánh, push nhánh, mở PR |

## 5. Hỏi ở đâu

**Không có câu hỏi nào là ngớ ngẩn.** Mentor viết track này vì muốn bạn hỏi. Câu bạn đang thắc mắc, chắc chắn có người khác cũng đang thắc mắc.

- **Hỏi chung:** kênh Discord của track trên server HCMUTE DSC. Hỏi ở đây thì người khác cũng học được từ câu trả lời.
- **Hỏi riêng:** ngại hỏi trước mọi người thì nhắn riêng (DM) cho mentor của track trên Discord: **@TienNHM**. Hỏi riêng cũng hoàn toàn bình thường.
- **Sau khi nộp bài:** trả lời ngay trong mục "Trao đổi với mentor" dưới nhận xét của bài.

Mọi người trong CLB theo [Quy tắc ứng xử](https://github.com/hcmute-dsc/.github/blob/master/CODE_OF_CONDUCT.md): không ai được chê câu hỏi của bạn, và câu hỏi riêng được giữ kín. Bị đối xử không đúng thì nhắn riêng Ban chủ nhiệm trên Discord.

Khi hỏi, gửi kèm: bạn đang ở bài nào, **link lần chạy** trong tab Actions (hoặc lệnh đã chạy), và ảnh chụp lỗi. Nếu lỗi có token, mật khẩu hay webhook URL thì **che phần đó** trước khi gửi (chương 4, bài "Secrets", mục "Hỏi bài mà không lộ secret"). Link lần chạy thường an toàn để gửi: GitHub đã che secret thành `***` trong log, **miễn là** workflow không in secret đã bị biến đổi (đảo ngược, base64… xem chương 4). Thấy log có chuỗi lạ giống token thì đừng gửi link, hỏi riêng mentor.
