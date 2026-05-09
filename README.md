# Televic D-Cerno CUR Mic Controller

Ứng dụng Python (Tkinter) để bật/tắt micro cho Televic D-Cerno CUR qua TCP API.

## Tính năng

- Kết nối tới D-Cerno CUR theo IP/Port (mặc định `192.168.0.20:5011`)
- Bật micro theo `UID`
- Tắt micro theo `UID`
- Toggle micro theo `UID`
- Tắt toàn bộ delegate (`uid=0`, `stat=0`)
- Hiển thị log gói tin nhận về (`evt`, `rep`, `err`)

## Chuẩn lệnh đã dùng

Theo tài liệu `d-cerno_cur_api.pdf` (mục 3.2.4):

- `{"nam":"smicstat","uid":"<serial>","stat":"1"}` => ON
- `{"nam":"smicstat","uid":"<serial>","stat":"0"}` => OFF
- `{"nam":"micstat","uid":"<serial>","stat":"0"}` => TOGGLE

> Lưu ý: API socket của D-Cerno không mô tả trường password riêng trong lệnh `con`. Trường password trong UI được đưa vào `inf` để tiện theo dõi/log.

## Chạy ứng dụng

Yêu cầu: Python 3.10+

```bash
python app.py
```

## Hướng dẫn nhanh

1. Mở app.
2. Để IP: `192.168.0.20`, Port: `5011`.
3. Nhấn **Connect**.
4. Điền `UID` của máy cần điều khiển (ví dụ `101008d2`).
5. Nhấn **Mic ON** hoặc **Mic OFF**.
6. Xem phản hồi ở vùng log.

## Xử lý lỗi thường gặp

- `Connect failed`: kiểm tra PC và CUR cùng mạng, ping được `192.168.0.20`.
- `Wrong serial number`: UID chưa đúng.
- Không thấy phản hồi: kiểm tra firmware CUR có bật API TCP hay không.
