---
name: lumi-bao-cao
description: Báo cáo hiệu suất kênh, khách hàng và quảng cáo từ Lumi MCP, so với kỳ trước, kèm đề xuất việc nên làm. Dùng khi người dùng hỏi "tuần này thế nào", "báo cáo tuần/tháng", "kênh nào hiệu quả", "quảng cáo có lời không", "nên làm gì tiếp", "đề xuất chiến lược".
---

# Lumi – báo cáo và đề xuất

Số liệu lấy từ Lumi qua các công cụ MCP. Không bịa, không ước đoán số; thiếu dữ liệu thì nói rõ thiếu gì.

## 1. Lấy số
- `tong_quan`: khách mới, bài đăng, chi tiêu quảng cáo.
- `chi_so` với `period` = `week` (hoặc `month` nếu người dùng hỏi tháng): kỳ này so với kỳ trước.
- `bai_dang`: bài đã đăng và tương tác; tìm bài mang về tin nhắn / khách.
- `bac_si_quang_cao`: chiến dịch tốn tiền mà ít khách, cảnh báo đang mở.
- `khach_hang`: khách mới, khách nóng.
- `bao_cao_ceo`: nhận định AI hằng tuần Lumi đã lập (nếu có).

## 2. Viết báo cáo (ngắn, đọc trên điện thoại)
1. Một câu kết luận: tuần này tốt hơn hay kém hơn tuần trước, vì sao.
2. Khách: số khách mới, số để lại số điện thoại, nguồn nào nhiều nhất.
3. Kênh: kênh nào ra khách, bài nào tốt nhất (tên bài, số khách).
4. Quảng cáo: chi bao nhiêu, mỗi khách tốn bao nhiêu, chiến dịch nào nên dừng hoặc tăng.
5. **3 việc nên làm tuần tới**, cụ thể (ví dụ: "đăng thêm 2 video kiểu bài X vào 19h", "gọi lại 4 khách nóng chưa liên hệ").

## Lưu ý
- Số điện thoại khách chỉ hiện 3 số cuối; không cố tìm số đầy đủ.
- Đổi ngân sách, bật/tắt quảng cáo chỉ làm trong app Lumi; chỉ đề xuất, không tự làm.
- Muốn đăng bài theo đề xuất: dùng skill `lumi-dang-bai`.
