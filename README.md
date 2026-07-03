# Nhiếp Ảnh Viễn Đông - GitHub Pages Hybrid

Gói này dùng để chạy giao diện trên GitHub Pages, còn Apps Script chỉ làm API đọc ảnh từ Google Drive.

## File trong gói

- `Code.gs`: dán vào Google Apps Script.
- `index.html`: upload lên GitHub Pages.
- `README.md`: hướng dẫn này.

## Cách làm

### Bước 1 - Apps Script

1. Mở dự án Apps Script hiện tại hoặc tạo dự án mới.
2. Thay toàn bộ `Code.gs` bằng file `Code.gs` trong gói này.
3. Deploy:
   - **Triển khai** → **Quản lý tùy chọn triển khai** hoặc **Triển khai mới**
   - Loại: **Ứng dụng web**
   - Thực thi bằng tên: **Tôi**
   - Ai có quyền truy cập: **Bất kỳ ai**
4. Copy URL Web App dạng `https://script.google.com/macros/s/.../exec`.

### Bước 2 - GitHub Pages

1. Mở file `index.html`.
2. Tìm dòng:

```js
const API_BASE_URL = 'PASTE_APPS_SCRIPT_EXEC_URL_HERE';
```

3. Thay bằng URL Web App Apps Script vừa copy, ví dụ:

```js
const API_BASE_URL = 'https://script.google.com/macros/s/AKfycb.../exec';
```

4. Upload `index.html` vào repo GitHub.
5. Vào **Settings** → **Pages** → chọn branch `main`, folder `/root`.
6. Mở link GitHub Pages để test.

## Ghi chú

- Không cần dán `Index.html` vào Apps Script cho bản GitHub.
- Nếu ảnh không hiện, kiểm tra folder Google Drive đã share quyền xem cho người dùng hoặc Apps Script account có quyền đọc folder.
- Sau khi đổi `Code.gs`, luôn deploy version mới.
- Nếu GitHub vẫn gọi dữ liệu cũ, thêm `?v=github-v1` vào cuối link để né cache.
