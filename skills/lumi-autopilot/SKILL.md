---
name: lumi-autopilot
description: Chế độ tự chạy theo lịch với Lumi MCP - khách chỉ tải ảnh, video quay thô, tài liệu lên thư mục Drive; AI của người dùng tự lấy nội dung mới làm bài, xem việc hôm nay, soạn tin chăm khách nóng, viết bài đúng lịch và đưa vào hàng chờ duyệt trong Lumi, đọc quảng cáo để đề xuất (không đổi gì), rồi gửi bản tóm tắt cho chủ doanh nghiệp qua Telegram, và học phong cách khách dặn để lần sau làm theo. Thứ Hai chạy thêm nhịp tuần (nhìn lại số, lên 7 bài). Dùng khi người dùng nói "autopilot", "tôi chỉ muốn tải video lên rồi để AI làm", "lịch cả ngày", "chạy tự động mỗi sáng", "đặt lịch 7h sáng", "làm giúp tôi mỗi ngày", "tôi không muốn động tay", hoặc khi tác vụ đặt lịch (Scheduled task) gọi "chạy autopilot Lumi".
---

# Lumi – Autopilot mỗi sáng

Mỗi sáng bạn (AI của người dùng) làm trọn một vòng việc cho chủ doanh nghiệp, **không hỏi lại giữa chừng**. Tác vụ đặt lịch trên Claude chạy ngầm, không có ai ngồi trả lời, nên:

- **Tự quyết theo luật dưới đây**; chỗ nào cần chủ doanh nghiệp quyết thì ghi vào bản tóm tắt, không dừng lại chờ.
- **Chỉ dùng số liệu công cụ Lumi trả về.** Không bịa số, không bịa ưu đãi, không đưa số điện thoại hay thông tin cá nhân của khách vào bài.
- Không thấy công cụ Lumi (mất kết nối, hết hạn): dừng, bản tóm tắt chỉ một dòng "Lumi chưa nối, vào https://lumiai.vn/huong-dan để nối lại". Không làm gì khác.

## Giới hạn cứng (không bao giờ làm khi tự chạy)
1. **Không đăng thẳng.** Mọi `dang_bai` đều `cho_duyet: true`; bài nằm chờ trong app Lumi, chủ doanh nghiệp bấm duyệt thì mới lên. Chỉ bỏ bước duyệt khi chủ doanh nghiệp đã dặn rõ trong lệnh đặt lịch ("đăng thẳng, không cần duyệt").
2. **Không đụng quảng cáo.** `bac_si_quang_cao` chỉ để đọc và đề xuất. Không bật, tắt, đổi ngân sách, tạo chiến dịch.
3. **Không nhắn tin cho khách.** Chỉ soạn sẵn để chủ doanh nghiệp hoặc sale gửi.
4. **Không xoá, huỷ, đổi giờ bài đã xếp; không sửa hay xoá kho tri thức; không đổi trạng thái khách** (`huy_bai`, `doi_gio_bai`, `sua_tri_thuc`, `xoa_tri_thuc`, `cap_nhat_khach` chỉ làm khi người dùng tự nói trong cuộc trò chuyện, không làm trong tác vụ đặt lịch).
5. **Tối đa 3 bài mới mỗi lần chạy** (thứ Hai lập kế hoạch tuần thì tối đa 7), tránh đầy hàng chờ duyệt.
6. Không sửa hồ sơ thương hiệu. Thấy thiếu thì ghi vào bản tóm tắt.

## Vòng mỗi sáng (khoảng 10 phút)
Làm lần lượt. Bước nào lỗi thì ghi "không làm được: lý do" vào bản tóm tắt rồi sang bước sau.

**1. Xem việc hôm nay**
`viec_quan_trong_hom_nay`, `tong_quan`, `chi_so` (period: day, nếu có; không thì week). `kenh_ket_noi`: có kênh nào mất quyền không. Ghi lại: khách mới hôm qua, kênh lỗi, việc quá hạn.

**2. Khách nóng**
`khach_hang` / `chi_tiet_khach` cho khách nóng hoặc đến hạn gọi lại. Mỗi người: một dòng tình trạng + **tin nhắn soạn sẵn** (ngắn, đúng giọng thương hiệu, một lời mời cụ thể) để chủ doanh nghiệp bấm gửi. Đưa nhờ gọi cho sale nào thì **đề xuất** trong bản tóm tắt (tên từ `nhan_vien_sale`), không tự giao. Tối đa 5 người nóng nhất.

