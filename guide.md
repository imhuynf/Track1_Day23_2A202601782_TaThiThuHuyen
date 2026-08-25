# 0. Đọc trước khi làm (3 phút)

## Trước khi bắt đầu

Mỗi học viên áp dụng framework product metrics của buổi giảng lên chính dự án mình đang build: chọn core action, xây bộ metric tối ưu core action, định nghĩa retention theo nhịp tự nhiên, phác product loop và đặt yêu cầu tracking.

**Cơ bản**

### Thời lượng dự kiến

90 phút

### Môi trường cần có

macOS, Linux, Windows · Một tệp trình bày trực quan của riêng bạn (FigJam, slide, Notion, HTML hoặc tương đương), Deck bài giảng Day 23 để tra framework, Tài khoản GitHub để nộp bài, Đồng hồ bấm giờ

### Cần biết trước

Đã tham gia bài giảng Day 23 (North Star Metric, Retention & Engagement, Nature vs Nurture, Habit Loop) · Có một dự án đang build (dự án nhóm của khoá học hoặc dự án cá nhân đều được)

### Xong bài này, bạn sẽ

Chọn được một core action gần core value, phân biệt được core action với thao tác giao diện và output hệ thống · Xác định natural cadence của core action từ bản chất hành vi (nature) thay vì chọn daily/weekly theo thói quen dashboard · Xây dựng bộ metric tối ưu core action: activation, engagement, North Star, leading indicators, counter-metric · Định nghĩa retention đầy đủ sáu thành phần (unit, cohort entry, return event, window, threshold, segment) khớp nhịp tự nhiên · Thiết kế product loop như một giả thuyết có metric hypothesis, và đặt yêu cầu tracking tối thiểu cho bộ metric

### Nếu bị chặn

Bài này làm gì? Bạn đóng vai PM của chính dự án mình đang build và đi một chuỗi quyết định: hành vi nào là core action → nhịp tự nhiên của nó là gì → đo nó bằng bộ metric nào, retention ra sao → thiết kế loop nào để metric đó tăng → cần tracking event gì.

### Từ ngữ sẽ gặp liên tục (đọc một lần là đủ):

| Từ | Nghĩa đơn giản |
|---|---|
| Core action | Hành vi quan trọng user thực hiện để nhận giá trị cốt lõi — không phải mở app hay đăng nhập |
| Core value event | Sự kiện chứng minh giá trị đã xảy ra (vd task_completed ) |
| Nature / Natural cadence | Nhịp nhu cầu tự nhiên của user — trước khi có notification hay gamification |
| Nurture | Những gì team chủ động làm để nuôi nhịp đó — notification, email, onboarding |
| Activation | Thời điểm user lần đầu thực sự nhận được giá trị |
| Retention (6 thành phần) | Unit · cohort entry · return event · window · threshold · segment |
| North Star Metric | Chỉ số cốt lõi = unit of value + quality threshold + frequency |
| Counter-metric | Chỉ số phát hiện "metric chính tăng nhưng trải nghiệm xấu đi" |
| Metric hypothesis | Câu giả thuyết: "loop này đúng thì metric X sẽ đổi theo hướng Y" |

### Làm ở đâu?

Toàn bộ bài làm trên một tệp trình bày trực quan của riêng bạn (FigJam/slide/Notion...). Không cần viết code, nhưng bài nộp cuối là một repository cá nhân (xem mục 10). Các thẻ bài (Core Action Card, Action Nature Card...) có template ngay trong brief này — copy sang tệp của bạn rồi điền.

Cứ 1 phase xong là có 1 "gate" — ô kiểm tra nhỏ tự đối chiếu. Qua gate thì đi tiếp, không qua thì gọi coach.

# 1. Đề bài và cách làm

Dự án của bạn đã có ý tưởng, có thể đã có prototype. Nhưng trả lời được câu này chưa:

**Hành vi nào chứng minh người dùng thực sự nhận được giá trị — và bạn sẽ biết điều đó bằng cách đo gì?**

Nếu core action chưa rõ, toàn bộ metric, loop và tracking phía sau đều không có cơ sở. Vì vậy bài lab đi theo chuỗi bắt buộc:

**Core action → Nhịp tự nhiên (nature) → Bộ metric + retention → Product loop (giả thuyết) → Tracking (phép thử)**

