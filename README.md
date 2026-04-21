# Telegram Image Background Remover Bot (n8n Workflow)

Đây là dự án giữa kỳ môn học: Xây dựng hệ thống tự động hóa sử dụng n8n để nhận hình ảnh từ người dùng qua Telegram, gọi API tách nền trong suốt và tự động lưu trữ kết quả vào Google Drive.

## 🚀 Luồng hoạt động (Workflow)
1. **Telegram Trigger:** Lắng nghe tin nhắn và nhận hình ảnh từ người dùng.
2. **Prepare FileName:** Tự động sinh tên file mới dựa trên thời gian thực.
3. **HTTP Request (Remove.bg):** Gọi API để xử lý xóa phông nền ảnh.
4. **Google Drive:** Tự động lưu bức ảnh đã xóa nền (.png) vào thư mục chỉ định.

## ⚙️ Yêu cầu hệ thống (Prerequisites)
Để chạy được luồng này, bạn cần chuẩn bị:
- Đã cài đặt n8n (Local hoặc Cloud).
- **Telegram Bot Token** (Lấy từ `@BotFather` trên Telegram).
- **Remove.bg API Key** (Đăng ký miễn phí tại remove.bg/api).
- **Google Drive API Credentials** (Thiết lập OAuth2 trên Google Cloud Console).

## 🛠️ Hướng dẫn cài đặt
1. Tải file `Midterm_n8n_Telegram_Image_Editor.json` từ repository này về máy.
2. Mở n8n, chọn dấu `...` ở góc trên bên phải màn hình làm việc và chọn **Import from File**, sau đó tải file vừa tải lên.
3. Mở từng Node và thiết lập lại các thông tin xác thực (Credentials) bằng tài khoản của bạn:
   - Node **Telegram Trigger**: Chọn/Thêm Telegram account.
   - Node **HTTP Request**: Đổi `Value` của trường `X-Api-Key` thành API Key Remove.bg của bạn.
   - Node **Google Drive**: Chọn/Thêm Google Drive account và trỏ lại đúng thư mục lưu trữ (`Parent Folder`).
4. Bật công tắc **Active** (góc phải trên cùng n8n) để kích hoạt Bot.
