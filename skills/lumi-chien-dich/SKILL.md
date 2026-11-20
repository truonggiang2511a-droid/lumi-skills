---
name: lumi-chien-dich
description: Lên kế hoạch một chiến dịch marketing 2–6 tuần cho doanh nghiệp nhỏ (mở bán sản phẩm mới, ưu đãi theo mùa, đẩy một dịch vụ) - mục tiêu đo được, khách nhắm tới, thông điệp, kênh, lịch nội dung, việc cần làm, đề xuất ngân sách - rồi xếp lịch bài qua Lumi và theo dõi kết quả mỗi tuần bằng số Lumi để chỉnh. Dùng khi người dùng nói "lên chiến dịch", "kế hoạch marketing tháng này", "mở bán căn mới thì làm gì", "chạy chương trình khuyến mãi", "chiến dịch tuần này hiệu quả không".
---

# Lumi – chiến dịch

Một chiến dịch = **một mục tiêu, một nhóm khách, một thông điệp chính**, chạy trong thời gian có hạn, đo bằng số trên Lumi.
Ngân sách quảng cáo chỉ là **đề xuất**: chủ doanh nghiệp tự đặt trần và duyệt chi trong app Lumi / trình quản lý quảng cáo.

Không thấy công cụ của Lumi: hướng dẫn nối Lumi MCP theo https://lumiai.vn/huong-dan.

## 1. Đầu vào
- Hỏi: chiến dịch cho **sản phẩm / ưu đãi nào**, **bao lâu** (2–6 tuần), **mục tiêu** (bao nhiêu khách nhắn / để lại số / chốt), **ngân sách quảng cáo** dự kiến (có thể 0).
- Lumi: `thuong_hieu` (khách mục tiêu, điểm mạnh, ưu đãi, giọng văn), `san_pham`, `kenh_ket_noi`, `chi_so` + `bao_cao_ceo` (kỳ trước làm được bao nhiêu khách, chi phí mỗi khách — làm mốc), `bai_dang` (góc nào đã ra khách).
- Không có số kỳ trước thì nói rõ mục tiêu là ước đoán; không bịa mốc.

## 2. Bản kế hoạch (gọn, một trang)
1. **Tổng quan**: tên chiến dịch · thời gian · **một mục tiêu đo được** (ví dụ "40 khách để lại số trong 4 tuần") · vì sao bây giờ (lý do thật).
2. **Khách nhắm tới**: một nhóm chính từ `thuong_hieu` — nỗi lo, mong muốn, e ngại khi mua.
3. **Thông điệp**: một câu chính + 3 ý chứng minh (thông tin thật) + lời mời nhắn tin chung cho cả chiến dịch.
4. **Kênh**: kênh đã nối trên Lumi, mỗi kênh một vai (ví dụ: fanpage = thông tin + bằng chứng; TikTok / Reels = video thu hút; quảng cáo = đẩy khách nhắn tin; chatbot Lumi = trả lời ngay và xin số).
5. **Lịch nội dung**: theo tuần — tuần 1 giới thiệu / gây chú ý, giữa = bằng chứng / trả lời băn khoăn, cuối = ưu đãi / nhắc hạn (chỉ hạn thật). Mỗi bài: ngày · kênh · định dạng · góc.
6. **Việc cần chuẩn bị**: ảnh / video cần quay, bảng giá và câu hỏi thường gặp cần nạp vào kho tri thức (để chatbot trả lời đúng), sale nhận khách (CRM Lumi).
7. **Đo lường**: chỉ số trên Lumi — tin nhắn / khách mới, khách nóng, chi phí mỗi khách (nếu có quảng cáo), bài nào ra khách. Mốc kiểm tra mỗi tuần.
8. **Ngân sách đề xuất** (nếu có): chia theo kênh và tuần, giữ phần nhỏ để thử góc mới; ghi rõ "chủ doanh nghiệp đặt trần và duyệt trong app".
9. **Rủi ro**: ví dụ ít ảnh thật, sale phản hồi chậm, ưu đãi chưa rõ — mỗi rủi ro một cách xử lý.
10. **Việc tiếp theo**: 3 việc làm ngay.

## 3. Duyệt rồi xếp lịch
Người dùng duyệt kế hoạch → viết bài theo lịch (skill `lumi-fanpage`, `lumi-tiktok`, `lumi-instagram`, `lumi-youtube-shorts`, hoặc `lumi-1-thanh-nhieu` khi một nội dung cho nhiều kênh)
→ `dang_bai` từng bài đúng ngày, `cho_duyet: true` nếu họ muốn xem lại trong app. Thông tin mới (bảng giá, câu hỏi) → `them_tri_thuc` sau khi hỏi.
Chữ quảng cáo cho chiến dịch: skill `lumi-quang-cao`.

## 4. Theo dõi mỗi tuần
Dùng `chi_so` (period: week), `bai_dang`, `bac_si_quang_cao`, `khach_hang`:
- Mục tiêu đã đạt bao nhiêu % · kênh / bài / góc nào ra khách · chi phí mỗi khách so với tuần trước.
- **Giữ** góc ra khách, **thay** góc không hiệu quả (đổi góc, không chỉ đổi chữ), báo khách nóng cần gọi.
- Kết thúc bằng 3 việc chỉnh cho tuần tới. Chỉ dùng số Lumi trả về; tuần đầu ít số thì nói rõ chưa đủ để kết luận.
Báo cáo đầy đủ theo tuần / tháng: skill `lumi-bao-cao`.

## Nguồn
Phát triển từ campaign-plan và performance-report trong [knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins) của Anthropic
(giấy phép Apache 2.0, bản gốc ở `LICENSE-goc.txt`); đã viết lại cho doanh nghiệp nhỏ Việt Nam, công cụ và quy tắc chi tiền của Lumi.
