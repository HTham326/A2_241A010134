# A2 - Đồng hồ bấm giờ

## Thông tin sinh viên

- Họ và tên: Nguyễn Thị Hồng Thắm
- MSSV: 241A010134
- Lớp: CNTT - LTDD
- Package: `vn.edu.vhu.ltdd.a2stopwatch`

## Giới thiệu

Ứng dụng Android "Đồng hồ bấm giờ" được xây dựng bằng Java và XML Layout.

Ứng dụng thực hiện các chức năng cơ bản của một đồng hồ bấm giờ và minh họa cách quản lý vòng đời Activity, lưu và khôi phục trạng thái khi Activity được tạo lại.

## Chức năng chính

- **Bắt đầu / Tạm dừng:** bắt đầu hoặc tạm dừng đồng hồ.
- **Đặt lại:** đưa thời gian về `00:00.0`.
- **Vòng (Lap):** lưu lại các mốc thời gian trong quá trình bấm giờ.
- **Khôi phục trạng thái:** thời gian, trạng thái chạy và danh sách Lap được lưu và khôi phục khi Activity được tạo lại, ví dụ khi xoay màn hình.
- **Đổi màu thời gian:** số thời gian chuyển sang màu đỏ khi vượt quá 60 giây.
- **Rung khi đặt lại:** gọi hiệu ứng rung ngắn khi nhấn nút Đặt lại.

## Công nghệ sử dụng

- Android Studio
- Java
- XML Layout
- Android SDK
- `Handler` và `Runnable` để cập nhật thời gian.
- `SystemClock.elapsedRealtime()` để tính thời gian đã trôi qua.
- `Bundle` để lưu và khôi phục trạng thái Activity.
- `ArrayList<String>` để lưu danh sách Lap.
- `Vibrator` / `VibrationEffect` cho chức năng rung.

## Các kịch bản kiểm thử

### 1. Chạy ứng dụng

- Nhấn **Bắt đầu**.
- Đồng hồ bắt đầu tăng thời gian.
- Nút chuyển thành **Tạm dừng**.

### 2. Tạm dừng

- Nhấn **Tạm dừng**.
- Đồng hồ dừng tại thời điểm hiện tại.
- Nút chuyển lại thành **Bắt đầu**.

### 3. Xoay màn hình

- Đang chạy hoặc tạm dừng đồng hồ.
- Xoay màn hình.
- Activity được tạo lại.
- Thời gian và trạng thái trước đó được khôi phục.

### 4. Don't keep activities

- Bật tùy chọn **Don't keep activities** trong Developer Options.
- Activity bị hủy và tạo lại.
- Trạng thái đồng hồ được lưu thông qua `Bundle` và khôi phục sau khi tạo lại.

### 5. Thoát và mở lại ứng dụng

- Nhấn Back để thoát Activity.
- Mở lại ứng dụng.
- Ứng dụng được khởi tạo trạng thái mới.

## Chức năng nâng cao

### NC1 - Vòng (Lap)

Danh sách Lap được lưu bằng `ArrayList<String>`.

Khi Activity được tạo lại, danh sách Lap được khôi phục từ `Bundle`:

```java
outState.putStringArrayList(KEY_LAP, laps);