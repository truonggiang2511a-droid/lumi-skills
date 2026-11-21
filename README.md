# Lumi Skills

20 skill marketing tiếng Việt cho Claude và các AI khác, viết cho chủ shop và doanh nghiệp nhỏ. Miễn phí, giấy phép MIT. Nối với [Lumi](https://lumiai.vn) để AI đăng bài lên mọi kênh, trả lời tin nhắn, gom khách và báo cáo bằng số thật.

| Skill | Dùng khi |
|---|---|
| [lumi](skills/lumi/SKILL.md) | Cài một lần: tự mở đúng skill bên dưới |
| [lumi-quy-trinh](skills/lumi-quy-trinh/SKILL.md) | Khởi động, nhịp làm mỗi tuần |
| [lumi-autopilot](skills/lumi-autopilot/SKILL.md) | Tự viết bài mỗi sáng từ ảnh/video trên Drive |
| [lumi-dang-bai](skills/lumi-dang-bai/SKILL.md) · [lumi-lich-noi-dung](skills/lumi-lich-noi-dung/SKILL.md) | Đăng bài, lịch 7–30 bài |
| [lumi-fanpage](skills/lumi-fanpage/SKILL.md) · [lumi-tiktok](skills/lumi-tiktok/SKILL.md) · [lumi-youtube-shorts](skills/lumi-youtube-shorts/SKILL.md) · [lumi-instagram](skills/lumi-instagram/SKILL.md) | Nội dung từng nền tảng |
| [lumi-1-thanh-nhieu](skills/lumi-1-thanh-nhieu/SKILL.md) · [lumi-hook-kich-ban](skills/lumi-hook-kich-ban/SKILL.md) | Một nội dung cho mọi kênh, hook, kịch bản |
| [lumi-anh-bia](skills/lumi-anh-bia/SKILL.md) · [lumi-thiet-ke](skills/lumi-thiet-ke/SKILL.md) | Ảnh bìa, banner không "nhìn là biết AI" |
| [lumi-giong-thuong-hieu](skills/lumi-giong-thuong-hieu/SKILL.md) · [lumi-soi-doi-thu](skills/lumi-soi-doi-thu/SKILL.md) | Học giọng văn, soi đối thủ (cả video đối thủ hút xem) |
| [lumi-quang-cao](skills/lumi-quang-cao/SKILL.md) · [lumi-chien-dich](skills/lumi-chien-dich/SKILL.md) · [lumi-uu-dai](skills/lumi-uu-dai/SKILL.md) | Chữ quảng cáo, chiến dịch, ưu đãi |
| [lumi-cham-khach](skills/lumi-cham-khach/SKILL.md) · [lumi-bao-cao](skills/lumi-bao-cao/SKILL.md) | Khách cần gọi hôm nay, báo cáo tuần |

Mỗi thư mục có `VI-DU.md`: ví dụ câu nhờ và kết quả mẫu.

## Cài đặt

- **Claude:** tải `lumi.zip` ở [lumiai.vn/huong-dan](https://lumiai.vn/huong-dan) (hoặc nén một thư mục trong `skills/`), rồi vào **Plugin** (Customize) → **Skills** → **Tải lên**.
- **Claude Code:** chép các thư mục trong `skills/` vào `~/.claude/skills/`, để chúng nằm cạnh nhau.
- **ChatGPT, Gemini:** dán nội dung `SKILL.md` vào phần hướng dẫn của GPT, Project hoặc Gem.

Skill lấy thông tin thật (thương hiệu, sản phẩm, số liệu) từ Lumi qua MCP. Đã kết nối thêm vidIQ, Canva, Meta Ads, Adobe… thì AI tự dùng để soi video đối thủ và làm ảnh; không có vẫn làm được bằng cách thủ công ([danh sách công cụ](skills/lumi-quy-trinh/references/cong-cu.md)). Tạo tài khoản ở [lumiai.vn](https://lumiai.vn), nối theo [hướng dẫn](https://lumiai.vn/huong-dan), rồi nhờ AI: *"Lumi ơi, mình mới dùng, nên bắt đầu từ đâu?"* AI luôn hỏi bạn duyệt trước khi đăng bài, gửi tin hay chi tiền.

Góp ý hoặc sửa skill: mở Issue hoặc Pull Request.

## Ghi công

Một số skill phát triển từ [sergebulaev](https://github.com/sergebulaev), [marcosmodly/marketing-skill](https://github.com/marcosmodly/marketing-skill), [Jakeschincariol/youtube-agent-skill](https://github.com/Jakeschincariol/youtube-agent-skill), [charlie947/social-media-skills](https://github.com/charlie947/social-media-skills), [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) (MIT) và [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins) (Apache-2.0). Giấy phép gốc nằm ở `LICENSE-goc.txt` trong từng thư mục, mục "Nguồn" cuối mỗi `SKILL.md` ghi rõ đã sửa gì. Phần còn lại: [MIT](LICENSE).
