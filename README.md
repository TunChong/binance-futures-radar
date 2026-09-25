# Futures Radar

Theo dõi Binance Futures bằng tiếng Việt. Tệp `index.html` chứa toàn bộ trang web, CSS và JavaScript; không cần cài thêm thư viện hay API key.

## Sử dụng

- Quét USDⓈ-M và COIN-M, gồm hợp đồng vĩnh cửu và có kỳ hạn đang giao dịch.
- Cảnh báo khi tăng hoặc giảm từ **2% trong 30 giây**. Có mức chọn nhanh 2%, 5%, 10%, thanh kéo 2–10% và ô nhập 0,1–100%.
- Biến động vượt 10% vẫn được cảnh báo. Coin đạt ngưỡng được làm nổi bật, cảnh báo mới nằm đầu danh sách, kèm thông báo nổi và âm thanh nếu bật.
- Chờ đủ 30 giây sau lần nhận giá đầu tiên. Sau mất kết nối, trang tự kết nối và xây dựng lại cửa sổ dữ liệu.
- Giữ trang mở. Khi khóa điện thoại hoặc chuyển ứng dụng, trình duyệt có thể tạm dừng; đây không phải dịch vụ giám sát nền 24/7.

## Cách tính và phạm vi

`% biến động = (giá hiện tại − giá quan sát tại mốc 30 giây trước) / giá quan sát tại mốc đó × 100`

Sử dụng giá gần nhất `c` và thời điểm sự kiện `E` từ luồng Binance Futures `!miniTicker@arr`. Không dùng tỷ lệ biến động 24 giờ. Mốc đầu là giá quan sát cuối cùng tại hoặc trước 30 giây trước. Luồng cập nhật khoảng mỗi giây nên có thể bỏ lỡ biến động rất ngắn giữa hai lần cập nhật.

Danh mục hợp đồng được cập nhật mỗi 10 phút qua `exchangeInfo`. Nếu danh mục không tải được, trang ghi rõ phạm vi chưa xác minh và vẫn theo dõi các mã mà luồng trả về. Nguồn mất kết nối hoặc im lặng quá 8 giây sẽ được xóa dữ liệu và kết nối lại.

Mỗi chiều báo một lần khi vượt ngưỡng; kích hoạt lại khi độ lớn xuống dưới 80% ngưỡng, đảo chiều vượt ngưỡng hoặc ngưỡng được đổi. Lưu tối đa 100 cảnh báo trong phiên; ngưỡng tùy chỉnh lưu trên thiết bị.

## GitHub Pages

Trong **Settings → Pages**, chọn **Deploy from a branch → main → /(root) → Save**. Địa chỉ web chính thức được hiển thị trong mục Pages sau khi triển khai hoàn tất.

## Mã nguồn và kiểm tra

Có thể sửa trực tiếp `index.html`. Bản nguồn chia tệp, tài liệu đầy đủ, script ghép HTML và 12 kiểm tra logic/mô phỏng tích hợp nằm trong [Binance-Futures-Radar-GitHub.zip](./Binance-Futures-Radar-GitHub.zip).

Giải nén rồi chạy `npm test` và `npm run build`. Tệp xuất ra là `docs/index.html`; dùng nội dung đó để cập nhật `index.html` ở gốc kho mã này.

## Tài liệu nguồn

- [Binance Futures WebSocket](https://developers.binance.com/en/docs/catalog/core-trading-derivatives-trading-usd-s-m-futures/api/ws-streams/market)
- [GitHub Pages](https://docs.github.com/en/pages/quickstart)
