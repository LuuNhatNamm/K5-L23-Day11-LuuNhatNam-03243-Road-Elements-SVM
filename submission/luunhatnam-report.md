# Báo cáo cá nhân — Ngày 11

| Thông tin | Nội dung |
| --- | --- |
| Họ tên | Lưu Nhật Nam |
| Mã học viên | 03243 |
| Bài lab | Road Elements & SVM |
| Công cụ | CVAT local 2.82.0 |
| Guideline | Road v1.0 |
| Ngày viết báo cáo | 21/11/2026 |
| Lần nộp theo manifest | 2, bản cập nhật phần B |
| Thời điểm export | A, A-extra, B-extra dùng bản ngày 21/11/2026 từ 08:47 đến 08:48. B được export lại lúc 10:16 ngày 21/11/2026, Asia/Jakarta. |
| Số lần nộp lại sau Rework | Bổ sung theo lịch sử nộp thực tế |

Tôi đã gán nhãn 28 ảnh trong bốn task A, A extra, B và B-extra. Tôi sử dụng công cụ hỗ trợ tạo đề xuất nhãn, sau đó xem lại và chỉnh sửa trên CVAT. Bài làm bao gồm 20 ảnh bắt buộc và 8 ảnh thêm.

## 1. Kiểm project

| Mục | Kết quả đối chiếu Road v1.0 | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | Cấu hình có đủ sáu nhãn hình | lane và road_curb dùng polyline; crosswalk và drivable dùng polygon; traffic_light và traffic_sign dùng rectangle. |
| Thuộc tính và giá trị | Đã đối chiếu cấu hình nhãn với guideline | Lane có position, style, color, kind; drivable có area_type; đèn và biển có các thuộc tính tương ứng theo Road v1.0. Tôi kiểm lại giá trị của từng đối tượng khi rà ảnh. |
| 4 tag ảnh | Đủ 112 tag trên 28 ảnh | Mỗi ảnh có camera, timeofday, weather, source. Các tag có thuộc tính select tên value. |
| Trạng thái job | Đã hoàn tất trên CVAT | Completed. |

## 2. Số lượng đã gán


| Task trong bài lab | Tên trên CVAT | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | A | 12 | 41 | 27 | 8 | 40 | 26 | 25 |
| front-extra, đã làm 4/4 | A extra | 4 | 12 | 6 | 8 | 13 | 8 | 10 |
| fisheye | B | 8 | 6 | 15 | 11 | 11 | 7 | 4 |
| fisheye-extra, đã làm 4/4 | B-extra | 4 | 0 | 5 | 4 | 1 | 0 | 0 |
| **Tổng** | | **28** | **59** | **53** | **31** | **65** | **41** | **39** |

Tổng cộng có **288 shape và 112 tag**. Số lượng cần cập nhật nếu tôi tiếp tục thêm hoặc xóa nhãn trước khi export.

## 3. Bảng ca khó

| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
| --- | --- | --- | --- | --- |
| A13 | weather | rain và overcast | rain | Ảnh có dấu hiệu mưa, giọt nước trên kính và mặt đường ướt. |
| B11 | lane | Vạch phân làn và đường biên ô đỗ | Loại các đường biên ô đỗ khỏi lane | Các vạch bao quanh ô đỗ dành cho người khuyết tật và vùng gạch chéo thuộc khu vực đỗ xe. |
| A05 | lane | Cảnh báo thiếu L1 và R1 và phần vạch thực sự nhìn thấy | Giữ nhãn theo phần vạch nhìn thấy | xác nhận ảnh không thấy L1 và R1; ghi nhận để coach đối chiếu miễn QC1-02. |
| A06 | lane | Cảnh báo thiếu R1 và phần vạch thực sự nhìn thấy | Giữ nhãn theo phần vạch nhìn thấy | xác nhận ảnh không thấy R1; ghi nhận để coach đối chiếu miễn QC1-02. |
| A09 | lane | Cảnh báo thiếu R1 và phần vạch thực sự nhìn thấy | Giữ nhãn theo phần vạch nhìn thấy | xác nhận ảnh không thấy R1; ghi nhận để coach đối chiếu miễn QC1-02. |
| A14 | lane | Cảnh báo thiếu R1 và phần vạch thực sự nhìn thấy | Giữ nhãn theo phần vạch nhìn thấy | xác nhận ảnh không thấy R1; ghi nhận để coach đối chiếu miễn QC1-02. |

## 4. Phiếu QC 1 nhận được

| Thông tin QC chéo | Nội dung cần điền |
| --- | --- |
| Bạn kiểm lô của tôi |  Nguyễn Việt Anh|
| Quyết định nhận được |  Hold |

| Mã lỗi | Ảnh và nhãn | Số lỗi ghi nhận | Đồng ý? | Xử lý |
| --- | --- | ---: | --- | --- |
| QC1-04 | A08, lane ID 2144 | 1 lỗi chính | Đồng ý với quy tắc vẽ từ gần ra xa | Cách khắc phục là đảo thứ tự điểm của polyline. Tôi đã xác nhận hoàn tất chỉnh sửa trong trao đổi, cần đối chiếu với bản export cuối. |

Với phần drivable, tôi ghi nhận xác nhận của giảng viên trong bảng ca khó để người kiểm có cơ sở đối chiếu.

