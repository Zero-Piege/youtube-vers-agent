<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Turn YouTube tutorials into clear, verified Claude Code skills.</strong></p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-2ea44f?style=flat" alt="MIT License" /></a>
  <a href="https://github.com/Zero-Piege/youtube-vers-agent/stargazers"><img src="https://img.shields.io/github/stars/Zero-Piege/youtube-vers-agent?style=flat&logo=github" alt="GitHub stars" /></a>
  <a href=".claude/skills/youtube-vers-agent/SKILL.md"><img src="https://img.shields.io/badge/Claude%20Code-skill-cb785c?style=flat&logo=anthropic&logoColor=white" alt="Claude Code skill" /></a>
  <img src="https://img.shields.io/badge/languages-33-2ea44f?style=flat" alt="33 languages" />
</p>

---

## Read this project in your language

<p align="center">
  <a href="docs/readmes/README.en.md">🇬🇧 English</a> · <a href="docs/readmes/README.zh.md">🇨🇳 中文</a> · <a href="docs/readmes/README.zh-TW.md">🇹🇼 繁體中文</a> · <a href="docs/readmes/README.ja.md">🇯🇵 日本語</a> · <a href="docs/readmes/README.pt.md">🇵🇹 Português</a> · <a href="docs/readmes/README.pt-BR.md">🇧🇷 Português (Brasil)</a> · <a href="docs/readmes/README.ko.md">🇰🇷 한국어</a><br />
  <a href="docs/readmes/README.es.md">🇪🇸 Español</a> · <a href="docs/readmes/README.de.md">🇩🇪 Deutsch</a> · <a href="docs/readmes/README.fr.md">🇫🇷 Français</a> · <a href="docs/readmes/README.he.md">🇮🇱 עברית</a> · <a href="docs/readmes/README.ar.md">🇸🇦 العربية</a> · <a href="docs/readmes/README.ru.md">🇷🇺 Русский</a> · <a href="docs/readmes/README.pl.md">🇵🇱 Polski</a><br />
  <a href="docs/readmes/README.cs.md">🇨🇿 Čeština</a> · <a href="docs/readmes/README.nl.md">🇳🇱 Nederlands</a> · <a href="docs/readmes/README.tr.md">🇹🇷 Türkçe</a> · <a href="docs/readmes/README.uk.md">🇺🇦 Українська</a> · <a href="docs/readmes/README.vi.md">🇻🇳 Tiếng Việt</a> · <a href="docs/readmes/README.tl.md">🇵🇭 Tagalog</a> · <a href="docs/readmes/README.id.md">🇮🇩 Bahasa Indonesia</a><br />
  <a href="docs/readmes/README.th.md">🇹🇭 ไทย</a> · <a href="docs/readmes/README.hi.md">🇮🇳 हिन्दी</a> · <a href="docs/readmes/README.bn.md">🇧🇩 বাংলা</a> · <a href="docs/readmes/README.ur.md">🇵🇰 اردو</a> · <a href="docs/readmes/README.ro.md">🇷🇴 Română</a> · <a href="docs/readmes/README.sv.md">🇸🇪 Svenska</a> · <a href="docs/readmes/README.it.md">🇮🇹 Italiano</a><br />
  <a href="docs/readmes/README.el.md">🇬🇷 Ελληνικά</a> · <a href="docs/readmes/README.hu.md">🇭🇺 Magyar</a> · <a href="docs/readmes/README.fi.md">🇫🇮 Suomi</a> · <a href="docs/readmes/README.da.md">🇩🇰 Dansk</a> · <a href="docs/readmes/README.no.md">🇳🇴 Norsk</a>
</p>

## What it does

Give the skill a YouTube video and a goal. It analyzes the video with Claude and, when available, Gemini; reconciles the findings into a specification; then builds and validates a reusable Claude Code skill. If Gemini is unavailable, it continues with Claude and marks the result as single-source.

## Get started

Install the project skill in Claude Code:

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Then run it with a video URL and your goal:

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "the whole project" "a Claude Code skill"
```

## Project files

- [Full English guide](docs/readmes/README.en.md)
- [Installable Claude Code skill](.claude/skills/youtube-vers-agent/SKILL.md)
- Language guides are grouped in [`docs/readmes/`](docs/readmes/).

The root README is this short GitHub landing page and language index. The complete English guide and all 32 translated guides live in `docs/readmes/`.

## License

MIT. See [LICENSE](LICENSE).
