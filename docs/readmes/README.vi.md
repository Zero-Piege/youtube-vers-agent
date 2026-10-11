<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Biến video hướng dẫn trên YouTube thành skill và quy trình rõ ràng, đã kiểm chứng cho nhiều tác nhân AI.</strong></p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/badge/License-MIT-2ea44f?style=flat" alt="MIT License" /></a>
  <a href="https://github.com/Zero-Piege/youtube-vers-agent/stargazers"><img src="https://img.shields.io/github/stars/Zero-Piege/youtube-vers-agent?style=flat&logo=github" alt="GitHub stars" /></a>
  <a href="../../docs/platforms/README.md"><img src="https://img.shields.io/badge/Agent%20Skills-multi--platform-6f42c1?style=flat&logo=github" alt="Multi-platform support" /></a>
</p>

<p align="center">
  <a href="../../README.md">🇬🇧 English</a> · <a href="README.zh.md">🇨🇳 中文</a> · <a href="README.zh-TW.md">🇹🇼 繁體中文</a> · <a href="README.ja.md">🇯🇵 日本語</a> · <a href="README.pt.md">🇵🇹 Português</a> · <a href="README.pt-BR.md">🇧🇷 Português (Brasil)</a> · <a href="README.ko.md">🇰🇷 한국어</a><br />
  <a href="README.es.md">🇪🇸 Español</a> · <a href="README.de.md">🇩🇪 Deutsch</a> · <a href="README.fr.md">🇫🇷 Français</a> · <a href="README.he.md">🇮🇱 עברית</a> · <a href="README.ar.md">🇸🇦 العربية</a> · <a href="README.ru.md">🇷🇺 Русский</a> · <a href="README.pl.md">🇵🇱 Polski</a><br />
  <a href="README.cs.md">🇨🇿 Čeština</a> · <a href="README.nl.md">🇳🇱 Nederlands</a> · <a href="README.tr.md">🇹🇷 Türkçe</a> · <a href="README.uk.md">🇺🇦 Українська</a> · <a href="README.vi.md">🇻🇳 Tiếng Việt</a> · <a href="README.tl.md">🇵🇭 Tagalog</a> · <a href="README.id.md">🇮🇩 Bahasa Indonesia</a><br />
  <a href="README.th.md">🇹🇭 ไทย</a> · <a href="README.hi.md">🇮🇳 हिन्दी</a> · <a href="README.bn.md">🇧🇩 বাংলা</a> · <a href="README.ur.md">🇵🇰 اردو</a> · <a href="README.ro.md">🇷🇴 Română</a> · <a href="README.sv.md">🇸🇪 Svenska</a> · <a href="README.it.md">🇮🇹 Italiano</a><br />
  <a href="README.el.md">🇬🇷 Ελληνικά</a> · <a href="README.hu.md">🇭🇺 Magyar</a> · <a href="README.fi.md">🇫🇮 Suomi</a> · <a href="README.da.md">🇩🇰 Dansk</a> · <a href="README.no.md">🇳🇴 Norsk</a>
</p>

---

Kho lưu trữ này hỗ trợ nhiều nền tảng agent. Trang này mô tả quy trình Claude Code; định dạng dùng chung và cách thiết lập Codex, Gemini CLI, GitHub Copilot, ChatGPT cùng OpenAI API có trong [hướng dẫn nền tảng](../../docs/platforms/README.md).

Cung cấp liên kết YouTube và mục tiêu. Skill phân tích video độc lập bằng Claude và Gemini, tổng hợp kết quả trong notes/SPEC.md, sau đó tạo và kiểm tra một skill Claude Code có thể tái sử dụng. Gemini là tùy chọn; nếu không có Gemini, kết quả sẽ được đánh dấu là dựa trên một nguồn.

## Quy trình

1. **Làm rõ yêu cầu** — xác định nội dung cần trích xuất từ video và thứ cần xây dựng. Với video dài hơn 20 phút, có thể chọn một đoạn cụ thể.
2. **Claude phân tích** — dùng engine cục bộ của watch:watch và lưu bản đặc tả gồm sáu phần vào notes/lecture-claude.md.
3. **Gemini phân tích độc lập** — thực hiện cùng phân tích hai lần mà không cho Gemini xem ghi chú của Claude, rồi lưu cả hai câu trả lời vào notes/lecture-gemini.md. Nếu không dùng được Gemini, tiếp tục chỉ với Claude và đánh dấu là một nguồn.
4. **Đối chiếu kết quả** — gắn nhãn từng mục trong notes/SPEC.md là CONFIRMED, UNE SOURCE hoặc DÉSACCORD. Xem lại khung hình để giải quyết khác biệt và giữ nguyên lệnh, tên gói, cài đặt cùng thông báo lỗi chính xác.
5. **Xây dựng và kiểm tra** — đưa bản đặc tả cho skill-creator, tạo skill và chạy thử trên một trường hợp thực tế.

## Yêu cầu

- Claude Code
- Skill watch:watch để phân tích video YouTube
- Skill skill-creator để tạo kết quả
- Quyền truy cập Gemini (tùy chọn; có thể tiếp tục chỉ với Claude)

## Cài đặt

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Sau đó chạy /reload-plugins trong Claude Code để tải lại các plugin.

## Cách dùng

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "toàn bộ dự án" "một skill Claude Code"
```

## Tệp được tạo

- `notes/lecture-claude.md` — Bản phân tích video sáu phần của Claude
- `notes/lecture-gemini.md` — Hai lần phân tích độc lập của Gemini nếu có
- `notes/SPEC.md` — Bản đặc tả đã đối chiếu và câu hỏi còn mở
- Skill được tạo trong thư mục đầu ra đã chọn

## Cấu trúc kho mã

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## Giấy phép

Dự án được phát hành theo giấy phép MIT. Xem LICENSE.
