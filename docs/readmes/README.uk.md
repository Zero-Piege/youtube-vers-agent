<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Перетворюйте навчальні відео YouTube на зрозумілі й перевірені навички та робочі процеси для кількох ШІ-агентів.</strong></p>

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

Цей репозиторій підтримує кілька платформ агентів. На цій сторінці описано роботу з Claude Code; портативні формати й налаштування Codex, Gemini CLI, GitHub Copilot, ChatGPT та OpenAI API наведено в [посібнику з платформ](../../docs/platforms/README.md).

Надайте посилання на YouTube і мету. Навичка незалежно аналізує відео за допомогою Claude і Gemini, зводить результати у notes/SPEC.md, а потім створює та перевіряє навичку Claude Code для повторного використання. Gemini необов’язковий; без нього результат позначається як заснований на одному джерелі.

## Як це працює

1. **Уточнення запиту** — визначити, що потрібно отримати з відео та що створити. Для відео довших за 20 хвилин можна вибрати потрібний фрагмент.
2. **Аналіз Claude** — використати локальний рушій watch:watch і зберегти специфікацію з шести частин у notes/lecture-claude.md.
3. **Незалежний аналіз Gemini** — двічі виконати такий самий аналіз, не показуючи нотатки Claude, і зберегти обидві відповіді в notes/lecture-gemini.md. Якщо Gemini недоступний, продовжити лише з Claude та позначити одне джерело.
4. **Зіставлення результатів** — позначити кожен пункт у notes/SPEC.md як CONFIRMED, UNE SOURCE або DÉSACCORD. Для розбіжностей повторно переглянути кадри та зберегти точні команди, назви пакетів, налаштування й повідомлення про помилки.
5. **Створення й перевірка** — передати специфікацію до skill-creator, створити навичку та запустити її на реальному прикладі.

## Вимоги

- Claude Code
- Навичка watch:watch для аналізу відео YouTube
- Навичка skill-creator для створення результату
- Доступ до Gemini (необов’язковий; доступний режим лише з Claude)

## Встановлення

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Потім виконайте /reload-plugins у Claude Code, щоб перезавантажити плагіни.

## Використання

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "увесь проєкт" "навичку Claude Code"
```

## Створені файли

- `notes/lecture-claude.md` — Шість частин аналізу відео від Claude
- `notes/lecture-gemini.md` — Два незалежні аналізи Gemini, якщо доступні
- `notes/SPEC.md` — Зіставлена специфікація та відкриті питання
- Створена навичка у вибраному каталозі виводу

## Структура репозиторію

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## Ліцензія

Проєкт поширюється за ліцензією MIT. Див. LICENSE.