| Phase | Thời gian | Câu hỏi trung tâm | Đầu ra |
|---|---:|---|---|
| 0. Chốt phạm vi | 10 phút | Dự án nào, persona nào, core job nào? | Phạm vi bài làm |
| 1. Core Action | 15 phút | Hành vi nào gần core value nhất? | Core Action Card |
| 2. Nature & cadence | 15 phút | Nhu cầu tự nhiên xuất hiện bao lâu một lần? | Action Nature Card + kết luận cadence |
| 3. Metric System + Retention | 25 phút | Đo core action bằng gì, quay lại tính thế nào? | Metric System + Retention Definition |
| 4. Ghi nhanh: Loop + Tracking | 15 phút | Loop nào di chuyển metric đó, đo bằng event gì? | Loop 2 chu kỳ + 4–8 events |
| 5. Tự soi lỗi & nộp | 10 phút | Bài có mắc lỗi kinh điển nào không? | Bản hoàn chỉnh |

## Luật của bài lab

1. Metric đi từ use case lên. Không "app kia dùng DAU mình cũng dùng DAU", không "MAU số to dễ báo cáo".
2. Nurture chỉ khuếch đại nature. Không được dùng notification để bịa ra một nhịp quay lại không tồn tại.
3. Không ép daily habit. Frequency phải đi từ bản chất hành vi — sản phẩm theo tháng/dự án không cần DAU.
4. Mọi event phải map về một metric. Event nào không tính được metric nào thì bỏ.
5. Loop là giả thuyết, metric là phép thử. Mọi loop phải kèm metric hypothesis.

## Cách làm việc

Bài làm hoàn toàn cá nhân — kể cả khi dự án bạn chọn là dự án nhóm của khoá học, mỗi người tự chọn core action, tự kết luận cadence, tự viết metric. Hai người cùng một dự án có thể ra hai Metrics Pack khác nhau; điều đó bình thường, miễn là lập luận đứng được.

Coach sẽ hỏi ngẫu nhiên bất kỳ ai: bảo vệ core action, một thành phần retention hoặc một event bất kỳ trong bài của bạn.

Phase 4 cố ý chỉ có 15 phút: ghi ý chính, không trau chuốt. Muốn làm bản tracking đầy đủ thì làm tiếp ngoài giờ.

## Sử dụng AI trong bài lab

Được dùng AI để brainstorm ứng viên core action, phản biện định nghĩa retention, gợi ý tên event. Không được dùng AI để chọn thay core action, viết thay kết luận cadence hay metric hypothesis — các quyết định lõi phải là của bạn. Mọi cách dùng AI phải khai báo trong AI Support Log.

# 2. Đầu vào và tài nguyên

- Dự án bạn đang build — dự án nhóm của khoá học hoặc dự án cá nhân đều được. Chọn một use case chính để phân tích sâu, không phân tích toàn bộ sản phẩm.
- Deck Day 23 — tra lại framework: Nature vs Nurture (S21–24), chọn metric từ use case (S25–28), Active ≠ Activated (S26), cohort retention (S29–30), retention so với ba mốc (S34), Metric Definition Contract (S47), case health app bốn bước (S48–51).
- Template các thẻ — nằm ngay trong từng phase của brief này.

Nếu chưa có dự án nào, chọn một trong các hướng quen thuộc: AI Travel Planner · AI Personal Assistant for Students · AI Customer Support Agent.

# 3. Phase 0 — Chốt phạm vi · 10 phút

Làm — ghi rõ một dòng mỗi mục lên đầu tệp của bạn:

1. Dự án: sản phẩm bạn đang build là gì?
2. Persona: ai là người dùng chính của use case này — một persona thôi.
3. Core job: họ đang cố hoàn thành việc gì — viết bằng lời người dùng, không mô tả bằng tính năng.

## Lỗi thường gặp

Viết core job kiểu "cần một AI assistant thông minh" — đó là tính năng, không phải vấn đề. Hãy viết kiểu: "Tôi mất quá nhiều thời gian gom thông tin môn học và vẫn bỏ lỡ deadline."

**Ghi lại ở đâu:** mục 00 — Phạm vi của tệp bạn.

# 4. Phase 1 — Core Action · 15 phút

## Kiến thức cần dùng

