# PvZ Demo (Android)

Bản demo Plants vs Zombies viết lại bằng Java thuần cho Android (SurfaceView + Canvas,
không dùng Unity/JavaFX). Dùng lại toàn bộ ảnh và âm thanh gốc từ repo Plants-Vs-Zombies-master.

**Nội dung demo:**
- 1 màn chơi (8 zombie thường + 4 zombie chóp nón, random ngẫu nhiên)
- 2 loại cây: Hoa hướng dương (50 sun), Bắn đậu (100 sun)
- **Máu zombie tăng gấp đôi** so với bản gốc (zombie thường: 14 máu, zombie chóp nón: 28 máu)
- Mặt trời rơi ngẫu nhiên + hoa hướng dương tạo mặt trời
- Máy cắt cỏ (lawnmower) cứu nguy mỗi hàng, 1 lần dùng

## Build ra file APK bằng GitHub Actions (làm trên điện thoại, không cần máy tính)

### Bước 1 — Tạo repo trên GitHub
1. Mở **github.com** bằng trình duyệt điện thoại (Chrome/Safari), đăng nhập.
2. Bấm nút **+** → **New repository**.
3. Đặt tên repo (vd: `pvz-demo`), để **Public**, KHÔNG tick "Add a README" (repo phải trống).
4. Bấm **Create repository**.

### Bước 2 — Tải toàn bộ project lên
1. Ở trang repo vừa tạo, bấm **"uploading an existing file"** (hoặc Add file → Upload files).
2. Giải nén file `PVZDemo.zip` mình gửi ra một thư mục trên điện thoại (dùng app quản lý file có
   chức năng giải nén, ví dụ ZArchiver/Files).
3. Trong trang Upload của GitHub, chọn **toàn bộ file và thư mục con** đã giải nén (kéo-thả cả
   thư mục nếu trình duyệt hỗ trợ, hoặc chọn từng file/folder trong hộp thoại chọn file — phải giữ
   đúng cấu trúc thư mục như trong zip, đặc biệt là `.github/workflows/build-apk.yml`).
4. Cuộn xuống, bấm **Commit changes** (commit thẳng vào nhánh `main`).

> Nếu trình duyệt điện thoại không cho chọn cả thư mục, cách chắc ăn nhất là dùng **GitHub Desktop
> hoặc git trên máy tính bất kỳ mượn được** một lần để `git push`, hoặc dùng app **Termux** (Android)
> cài `git` rồi `git add . && git commit -m init && git push`.

### Bước 3 — Lấy file APK
1. Sau khi commit, vào tab **Actions** của repo.
2. Sẽ thấy workflow **"Build APK"** đang chạy (biểu tượng vàng đang xoay) — đợi khoảng 3-6 phút.
3. Khi chuyển sang dấu ✅ xanh, bấm vào lần chạy đó → cuộn xuống mục **Artifacts** →
   tải file **pvz-demo-debug-apk.zip**.
4. Giải nén ra sẽ được file `app-debug.apk`. Copy file này vào điện thoại (nếu build trên máy khác)
   rồi bấm cài đặt (Android sẽ hỏi cho phép "cài ứng dụng từ nguồn không xác định" — đồng ý).

## Sau này muốn mod thêm
- Đổi số liệu máu/sát thương/giá: sửa `PlantType.java`, `ZombieType.java`.
- Đổi tốc độ zombie, tốc độ đạn: sửa các hằng số `ZOMBIE_SPEED`, `PEA_SPEED` trong `World.java`.
- Đổi danh sách zombie trong màn: sửa hàm `buildLevel()` trong `World.java`.
- Mỗi lần sửa xong, chỉ cần `git push` (hoặc upload lại file đã sửa lên GitHub) — Actions sẽ tự
  build lại APK mới.
