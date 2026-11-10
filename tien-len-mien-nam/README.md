# Tiến Lên Miền Nam

Game Tiến Lên Miền Nam chạy ngay trên trình duyệt. Có thể chơi một mình với máy, hoặc tạo phòng rồi gửi link cho bạn bè vào chơi cùng. Ghế nào trống thì máy đánh thay.

Toàn bộ game nằm trong một file `index.html`, không cần cài đặt hay build gì.

## Đưa lên GitHub Pages

1. Tạo repo mới trên GitHub, ví dụ `tien-len`.
2. Đẩy code lên:

   ```bash
   git init
   git add index.html README.md
   git commit -m "Tiến Lên Miền Nam"
   git branch -M main
   git remote add origin https://github.com/<tên-github>/tien-len.git
   git push -u origin main
   ```

3. Trên GitHub, vào repo → **Settings** → **Pages**. Ở mục **Source** chọn **Deploy from a branch**, nhánh `main`, thư mục `/ (root)`, rồi bấm **Save**.
4. Đợi khoảng 1 phút. Game sẽ có ở `https://<tên-github>.github.io/tien-len/`.

## Mời bạn bè vào chơi

1. Mở trang game, bấm **Chơi với bạn**, nhập tên, rồi bấm **Tạo phòng**.
2. Bấm **Chép link** (hoặc **Gửi** trên điện thoại) rồi gửi link cho mọi người qua Zalo hay Messenger. Link có dạng `https://<tên-github>.github.io/tien-len/?phong=AB3CD`.
3. Ai mở link thì nhập tên là vào phòng. Đủ người thì chủ phòng bấm **Chia bài**.

Một vài điều nên biết:

- **Chủ phòng phải giữ trang mở.** Ván bài chạy trên máy của chủ phòng. Chủ phòng tắt trang hoặc khóa điện thoại lâu thì phòng sẽ đóng.
- Phòng tối đa 4 người. Người vào sau sẽ ngồi thay máy, kể cả đang giữa ván.
- Ai rớt mạng thì máy đánh hộ. Mở lại đúng link đó trên cùng trình duyệt là ngồi lại ghế cũ.
- Mỗi lượt có 30 giây. Hết giờ thì máy tự đánh hoặc bỏ lượt.
- Xu chỉ để cho vui. Trong phòng online, mọi người bắt đầu với 2.000 xu và xu không được lưu lại sau khi đóng phòng.

## Cách kết nối hoạt động

GitHub Pages chỉ phát file tĩnh, nên game không có máy chủ riêng. Các trình duyệt kết nối thẳng với nhau bằng WebRTC, thông qua thư viện [PeerJS](https://peerjs.com). Máy chủ công cộng miễn phí của PeerJS chỉ làm nhiệm vụ "giới thiệu" để hai bên tìm thấy nhau. Sau đó dữ liệu ván bài đi thẳng giữa các máy.

Hạn chế của cách này:

- Mạng công ty hoặc trường học có thể chặn máy chủ PeerJS (`0.peerjs.com`). Khi đó sẽ báo "Không tạo được phòng". Chuyển sang Wi-Fi nhà hoặc 4G là được.
- Một số mạng 4G không cho hai máy nối thẳng với nhau, nên có người sẽ không vào được phòng. Muốn khắc phục thì thêm một máy chủ TURN vào mảng `ICE` ở gần đầu phần `<script>` trong `index.html`. Có thể lấy TURN miễn phí từ Metered hoặc Cloudflare Calls, ví dụ:

  ```js
  const ICE = [
    { urls:'stun:stun.l.google.com:19302' },
    { urls:'turn:<máy-chủ-turn>:3478', username:'<tên>', credential:'<mật-khẩu>' },
  ];
  ```

## Chạy thử trên máy

Mở trực tiếp file `index.html` bằng trình duyệt là chơi một mình được ngay. Muốn thử phần online thì chạy một server tĩnh:

```bash
python3 -m http.server 8765
```

rồi mở `http://localhost:8765`.
