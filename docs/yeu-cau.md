# Yêu cầu hệ thống quản lý thiết bị thí nghiệm (LEMS)
 
Phụ trách: N05-D
 
Gói 2 · M1 · [Issue #5](https://github.com/uit-se100-2026-hk1/se100-N05/issues/5). Chưa nghiệm thu.
 
Luồng chính (đơn mượn → duyệt → bàn giao → nhận lại) là nguồn của FR-01 đến FR-07, trùng với phạm vi [Issue #1](https://github.com/uit-se100-2026-hk1/se100-N05/issues/1).
 
Mỗi đơn mượn có trạng thái: **Chờ duyệt**, **Đã duyệt**, **Từ chối**, **Đang mượn**, **Đã trả**. Đơn Chờ duyệt chưa giữ thiết bị; thiết bị chỉ được giữ từ lúc đơn Đã duyệt cho đến lúc đơn Đã trả.
 
Phạm vi Gói 2 là luồng lõi. Hư hỏng, mất thiết bị, phạt trả trễ và quyền mượn phòng Lab AI chưa có quy định từ khách hàng nên để trong phần câu hỏi mở, không đưa vào phạm vi triển khai.
 
## Tác nhân
 
| Tác nhân | Là ai | Muốn gì từ hệ thống |
|---|---|---|
| Người mượn | Học sinh hoặc sinh viên cần mượn thiết bị thí nghiệm | Xem thiết bị còn cho mượn, gửi đơn mượn và theo dõi trạng thái đơn |
| Giáo viên | Giáo viên duyệt đơn mượn của học sinh, sinh viên | Xem các đơn đang chờ và quyết định duyệt hoặc từ chối |
| Cán bộ quản lý phòng lab | Người giữ thiết bị và làm việc trực tiếp với người mượn tại phòng lab | Bàn giao thiết bị cho đơn đã duyệt và nhận lại thiết bị khi người mượn trả |
 
## Yêu cầu chức năng
 
### Phạm vi Gói 2
 
| # | Tác nhân | Muốn | Để | Ai làm |
|---|---|---|---|---|
| FR-01 | Người mượn | Xem danh sách thiết bị và số lượng còn có thể mượn | Chọn thiết bị phù hợp trước khi gửi đơn | Người: mở danh sách, xem · Phần mềm: hiện tên thiết bị, tổng số và số còn có thể mượn; số đã được giữ cho đơn khác không tính vào số còn có thể mượn |
| FR-02 | Người mượn | Gửi đơn mượn thiết bị | Đề nghị được mượn thiết bị trong một khoảng thời gian | Người: chọn thiết bị, nhập số lượng, ngày mượn, ngày trả dự kiến rồi gửi · Phần mềm: từ chối và báo lý do nếu số lượng nhỏ hơn 1, vượt số còn có thể mượn hoặc ngày trả không sau ngày mượn; nếu hợp lệ thì lưu đơn ở trạng thái Chờ duyệt |
| FR-03 | Người mượn | Xem các đơn của mình và trạng thái hiện tại | Biết đơn đã được duyệt, từ chối hay cần trả | Người: mở danh sách đơn của mình · Phần mềm: chỉ hiện đơn của người đang dùng, kèm thiết bị, số lượng, ngày mượn, ngày trả dự kiến, trạng thái và lý do từ chối nếu có |
| FR-04 | Giáo viên | Xem danh sách đơn đang chờ duyệt | Biết đơn nào cần quyết định | Người: mở danh sách, chọn đơn · Phần mềm: hiện các đơn Chờ duyệt kèm người mượn, thiết bị, số lượng, ngày mượn, ngày trả dự kiến, sắp theo thời điểm gửi |
| FR-05 | Giáo viên | Duyệt hoặc từ chối một đơn đang chờ | Quyết định ai được mượn thiết bị | Người: chọn đơn, bấm duyệt hoặc từ chối, nhập lý do nếu từ chối · Phần mềm: khi duyệt thì kiểm số lượng còn đủ, giữ thiết bị và chuyển đơn sang Đã duyệt; nếu không còn đủ thì từ chối thao tác và báo lý do; khi từ chối thì chuyển đơn sang Từ chối, không giữ thiết bị |
| FR-06 | Cán bộ quản lý phòng lab | Xác nhận đã bàn giao thiết bị cho đơn đã duyệt | Ghi nhận thiết bị đang ở chỗ người mượn | Người: giao thiết bị thực tế, bấm xác nhận bàn giao · Phần mềm: chỉ nhận đơn Đã duyệt; chuyển đơn sang Đang mượn và ghi thời điểm bàn giao |
| FR-07 | Cán bộ quản lý phòng lab | Xác nhận đã nhận lại thiết bị | Kết thúc đơn và cho người khác mượn tiếp | Người: nhận thiết bị thực tế, bấm xác nhận nhận lại · Phần mềm: chỉ nhận đơn Đang mượn; chuyển đơn sang Đã trả, ghi thời điểm nhận lại và cộng số lượng trả về số còn có thể mượn |
 
### Đề xuất, chờ xác nhận với khách hàng
 
| # | Tác nhân | Muốn | Để | Ai làm |
|---|---|---|---|---|
| FR-08 | Cán bộ quản lý phòng lab | Ghi tình trạng thiết bị khi nhận lại | Có căn cứ khi thiết bị bị hư hỏng hoặc thiếu | Người: kiểm thiết bị, chọn tình trạng · Phần mềm: lưu tình trạng cùng đơn. Ai chịu trách nhiệm khi hư hỏng chưa chốt |
| FR-09 | Cán bộ quản lý phòng lab | Xem các đơn đã quá ngày trả dự kiến | Nhắc người mượn trả thiết bị | Người: mở danh sách đơn quá hạn · Phần mềm: hiện các đơn Đang mượn có ngày trả dự kiến đã qua. Chính sách phạt trả trễ chưa chốt |
| FR-10 | Cán bộ quản lý phòng lab | Thêm hoặc sửa thiết bị và số lượng trong danh sách | Danh sách thiết bị đúng với thực tế phòng lab | Người: nhập hoặc sửa tên, số lượng · Phần mềm: lưu thay đổi và không cho tổng số nhỏ hơn số đang được giữ |
 
## Yêu cầu phi chức năng
 
Mỗi dòng đủ chỉ số, ngưỡng có số kèm đơn vị, điều kiện đo và cách đo. Có ít nhất một dòng không nói về tốc độ (NFR-02 đến NFR-05).
 
| # | Chỉ số | Ngưỡng | Điều kiện đo | Cách đo | Ảnh hưởng tới thiết kế nào |
|---|---|---|---|---|---|
| NFR-01 | Thời gian hiển thị danh sách thiết bị | ≤ 2 giây tại phân vị 95 | Tải trang 20 lần trên bản deploy với 100 thiết bị mẫu | Dùng Chrome DevTools đo thời gian từ lúc mở trang đến lúc danh sách hiện đủ, lấy phân vị 95 của 20 lần | Danh sách đọc từ dữ liệu đã lưu trong trình duyệt, không tải dữ liệu thừa. N05-D |
| NFR-02 | Số lần vi phạm luật tồn kho (số còn có thể mượn âm hoặc không bằng tổng trừ số đang giữ) | 0 lần trên 100 chuỗi thao tác | Mỗi chuỗi gồm 50 thao tác ngẫu nhiên (gửi đơn, duyệt, từ chối, bàn giao, nhận lại) trên dữ liệu mẫu | Chạy script sinh chuỗi ngẫu nhiên, sau mỗi thao tác kiểm công thức tồn kho và đếm số lần sai | Luật tồn kho đặt trong lớp miền, đổi trạng thái đơn và đổi số lượng trong cùng một thao tác. N05-D |
| NFR-03 | Tỷ lệ đơn giữ nguyên nội dung và trạng thái sau khi tải lại trang | 100% (60/60 lượt đối chiếu) | 20 đơn đủ cả năm trạng thái, tải lại trang 3 lần trong cùng một trình duyệt | Ghi mã đơn, người mượn, số lượng, trạng thái của 20 đơn trước khi tải lại; sau mỗi lần tải lại đối chiếu từng đơn | Lưu đơn và tồn kho vào bộ nhớ trình duyệt rồi đọc lại khi mở trang, không chỉ giữ trong biến giao diện. N05-D |
| NFR-04 | Tỷ lệ thao tác sai bị từ chối mà dữ liệu không đổi | 100% (20/20 ca) | 20 ca sai chạy trên bản deploy: duyệt đơn đã duyệt, bàn giao đơn Từ chối, nhận lại đơn chưa bàn giao, mượn vượt số còn lại, ngày trả trước ngày mượn | Chụp dữ liệu đơn và tồn kho trước và sau từng ca; đạt khi cả 20 ca hiện thông báo lỗi và dữ liệu giữ nguyên | Kiểm điều kiện tại lớp miền, giao diện chỉ hiển thị thông báo lỗi. N05-D |
| NFR-05 | Số thao tác để người mượn gửi xong một đơn | ≤ 5 thao tác | Người chưa từng dùng hệ thống, bắt đầu từ trang chủ trên bản deploy, thử 5 lượt | Đếm số lần bấm và nhập từ trang chủ đến khi đơn hiện ở trạng thái Chờ duyệt, lấy giá trị lớn nhất của 5 lượt | Form gửi đơn gọn trên một màn hình, ngày mượn có giá trị mặc định. N05-D |
 
## Ràng buộc nghiệp vụ — điều KHÔNG được phép xảy ra
 
| # | Ràng buộc | Ai chịu trách nhiệm bảo vệ (lớp nào, điền ở Gói 4) |
|---|---|---|
| BR-01 | Số thiết bị đang được giữ (đơn Đã duyệt và Đang mượn) của một loại không được vượt tổng số của loại đó, kể cả khi giáo viên duyệt nhiều đơn liên tiếp. Số còn có thể mượn không bao giờ âm | Chưa xác định lớp; điền ở Gói 4 |
| BR-02 | Đơn chỉ đi theo thứ tự Chờ duyệt → Đã duyệt → Đang mượn → Đã trả, hoặc Chờ duyệt → Từ chối. Không bỏ bước, không quay lại bước trước; đơn Từ chối và Đã trả là trạng thái cuối | Chưa xác định lớp; điền ở Gói 4 |
| BR-03 | Chỉ giáo viên được duyệt hoặc từ chối đơn; chỉ cán bộ quản lý phòng lab được xác nhận bàn giao và nhận lại; người mượn không tự đổi trạng thái đơn của mình | Chưa xác định lớp; điền ở Gói 4 |
 
## Câu hỏi còn mở cho khách hàng
 
- Khi thiết bị bị hư hỏng hoặc mất, ai chịu trách nhiệm và ai quyết định cách xử lý?
- Ai được quyền mượn phòng Lab AI, và đơn mượn phòng có đi qua cùng quy trình duyệt không?
- Trả trễ thì xử lý thế nào: có phạt, có hạn chế mượn lần sau không, và ai quyết định?
- Đơn mượn do giáo viên nào duyệt: bất kỳ giáo viên nào hay giáo viên phụ trách môn hoặc phòng lab đó?
- Giới hạn số lượng và số ngày được mượn cho một đơn là bao nhiêu, có khác nhau giữa học sinh và sinh viên không?
- Thiết bị có cần theo dõi từng chiếc bằng mã riêng, hay chỉ tính theo loại và số lượng?
- Đơn đã duyệt nhưng người mượn không đến nhận thì giữ thiết bị bao lâu?
- Người mượn có được hủy đơn khi chưa được duyệt không?
