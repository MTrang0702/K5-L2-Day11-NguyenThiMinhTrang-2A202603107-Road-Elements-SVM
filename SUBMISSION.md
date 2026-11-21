# Nộp bài (hạn 16:35, Ngày 11)

- **Học viên:** Nguyễn Thị Minh Trang (MSSV: `2A202603107`)
- **Link Google Drive chứa file nộp bài:** [https://drive.google.com/drive/folders/1PxzrY3ivPhkXwZonGBGVj6Vs3B6WM6Ej](https://drive.google.com/drive/folders/1PxzrY3ivPhkXwZonGBGVj6Vs3B6WM6Ej)

Nộp đúng 5 file lên kênh nộp bài coach chỉ định. Không gửi file GT, không gửi ảnh và không đăng file lên kênh chung của lớp.

- [x] `<tên>-front.zip`: `nguyenthiminhtrang-front.zip` (CVAT for images 1.1, không kèm ảnh; task front A01–A12).
- [x] `<tên>-fisheye.zip`: `nguyenthiminhtrang-fisheye.zip` (CVAT for images 1.1, không kèm ảnh; task fisheye B01–B08).
- [x] `<tên>-manifest.json`: `nguyenthiminhtrang-manifest.json` (manifest bàn giao sha256).
- [x] `<tên>-qc1-for-<tên bạn được kiểm>.md`: `nguyenthiminhtrang-qc1-for-DoPhuongManh.md` (Phiếu QC 1 kiểm bài bạn Đỗ Phương Mạnh).
- [x] `<tên>-report.md`: `nguyenthiminhtrang-report.md` (báo cáo cá nhân).
- [x] `<tên>-screenshots.zip`: `nguyenthiminhtrang-screenshots.zip` (4 ảnh chụp màn hình minh chứng).

Trước khi nộp:

- [x] Mọi job ở trạng thái **completed**.
- [x] Đã mở lại hai file zip và chạy `PYTHONPATH=src python3 -m road_lab.road_check lint <tên>-front.zip <tên>-fisheye.zip`; không còn dòng nào mức nặng (ngoại lệ QC1-02 ở A05 không có vạch sơn được miễn).
- [x] Đã tạo manifest: `nguyenthiminhtrang-manifest.json` với `--name nguyenthiminhtrang --revision 1`; trong file, `contains_images` là `false`.
- [x] Mọi ảnh có đủ bốn tag, tag camera đúng.
- [x] Báo cáo có ảnh chụp màn hình và bảng kiểm file (mục 1).

Sửa sau buffer: trước khi export lại, chép hai zip và manifest cũ vào thư mục `r1/` trên máy (manifest cũ đổi tên thành `<tên>-manifest-r1.json`). Sau đó nộp hai file zip **cùng tên** và manifest mới với `--revision 2`. Ghi vào mục 4 của báo cáo đã sửa những gì.
