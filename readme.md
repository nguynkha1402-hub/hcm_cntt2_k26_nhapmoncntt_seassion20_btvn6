1. Pre-push Checklist (Quét API Keys)

- Dùng công cụ (`gitleaks`, `trufflehog`) quét tự động lịch sử commit.
- Thiết lập Git Hook (`pre-push`) để chặn đẩy code nếu phát hiện chuỗi giống Token/Password.
- Xóa mã hardcode, thay bằng biến môi trường và loại bỏ các tệp nhạy cảm khỏi thư mục public. 
 

2. Cấu trúc tệp `.env.example`

```
# DEV
DEV_DB_HOST=localhost
DEV_API_KEY=your_dev_api_key_here
# TEST
TEST_DB_HOST=test-db.internal
# PROD (Bỏ trống giá trị)
PROD_DB_HOST=
PROD_AWS_ACCESS_KEY_ID=
```

3. Bắt buộc 2FA cho Organization

- Vào GitHub > Your organizations > Chọn tổ chức > Settings.
- Mục Security > Authentication security > Tick chọn Require two-factor authentication for everyone > Save.

4. Cấu trúc Repository & Rủi ro thiếu `.gitignore`

-Cấu trúc: Cần có thư mục `src/`, `docs/`, file `.env.example`, `.gitignore` và `README.md`.

-Rủi ro thiếu `.gitignore`:

- Rò rỉ mật khẩu, API Key dẫn đến bị hack hệ thống hoặc đánh cắp dữ liệu.   
- Đẩy nhầm thư mục nặng (`node_modules/`,` build/`) làm treo hệ thống CI/CD.
- Gây xung đột liên tục do các file log hoặc file cấu hình máy cá nhân.