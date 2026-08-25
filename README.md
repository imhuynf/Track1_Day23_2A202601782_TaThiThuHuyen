# Track 1 — Ngày 23: Bộ chỉ số sản phẩm

## Thông tin học viên

- **Họ và tên:** Tạ Thị Thu Huyền
- **Mã học viên:** 2A202601782
- **Dự án:** Intelligent Resume Screening Automation (iRSA)
- **Giai đoạn hiện tại:** Đã triển khai. Chưa đủ dữ liệu để xác định phạm vi triển khai, nhóm người dùng thực tế và việc sử dụng CV thật.
- **Người dùng chính (persona):** Chuyên viên tuyển dụng chịu trách nhiệm sàng lọc ban đầu cho các vị trí có số lượng hồ sơ lớn.
- **Tình huống sử dụng (use case):** Chuyên viên tuyển dụng xem xét từng hồ sơ ứng tuyển trong bối cảnh của vị trí tương ứng và ghi nhận quyết định sàng lọc ban đầu.
- **Ứng dụng đã triển khai:** [Cổng thông tin ứng viên](https://portal-irsa.vercel.app/) · [Cổng thông tin chuyên viên tuyển dụng/quản trị viên](https://irsa-admin.vercel.app/)

## Quyết định Giai đoạn 00 — Phạm vi

- **Bối cảnh nghiệp vụ:** Một vị trí tuyển dụng (`Job Opening`) có bộ tiêu chí và trọng số riêng.
- **Đơn vị công việc nhỏ nhất:** Một hồ sơ ứng tuyển (`Candidate Application`) gắn với vị trí tương ứng.
- **Lập luận cá nhân:** Tôi chọn phạm vi theo từng hồ sơ ứng tuyển vì đây là đơn vị nhỏ nhất mà chuyên viên tuyển dụng trực tiếp xem xét, đưa ra quyết định và làm thay đổi trạng thái trong quy trình. Vị trí tuyển dụng vẫn là bối cảnh bắt buộc vì mức độ phù hợp của CV chỉ có ý nghĩa khi đặt cạnh tiêu chí của một vị trí cụ thể. Đổi lại, bài chưa phản ánh hiệu quả của toàn bộ quy trình tuyển dụng, nhưng xác định được rõ người thực hiện, đối tượng và điểm kết thúc của một lượt sàng lọc.

## Quyết định Giai đoạn 01 — Hành động cốt lõi (Core Action)

- **Hành động cốt lõi:** Chuyên viên tuyển dụng hoàn tất việc xem xét và ghi nhận quyết định sàng lọc cho một hồ sơ ứng tuyển trong bối cảnh vị trí tương ứng.
- **Đối tượng:** Một hồ sơ ứng tuyển gắn với một vị trí cụ thể.
- **Điều kiện hoàn tất:** Hệ thống lưu thành công một kết quả sàng lọc rõ ràng. Giao diện hiện có hai trạng thái quan sát được là `shortlisted` và `rejected`; cần xác minh `rejected` có đúng là “không được chọn ở vòng sàng lọc ban đầu” hay không.
- **Sự kiện đo lường đề xuất:** `application_screening_decision_recorded`. Chưa có bằng chứng cho thấy sự kiện này đã được cài đặt trong sản phẩm.
- **Gate 1:** Đạt 4/5 tiêu chí. Tiêu chí “có ý nghĩa” chỉ đạt có điều kiện vì số quyết định tăng có thể chỉ phản ánh số hồ sơ tăng, chưa chứng minh chất lượng sản phẩm tốt hơn.
- **Lập luận cá nhân:** Tôi chọn thời điểm hoàn tất xem xét và ghi nhận quyết định vì đây là lúc khuyến nghị của hệ thống trở thành kết quả do chuyên viên tuyển dụng chịu trách nhiệm. Tôi không chọn đầu ra của AI, lượt xem CV hoặc riêng hành vi đưa vào danh sách ngắn vì các lựa chọn đó chưa bao phủ một lượt sàng lọc hoàn chỉnh. Đổi lại, quyết định được lưu mới chỉ chứng minh giá trị vận hành, chưa chứng minh tính chính xác hoặc công bằng; vì vậy không thể dùng số lượng quyết định tuyệt đối làm chỉ số thành công duy nhất.

## Quyết định Giai đoạn 02 — Bản chất hành vi và nhịp tự nhiên

- **Bản chất chính:** Phản ứng theo sự kiện (`event-response`). Quy trình của nhóm là bối cảnh vận hành; hồ sơ đủ điều kiện xem xét mới là nguyên nhân làm hành động cốt lõi xuất hiện lại.
- **Tác nhân tự nhiên:** Một hồ sơ thuộc vị trí mà chuyên viên phụ trách đã có đủ dữ liệu và kết quả sàng lọc để xem xét. Thông báo chỉ nhắc việc, không tạo ra nhu cầu sàng lọc.
- **Điều kiện lặp lại:** Có hồ sơ tiếp theo đủ điều kiện xem xét.
- **Nhịp đo:** Theo từng cơ hội phát sinh (`opportunity-based`), tổng hợp ở cấp chuyên viên tuyển dụng × vị trí tuyển dụng. Không mặc định đo theo ngày, tuần hoặc tháng.
- **Gate 2:** Đạt, nhưng còn dữ liệu cần kiểm chứng. Chưa rõ chuyên viên xử lý ngay từng hồ sơ hay gom thành phiên và chưa có phân bố thời gian giữa các cơ hội sàng lọc.
- **Lập luận cá nhân:** Tôi chọn nhịp theo cơ hội vì chuyên viên chỉ có lý do thực hiện hành động cốt lõi khi một hồ sơ thực sự đủ điều kiện xem xét. Đo theo ngày hoặc tuần sẽ đánh đồng “không có nhu cầu” với “có nhu cầu nhưng không dùng sản phẩm”. Đổi lại, hệ thống phải ghi nhận chính xác điều kiện và thời điểm một cơ hội bắt đầu; tôi chấp nhận độ phức tạp này để chỉ số phản ánh đúng nhu cầu thực tế.

## Quyết định Giai đoạn 03 — Hệ thống chỉ số và retention

- **Kích hoạt (activation), định nghĩa đề xuất:** Tỷ lệ chuyên viên mới ghi nhận quyết định sàng lọc đạt chuẩn đầu tiên trước hạn, tính từ cơ hội sàng lọc đầu tiên. Cần phân tích theo nhóm cùng mốc bắt đầu để xác định một lần đã đủ chứng minh giá trị ban đầu hay chưa.
- **Mức độ sử dụng (engagement):** Tỷ lệ hoàn tất quyết định theo cơ hội và tỷ lệ quyết định đạt chuẩn. Không dùng số lượng quyết định tuyệt đối vì chỉ số đó tăng theo số hồ sơ.
- **North Star Metric đề xuất:** **Mức độ bao phủ quyết định sàng lọc đạt chuẩn** — tỷ lệ hồ sơ đủ điều kiện nhận được quyết định do chuyên viên có thẩm quyền ghi nhận, đáp ứng bộ điều kiện chất lượng và đúng hạn trong mỗi chu kỳ vị trí tuyển dụng.
- **Retention:** Đo ở cấp chuyên viên tuyển dụng × vị trí tuyển dụng. Chỉ tính quay lại khi chuyên viên ghi nhận quyết định đạt chuẩn cho một hồ sơ khác trở thành đủ điều kiện sau mốc đầu tiên; hồ sơ đã nằm sẵn trong cùng hàng đợi chỉ được tính là engagement. Trường hợp chưa có cơ hội mới được loại khỏi mẫu số thay vì bị xem là rời bỏ.
- **Chỉ số cảnh báo (counter-metric):** Tỷ lệ quyết định không đạt trong mẫu kiểm toán chất lượng. Rào chắn bắt buộc: số quyết định sàng lọc không có người có thẩm quyền xem xét phải bằng `0`.
- **Gate 3:** Đạt về định nghĩa, nhưng còn yêu cầu cài đặt đo lường và kiểm chứng. Chưa có dữ liệu để đặt mốc so sánh, xác nhận ngưỡng kích hoạt hoặc tính kết quả thực tế.
- **Lập luận cá nhân:** Tôi chọn tỷ lệ đã chuẩn hóa theo số cơ hội thay vì số quyết định tuyệt đối vì mục tiêu là hoàn tất đúng lượng công việc thực sự tồn tại, không phải tối đa hóa thao tác. Tôi đưa trách nhiệm của con người, tính đầy đủ của quyết định và thời hạn vào bộ điều kiện chất lượng để North Star Metric không tăng bằng cách tự động ra quyết định hoặc lưu kết quả thiếu căn cứ. Đổi lại, chỉ số cần thêm dữ liệu về điều kiện sẵn sàng, hạn xử lý, người xem xét và phiên bản tiêu chí; nếu thiếu các trường đó, bảng theo dõi chưa đủ cơ sở để kết luận sản phẩm tạo ra giá trị.

## Tệp bài làm

- **Bản HTML trong kho mã nguồn:** [Mở Bộ chỉ số sản phẩm](./metrics-pack.html)
- **Đường dẫn công khai để nộp:** [Mở Bộ chỉ số sản phẩm trên GitHub Pages](https://imhuynf.github.io/Track1_Day23_2A202601782_TaThiThuHuyen/)
- **Đường dẫn trực tiếp đến tệp HTML:** [metrics-pack.html](https://imhuynf.github.io/Track1_Day23_2A202601782_TaThiThuHuyen/metrics-pack.html)
- **Kho mã nguồn GitHub:** [Track1_Day23_2A202601782_TaThiThuHuyen](https://github.com/imhuynf/Track1_Day23_2A202601782_TaThiThuHuyen)

Tệp Bộ chỉ số sản phẩm gồm:

1. `00 — Dự án, persona và công việc cốt lõi (core job)`
2. `01 — Thẻ Core Action và kết quả tự kiểm 5 tiêu chí`
3. `02 — Thẻ bản chất hành vi và kết luận cadence`
4. `03 — Hệ thống chỉ số: activation, engagement, NSM, chỉ số dẫn dắt và counter-metric`
5. `04 — Định nghĩa retention: đủ 6 thành phần`
6. `05 — Product Loop: ít nhất 2 chu kỳ và giả thuyết chỉ số`
7. `06 — Danh sách 4–8 event và ít nhất 2 tiêu chí nghiệm thu`
8. `07 — Điều chỉnh nếu có thay đổi lớn`

Các tên tiếng Anh còn giữ lại là thuật ngữ của khung bài học hoặc tên kỹ thuật cần dùng chính xác.

## Điều tôi mang về áp dụng cho dự án thật

> Phần này phải do người nộp tự viết: nêu một bài học quan trọng từ bài thực hành và cách áp dụng cụ thể vào iRSA.

## Kiểm tra trước khi nộp

- [x] Kho mã nguồn có đúng tên `Track1_Day23_2A202601782_TaThiThuHuyen`.
- [x] Đã bổ sung đường dẫn công khai của Bộ chỉ số sản phẩm; GitHub Pages không yêu cầu quyền đăng nhập để xem.
- [x] Thẻ Core Action có kết quả tự kiểm 5 tiêu chí.
- [x] Cadence xuất phát từ bản chất của hành vi.
- [x] Retention đủ 6 thành phần và khớp cadence.
- [x] North Star Metric gồm đơn vị giá trị, ngưỡng chất lượng và tần suất.
- [x] Có ít nhất một counter-metric.
- [x] Product Loop có ít nhất 2 chu kỳ và giả thuyết chỉ số.
- [x] Mỗi event trong bảng đo lường được dùng để tính ít nhất một chỉ số.
- [x] Có ít nhất 2 tiêu chí nghiệm thu cho hệ thống đo lường.
- [ ] Người nộp đã đọc, xác nhận và hoàn thiện `ai-support-log.md` bằng trải nghiệm thực tế của mình.
- [ ] Người nộp đã tự viết phần “Điều tôi mang về áp dụng cho dự án thật”.
