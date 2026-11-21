# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): DoPhuongManh (2A202603148)        Người kiểm (học viên): Nguyễn Thị Minh Trang (2A202603107)  
Ngày: 2026-11-21                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): DoPhuongManh-front.zip (revision 1)  
Số ảnh kiểm: 6 (A01–A06) (+ 0 ảnh thêm, ghi riêng)   Số nhãn đã kiểm (shape + tag): 67  

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 24 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 12 | 1 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 13 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 13 | 1 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 13 | 1 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 13 | 1 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 10 | 0 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 7 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 11 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 11 | 0 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 0 | 0 | chính |
| QC1-12 file | lỗi file | 1 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-02 | `A06_b8c66e31-37045eec.jpg` | `lane` | nặng | Bỏ sót vạch `L1` phân làn bên trái của xe đang đi, chỉ gán vạch `R1`. |
| 2 | QC1-04 | `A03_b1c66a42-6f7d68ca.jpg` | `lane` (R1) | chính | Vạch `R1` bắt đầu quá muộn ở lưng chừng ảnh (y = 466.0 px) thay vì vẽ sát đầu xe (dưới đáy ảnh). |
| 3 | QC1-05 | `A03_b1c66a42-6f7d68ca.jpg` | `lane` (L1) | chính | Vạch `L1` bị xe phía trước che khuất nhưng chưa bật cờ `occluded = true` (`occluded="0"`). |
| 4 | QC1-06 | `A03_b1c66a42-6f7d68ca.jpg` | `lane` (L1) | chính | Vạch `L1` phân làn cùng chiều bị gán nhầm thuộc tính `style = solid, color = yellow` (lẽ ra là `dashed, white`). |

*(Ảnh đối chứng không lỗi theo yêu cầu kiểm tra của Coach: Ảnh `A02_b3c26aff-63a0d7d6.jpg` đạt chuẩn 100%: vạch đứt L1 là 1 polyline liên tục 14 điểm từ gần ra xa, đủ L1/R1/L2, đủ vùng lái direct/alternative, đủ 4 tag).*

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| `A05_b2576c8c-2de20b8a.jpg` | Ảnh đường nông thôn không có vạch sơn kẻ đường (chỉ có mép vỉa hè `road_curb`), lint báo QC1-02 thiếu L1/R1 có tính lỗi không? | Được miễn QC1-02 theo quy định tại `CHECKPOINTS.md` Task 1 và `delivery_road_v1.0.md` mục 2 do coach xác nhận đường thực tế không có vạch sơn. |

## Quyết định
Lỗi nặng: 1   Lỗi chính: 3 / 67 nhãn = 4.48 %   Lỗi nhẹ: 0   Ca chờ lead: 0  
Quyết định (Release / Hold / Rework): **Rework**  
Lý do (theo luật của phiếu): Lô có 1 lỗi nặng (A06 thiếu vạch `L1` sát xe theo quy tắc QC1-02). Theo luật của phiếu QC 1: có ít nhất 1 lỗi nặng thì quyết định là Rework để bạn bổ sung vạch L1 trước khi bàn giao.

---
Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
