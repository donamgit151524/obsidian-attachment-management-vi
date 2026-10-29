# Attachment Management — bản tùy chỉnh tiếng Việt

Việt hóa và giữ các sửa lỗi nhập tệp, xử lý PDF trong bản đang dùng.

Đây là bản tùy chỉnh cá nhân, không phải bản phát hành chính thức. Đóng gói ngày 2026-10-29.

## Nguồn và giấy phép

- Plugin gốc: https://github.com/trganda/obsidian-attachment-management
- Phiên bản nền: 0.12.1; tác giả: trganda.
- Giữ giấy phép gốc trong LICENSE. source/upstream.zip chứa mã nguồn gốc đúng bản; source/*.patch ghi lại thay đổi của bản cài hiện tại so với bản sao lưu. patch-tools/ chứa công cụ sửa/Việt hóa ban đầu, tham chiếu cấu trúc vault gốc; không chạy trực tiếp trong repository này.
- main.js và styles.css là bản đang dùng, đã đóng gói để cài; thay đổi phiên bản manifest thành 0.12.1-vi.1. Các tùy chỉnh bổ sung có thể không nằm hết trong công cụ Việt hóa; bản diff là tài liệu đầy đủ của các thay đổi bundle.

## Cài qua BRAT

1. Cài và bật BRAT.
2. Chọn Add a beta plugin, nhập URL repository này.
3. Chọn release 0.12.1-vi.1 nếu BRAT yêu cầu.

ID vẫn là attachment-management để dùng được cấu hình hiện có. Trên vault đã cài plugin gốc, hãy sao lưu cấu hình trước khi chuyển sang bản này. Cập nhật từ danh mục Community plugins có thể ghi đè bản tùy chỉnh; dùng BRAT cho repository này. Không cài song song hai bản cùng ID.

## Phát hành

Tạo GitHub Release có tag khớp version trong manifest.json. Đính kèm main.js, manifest.json và styles.css (nếu có) trực tiếp vào release; không chỉ đính kèm ZIP. Khi cập nhật, tăng phiên bản và cập nhật versions.json.

Không chứa data.json, ghi chú, thông tin đăng nhập hoặc cấu hình cá nhân.

Mã nguồn và bản diff được đóng gói trong source-bundle.zip; giải nén để xem các thư mục source/ và patch-tools/.