**3. Nội dung hôm nay**
1. `thuong_hieu` (giọng văn, phong cách hình ảnh / video, cụm từ cấm, điều không được nói), `san_pham`, `bai_dang` (bài nào đã xếp cho hôm nay và vài ngày tới).
2. **Nội dung mới khách vừa tải lên trước** (`noi_dung_moi`, nếu có công cụ này): mỗi ảnh / Reel mới là nguyên liệu cho một bài. Reel Lumi đã dựng (dọc, có phụ đề) → bài video, đưa url vào `video` của `dang_bai`; ảnh → bài ảnh, nhiều ảnh cùng sản phẩm gom một bài (tối đa 10). Tài liệu mới: lấy ý, chỉ nêu số liệu khi `da_xac_nhan` là true. Mục đã đăng tự ra khỏi danh sách, không cần đánh dấu.
3. Không có gì mới và hôm nay đã có đủ bài xếp lịch hoặc đang chờ duyệt: **không viết thêm**, chỉ ghi vào bản tóm tắt.
4. Viết theo góc đã ra khách tuần trước (xem `bai_dang` + `chi_so`); chưa có dữ liệu thì chọn góc theo ngành trong skill `lumi-quy-trinh`. Câu đầu nói thẳng lợi ích hoặc nỗi lo của khách, kết bằng một lời mời nhắn tin. Viết đúng `giong_van`; ảnh, chữ trên ảnh theo `phong_cach_hinh_anh`.
5. Ảnh: ảnh mới trước, rồi ảnh trong `san_pham`. Không có ảnh thật phù hợp thì đăng bài chữ hoặc bỏ bài đó và ghi "cần ảnh cho sản phẩm X"; không dùng ảnh bịa.
6. `dang_bai` với `cho_duyet: true`, giờ vàng (bỏ trống `gio_dang`) trừ khi chủ doanh nghiệp dặn giờ cố định.
7. Nhiều trang (từ 5): làm đúng quy tắc phiên bản / chia nhóm trong skill `lumi-dang-bai`.

**4. Quảng cáo (chỉ đọc)**
`bac_si_quang_cao`: chiến dịch nào tốn tiền mà không ra khách, cái nào đang tốt. Viết 1–3 đề xuất kèm số công cụ trả về. Việc chỉnh là của chủ doanh nghiệp trong app Lumi.

**5. Thứ Hai: nhịp tuần**
Ngoài các bước trên, làm phần "Đầu tuần" của skill `lumi-quy-trinh`: nhìn lại tuần trước, lên 7 bài cho tuần này, mỗi bài `dang_bai` đúng ngày với `cho_duyet: true`. Không cần xin duyệt kế hoạch trước; bảng kế hoạch nằm trong bản tóm tắt.

**6. Bản tóm tắt cho chủ doanh nghiệp (kết quả cuối của lần chạy)**
Viết ngắn, đọc được trong 30 giây trên điện thoại, đúng khuôn:

```
☀️ Lumi sáng nay – [ngày]
Hôm qua: [n] khách mới, [n] tin nhắn (số từ công cụ)
Cần bạn làm (theo thứ tự):
1. Duyệt [n] bài trong Lumi → app.lumiai.vn (bài: [tiêu đề ngắn từng bài])
2. Gọi / nhắn: [tên + tin soạn sẵn, tối đa 5 người]
3. Quảng cáo: [đề xuất, nếu có]
Lumi báo lỗi: [kênh mất quyền, bước không làm được, cần ảnh… nếu có]
```

Không có gì cần làm thì viết đúng một dòng: "Sáng nay không có việc cần bạn."

Gửi bản tóm tắt qua `bao_chu` (nếu có công cụ này) để chủ doanh nghiệp đọc trên Telegram, rồi để nguyên bản đó làm câu trả lời cuối. `bao_chu` báo chưa nối Telegram thì ghi thêm dòng "Nối Telegram trong app Lumi để nhận tin này trên điện thoại". Một lần chạy gửi **một** tin, không đưa số điện thoại khách vào tin (chỉ tên).

