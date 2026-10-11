<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Преобразуйте обучающие видео YouTube в понятные и проверенные навыки и рабочие процессы для нескольких ИИ-агентов.</strong></p>

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

Этот репозиторий поддерживает несколько платформ для агентов. На этой странице описан процесс для Claude Code; переносимые форматы и настройка Codex, Gemini CLI, GitHub Copilot, ChatGPT и OpenAI API приведены в [руководстве по платформам](../../docs/platforms/README.md).

Укажите ссылку на YouTube и цель. Навык независимо анализирует видео с помощью Claude и Gemini, сводит результаты в notes/SPEC.md, а затем создаёт и проверяет повторно используемый навык Claude Code. Gemini необязателен; без него результат помечается как основанный на одном источнике.

## Как это работает

1. **Уточнение задачи** — определить, что нужно извлечь из видео и что создать. Для видео длиннее 20 минут можно выбрать нужный фрагмент.
2. **Анализ Claude** — использовать локальный движок watch:watch и сохранить спецификацию из шести частей в notes/lecture-claude.md.
3. **Независимый анализ Gemini** — дважды выполнить тот же анализ, не показывая Gemini заметки Claude, и сохранить оба ответа в notes/lecture-gemini.md. Если Gemini недоступен, продолжить только с Claude и отметить единственный источник.
4. **Сверка результатов** — пометить каждый пункт в notes/SPEC.md как CONFIRMED, UNE SOURCE или DÉSACCORD. Для разрешения расхождений повторно проверить кадры и сохранить точные команды, имена пакетов, настройки и сообщения об ошибках.
5. **Создание и проверка** — передать спецификацию в skill-creator, создать навык и запустить его на реальном примере.

## Требования

- Claude Code
- Навык watch:watch для анализа видео YouTube
- Навык skill-creator для создания результата
- Доступ к Gemini (необязательно; предусмотрен вариант только с Claude)

## Установка

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Затем выполните /reload-plugins в Claude Code, чтобы перезагрузить плагины.

## Использование

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "весь проект" "навык Claude Code"
```

## Создаваемые файлы

- `notes/lecture-claude.md` — Шесть разделов анализа видео от Claude
- `notes/lecture-gemini.md` — Два независимых анализа Gemini, если он доступен
- `notes/SPEC.md` — Сверенная спецификация и открытые вопросы
- Созданный навык в выбранной выходной папке

## Структура репозитория

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## Лицензия

Проект распространяется по лицензии MIT. См. LICENSE.
