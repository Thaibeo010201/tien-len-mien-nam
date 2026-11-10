# Tiến Lên Miền Nam

Game Tiến Lên Miền Nam chạy ngay trên trình duyệt. Có thể chơi một mình với máy, hoặc tạo phòng rồi gửi link cho bạn bè vào chơi cùng. Phòng online chỉ có người thật, từ 2 đến 4 người.

Chơi tại: **https://thaibeo010201.github.io/tien-len-mien-nam/**

Toàn bộ game nằm trong một file `index.html`, không cần cài đặt hay build gì.

## Cập nhật game lên GitHub Pages

1. Vào repo trên GitHub, bấm **Add file → Upload files**.
2. Kéo 2 file `index.html` và `README.md` vào trang. GitHub sẽ tự thay file cũ cùng tên.
3. Bấm **Commit changes**, đợi khoảng 1 phút rồi tải lại trang game.

GitHub Pages phải được bật một lần trong **Settings → Pages → Deploy from a branch → `main` / `(root)`**.

## Mời bạn bè vào chơi

Mở trang game sẽ thấy màn hình chọn **Chơi với máy** hoặc **Chơi với bạn**.

1. Bấm **Chơi với bạn**, nhập tên, rồi bấm **Tạo phòng**.
2. Bấm **Chép link** (hoặc **Gửi** trên điện thoại) rồi gửi link cho mọi người qua Zalo hay Messenger. Link có dạng `.../tien-len-mien-nam/?phong=AB3CD`.
3. Ai mở link thì nhập tên là vào phòng. Có từ 2 người là chủ phòng bấm **Chia bài** được. Không có máy chơi cùng, ghế nào không có người thì để trống.

Một vài điều nên biết:

- **Chủ phòng nên giữ trang game mở trên màn hình.** Ván bài chạy trên máy của chủ phòng. Chủ phòng chuyển sang Zalo hay khóa màn hình một lúc thì mọi người phải chờ.
- **Chủ phòng biến mất quá 25 giây** (tắt app, rớt mạng, đóng tab) thì người kế tiếp trong phòng **tự lên làm chủ phòng**, ván bài chơi tiếp nguyên vẹn. Chủ phòng cũ mở lại link thì vào lại đúng ghế của mình như người chơi thường.
- Nút **Thoát phòng** ở thanh trên cùng. Chủ phòng thoát thì quyền chủ phòng được giao ngay cho người khác. Khách thoát giữa ván thì máy đánh nốt ván đó, sau đó ghế để trống.
- Trong phòng, game giữ cho màn hình điện thoại không tự tắt (nếu trình duyệt hỗ trợ).
- Phòng tối đa 4 người. Ai vào giữa ván thì ngồi xem, chơi từ ván sau.
- Lỡ bấm **F5** (tải lại trang) cũng không sao: chủ phòng tải lại thì phòng và ván bài vẫn còn nguyên, khách tải lại thì tự ngồi lại đúng ghế với bài cũ. Chủ phòng chỉ được tải lại trên chính tab đang mở phòng. Đóng hẳn tab thì phòng sẽ mất.
- Cầm điện thoại dọc thì game tự quay bàn chơi nằm ngang, và dùng bàn phím riêng cũng nằm ngang. Bàn phím này gõ Telex tiếng Việt (`aa`→â, `dd`→đ, `s f r x j` là dấu sắc, huyền, hỏi, ngã, nặng), bấm **VN/EN** để bật tắt.
- Bấm nút **💬** ở góc trên bên trái bàn để trò chuyện: gõ chữ hoặc bấm câu nói nhanh. Tin nhắn hiện thành bóng thoại trên đầu người nói, có số tin chưa đọc khi khung chat đang đóng.
- Mỗi lượt có **15 giây**, số giây hiện ngay trên ảnh đại diện. Hết giờ mà chưa đánh thì tự bỏ lượt. Nếu đang tới lượt ra bài đầu vòng thì tự đánh lá nhỏ nhất.
- Ai rớt mạng thì máy đánh hộ tới hết ván. Mở lại đúng link đó trên cùng trình duyệt là ngồi lại ghế cũ.
- Chơi ít hơn 4 người thì mỗi người vẫn 13 lá. Ván đầu, ai giữ lá nhỏ nhất được chia ra thì đi trước.
- Xu chỉ để cho vui. Trong phòng online, mọi người bắt đầu với 2.000 xu và xu không được lưu lại sau khi đóng phòng.

## Cách kết nối hoạt động

GitHub Pages chỉ phát file tĩnh, nên game không có máy chủ riêng. Mọi tin nhắn trong phòng đi qua một máy chủ MQTT công cộng miễn phí (`broker.emqx.io`). Nếu máy chủ đó không vào được, game tự thử `broker.hivemq.com` rồi `test.mosquitto.org`. Các điện thoại không cần nối thẳng với nhau, nên chơi được cả khi dùng 4G.

Hạn chế:

- Mạng công ty hoặc trường học có thể chặn các máy chủ này. Khi đó sẽ báo "Không tạo được phòng". Chuyển sang Wi-Fi nhà hoặc 4G là được.
- Đây là máy chủ công cộng, ai biết mã phòng và rành kỹ thuật thì có thể đọc được tin nhắn trong phòng, kể cả bài của người khác. Chơi cho vui với bạn bè thì không sao.
- Máy chủ miễn phí đôi khi chậm hoặc bảo trì. Nếu lúc đó không tạo được phòng, đợi một lúc rồi thử lại.

## Chạy thử trên máy

Mở trực tiếp file `index.html` bằng trình duyệt là chơi một mình được ngay. Muốn thử phần online thì chạy một server tĩnh:

```bash
python3 -m http.server 8765
```

rồi mở `http://localhost:8765`.
