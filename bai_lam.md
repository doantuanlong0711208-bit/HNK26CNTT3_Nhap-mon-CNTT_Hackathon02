# BÀI LÀM – HACKATHON 02

- **Mã đề:** 06
- **Họ tên:** Đoàn Tuấn Long 
- **Lớp:** CNTT3
- **Link repository:** https://github.com/doantuanlong0711208-bit/HNK26CNTT3_Nhap-mon-CNTT_Hackathon02.git
- **Hệ điều hành (Windows/macOS):** Windows

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
1. pwd
2. ls -Force
3. mv .\yeu_cau_khach_hang.txt .\docs\
4. mkdir backup
5. cp .\data\don_in_thang_6.xlsx .\backup\
6. rm .\temp_606.tmp
7. cd .\logs\
   ls -Force
   cd..
8. Get-ChildItem -Recurse -Force

```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
Directory: D:\starter-kit\starter-kit\xuong-in-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026  10:49 AM                backup
d-----        11/11/2026  10:48 AM                data
d-----        11/11/2026  10:49 AM                docs
d-----        11/11/2026  10:47 AM                evidence
d-----        11/11/2026  10:48 AM                logs
d-----        11/11/2026  10:44 AM                web
------         11/3/2026   7:07 AM             76 .env
-a----         11/3/2026   7:07 AM           2407 bai_lam.md


    Directory: D:\starter-kit\starter-kit\xuong-in-website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM           6137 don_in_thang_6.xlsx


    Directory: D:\starter-kit\starter-kit\xuong-in-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM           6137 don_in_thang_6.xlsx


    Directory: D:\starter-kit\starter-kit\xuong-in-website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM            153 yeu_cau_khach_hang.txt


    Directory: D:\starter-kit\starter-kit\xuong-in-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM            981 order.log


    Directory: D:\starter-kit\starter-kit\xuong-in-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026  10:44 AM                images
------         11/3/2026   7:07 AM            594 app.js
------         11/3/2026   7:07 AM            516 index.html
------         11/3/2026   7:07 AM            460 style.css


    Directory: D:\starter-kit\starter-kit\xuong-in-website\web\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
------         11/3/2026   7:07 AM           3092 logo-printnow.png

```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
 Get-Content .\logs\order.log | Select-String "status=500" > .\logs\loi_500.txt

```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
2026-06-28 08:15:01 POST /api/thanh-toan status=500
2026-06-28 08:34:07 POST /api/tai-file status=500

```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
(Get-Content .\logs\order.log | Select-String "status=404").count

```

```text
4

```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\tong_hop.ps1

```

### Nội dung file logs/tong_hop.txt

```text
=== BAO CAO SU CO WEBSITE ===

2026-06-28 08:08:39 GET /mau-tet-cu status=404
2026-06-28 08:19:12 GET /images/poster-2.jpg status=404
2026-06-28 08:23:23 GET /images/poster-2.jpg status=404
2026-06-28 08:54:24 GET /tin-tuc status=404




Count    : 6
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [x] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [x] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 | network | lỗi không hiển thị logo | vào index.html đổi tên logo.png thành logo-printnow.png |
| 2 | console | app.js:18 Uncaught ReferenceError: hienThiSanPham is not defined |  |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:** hiện tại tôi là sinh viên năm nhất ngành cntt và chưa biết gì về fix lỗi web.
- **Expected:** tôi muốn fix lỗi hiển thị bảng trên trang web Printnow.
- **Actual:** Thực tế khi mở web tôi vào phần console và thấy hiển thị lỗi sau: app.js:18 Uncaught ReferenceError: hienThiSanPham is not defined
- **Log:** app.js:18 Uncaught ReferenceError: hienThiSanPham is not defined

### Câu tìm kiếm Google

```text
site: stackoverflow.com "Uncaught ReferenceError"

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/don_in_thang_6.xlsx`, không cần ghi vào đây.
