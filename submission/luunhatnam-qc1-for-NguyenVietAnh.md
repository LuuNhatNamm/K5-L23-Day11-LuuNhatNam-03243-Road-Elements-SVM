# Phiếu QC 1 — Road v1.0

| Thông tin | Nội dung |
| --- | --- |
| Lô được kiểm | Lưu Nhật Nam, mã học viên 03243 |
| Người kiểm chéo là học viên | Nguyễn Việt Anh |
| Ngày | 21/11/2026 |
| Phiên bản guideline | Road v1.0 |
| File được đối chiếu | luunhatnam-front.zip và luunhatnam-fisheye.zip |
| Revision trong manifest | 1 |
| Mẫu 6 ảnh | A01, A02, A05, A08, B01, B06 |
| Ảnh thêm trong mẫu | 0 |
| Số nhãn trong mẫu, shape cộng tag | 91, gồm 67 shape và 24 tag |


## Tổng hợp theo mã

| Mã | Loại lỗi | Số mục đối chiếu trong mẫu | Số lỗi và kết quả | Mức |
| --- | --- | --- | --- | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 camera và 24 tag | 0 ở mẫu camera/tag đã đối chiếu | nặng / nhẹ |
| QC1-02 đủ L1, R1 | bỏ sót | 5 ảnh camera trước | 0 lỗi | nặng |
| QC1-03 position | sai thuộc tính / thừa | 14 lane | 0 lỗi | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 27 polyline | 1 lỗi chính | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 14 lane | 0 lỗi | chính |
| QC1-06 style, color, kind | sai thuộc tính | 14 lane | 0 lỗi | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 17 drivable | 0 lỗi | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 11 đèn | 0 lỗi | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 20 hộp đèn/biển | 0 lỗi | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 9 biển | 0 lỗi | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 2 ảnh B01, B06 | Chưa đo sai lệch 5 px trên toàn bộ đường | chính |
| QC1-12 file | lỗi file | 2 ZIP nhãn | Đọc được hai ZIP | nhẹ / nặng |

## Danh sách lỗi

| # | Mã | Ảnh | Nhãn, ID tham chiếu | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-04 | A08 | lane, ID 2144 ở bản chụp QC trước; điểm đầu khoảng (566, 279) | Chính | Polyline bắt đầu ở phần xa và kết thúc ở phần gần xe, ngược chiều quy định. Cách khắc phục là đảo thứ tự điểm để đường đi từ gần ra xa. |

Học viên cho biết đã sửa lỗi. Trong ZIP front revision 1 được gửi để gộp, polyline nêu trên vẫn có thứ tự từ điểm xa về điểm gần. Cần đối chiếu bản lưu mới nhất trên CVAT và export lại nếu hình đã được sửa sau thời điểm export.

## Ca mơ hồ

| Ảnh | Câu hỏi cho lead | Lời đáp hoặc trạng thái |
| --- | --- | --- |
| Các ảnh có xe che mặt đường | Cách vẽ drivable theo phần mặt đường nhìn thấy có được chấp nhận không? | Theo thông tin học viên cung cấp, giảng viên xác nhận cách vẽ này vẫn đúng. Ghi nhận chấp thuận và rút các nhận xét trước về việc khoét theo xe. |
| A05, B01 | Ảnh không thấy vạch phân làn rõ có được miễn cảnh báo thiếu L1/R1 không? | Chờ coach xác nhận theo từng ảnh và ghi vào phiếu. |

## Bổ sung về cảnh báo QC1-02 của toàn lô

Học viên xác nhận các vạch dưới đây không xuất hiện rõ trong ảnh. Ghi nhận các trường hợp này để đối chiếu miễn cảnh báo theo quy định của lab. Xác nhận này do học viên cung cấp, phần xác nhận miễn chính thức của coach sẽ được bổ sung khi có.

| Ảnh | Cảnh báo lint | Giải thích của học viên |
| --- | --- | --- |
| A05 | Thiếu L1 | Không thấy vạch L1 trong ảnh |
| A05 | Thiếu R1 | Không thấy vạch R1 trong ảnh |
| A06 | Thiếu R1 | Không thấy vạch R1 trong ảnh |
| A09 | Thiếu R1 | Không thấy vạch R1 trong ảnh |
| A14 | Thiếu R1 | Không thấy vạch R1 trong ảnh |

Các ca trên là ghi chú giải thích cảnh báo tự động của toàn lô. Danh sách một lỗi chính QC1-04 đã chọn trong phiếu được giữ theo nội dung kiểm chéo.

## Quyết định

| Mục | Kết quả |
| --- | --- |
| Lỗi chính được ghi trong phiếu | 1 |
| Tỉ lệ lỗi chính được ghi | 1 / 91 nhãn = 1,10% |
| Lỗi nặng và lỗi nhẹ của toàn mẫu | 1 |
| Ca chờ lead | 2 ảnh A05, B01 cần xác nhận về vạch làn |
| Quyết định | Hold |
| Lý do | Còn ca cần coach xác nhận ảnh hưởng đến kết luận. Người kiểm chéo cần hoàn tất các mục còn chờ và xác nhận trạng thái sửa lỗi trước khi quyết định bàn giao. |

Tỉ lệ 1,10% được tính từ một lỗi đã chọn ghi trên 91 nhãn trong mẫu. Kết quả này chỉ phản ánh nội dung hiện có của phiếu. Hai ZIP đã đọc được bằng bộ kiểm của lab và manifest ghi contains_images=false. Kết quả lint đầy đủ được lưu kèm để đối chiếu.

## Tài liệu đối chiếu

- [Báo cáo cá nhân](../submission/luunhatnam-report.md)
- [Manifest revision 1](../submission/r1/luunhatnam-manifest-r1.json)
- [Kết quả lint hai ZIP revision 1](../outputs/export-merge/r1/lint.txt)
- [Ảnh A08 trong lần QC trước](../outputs/qc-20261121/A08-overlay.jpg)
- [Thang mức lỗi](../docs/qc_severity_road_v1.0.md)