## 5. Kiểm file export

Bản B mới đã được ghép với B-extra. Kiểm tra lại xác nhận lane trên B08 có position=other. Lint còn 5 cảnh báo QC1-02 về thiếu vị trí làn. Tôi xác nhận A05 không thấy L1/R1, còn A06, A09 và A14 không thấy R1. Tôi ghi các trường hợp này là ca không nhìn thấy vạch để đối chiếu miễn cảnh báo theo quy định của lab.

Định dạng bàn giao là **CVAT for images 1.1**, tắt Save images. Bộ front cần chứa A01–A16 và bộ fisheye cần chứa B01–B12.

| File dự kiến | Mở lại được? | Số shape ảnh 1, job / file | Số shape ảnh 2, job / file | Tag camera có trong XML? |
| --- | --- | --- | --- | --- |
| luunhatnam-front.zip | Đọc lại được XML trong ZIP | A01, 13 / 13 | A02, 8 / 8 | Có |
| luunhatnam-fisheye.zip | Đọc lại được XML trong ZIP | B01, 4 / 4 | B02, 15 / 15 | Có |

Hai ZIP đã được gộp từ bốn bản export gốc và đọc lại bằng bộ kiểm của lab. Tôi dùng lệnh sau từ thư mục gốc bài lab trong PowerShell.

```powershell
$env:PYTHONPATH = "src"
python -X utf8 -m road_lab.road_check lint submission/luunhatnam-front.zip submission/luunhatnam-fisheye.zip --manifest submission/luunhatnam-manifest.json --name luunhatnam --revision 2
```

Manifest được cập nhật lên revision 2 sau khi thay phần B bằng bản export mới. Hai ZIP và manifest revision 1 được lưu trong thư mục submission/r1 để đối chiếu lịch sử.

| Nội dung kiểm tra cuối | Trạng thái |
| --- | --- |
| Mở được hai ZIP và đọc annotations.xml | Đã đọc lại thành công bằng bộ kiểm của lab |
| Đối chiếu số shape giữa job và XML ở hai ảnh mỗi bộ | Số shape trong bản export khớp số liệu job đã ghi cho A01, A02, B01, B02 |
| Chạy lint trên hai ZIP thực tế | Đã chạy, có 44 cảnh báo gợi ý. Kết quả được lưu tại outputs/export-merge/lint.txt |
| Tạo manifest và kiểm contains_images=false | Đã tạo revision 2, cả hai ZIP đều contains_images=false |
| Hoàn tất trạng thái Completed của bốn job |  Đã hoàn thành.|

## 6. Ảnh chụp màn hình

**Nhãn của project**

Project d11-road-LuuNhatNam có sáu label hình gồm lane, road_curb, crosswalk, drivable, traffic_light, traffic_sign và bốn tag camera, timeofday, weather, source.

![Danh sách sáu label và bốn tag trong project d11-road-LuuNhatNam](images/01-project-labels.png)

**Ảnh camera trước A12**

Ảnh thể hiện các polyline làn đường, vùng drivable, crosswalk và hộp đèn, biển sau khi gán nhãn.

![Kết quả gán nhãn trên ảnh camera trước A12](images/02-front-A12.png)

**Ảnh fisheye B03**

Ảnh B03_04267_RV.png được phóng to để quan sát đường polyline theo cung cong, vùng drivable và các nhãn liên quan.

![Đường polyline cong và các nhãn trên ảnh fisheye B03](images/03-fisheye-B03.png)

**Nhãn lane trong file XML**

Ảnh chụp annotations.xml của A01 thể hiện các thẻ `<polyline label="lane" ...>`, tọa độ points và các thuộc tính position, style, color, kind.

![Các thẻ polyline lane với tọa độ và thuộc tính trong XML của ảnh A01](images/04-xml-lane.png)

## 7. Tự đánh giá

Điểm tôi cần chú ý hơn là thứ tự vẽ polyline theo mã QC1-04. Khi tập trung bám theo vệt sơn, tôi dễ bắt đầu từ điểm thuận tay. Ở những buổi sau, tôi sẽ xác định điểm gần xe trước, vẽ từ gần ra xa và kiểm lại chiều điểm ngay khi hoàn thành từng vạch.

Với ảnh fisheye, tôi cần quan sát kỹ độ cong và phần thân xe ở rìa ảnh. Tôi cũng cần phân biệt vạch phân làn với vạch sang đường và vạch ô đỗ trước khi chọn nhãn.

Polyline lane có thể được nội suy thành vị trí x tại các hàng ảnh để tạo đích học cho model nhận diện làn. Khi thứ tự điểm bị đảo, các bước xử lý dựa trên điểm đầu hoặc hướng của đường có thể hiểu sai đầu gần xe. Nếu một bước nội suy chỉ dựa vào tọa độ các đoạn thẳng thì đảo thứ tự điểm vẫn giữ nguyên hình học, nhưng tuân thủ cùng quy tắc giúp dữ liệu nhất quán và thuận tiện kiểm tra.

Qua bài lab, tôi thấy việc rà thuộc tính và kiểm lại hình sau khi dùng công cụ hỗ trợ là cần thiết. Tôi cần kiểm tra cả ý nghĩa của nhãn, cách đặt biên và định dạng bàn giao trước khi nộp.
