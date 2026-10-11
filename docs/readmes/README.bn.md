<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>YouTube টিউটোরিয়ালকে স্পষ্ট ও যাচাইকৃত Claude Code স্কিলে রূপান্তর করুন।</strong></p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/badge/License-MIT-2ea44f?style=flat" alt="MIT License" /></a>
  <a href="https://github.com/Zero-Piege/youtube-vers-agent/stargazers"><img src="https://img.shields.io/github/stars/Zero-Piege/youtube-vers-agent?style=flat&logo=github" alt="GitHub stars" /></a>
  <a href="../../.claude/skills/youtube-vers-agent/SKILL.md"><img src="https://img.shields.io/badge/Claude%20Code-skill-cb785c?style=flat&logo=anthropic&logoColor=white" alt="Claude Code skill" /></a>
</p>

<p align="center">
  <a href="README.en.md">🇬🇧 English</a> · <a href="README.zh.md">🇨🇳 中文</a> · <a href="README.zh-TW.md">🇹🇼 繁體中文</a> · <a href="README.ja.md">🇯🇵 日本語</a> · <a href="README.pt.md">🇵🇹 Português</a> · <a href="README.pt-BR.md">🇧🇷 Português (Brasil)</a> · <a href="README.ko.md">🇰🇷 한국어</a><br />
  <a href="README.es.md">🇪🇸 Español</a> · <a href="README.de.md">🇩🇪 Deutsch</a> · <a href="README.fr.md">🇫🇷 Français</a> · <a href="README.he.md">🇮🇱 עברית</a> · <a href="README.ar.md">🇸🇦 العربية</a> · <a href="README.ru.md">🇷🇺 Русский</a> · <a href="README.pl.md">🇵🇱 Polski</a><br />
  <a href="README.cs.md">🇨🇿 Čeština</a> · <a href="README.nl.md">🇳🇱 Nederlands</a> · <a href="README.tr.md">🇹🇷 Türkçe</a> · <a href="README.uk.md">🇺🇦 Українська</a> · <a href="README.vi.md">🇻🇳 Tiếng Việt</a> · <a href="README.tl.md">🇵🇭 Tagalog</a> · <a href="README.id.md">🇮🇩 Bahasa Indonesia</a><br />
  <a href="README.th.md">🇹🇭 ไทย</a> · <a href="README.hi.md">🇮🇳 हिन्दी</a> · <a href="README.bn.md">🇧🇩 বাংলা</a> · <a href="README.ur.md">🇵🇰 اردو</a> · <a href="README.ro.md">🇷🇴 Română</a> · <a href="README.sv.md">🇸🇪 Svenska</a> · <a href="README.it.md">🇮🇹 Italiano</a><br />
  <a href="README.el.md">🇬🇷 Ελληνικά</a> · <a href="README.hu.md">🇭🇺 Magyar</a> · <a href="README.fi.md">🇫🇮 Suomi</a> · <a href="README.da.md">🇩🇰 Dansk</a> · <a href="README.no.md">🇳🇴 Norsk</a>
</p>

---

একটি YouTube লিংক ও লক্ষ্য দিন। এই স্কিল Claude ও Gemini দিয়ে ভিডিওটি স্বাধীনভাবে বিশ্লেষণ করে, ফলাফল notes/SPEC.md-এ মিলিয়ে নেয়, তারপর পুনর্ব্যবহারযোগ্য Claude Code স্কিল তৈরি ও যাচাই করে। Gemini ঐচ্ছিক; এটি না থাকলে ফলাফলকে একক-উৎস হিসেবে চিহ্নিত করা হয়।

## কাজের ধাপ

1. **অনুরোধ স্পষ্ট করুন** — ভিডিও থেকে কী নিতে হবে এবং কী তৈরি করতে হবে তা ঠিক করুন। ২০ মিনিটের বেশি ভিডিও হলে নির্দিষ্ট অংশ বেছে নেওয়া যায়।
2. **Claude-এর বিশ্লেষণ** — watch:watch-এর স্থানীয় ইঞ্জিন ব্যবহার করে ছয় অংশের স্পেসিফিকেশন notes/lecture-claude.md-এ সংরক্ষণ করুন।
3. **Gemini-এর স্বাধীন বিশ্লেষণ** — Claude-এর নোট না দেখিয়ে একই বিশ্লেষণ দুবার করুন এবং দুই উত্তর notes/lecture-gemini.md-এ সংরক্ষণ করুন। Gemini না থাকলে শুধু Claude দিয়ে চালিয়ে যান এবং একক-উৎস হিসেবে চিহ্নিত করুন।
4. **ফলাফল মিলিয়ে দেখুন** — notes/SPEC.md-এর প্রতিটি বিষয়কে CONFIRMED, UNE SOURCE বা DÉSACCORD হিসেবে চিহ্নিত করুন। মতভেদ মেটাতে ভিডিওর ফ্রেম আবার দেখুন এবং সঠিক কমান্ড, প্যাকেজের নাম, সেটিংস ও ত্রুটির বার্তা অক্ষত রাখুন।
5. **তৈরি ও যাচাই করুন** — স্পেসিফিকেশন skill-creator-কে দিন, স্কিল তৈরি করুন এবং বাস্তব ক্ষেত্রে চালান।

## প্রয়োজনীয়তা

- Claude Code
- YouTube ভিডিও বিশ্লেষণের জন্য watch:watch স্কিল
- ফলাফল তৈরির জন্য skill-creator স্কিল
- Gemini অ্যাক্সেস (ঐচ্ছিক; শুধু Claude দিয়েও এগোনো যায়)

## ইনস্টলেশন

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

এরপর প্লাগইন পুনরায় লোড করতে Claude Code-এ /reload-plugins চালান।

## ব্যবহার

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "পুরো প্রকল্প" "একটি Claude Code স্কিল"
```

## তৈরি হওয়া ফাইল

- `notes/lecture-claude.md` — Claude-এর ছয় অংশের ভিডিও বিশ্লেষণ
- `notes/lecture-gemini.md` — উপলভ্য হলে Gemini-এর দুটি স্বাধীন বিশ্লেষণ
- `notes/SPEC.md` — মিলিয়ে তৈরি স্পেসিফিকেশন ও খোলা প্রশ্ন
- নির্বাচিত আউটপুট ডিরেক্টরিতে তৈরি স্কিল

## রিপোজিটরির বিন্যাস

```text
README.md
docs/
└── readmes/
    ├── README.en.md
    └── README.<locale>.md
.claude/
└── skills/
    └── youtube-vers-agent/
        └── SKILL.md
```

## লাইসেন্স

এই প্রকল্প MIT লাইসেন্সের অধীনে প্রকাশিত। LICENSE দেখুন।