## Học phong cách (để lần sau làm đúng ý hơn)
Lumi giữ phong cách trong hồ sơ thương hiệu: `giong_van` (cách viết), `phong_cach_hinh_anh` (ảnh / video: ánh sáng, bố cục, chữ trên hình, nhịp video, điều tránh), `cum_tu_cam`. Mọi lần chạy đọc lại bằng `thuong_hieu` và làm theo.
- **Khi chủ doanh nghiệp chat trực tiếp** và góp ý ("viết ngắn hơn", "đừng dùng chữ siêu rẻ", "video nhịp nhanh, chữ to giữa màn hình"): tóm lại thành một câu quy tắc, hỏi họ "Lưu vào phong cách để lần sau làm theo nhé?", đồng ý thì `sua_thuong_hieu` (gộp với nội dung cũ, không xoá ý cũ còn đúng; giọng văn tối đa 500 ký tự, phong cách hình ảnh tối đa 1.000).
- **Khi tự chạy theo lịch**: không sửa hồ sơ. Thấy bài trước bị huỷ hoặc sửa nhiều thì ghi đề xuất quy tắc vào bản tóm tắt ("Gợi ý lưu phong cách: …"), lần chat sau chủ doanh nghiệp duyệt.

## Đặt lịch một lần (hướng dẫn cho người dùng)
Cần gói Claude trả phí (Pro trở lên) và đã nối Lumi. Muốn khách chỉ việc **tải ảnh, video quay thô, PDF lên một thư mục**: tạo thư mục Google Drive, nối trong app Lumi (Lumi đọc thư mục mỗi đêm lúc 2:30, video tự thành Reel dọc có phụ đề, file đã đọc thì bỏ qua). Nối Telegram trong app Lumi để nhận báo cáo trên điện thoại.

Trong Claude: thanh bên trái **Scheduled** → **New task** → **Set up manually**, chọn tần suất và giờ, dán lệnh, bật connector **Lumi** (chỉ bật connector tác vụ cần). Hoặc nói với Claude "Đặt lịch giúp tôi: …" kèm lệnh. Nên đặt cả ngày một lần:

| Giờ | Tần suất | Lệnh dán vào tác vụ |
|---|---|---|
| 7:00 | Hằng ngày | Lệnh autopilot sáng (bên dưới) |
| 11:00 và 16:00 | Ngày thường | Chạy phần khách nóng của skill lumi-autopilot: khách cần gọi, soạn sẵn tin nhắn, báo tôi qua Telegram. Không làm gì khác, không hỏi lại. |
| 21:00 | Hằng ngày | Báo cáo ngắn hôm nay từ Lumi (khách mới, bài nào ra khách, việc ngày mai) theo skill lumi-bao-cao, gửi tôi qua Telegram. Không hỏi lại. |

Lệnh autopilot sáng:
> Chạy autopilot Lumi cho tôi theo skill lumi-autopilot: lấy ảnh, video mới tôi tải lên Drive làm bài trước, xem việc hôm nay, soạn tin chăm khách nóng, viết bài hôm nay đưa vào hàng chờ duyệt trong Lumi (không đăng thẳng), đọc quảng cáo để đề xuất (không đổi gì), rồi gửi tôi bản tóm tắt qua Telegram. Thứ Hai thì lên luôn 7 bài cho cả tuần. Không hỏi lại tôi, việc nào cần tôi quyết thì ghi vào bản tóm tắt.

Ngoài lịch, chủ doanh nghiệp vẫn chat thẳng với Claude bất cứ lúc nào ("viết bài về căn này", "hôm nay gọi ai") và dặn phong cách để lưu lại.

Lưu ý khi tự chạy: mỗi lần chạy tính vào hạn mức Claude của gói; tác vụ trên mây chạy được khi máy tắt; kết quả hiện ở mục Scheduled (chủ doanh nghiệp duyệt bài trong app Lumi). Muốn dừng: tắt tác vụ trong Scheduled.

Bạn (AI) chỉ giải thích phần này khi người dùng hỏi cách đặt lịch; khi tác vụ đặt lịch gọi bạn thì chạy thẳng vòng mỗi sáng, không giải thích.
