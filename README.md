# 🎄 Noel Effect 2025 — Magical Christmas Tree (v2.0)

Phiên bản gọn, tương tác bằng cử chỉ tay sử dụng Three.js và MediaPipe Hands. Trang demo dựng một cây thông 3D kết hợp hệ thống particle (tuyết, pháo hoa, confetti), ảnh kỷ niệm và nhiều chế độ tương tác tùy theo cử chỉ người dùng.

---

## Tính năng chính

- Cây thông 3D nhiều tầng với ngôi sao phát sáng
- Particle systems: tuyết, pháo hoa, confetti, dust
- 5 ảnh kỷ niệm quay quanh cây và phóng to khi "pinch"
- Màu sắc động theo vị trí tay (`vibe` / hue)
- 4 chế độ tương tác: TREE, SPHERE, ZOOM_PHOTO, HEART
- Gọn nhẹ, chạy hoàn toàn trên trình duyệt (WebGL + webcam)

## Yêu cầu

- Trình duyệt hiện đại (Chrome/Edge/Firefox)
- Webcam (cho phép truy cập)
- Chạy trên `localhost` hoặc HTTPS (trình duyệt yêu cầu để mở camera)

## Chạy nhanh (local)

1. Clone repo và vào thư mục:

```bash
git clone https://github.com/yourusername/noel-effect-2025.git
cd noel-effect-2025
```

2. (Tùy chọn) Thêm ảnh vào `img/` và nhạc vào `audio.mp3`.

3. Chạy server tĩnh rồi mở `http://localhost:8000`:

```bash
# Python 3
python -m http.server 8000

# hoặc Node.js
npx http-server -p 8000
```

4. Nhấn nút **BẮT ĐẦU PHÉP THUẬT** trên trang, cho phép camera.

---

## Hướng dẫn sử dụng (cử chỉ)

- ✊ Nắm tay — `TREE` : Cây thông và album ảnh quay chậm
- 🖐 Xòe tay — `SPHERE` : Hiệu ứng pháo hoa hình cầu
- 👌 Pinch (ngón cái + trỏ) — `ZOOM_PHOTO` : Phóng to ảnh được chọn
- ✌️ Victory (index + middle up) — `HEART` : Hiệu ứng trái tim/tuyết

Ghi chú kỹ thuật: hệ thống dùng vị trí landmark (MediaPipe) để xác định ngón lên/xuống và khoảng cách pinch.

---

## Kiến trúc & tập trung mã

- `index.html` — giao diện + logic Three.js + MediaPipe
- Hàm chính (ví dụ): `init3D()`, `createPhotos()`, `createTopStar()`, `animate()`, `startSystem()`
- Cấu hình particle/độ chi tiết nằm trong `CONFIG` (số lượng particle, bán kính, kích thước)

## Gesture detection (tóm tắt)

- Pinch: khoảng cách giữa landmark ngón cái và ngón trỏ < 0.05 → `ZOOM_PHOTO`
- Victory: index & middle up, ring & pinky down → `HEART`
- All fingers open → `SPHERE`
- Mặc định khác → `TREE`

---

## Tối ưu & Troubleshooting

- Camera không lên: kiểm tra quyền trình duyệt và chạy trên `localhost`/HTTPS
- Hiệu năng kém: giảm `CONFIG.count` (particle), tắt shadow hoặc giảm `renderer.setPixelRatio(1)`
- Thiếu ảnh: thêm vào thư mục `img/` hoặc để mặc định dùng URL remote

---

## Đóng góp

1. Fork repo
2. Tạo branch: `git checkout -b feature/name`
3. Commit & push
4. Tạo Pull Request

---

## License

MIT — xem file `LICENSE`.

---

Nếu bạn muốn, tôi có thể: tối ưu `index.html` cho máy yếu, thêm biến cấu hình dễ chỉnh, hoặc tạo phiên bản minimal để test nhanh. Chọn hành động tiếp theo bạn muốn nhé.

---

# MADE BY ZDEV
 - Github: [ZDEV GITHUB](https://github.com/zdev-aka)
 - Gmail: tranmanhtiendev@gmail.com