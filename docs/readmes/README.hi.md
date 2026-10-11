<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>YouTube ट्यूटोरियल को कई AI एजेंट के लिए स्पष्ट और सत्यापित स्किल व वर्कफ़्लो में बदलें।</strong></p>

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

यह रिपॉज़िटरी कई एजेंट प्लेटफ़ॉर्म का समर्थन करती है। यह पृष्ठ Claude Code की कार्यप्रणाली बताता है; Codex, Gemini CLI, GitHub Copilot, ChatGPT और OpenAI API के पोर्टेबल फ़ॉर्मैट व सेटअप [प्लेटफ़ॉर्म गाइड](../../docs/platforms/README.md) में दिए गए हैं।

YouTube लिंक और लक्ष्य दें। यह स्किल Claude और Gemini से वीडियो का स्वतंत्र विश्लेषण कराती है, निष्कर्षों को notes/SPEC.md में मिलाती है, फिर पुनः उपयोग योग्य Claude Code स्किल बनाकर सत्यापित करती है। Gemini वैकल्पिक है; उपलब्ध न होने पर परिणाम को एकल-स्रोत के रूप में चिह्नित किया जाता है।

## कार्यप्रवाह

1. **अनुरोध स्पष्ट करें** — तय करें कि वीडियो से क्या निकालना है और क्या बनाना है। 20 मिनट से लंबे वीडियो के लिए कोई खास हिस्सा चुना जा सकता है।
2. **Claude से विश्लेषण** — watch:watch के स्थानीय इंजन का उपयोग करें और छह भागों वाला विनिर्देश notes/lecture-claude.md में सहेजें।
3. **Gemini से स्वतंत्र विश्लेषण** — Claude के नोट दिखाए बिना वही विश्लेषण दो बार करें और दोनों उत्तर notes/lecture-gemini.md में सहेजें। Gemini उपलब्ध न हो तो केवल Claude के साथ आगे बढ़ें और एकल स्रोत का संकेत दें।
4. **निष्कर्षों का मिलान करें** — notes/SPEC.md में हर बिंदु को CONFIRMED, UNE SOURCE या DÉSACCORD से चिह्नित करें। मतभेद सुलझाने के लिए वीडियो के फ़्रेम फिर देखें और सटीक कमांड, पैकेज नाम, सेटिंग तथा त्रुटि संदेश सुरक्षित रखें।
5. **बनाएँ और जाँचें** — विनिर्देश skill-creator को दें, स्किल बनाएँ और वास्तविक उपयोग के मामले में चलाएँ।

## आवश्यकताएँ

- Claude Code
- YouTube वीडियो विश्लेषण के लिए watch:watch स्किल
- परिणाम बनाने के लिए skill-creator स्किल
- Gemini की पहुँच (वैकल्पिक; केवल Claude वाला विकल्प उपलब्ध)

## इंस्टॉल करें

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

इसके बाद प्लगइन फिर से लोड करने के लिए Claude Code में /reload-plugins चलाएँ।

## उपयोग

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "पूरा प्रोजेक्ट" "एक Claude Code स्किल"
```

## बनाई गई फ़ाइलें

- `notes/lecture-claude.md` — Claude का छह भागों वाला वीडियो विश्लेषण
- `notes/lecture-gemini.md` — उपलब्ध होने पर Gemini के दो स्वतंत्र विश्लेषण
- `notes/SPEC.md` — मिलान किया हुआ विनिर्देश और खुले प्रश्न
- चुनी हुई आउटपुट डायरेक्टरी में बनी स्किल

## रिपॉज़िटरी की संरचना

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## लाइसेंस

यह प्रोजेक्ट MIT लाइसेंस के अंतर्गत जारी किया गया है। LICENSE देखें।
