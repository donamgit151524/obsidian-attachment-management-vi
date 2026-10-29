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


## Công dụng

Attachment Management tổ chức tệp đính kèm theo ghi chú: chọn thư mục lưu ảnh/PDF, đặt tên bằng biến và tự đổi đường dẫn khi đổi tên ghi chú. Bản này giữ Việt hóa cùng các sửa lỗi nhập tệp/PDF của bản tùy chỉnh.

## Thiết lập lần đầu

1. Mở Settings → Attachment Management. Mục **Ngôn ngữ / Language — VI / EN** bật tương ứng tiếng Việt.
2. Chọn **Vị trí gốc lưu tệp đính kèm** phù hợp. Nếu chọn thư mục chỉ định, điền thư mục gốc, ví dụ `Tai lieu dinh kem`.
3. Đặt **Đường dẫn tệp đính kèm**, ví dụ `${notename}` để mỗi ghi chú có thư mục con theo tên.
4. Đặt **Mẫu tên tệp đính kèm**, ví dụ `${originalname}` để giữ tên gốc, hoặc `IMG-${date}` nếu muốn dùng ngày giờ. Plugin xử lý phần mở rộng; không thêm `.png` cố định cho mọi loại tệp.
5. Nếu dùng `${date}`, kiểm tra **Định dạng ngày giờ**, ví dụ `YYYYMMDD-HHmmss`.
6. Tạo ghi chú thử, dán ảnh hoặc đính kèm một bản sao PDF và kiểm tra vị trí/tên tệp thực tế.

Ví dụ với thư mục gốc `Tai lieu dinh kem`, đường dẫn `${notename}` và tên `${originalname}`: tệp `datasheet.pdf` được đính kèm cho ghi chú `RCC.md` sẽ nằm trong thư mục con theo tên `RCC`, theo thiết lập vị trí gốc đã chọn.

## Các biến thường dùng

| Biến | Công dụng |
|---|---|
| `${notename}` | Tên ghi chú |
| `${notepath}` | Đường dẫn ghi chú |
| `${parent}` | Thông tin thư mục cha theo quy tắc của plugin |
| `${originalname}` | Tên gốc của tệp đính kèm |
| `${date}` | Ngày giờ theo định dạng đã đặt |
| `${md5}` | Mã băm nội dung để tạo tên tệp |

Những biến được hỗ trợ có thể khác nhau giữa đường dẫn và mẫu tên; xem mô tả ngay dưới từng ô và thông báo kiểm tra của plugin.

## Quy tắc riêng và đổi tên ghi chú

- **Cài đặt riêng theo phần mở rộng:** đặt quy tắc khác cho PDF, ảnh hoặc các nhóm tệp được hỗ trợ. Ví dụ dùng quy tắc riêng cho `pdf` để tránh đặt tên tài liệu giống ảnh chụp.
- **Tự động đổi tên tệp đính kèm:** khi bật, plugin có thể đổi tên/di chuyển tệp để theo tên mới của ghi chú. Thử với ghi chú và tệp mẫu trước khi dùng trên bộ tài liệu lớn.
- **Mẫu phần mở rộng cần loại trừ** và **Đường dẫn cần loại trừ:** loại các tệp/thư mục không muốn plugin xử lý.
- Lệnh sắp xếp lại tệp đính kèm trong khay lệnh có thể tác động tới nhiều tệp đã tồn tại. Sao lưu vault trước khi chạy hàng loạt, và kiểm tra liên kết sau khi sắp xếp.

## Khi tệp không đi đúng thư mục

Kiểm tra ghi chú hiện đang mở, vị trí gốc, mẫu đường dẫn và các quy tắc loại trừ. Phân biệt đường dẫn tương đối trong vault với đường dẫn hệ thống. Với PDF quan trọng, thử bằng bản sao trước khi thay đổi quy tắc.

## Cài và cập nhật bản Việt hóa

Trong BRAT → **Add beta plugin**, nhập `donamgit151524/obsidian-attachment-management-vi`. ID giữ nguyên `attachment-management`; không cài song song với bản gốc cùng ID. Dùng BRAT để cập nhật bản tùy chỉnh.

Tham khảo [repository Attachment Management gốc](https://github.com/trganda/obsidian-attachment-management) để xem tính năng và quy tắc chi tiết.

