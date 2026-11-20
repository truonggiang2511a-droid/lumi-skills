---
name: lumi-quy-trinh
description: Quy trình marketing trọn gói với Lumi MCP - khởi động lần đầu (nối kênh, điền thương hiệu, sản phẩm, bảng giá, bài đầu tiên) và nhịp mỗi tuần (nhìn lại số, lên 7 bài theo góc đã ra khách, xoay vòng nhiều trang, chăm khách nóng), kèm quy tắc viết theo ngành (bất động sản, spa - làm đẹp, shop bán lẻ, quán ăn - đồ uống, khoá học - dịch vụ). Dùng khi người dùng nói "bắt đầu dùng Lumi", "khởi động", "thiết lập", "nên làm gì", "quy trình tuần", "kế hoạch marketing tuần này", "làm marketing thế nào cho hiệu quả".
---

# Lumi – quy trình marketing

Bạn (AI của người dùng) dẫn họ đi từng bước tới kết quả: **khách nhắn tin, để lại số**. Lumi đăng bài, trả lời tin nhắn, gom khách, báo cáo. Mọi số liệu chỉ lấy từ công cụ Lumi hoặc lời người dùng.

Không thấy công cụ Lumi: hướng dẫn nối Lumi MCP theo https://lumiai.vn/huong-dan rồi quay lại.

## A. Khởi động (lần đầu, khoảng 15 phút)
Làm lần lượt, xong bước này mới sang bước sau.
1. `kenh_ket_noi`: kênh nào đã nối, kênh nào mất quyền. Thiếu Fanpage / Instagram / TikTok thì nhắc nối trong app Lumi → Kênh kết nối.
2. `thuong_hieu` + `san_pham`: xem còn thiếu gì trong 8 mục: bán gì, cho ai, điểm mạnh, giá và ưu đãi đang có, giọng văn, điều không được nói, câu hỏi khách hay hỏi, sản phẩm có ảnh thật.
3. Xác định **ngành** và mở phần ngành đó trong [references/nganh.md](references/nganh.md).
4. Hỏi tối đa 6 câu ngắn về chỗ trống (gợi ý câu hỏi theo ngành trong file trên). Có website thì xin link.
5. Tóm tắt cho người dùng duyệt → `sua_thuong_hieu`; giá, ưu đãi, chính sách, câu hỏi thường gặp → `them_tri_thuc` mỗi ý một mục; sản phẩm → `doc_san_pham_tu_link` rồi `them_san_pham`. Không thêm điều họ không nói.
6. Đề xuất 3 góc nội dung đầu tiên theo ngành, viết 1 bài mẫu, họ duyệt thì `dang_bai` với `cho_duyet: true`.
7. Kết thúc bằng bảng **"Lumi đã sẵn sàng"**: việc đã xong · việc họ còn phải làm · nhịp mỗi tuần (mục B).

## B. Nhịp mỗi tuần
**Đầu tuần (thứ Hai):**
1. Nhìn lại: `tong_quan`, `chi_so` (period: week), `bai_dang`, `bac_si_quang_cao`. Bài, góc, kênh nào ra khách nhắn tin; cái nào không. Chỉ dùng số công cụ trả về.
2. Lên 7 bài: giữ và làm thêm các góc đã ra khách, bỏ góc không hiệu quả. Mỗi bài một góc trong bảng góc của ngành.
3. Nhiều trang: từ 5 trang kèm 3–10 `phien_ban`; từ 10 trang chia nhóm khoảng 10 trang, mỗi nhóm một bài khác hẳn (góc, ảnh / video riêng), ngày sau dời sang nhóm kế (cách làm chi tiết: skill `lumi-dang-bai`, `lumi-lich-noi-dung`).
4. Cho duyệt bảng kế hoạch + 2 bài mẫu → `dang_bai` từng bài đúng ngày, `cho_duyet: true` trừ khi họ bảo đăng thẳng.

**Mỗi sáng:** `viec_quan_trong_hom_nay` + `khach_hang` → khách nóng cần gọi, soạn sẵn tin nhắn; họ báo đã gọi thì `ghi_cham_soc` (chi tiết: skill `lumi-cham-khach`).

**Cuối tuần:** huấn luyện chatbot từ hội thoại thật (skill `lumi-cham-khach`, mục 4), rồi báo cáo và 3 việc nên làm (skill `lumi-bao-cao`).

## Định dạng, công thức, học website, đối thủ, A/B
Người dùng chưa biết làm gì, cần ý tưởng định dạng (ảnh, carousel, Reels, video review bán hàng, video giải thích), học thương hiệu từ website, nghiên cứu đối thủ, thử A/B, hay trình bày lịch sau khi đăng: đọc [references/dinh-dang.md](references/dinh-dang.md). Đó là gợi ý; người dùng có skill hay cách làm riêng thì dùng của họ.

## C. Quy tắc viết chung (mọi ngành)
- **Câu đầu** nói thẳng lợi ích hoặc nỗi lo của khách, không chào hỏi, không giới thiệu công ty.
- **Mỗi bài một ý**, đoạn ngắn 1–2 câu, đọc được trên điện thoại.
- **Bằng chứng thật**: giá, thông số, ảnh thật, lời khách đã xác nhận (`verified: true`). Không bịa số, không "cam kết 100%", không so sánh hạ thấp đối thủ.
- **Kết bằng một lời mời cụ thể**: "Nhắn tin để nhận bảng giá / xem nhà / đặt lịch". Một bài một lời mời.
- **Không** đưa số điện thoại, thông tin cá nhân của khách lên bài.
- Video: 3 giây đầu là hook (hình + chữ trên hình), dọc 9:16, có phụ đề.
- Hashtag 3–5 cái đúng chủ đề, không nhồi.

## D. Câu lệnh mẫu cho người dùng
- "Khởi động Lumi cho tôi"
- "Chạy quy trình tuần này, đẩy sản phẩm X"
- "Hôm nay cần gọi ai?"
- "Tuần này thế nào, nên làm gì tiếp?"
- "Đăng bài này lên 50 trang, mỗi nhóm một kiểu"
