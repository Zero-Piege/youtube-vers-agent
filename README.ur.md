<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>YouTube ٹیوٹوریلز کو واضح اور جانچے ہوئے Claude Code اسکلز میں تبدیل کریں۔</strong></p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-2ea44f?style=flat" alt="MIT License" /></a>
  <a href="https://github.com/Zero-Piege/youtube-vers-agent/stargazers"><img src="https://img.shields.io/github/stars/Zero-Piege/youtube-vers-agent?style=flat&logo=github" alt="GitHub stars" /></a>
  <a href=".claude/skills/youtube-vers-agent/SKILL.md"><img src="https://img.shields.io/badge/Claude%20Code-skill-cb785c?style=flat&logo=anthropic&logoColor=white" alt="Claude Code skill" /></a>
</p>

<p align="center">
  <a href="README.md">🇬🇧 English</a> · <a href="README.zh.md">🇨🇳 中文</a> · <a href="README.zh-TW.md">🇹🇼 繁體中文</a> · <a href="README.ja.md">🇯🇵 日本語</a> · <a href="README.pt.md">🇵🇹 Português</a> · <a href="README.pt-BR.md">🇧🇷 Português (Brasil)</a> · <a href="README.ko.md">🇰🇷 한국어</a><br />
  <a href="README.es.md">🇪🇸 Español</a> · <a href="README.de.md">🇩🇪 Deutsch</a> · <a href="README.fr.md">🇫🇷 Français</a> · <a href="README.he.md">🇮🇱 עברית</a> · <a href="README.ar.md">🇸🇦 العربية</a> · <a href="README.ru.md">🇷🇺 Русский</a> · <a href="README.pl.md">🇵🇱 Polski</a><br />
  <a href="README.cs.md">🇨🇿 Čeština</a> · <a href="README.nl.md">🇳🇱 Nederlands</a> · <a href="README.tr.md">🇹🇷 Türkçe</a> · <a href="README.uk.md">🇺🇦 Українська</a> · <a href="README.vi.md">🇻🇳 Tiếng Việt</a> · <a href="README.tl.md">🇵🇭 Tagalog</a> · <a href="README.id.md">🇮🇩 Bahasa Indonesia</a><br />
  <a href="README.th.md">🇹🇭 ไทย</a> · <a href="README.hi.md">🇮🇳 हिन्दी</a> · <a href="README.bn.md">🇧🇩 বাংলা</a> · <a href="README.ur.md">🇵🇰 اردو</a> · <a href="README.ro.md">🇷🇴 Română</a> · <a href="README.sv.md">🇸🇪 Svenska</a> · <a href="README.it.md">🇮🇹 Italiano</a><br />
  <a href="README.el.md">🇬🇷 Ελληνικά</a> · <a href="README.hu.md">🇭🇺 Magyar</a> · <a href="README.fi.md">🇫🇮 Suomi</a> · <a href="README.da.md">🇩🇰 Dansk</a> · <a href="README.no.md">🇳🇴 Norsk</a>
</p>

---

YouTube کا لنک اور مقصد دیں۔ یہ اسکل Claude اور Gemini کے ذریعے ویڈیو کا الگ الگ تجزیہ کرتی ہے، نتائج کو notes/SPEC.md میں یکجا کرتی ہے، پھر دوبارہ استعمال کے قابل Claude Code اسکل بناتی اور جانچتی ہے۔ Gemini اختیاری ہے؛ دستیاب نہ ہو تو نتیجے کو ایک ہی ماخذ پر مبنی نشان زد کیا جاتا ہے۔

## طریقۂ کار

1. **درخواست واضح کریں** — طے کریں کہ ویڈیو سے کیا حاصل کرنا ہے اور کیا بنانا ہے۔ 20 منٹ سے طویل ویڈیو کے لیے مخصوص حصہ منتخب کیا جا سکتا ہے۔
2. **Claude کا تجزیہ** — watch:watch کا مقامی انجن استعمال کریں اور چھ حصوں پر مشتمل وضاحت notes/lecture-claude.md میں محفوظ کریں۔
3. **Gemini کا آزادانہ تجزیہ** — Claude کے نوٹس دکھائے بغیر یہی تجزیہ دو بار کریں اور دونوں جوابات notes/lecture-gemini.md میں محفوظ کریں۔ Gemini دستیاب نہ ہو تو صرف Claude کے ساتھ جاری رکھیں اور واحد ماخذ کی نشاندہی کریں۔
4. **نتائج کا تقابل** — notes/SPEC.md میں ہر نکتے کو CONFIRMED، UNE SOURCE یا DÉSACCORD کا لیبل دیں۔ اختلاف حل کرنے کے لیے ویڈیو کے فریم دوبارہ دیکھیں اور درست کمانڈز، پیکیج کے نام، ترتیبات اور خرابی کے پیغامات محفوظ رکھیں۔
5. **تیاری اور جانچ** — وضاحت skill-creator کو دیں، اسکل بنائیں اور اسے حقیقی مثال پر چلائیں۔

## ضروریات

- Claude Code
- YouTube ویڈیو کے تجزیے کے لیے watch:watch اسکل
- نتیجہ بنانے کے لیے skill-creator اسکل
- Gemini تک رسائی (اختیاری؛ صرف Claude کے ساتھ بھی جاری رکھا جا سکتا ہے)

## انسٹالیشن

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

اس کے بعد پلگ اِنز دوبارہ لوڈ کرنے کے لیے Claude Code میں /reload-plugins چلائیں۔

## استعمال

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "پورا پروجیکٹ" "ایک Claude Code اسکل"
```

## تیار ہونے والی فائلیں

- `notes/lecture-claude.md` — Claude کا چھ حصوں پر مشتمل ویڈیو تجزیہ
- `notes/lecture-gemini.md` — دستیاب ہونے پر Gemini کے دو آزادانہ تجزیے
- `notes/SPEC.md` — موازنہ شدہ وضاحت اور کھلے سوالات
- منتخب آؤٹ پٹ ڈائریکٹری میں تیار کردہ اسکل

## ریپوزٹری کی ساخت

- `README.md` — انگریزی میں پروجیکٹ کا مرکزی صفحہ
- `README.<locale>.md` — فائل کے نام میں زبان کا کوڈ رکھنے والے ترجمے
- `SKILL.md` — ریپوزٹری کی جڑ میں اسکل کی حوالہ جاتی نقل
- `.claude/skills/youtube-vers-agent/SKILL.md` — Claude Code پروجیکٹ اسکل کے لیے قابلِ تنصیب نقل، جو جڑ والی نقل کے ساتھ ہم آہنگ رکھی جاتی ہے

## لائسنس

یہ پروجیکٹ MIT لائسنس کے تحت جاری کیا گیا ہے۔ LICENSE دیکھیں۔
