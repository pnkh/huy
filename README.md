# Photoshop Huy Gallery - GitHub Pages + Apps Script Backend

Bản này dùng:

- GitHub Pages: chạy giao diện chính, không còn banner Apps Script.
- Apps Script: làm backend đọc ảnh từ Google Drive folder.

## File trong gói

- `index.html`: upload lên GitHub Pages.
- `.nojekyll`: giúp GitHub Pages phục vụ file tĩnh trực tiếp.
- `Code.gs`: dán vào Apps Script project hiện tại để mở API JSONP.
- `README.md`: hướng dẫn.

## Bước 1: Cập nhật Apps Script backend

Trong Apps Script project hiện tại:

1. Mở `Code.gs`.
2. Thay bằng file `Code.gs` trong gói này.
3. Deploy → Manage deployments → Edit → Version: New version → Deploy.
4. Copy Web App URL dạng:

```txt
https://script.google.com/macros/s/.../exec
```

## Bước 2: Cấu hình `index.html`

Mở file `index.html`, tìm dòng:

```js
const API_BASE_URL = 'PASTE_APPS_SCRIPT_EXEC_URL_HERE';
```

Thay bằng URL Apps Script `/exec` của bro:

```js
const API_BASE_URL = 'https://script.google.com/macros/s/.../exec';
```

## Bước 3: Upload lên GitHub

Upload lên repo GitHub:

```txt
index.html
.nojekyll
README.md
```

Rồi vào:

```txt
Settings → Pages
Source: Deploy from a branch
Branch: main
Folder: /root
Save
```

## Ghi chú

- GitHub Pages chỉ host giao diện, không đọc Drive trực tiếp được.
- Apps Script backend vẫn đọc Drive bằng `DriveApp`.
- Web mở từ GitHub nên không còn banner Apps Script.