- Core action gắn trực tiếp với core job, tạo ra hoặc tiến gần rõ rệt tới core value, quan sát và lặp lại được (slide S25–28).
- Core action ≠ output hệ thống: AI tạo ra kết quả chưa nghĩa là user đã nhận value từ nó.

## 1. Phân biệt bốn khái niệm (5')

Làm — điền nhanh hàng này trước khi điền thẻ:

| Khái niệm | Câu hỏi | Ví dụ (trợ lý học tập) |
|---|---|---|
| Core job | User đang cố hoàn thành việc gì? | Không bỏ lỡ nhiệm vụ học tập quan trọng |
| Core action | User làm gì trong sản phẩm để tiến tới giá trị? | Thêm và hoàn thành một nhiệm vụ |
| Core value | User nhận được lợi ích gì? | Biết rõ việc cần làm, hoàn thành đúng hạn |
| Core value event | Sự kiện nào chứng minh value đã xảy ra? | task_completed |

### Nghĩ

Core action và core value event có thể trùng nhau, nhưng không phải lúc nào cũng trùng: bấm đặt xe là action, chuyến xe hoàn thành mới là event xác nhận value.

## 2. Điền Core Action Card (10')

Làm — copy bảng này sang tệp của bạn và điền:

| Thành phần | Câu trả lời của bạn |
|---|---|
| Target user | Ai thực hiện hành vi? |
| Core job | Họ đang cố hoàn thành việc gì? |
| Core action | Hành vi được chọn là gì? |
| Object | Hành vi tác động lên đối tượng nào? |
| Preconditions | Điều gì phải có trước khi hành vi xảy ra? |
| Completion rule | Khi nào action được xem là hoàn tất? |
| Core value | Người dùng nhận được lợi ích gì? |
| Evidence of value | Dấu hiệu nào chứng minh value đã xảy ra? |
| Candidate event | Event nào có thể dùng để tracking? |

## 3. Tự kiểm 5 tiêu chí (trong cùng 10')

Làm — chấm core action vừa chọn; trượt ≥ 2 tiêu chí thì phải chọn lại:

1. Gần core value — hành vi xảy ra là user đã tiến gần rõ rệt tới value chưa?
2. Có thể lặp lại — hành vi có xuất hiện lại khi nhu cầu quay lại không?
3. Có thể quan sát — bạn biết chính xác khi nào nó hoàn tất không?
4. Có ý nghĩa — hành vi tăng có thật sự nghĩa là sản phẩm tốt hơn không?
5. Có thể tác động — team có thể cải thiện khả năng nó xảy ra không?

## Lỗi thường gặp

Chọn "mở app", "đăng nhập", "hỏi AI" — đó là thao tác giao diện, không phải hành vi tạo value.

Viết mơ hồ kiểu "engage", "sử dụng sản phẩm", "có trải nghiệm tốt".

**Ghi lại ở đâu:** Core Action Card + kết quả tự kiểm → mục 01 — Core Action của tệp bạn.

## Tự kiểm · GATE 1 — Core action đứng vững

Bạn qua gate khi: core action có actor, object, completion rule; qua ít nhất 4/5 tiêu chí tự kiểm; và bạn giải thích được vì sao nó không phải "mở app" hay "hỏi AI".

# 5. Phase 2 — Nature & cadence · 15 phút

## Kiến thức cần dùng

- Nature trước, nurture sau (slide S21–24): nhịp nhu cầu tự nhiên quyết định mọi thiết kế phía sau.
- Không thể chọn metric trước khi hiểu action xảy ra theo cơ chế nào trong đời thật của user.

## 1. Điền Action Nature Card (10')

Làm — copy bảng và điền:

| Thành phần | Câu hỏi |
|---|---|
| Actor | User, account, team hay object nào thực hiện? |
| Intent | Hành vi bắt đầu từ nhu cầu gì? |
| Trigger | Do user chủ động, sự kiện bên ngoài, người khác hay hệ thống kích hoạt? |
| Effort | Mất bao nhiêu thời gian, suy nghĩ, dữ liệu? |
| Value timing | Value xuất hiện ngay, trễ, tích lũy, hay phụ thuộc người khác? |
| State | Sau action, dữ liệu/trạng thái nào được giữ lại? |
| Dependency | Có phụ thuộc nguồn cung, thành viên khác, approval, thời điểm? |
| Repeat condition | Điều kiện nào khiến action có lý do xuất hiện lại? |

