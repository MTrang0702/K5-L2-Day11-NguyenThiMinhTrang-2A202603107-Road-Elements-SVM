# Báo cáo cá nhân — Ngày 11
Họ tên: Nguyễn Thị Minh Trang  
Mã học viên: 2A202603107  
Phiên bản CVAT (Help → About): CVAT 2.48.0 (Docker local `http://localhost:9080`)  
Guideline: Road v1.0    Lần nộp (`revision` trong manifest): 1  
Thời điểm export (ngày giờ trên CVAT): 2026-11-21 07:36:10 UTC    Số lần nộp lại sau Rework: 0  

## 1. Kiểm project
| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | Đúng | `lane` (polyline), `road_curb` (polyline), `crosswalk` (polygon), `drivable` (polygon), `traffic_light` (rectangle), `traffic_sign` (rectangle) |
| Thuộc tính và giá trị | Đúng | Khớp 100% với taxonomy Road v1.0 (`position`: L1/R1/L2/R2/other; `area_type`: direct/alternative; `edge_zone`,...) |
| 4 tag ảnh | Đúng | 4 nhãn Tag (`camera`, `timeofday`, `weather`, `source`), mỗi tag có thuộc tính select `value` |
Cách kết thúc polyline trên bản CVAT này: Nhấp đúp chuột trái (double-click) hoặc nhấn phím tắt `N`.  
Cách đặt tag ảnh trên bản CVAT này: Chọn tab Tags ở thanh bên phải, chọn label tag tương ứng và chọn giá trị từ dropdown `value`.  

## 2. Số lượng đã gán
| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 27 | 1 | 4 | 20 | 27 | 28 |
| front-extra (đã làm __ / 4) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| fisheye | 8 | 7 | 1 | 7 | 8 | 4 | 4 |
| fisheye-extra (đã làm __ / 4) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

## 3. Bảng ca khó
| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
| --- | --- | --- | --- | --- |
| `A01` | `traffic_sign` | Biển hiệu lệnh hay biển chỉ dẫn | `group = information` | Biển chữ nhật xanh lá chỉ hướng/lối ra đường cao tốc theo quy chuẩn biển báo Mỹ BDD100K. |
| `A03` | `lane` | Dừng polyline trước đầu xe hay nối qua | Nối liền qua xe và bật `occluded = true` | Tuân thủ quy tắc QC1-05: vật che ngắn nối liền qua chỗ che, không cắt vụn vạch. |
| `A04` | `lane` / `drivable` | Có gán `drivable` đè sang làn ngược chiều bên kia vạch vàng không | Dừng polygon sát vạch vàng tim đường, không lấn sang | Phía bên kia vạch vàng là làn xe chạy ngược chiều, tuyệt đối không gán `drivable` để tránh xe tự lái lấn làn đối đầu. |
| `A04` | `lane` | Single hay Double line | `kind = double`, `color = yellow` | Vạch tim đường đôi phân chia hai chiều ngược nhau ở Mỹ. |
| `A07` | `lane` | 2 vạch trắng liền song song vẽ 1 hay 2 đường | 1 polyline ở khe giữa, `kind = double`, `color = white` | Quy chuẩn Road v1.0 biểu diễn cặp vạch đôi bằng một polyline trung tâm kèm thuộc tính `kind = double`. |
| `B02` | `traffic_light` | Bật hay tắt `edge_zone` | Bật `edge_zone = true` | Cụm đèn trên cột bên trái và đèn đi bộ bên phải đều nằm ngoài bán kính 80% từ tâm ảnh fisheye. |
| `B04` | `drivable` | Bao phủ cả cản xe hay dừng ở mép | Dừng sát mép cản sau xe (y ≈ 670) | Guideline mục 4: Thân xe mình không được gán và không tính vào vùng lái. |
| `B06`, `B08` | `lane` | Chọn `position` L1/R1 hay other | `position = other` | Guideline mục 4: Camera hai bên sườn (`fisheye_left`, `fisheye_right`) luôn gán `position = other`. |

## 4. Phiếu QC 1 nhận được
Bạn kiểm lô của tôi: DoPhuongManh    Quyết định nhận được: Release  
| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
| --- | ---: | --- | --- |
| Không có lỗi nặng / chính | 0 | Đồng ý | Đạt chuẩn bàn giao, không cần sửa |

