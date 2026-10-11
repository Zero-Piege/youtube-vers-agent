<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>เปลี่ยนวิดีโอสอนบน YouTube ให้เป็นสกิล Claude Code ที่ชัดเจนและผ่านการตรวจสอบ</strong></p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/badge/License-MIT-2ea44f?style=flat" alt="MIT License" /></a>
  <a href="https://github.com/Zero-Piege/youtube-vers-agent/stargazers"><img src="https://img.shields.io/github/stars/Zero-Piege/youtube-vers-agent?style=flat&logo=github" alt="GitHub stars" /></a>
  <a href="../../.claude/skills/youtube-vers-agent/SKILL.md"><img src="https://img.shields.io/badge/Claude%20Code-skill-cb785c?style=flat&logo=anthropic&logoColor=white" alt="Claude Code skill" /></a>
</p>

<p align="center">
  <a href="../../README.md">🇬🇧 English</a> · <a href="README.zh.md">🇨🇳 中文</a> · <a href="README.zh-TW.md">🇹🇼 繁體中文</a> · <a href="README.ja.md">🇯🇵 日本語</a> · <a href="README.pt.md">🇵🇹 Português</a> · <a href="README.pt-BR.md">🇧🇷 Português (Brasil)</a> · <a href="README.ko.md">🇰🇷 한국어</a><br />
  <a href="README.es.md">🇪🇸 Español</a> · <a href="README.de.md">🇩🇪 Deutsch</a> · <a href="README.fr.md">🇫🇷 Français</a> · <a href="README.he.md">🇮🇱 עברית</a> · <a href="README.ar.md">🇸🇦 العربية</a> · <a href="README.ru.md">🇷🇺 Русский</a> · <a href="README.pl.md">🇵🇱 Polski</a><br />
  <a href="README.cs.md">🇨🇿 Čeština</a> · <a href="README.nl.md">🇳🇱 Nederlands</a> · <a href="README.tr.md">🇹🇷 Türkçe</a> · <a href="README.uk.md">🇺🇦 Українська</a> · <a href="README.vi.md">🇻🇳 Tiếng Việt</a> · <a href="README.tl.md">🇵🇭 Tagalog</a> · <a href="README.id.md">🇮🇩 Bahasa Indonesia</a><br />
  <a href="README.th.md">🇹🇭 ไทย</a> · <a href="README.hi.md">🇮🇳 हिन्दी</a> · <a href="README.bn.md">🇧🇩 বাংলা</a> · <a href="README.ur.md">🇵🇰 اردو</a> · <a href="README.ro.md">🇷🇴 Română</a> · <a href="README.sv.md">🇸🇪 Svenska</a> · <a href="README.it.md">🇮🇹 Italiano</a><br />
  <a href="README.el.md">🇬🇷 Ελληνικά</a> · <a href="README.hu.md">🇭🇺 Magyar</a> · <a href="README.fi.md">🇫🇮 Suomi</a> · <a href="README.da.md">🇩🇰 Dansk</a> · <a href="README.no.md">🇳🇴 Norsk</a>
</p>

---

ระบุลิงก์ YouTube และเป้าหมาย สกิลจะวิเคราะห์วิดีโออย่างเป็นอิสระด้วย Claude และ Gemini รวมผลไว้ใน notes/SPEC.md แล้วสร้างและตรวจสอบสกิล Claude Code ที่นำกลับมาใช้ได้ Gemini เป็นตัวเลือก หากไม่มี Gemini ผลลัพธ์จะระบุว่าอ้างอิงจากแหล่งเดียว

## ขั้นตอนการทำงาน

1. **กำหนดคำขอให้ชัดเจน** — ระบุว่าจะดึงอะไรจากวิดีโอและจะสร้างอะไร หากวิดีโอยาวเกิน 20 นาที ให้เลือกช่วงที่ต้องการได้
2. **วิเคราะห์ด้วย Claude** — ใช้เอนจินภายในเครื่องของ watch:watch และบันทึกข้อกำหนดหกส่วนไว้ที่ notes/lecture-claude.md
3. **วิเคราะห์แยกด้วย Gemini** — ทำการวิเคราะห์เดิมสองครั้งโดยไม่ให้ Gemini เห็นบันทึกของ Claude แล้วบันทึกคำตอบทั้งสองไว้ที่ notes/lecture-gemini.md หากใช้ Gemini ไม่ได้ ให้ทำต่อด้วย Claude เพียงตัวเดียวและระบุว่าเป็นแหล่งเดียว
4. **เทียบผลการวิเคราะห์** — ติดป้ายแต่ละรายการใน notes/SPEC.md ว่า CONFIRMED, UNE SOURCE หรือ DÉSACCORD ตรวจภาพวิดีโอซ้ำเพื่อแก้ข้อขัดแย้ง และคงคำสั่ง ชื่อแพ็กเกจ การตั้งค่า และข้อความผิดพลาดตามต้นฉบับ
5. **สร้างและตรวจสอบ** — ส่งข้อกำหนดให้ skill-creator สร้างสกิล แล้วทดลองใช้กับกรณีจริง

## สิ่งที่ต้องมี

- Claude Code
- สกิล watch:watch สำหรับวิเคราะห์วิดีโอ YouTube
- สกิล skill-creator สำหรับสร้างผลลัพธ์
- การเข้าถึง Gemini (ไม่บังคับ; มีขั้นตอนที่ใช้ Claude เพียงตัวเดียว)

## การติดตั้ง

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

จากนั้นเรียก /reload-plugins ใน Claude Code เพื่อโหลดปลั๊กอินใหม่

## วิธีใช้

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "ทั้งโปรเจกต์" "สกิล Claude Code"
```

## ไฟล์ที่สร้าง

- `notes/lecture-claude.md` — การวิเคราะห์วิดีโอหกส่วนของ Claude
- `notes/lecture-gemini.md` — การวิเคราะห์อิสระสองครั้งของ Gemini หากใช้งานได้
- `notes/SPEC.md` — ข้อกำหนดที่เทียบกันแล้วและคำถามที่ยังเปิดอยู่
- สกิลที่สร้างในไดเรกทอรีเอาต์พุตที่เลือก

## โครงสร้างรีโพซิทอรี

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## ใบอนุญาต

โปรเจกต์นี้เผยแพร่ภายใต้สัญญาอนุญาต MIT ดู LICENSE
