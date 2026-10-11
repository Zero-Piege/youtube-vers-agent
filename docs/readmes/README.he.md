<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>הפכו מדריכי YouTube למיומנויות ולתהליכי עבודה ברורים ומאומתים עבור כמה סוכני AI.</strong></p>

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

המאגר הזה תומך בכמה פלטפורמות לסוכנים. הדף הזה מתאר את תהליך העבודה של Claude Code; פורמטים ניידים והתקנה עבור Codex, Gemini CLI, GitHub Copilot, ChatGPT ו-OpenAI API מופיעים ב[מדריך הפלטפורמות](../../docs/platforms/README.md).

ספקו קישור ל-YouTube ומטרה. הכישור מנתח את הסרטון בנפרד באמצעות Claude ו-Gemini, מרכז את הממצאים ב-notes/SPEC.md, ואז בונה ומאמת כישור Claude Code לשימוש חוזר. Gemini אופציונלי; בלעדיו התוצאה תסומן כמבוססת על מקור יחיד.

## איך זה עובד

1. **הגדרת הבקשה** — מבררים מה לחלץ מהסרטון ומה לבנות. בסרטונים שאורכם יותר מ-20 דקות אפשר לבחור קטע ממוקד.
2. **ניתוח Claude** — משתמשים במנוע המקומי של watch:watch ושומרים מפרט בן שישה חלקים בקובץ notes/lecture-claude.md.
3. **ניתוח עצמאי של Gemini** — מריצים את אותו ניתוח פעמיים בלי להציג ל-Gemini את ההערות של Claude, ושומרים את שתי התשובות ב-notes/lecture-gemini.md. אם Gemini אינו זמין, ממשיכים עם Claude בלבד ומסמנים מקור יחיד.
4. **הצלבת הממצאים** — מסמנים כל פריט ב-notes/SPEC.md בתווית CONFIRMED, UNE SOURCE או DÉSACCORD. בודקים שוב את תמונות הסרטון כדי לפתור מחלוקות ושומרים פקודות, שמות חבילות, הגדרות והודעות שגיאה מדויקים.
5. **בנייה ואימות** — מעבירים את המפרט ל-skill-creator, יוצרים את הכישור ומריצים אותו על מקרה אמיתי.

## דרישות

- Claude Code
- הכישור watch:watch לניתוח סרטוני YouTube
- הכישור skill-creator ליצירת התוצאה
- גישה ל-Gemini (אופציונלית; אפשר להמשיך גם עם Claude בלבד)

## התקנה

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

לאחר מכן מריצים /reload-plugins ב-Claude Code כדי לטעון מחדש את התוספים.

## שימוש

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "הפרויקט כולו" "כישור Claude Code"
```

## קבצים שנוצרים

- `notes/lecture-claude.md` — ניתוח הווידאו של Claude בשישה חלקים
- `notes/lecture-gemini.md` — שני הניתוחים העצמאיים של Gemini, אם זמין
- `notes/SPEC.md` — המפרט שהוצלב והשאלות הפתוחות
- כישור שנוצר בתיקיית הפלט שנבחרה

## מבנה המאגר

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## רישיון

הפרויקט מופץ תחת רישיון MIT. ראו LICENSE.
