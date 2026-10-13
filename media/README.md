# Kho bài học của app

App Language Supper App đọc thẳng các file trong thư mục này qua
`https://raw.githubusercontent.com/PhamVuYen/data_language_test/main/media/…`.
Repo phải để công khai. File đã push lên nhánh `main` thì app thấy sau tối đa 5 phút.

```
catalog.json                       danh mục bài, hợp đồng catalog/1
feed.json                          tin của kênh, hợp đồng feed/1
v/<lesson_id>/r<phiên bản>/        file của một bài, không bao giờ ghi đè
    episode.json                   phần chữ, hợp đồng episode/1
    audio/mix.m4a                  audio
```

Hai hợp đồng `catalog/1` và `feed/1` được mô tả trong `README.md` của app
(`language_media/Language Supper App/README.md`).

## Thêm hoặc sửa một bài

1. Đặt file của bài vào `v/<lesson_id>/r1/`. Sửa bài đã có thì tạo `r2/` và tăng `version`
   trong `catalog.json`; không sửa file trong `r1/`.
2. Thêm bài vào `catalog.json`. `bytes` và `sha256` phải đúng với file, app kiểm cả hai:

   ```bash
   stat -f %z v/<lesson_id>/r1/episode.json
   shasum -a 256 v/<lesson_id>/r1/episode.json
   ```

3. Muốn báo trong mục Tin thì thêm một mục vào `feed.json`.
4. Commit và push lên `main`.

Giới hạn của GitHub: mỗi file dưới 100MB, cả repo nên dưới 1GB.

## Dữ liệu đang có (13/10/2026)

- `vi-260829-test-quy-trinh`: bài mẫu, trùng với bài đóng gói sẵn trong app.
- `thu-tai-ve-01`: bản sao của bài mẫu với id khác, chỉ để thử luồng tải về. Xoá được.
- `feed.json`: một mục bài học và một bài đăng mẫu, chỉ để thử mục Tin. Xoá được.