## 5. Kiểm file export
- **Link Google Drive nộp bài:** [https://drive.google.com/drive/folders/1PxzrY3ivPhkXwZonGBGVj6Vs3B6WM6Ej](https://drive.google.com/drive/folders/1PxzrY3ivPhkXwZonGBGVj6Vs3B6WM6Ej)

| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | --- | --- | --- | --- |
| `nguyenthiminhtrang-front.zip` | Có (`road_check lint`: PASS, mở lại 100%) | 9 shape (A01: 9 / 9) | 5 shape (A02: 5 / 5) | Có (`value = front`) |
| `nguyenthiminhtrang-fisheye.zip` | Có (`road_check lint`: PASS, mở lại 100%) | 3 shape (B01: 3 / 3) | 4 shape (B02: 4 / 4) | Có (`value = fisheye_front`) |

## 6. Ảnh chụp màn hình
*(Tất cả ảnh đã được đóng gói trong `nguyenthiminhtrang-screenshots.zip` và đẩy lên thư mục Google Drive trên)*
1. Tab Labels của project (`01-project-labels.png`).
2. Một ảnh camera trước đã gán đủ (`02-front-a01.png`).
3. Một ảnh fisheye đã gán, phóng to đoạn polyline cong (`03-fisheye-b03.png`).
4. Một đoạn XML có `<polyline label="lane">` (`04-xml-snippet.png`).

## 7. Tự đánh giá
- **Lỗi bạn mắc nhiều nhất hôm nay (theo mã QC1-xx), và cách tránh ở Ngày 20:**
  Lỗi dễ mắc nhất là phân vân phạm vi vùng lái `drivable` khi gặp vạch vàng tim đường (nguy cơ phạm lỗi QC1-07 tràn sang làn ngược chiều), vẽ polyline ngược chiều từ xa về gần (QC1-04) và quên chọn `kind = double` khi gặp 2 vạch liền song song. Cách tránh ở Ngày 20: luôn tuân thủ nguyên tắc "drivable chỉ dành cho chiều xe chạy hợp pháp", cạnh polygon dừng sát vạch vàng tim đường; vẽ polyline từ dưới đáy ảnh lên đỉnh; và luôn mở Details kiểm tra thuộc tính `kind`, `style`, `color` trước khi lưu.
- **Nhãn của bạn đi vào model ở đâu? Chọn một lỗi đã sửa và nói nó làm model học sai thế nào:**
  Nhãn `lane` đi vào đầu vào huấn luyện của mạng phát hiện làn đường (Row-anchor Lane Detection / Polyline Regression) và `drivable` đi vào mạng Semantic Segmentation (phân đoạn mặt đường đi được):
  1. **Lỗi vùng lái qua vạch vàng:** Nếu gán polygon `drivable` tràn qua vạch đôi màu vàng sang phần đường đối diện (như ở `A04`), mô hình Semantic Segmentation sẽ học sai rằng làn xe ngược chiều là vùng lái an toàn xe mình có thể đi vào. Khi đưa vào xe tự hành thực tế (Autonomous Driving), hệ thống lập quỹ đạo (Motion Planning) có thể điều khiển xe lấn sang làn ngược chiều gây tai nạn đâm trực diện nguy hiểm.
  2. **Lỗi vạch đôi màu vàng / vạch đôi trắng:** Nếu cặp vạch đôi song song bị gán nhầm thành `kind = single`, mô hình phát hiện làn sẽ không phân biệt được vạch đơn (cho phép đè/chuyển làn trong một số điều kiện) với vạch đôi cấm vượt/cấm chuyển làn tuyệt đối, làm sai lệch quyết định của hệ thống Hỗ trợ giữ làn (LKA - Lane Keeping Assist).

## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor
| y | 720 | 680 | 640 | 600 | 560 |
| --- | ---: | ---: | ---: | ---: | ---: |
| x của chúng tôi (vạch L1, A01) | 108.5 | 157.6 | 205.5 | 251.4 | 294.8 |
| x của bạn kia (vạch L1, A01) | 108.0 | 154.8 | 203.0 | 249.4 | 296.6 |

Trả lời 3 câu hỏi:
1. **Năm số x đó chính là đích mà một model row-anchor học cho vạch này. Nếu bạn dừng polyline sớm 40 px, hàng nào đổi thành "không có làn"?**  
   Hàng $y = 560$ (đỉnh vạch xa nhất) sẽ đổi thành "không có làn" (giá trị `None` / rỗng).
2. **So với bạn được kiểm (cùng ảnh): ở hàng 720 và hàng 560, hai bạn lệch nhau bao nhiêu pixel? Lệch ở hàng nào ảnh hưởng LKA nhiều hơn (slide 25)?**  
   Ở hàng $y = 720$ hai bạn lệch nhau $0.5	ext{ px}$, ở hàng $y = 560$ lệch nhau $1.8	ext{ px}$. Lệch ở các hàng gần xe hơn ($y = 720$ và $y = 680$) ảnh hưởng tới hệ thống giữ làn đường (LKA) nhiều hơn, vì đây là vùng không gian phản ứng trực tiếp để điều khiển góc lái tức thời.
3. **Nếu polyline vẽ từ xa về gần (ngược quy tắc 2), cách tính trên có đổi không? Script nào sẽ gặp khó?**  
   Về mặt hình học thuần túy tọa độ giao điểm không đổi, nhưng script trích xuất đặc trưng `rowanchor.py` và pipeline huấn luyện mạng nơ-ron sẽ gặp lỗi do giả định mảng điểm luôn được sắp xếp theo thứ tự từ đáy ảnh (gần xe) lên đỉnh ảnh (xa xe).