## 2. Kết luận cadence (5')

### Làm

1. Chọn một dạng hành vi: thói quen thường xuyên · tiến trình tích lũy · theo dự án · giao dịch · workflow của team · phản ứng theo sự kiện · theo chu kỳ.
2. Viết kết luận theo template:

Đối với __________, core action __________ thường xuất hiện __________ vì __________. Do đó, nhịp đo phù hợp là __________ ở cấp __________.

### Cân nhắc

Không chọn daily, weekly hay monthly chỉ vì dashboard thường dùng các khoảng này.

Hỏi thêm: frequency cao hơn có luôn nghĩa là value cao hơn không? Với sản phẩm AI, xong việc nhanh hơn có thể là tín hiệu tốt hơn dùng lâu hơn.

**Ghi lại ở đâu:** Action Nature Card + kết luận cadence → mục 02 — Nature & cadence của tệp bạn.

## Tự kiểm · GATE 2 — Cadence từ nature, không từ dashboard

Bạn qua gate khi: kết luận cadence theo đúng template, có lý do "vì" đứng được, và nhịp đo không mâu thuẫn với dạng hành vi đã chọn.

# 6. Phase 3 — Metric System + Retention · 25 phút

## Kiến thức cần dùng

- Active ≠ Activated (S26): active là có dùng trong window; activated là đã lặp đủ để xác suất ở lại cao hơn hẳn.
- Retention viết đầy đủ định nghĩa (S29–30, S34): thiếu một thành phần, hai người nhìn cùng dashboard ra hai kết luận.
- NSM = unit of value + quality threshold + frequency (S6–S9); có counter-metric vì metric nào cũng có thể bị game (S7).

## 1. Activation metric (5')

Làm — định nghĩa rõ ba thứ:

- Start event: khi nào user bắt đầu?
- Activation event: event nào xác nhận core action đầu tiên / first value?
- Time window: core action cần xảy ra trong bao lâu kể từ start event?

**Lỗi thường gặp** — dùng "hoàn thành tour giới thiệu" hay "đăng nhập" làm activation trong khi user chưa chạm core value.

## 2. Engagement metric (3')

Làm — chọn tối đa hai góc đo: frequency (core action xảy ra bao nhiêu lần trong cadence tự nhiên) · depth (mỗi lần action tạo bao nhiêu value) · breadth (bao nhiêu workflow/use case được dùng).

## 3. Retention Definition — đủ 6 thành phần (7')

Làm — copy bảng và điền:

| Thành phần | Câu hỏi |
|---|---|
| Unit | User, account, team, organization hay object? |
| Cohort entry | Event nào đưa unit vào cohort? |
| Return event | Core action / value event nào phải lặp lại? |
| Window | Daily, weekly, monthly, project-based hay custom bracket? |
| Threshold | Một lần hay nhiều lần trong window? |
| Segment | Retention đang áp dụng cho ai? |

### Nghĩ

Retention phải khớp kết luận cadence ở Phase 2 — action theo tháng mà đo D7 là sai. So retention với ba mốc: natural cycle, cohort đúng segment, benchmark category (S34) — không so với con số cứng.

## 4. North Star + leading + counter (10')

### Làm

1. North Star Metric theo công thức: unit of value + quality threshold + frequency. Phải phản ánh value user nhận được; không chỉ là revenue hay lượt mở app.
2. Leading indicators — tối đa ba, mỗi cái kèm một dòng "vì sao tin nó dự báo được core action lặp lại".
3. Counter-metric — ít nhất một: core action tăng nhưng cái gì không được xấu đi? (Với sản phẩm AI, gợi ý: chất lượng câu trả lời, chi phí mỗi lượt dùng, tỉ lệ kết quả bị bỏ qua.)

## Lỗi thường gặp

Viết "D7 retention" một mình — thiếu cohort, return event, window.

NSM là "số lượt hỏi AI" — số lượng thuần không có quality threshold, rất dễ bị game.

**Ghi lại ở đâu:** toàn bộ → mục 03 — Metric System và 04 — Retention Definition của tệp bạn.

## Tự kiểm · GATE 3 — Metric tính được, retention đủ nghĩa

