<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="64" alt="YouTube" /><br />
  youtube-vers-agent
</h1>

<p align="center"><strong>Turn YouTube tutorials into clear, verified Claude Code skills.</strong></p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-2ea44f?style=flat" alt="MIT License" /></a>
  <a href="https://github.com/Zero-Piege/youtube-vers-agent/stargazers"><img src="https://img.shields.io/github/stars/Zero-Piege/youtube-vers-agent?style=flat&logo=github" alt="GitHub stars" /></a>
  <a href=".claude/skills/youtube-vers-agent/SKILL.md"><img src="https://img.shields.io/badge/Claude%20Code-skill-cb785c?style=flat&logo=anthropic&logoColor=white" alt="Claude Code skill" /></a>
</p>

<p align="center">
  <a href="README.md">🇬🇧 English</a> · <a href="README.zh.md">🇨🇳 简体中文</a> · <a href="README.de.md">🇩🇪 Deutsch</a> · <a href="README.es.md">🇪🇸 Español</a> · <a href="README.fr.md">🇫🇷 Français</a> · <a href="README.it.md">🇮🇹 Italiano</a> · <a href="README.ja.md">🇯🇵 日本語</a> · <a href="README.ko.md">🇰🇷 한국어</a> · <a href="README.pt.md">🇵🇹 Português</a> · <a href="README.ru.md">🇷🇺 Русский</a>
</p>

---

Give the skill a YouTube link and a goal. It studies the tutorial independently with Claude and Gemini, reconciles the findings in a specification, then builds and validates a reusable Claude Code skill.

## How it works

1. **Frame the request** — clarify what to extract from the video and what to build. For videos longer than 20 minutes, focus on a specific segment when useful.
2. **Read with Claude** — use `watch:watch` with the local engine and save a six-part build specification to `notes/lecture-claude.md`.
3. **Read independently with Gemini** — run the same analysis twice without showing it Claude’s notes, then save both responses in `notes/lecture-gemini.md`. If Gemini is unavailable, continue with Claude and mark the specification as single-source.
4. **Cross-check the findings** — record each item in `notes/SPEC.md` as `CONFIRMED`, `UNE SOURCE`, or `DÉSACCORD`. Recheck video frames to resolve disagreements, and preserve exact commands, package names, settings, and error messages.
5. **Build and validate** — pass the specification to `skill-creator`, generate the skill, and run it on a real use case.

## Requirements

- Claude Code
- The `watch:watch` skill for YouTube video analysis
- The `skill-creator` skill to build the result
- Gemini access for the independent second source (optional; the workflow supports a Claude-only fallback)

## Install

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Then reload Claude Code plugins with `/reload-plugins`.

## Use

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "the whole project" "a Claude Code skill"
```

## Generated files

- `notes/lecture-claude.md` — Claude’s six-part video analysis
- `notes/lecture-gemini.md` — Gemini’s two independent analyses, when available
- `notes/SPEC.md` — the reconciled specification and open questions
- A generated skill in the selected output directory

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
