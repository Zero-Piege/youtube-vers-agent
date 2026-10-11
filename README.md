<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Turn YouTube tutorials into clear, verified Claude Code skills.</strong></p>

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

Provide a YouTube link and a goal. The skill analyzes the video independently with Claude and Gemini, reconciles the findings in notes/SPEC.md, then builds and validates a reusable Claude Code skill. Gemini is optional; without it, the result is marked as single-source.

## How it works

1. **Frame the request** — clarify what to extract from the video and what to build. For videos longer than 20 minutes, choose a specific segment when useful.
2. **Claude analysis** — use the local engine in watch:watch and save a six-part specification to notes/lecture-claude.md.
3. **Independent Gemini analysis** — run the same analysis twice without showing Gemini Claude’s notes, then save both responses to notes/lecture-gemini.md. If Gemini is unavailable, continue with Claude and mark the result as single-source.
4. **Cross-check findings** — label each item in notes/SPEC.md as CONFIRMED, UNE SOURCE, or DÉSACCORD. Recheck video frames to resolve disagreements, and preserve exact commands, package names, settings, and error messages.
5. **Build and validate** — pass the specification to skill-creator, generate the skill, and run it on a real use case.

## Requirements

- Claude Code
- The watch:watch skill for YouTube video analysis
- The skill-creator skill to build the result
- Gemini access (optional; a Claude-only fallback is supported)

## Install

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Then reload Claude Code plugins with /reload-plugins.

## Use

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "the whole project" "a Claude Code skill"
```

## Generated files

- `notes/lecture-claude.md` — Claude’s six-part video analysis
- `notes/lecture-gemini.md` — Gemini’s two independent analyses, when available
- `notes/SPEC.md` — The reconciled specification and open questions
- The generated skill in the selected output directory

## Repository layout

- `README.md` — English project landing page
- `README.<locale>.md` — Translated pages named with their locale code
- `SKILL.md` — Canonical source copy of the skill instructions
- `.claude/skills/youtube-vers-agent/SKILL.md` — Installable Claude Code project-skill copy, kept in sync with the root copy

## License

This project is distributed under the MIT License. See LICENSE.