Bạn qua gate khi: activation có start/activation event + time window; retention đủ 6 thành phần và khớp cadence; NSM đúng công thức 3 thành phần; có ít nhất 1 counter-metric.

# 7. Phase 4 — Ghi nhanh: Loop + Tracking · 15 phút

## Kiến thức cần dùng

- Loop suy ra từ metric — không bắt đầu bằng streak, badge, notification (S36–43, case Duolingo S46).
- Event đại diện điều đã xảy ra — không phải ý định của user; mỗi event map về một metric (S47).

## 1. Product Loop (khoảng 8')

### Làm

1. Vẽ nhanh loop tối thiểu hai chu kỳ:

Natural trigger → Core action → Immediate value → Saved state / investment → Next natural trigger → Core action tiếp theo → Repeat value

2. Chọn một loại loop chính: habit · progress · project · workflow · transaction · event-response · account-level.
3. Viết metric hypothesis (bắt buộc, một câu):

Nếu loop này hoạt động, metric __________ sẽ thay đổi theo hướng __________ trong __________ (khung thời gian), vì __________.

### Nghĩ

Reason to return là gì nếu bỏ notification đi? Không trả lời được thì loop đang dựa vào external trigger, chưa phải loop.

## 2. Tracking nhanh (khoảng 7')

### Làm

1. Liệt kê 4–8 core events, mỗi event ghi 4 trường:

| Trường | Nội dung |
|---|---|
| Tên event | Dạng object_action , ví dụ task_completed |
| Ý nghĩa | Hành vi / value nào được đại diện — điều đã xảy ra, không phải ý định |
| Thời điểm ghi nhận | Chính xác khi nào event được gửi? |
| Metric sử dụng | Event dùng để tính metric nào ở Phase 3? |

2. Viết ít nhất 2 tiêu chí nghiệm thu, ưu tiên hai bẫy phổ biến nhất:

- Event chỉ xuất hiện khi hành vi thật sự hoàn tất (không bắn khi mới bấm nút).
- Reload / retry / autosave không ghi trùng cùng một hành vi.

Ví dụ một tiêu chí viết đúng:

Với mỗi cặp user_id và task_id, hệ thống chỉ ghi task_completed khi nhiệm vụ chuyển từ chưa hoàn thành sang hoàn thành. Tải lại trang không được tạo thêm event cho cùng lần chuyển trạng thái.

### Cân nhắc

Làm bản đầy đủ ngoài giờ (không bắt buộc): bổ sung identity, object, properties bắt buộc, điều kiện loại trừ (bot, tài khoản nội bộ), timezone — đúng 7 điều của Metric Definition Contract (S47).

## Lỗi thường gặp

Track mọi click — event không map về metric nào.

Event bắn khi user bắt đầu hành vi thay vì khi hoàn tất.

**Ghi lại ở đâu:** loop + hypothesis → mục 05 — Product Loop ; bảng event + acceptance criteria → mục 06 — Tracking nhanh của tệp bạn.

## Tự kiểm · GATE 4 — Loop nối metric, event nối loop

Bạn qua gate khi: loop ≥ 2 chu kỳ và có metric hypothesis trỏ về một metric ở Phase 3; mọi event trong bảng đều map được về ít nhất một metric.

# 8. Phase 5 — Tự soi lỗi & nộp · 10 phút

Làm — đối chiếu nhanh từng dòng, sửa ngay chỗ mắc:

- Core action không phải thao tác giao diện hay output hệ thống?
- Activation không phải "xem hết hướng dẫn" hay "đăng nhập"?
- Frequency không cao hơn nhu cầu thật?
- Loop có reason to return ngoài notification?
- Retention không dùng chung một window cho mọi cadence?
- Mọi event đều map về một metric?
- Metric nào cũng có event để tính nó?

**Ghi lại ở đâu:** nếu phải sửa gì lớn (đổi core action, đổi cadence), ghi một dòng lý do vào cuối tệp — phần revision này được tính điểm rationale.

## Tự kiểm · GATE 5 — Bài sạch lỗi kinh điển

Bạn qua gate khi đối chiếu xong 7 câu tự soi và sửa mọi chỗ mắc — hoặc ghi rõ vì sao giữ nguyên một lựa chọn "phá rule".

# 9. Quy tắc dùng AI

## Được dùng AI để:

- Brainstorm ứng viên core action và câu hỏi phản biện để tự tranh luận với chính mình.
- Gợi ý tên event dạng object_action và acceptance criteria mẫu.
- Đóng vai "khách hàng khó tính" để test lại core job và cadence.

## Không được dùng AI để:

- Chọn thay core action, viết thay kết luận cadence hay metric hypothesis.
- Bịa benchmark hay số liệu retention "tham khảo" không có nguồn.
- Viết thay phần rationale và reflection.

## AI Support Log — viết ngắn

**AI đã giúp tôi ở đâu?**

........................................................................................................................

**AI sai, hời hợt hoặc đề xuất metric sai nature ở đâu?**

........................................................................................................................

**Tôi đã tự sửa hoặc quyết định lại điều gì?**

........................................................................................................................

# 10. Nộp bài

Mỗi học viên nộp một repository cá nhân:

`Track1_Day23_MHV_HoVaTen`

```text
Track1_Day23_MHV_HoVaTen/
├── README.md          # họ tên, MHV · dự án chọn làm · LINK tệp Metrics Pack
│                      # · điều tôi mang về áp dụng cho dự án thật
└── ai-support-log.md
```

Tệp Metrics Pack (link trong README) có cấu trúc:

```text
00 — Dự án, persona, core job
01 — Core Action Card (+ kết quả tự kiểm 5 tiêu chí)
02 — Action Nature Card + kết luận cadence
03 — Metric System (activation / engagement / NSM / leading / counter)
04 — Retention Definition (6 thành phần)
05 — Product Loop (2 chu kỳ + metric hypothesis)
06 — Tracking nhanh (4–8 events + 2 acceptance criteria)
07 — Revision (nếu có thay đổi lớn: lý do đổi core action / cadence)
```

## Năm gate đánh giá

| Gate | Đạt khi | Dấu hiệu chưa đạt |
|---|---|---|
| 1. Core Action | Có actor/object/completion rule, qua ≥4/5 tiêu chí tự kiểm | "Mở app", "hỏi AI", "engage" |
| 2. Cadence | Kết luận theo template, nhịp từ nature | Daily/weekly "cho quen", không có "vì" |
| 3. Metric & Retention | Retention đủ 6 thành phần, NSM đúng công thức, có counter-metric | "D7 retention" trơ trọi; NSM chỉ là số lượng |
| 4. Loop | ≥2 chu kỳ, hypothesis nối metric | Streak/badge không lý do; notification làm reason to return |
| 5. Tracking | 4–8 event map metric, ≥2 acceptance criteria | Track mọi click; event bắn khi chưa hoàn tất |

## Kiểm tra trước khi nộp

- Repo đúng tên Track1_Day23_MHV_HoVaTen ; README có link tệp Metrics Pack đã cấp quyền xem.
- Tệp đủ 7 mục (00–06), thêm mục 07 — Revision nếu có thay đổi lớn; mục nào cũng dùng lại kết quả mục trước (core action → cadence → metric → loop → event).
- Core Action Card có kết quả tự kiểm 5 tiêu chí.
- Retention đủ 6 thành phần và khớp kết luận cadence.
- Loop có metric hypothesis trỏ về metric ở Phase 3.
- Bảng tracking: mọi event map về một metric; ≥2 acceptance criteria viết rõ như ví dụ mẫu.
- Phần revision (nếu có) ghi lý do thay đổi.
- AI Support Log là của chính người nộp.

## Tự kiểm · HOÀN TẤT — Một chuỗi quyết định có logic

Bài hoàn tất khi bạn có một Metrics Pack xuyên suốt: core action đứng vững → cadence từ nature → bộ metric và retention tính được → loop là giả thuyết có metric hypothesis → tracking đủ để kiểm chứng; và bạn bảo vệ được từng quyết định lõi của mình.

## Góp ý cho buổi Lab

Không bắt buộc và không ảnh hưởng việc nộp bài. Giảng viên chỉ xem phản hồi ẩn danh.

### Góp ý bài Lab

### Nộp bài và đánh giá Lab

Dán link GitHub, Drive hoặc LMS của bài đã nộp. Điểm và nhận xét sẽ không hiển thị tại đây.

Đang tải trạng thái bài nộp…
