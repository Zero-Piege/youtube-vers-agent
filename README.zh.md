<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>把 YouTube 教程变成清晰、经过核实的 Claude Code 技能。</strong></p>

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

提供 YouTube 链接和目标后，此技能会分别用 Claude 与 Gemini 分析视频，将结果整理到 notes/SPEC.md，再构建并验证可复用的 Claude Code 技能。Gemini 可选；无法使用时会注明结果仅来自单一来源。

## 工作流程

1. **明确需求** — 确认要从视频中提取什么，以及要构建什么。视频超过 20 分钟时，可指定重点片段。
2. **Claude 分析** — 使用 watch:watch 的本地引擎，将六部分构建说明保存到 notes/lecture-claude.md。
3. **Gemini 独立分析** — 在不提供 Claude 笔记的情况下重复分析两次，并将两份结果保存到 notes/lecture-gemini.md。Gemini 不可用时，继续使用 Claude，并标记为单一来源。
4. **交叉核对** — 在 notes/SPEC.md 中将每项标记为 CONFIRMED、UNE SOURCE 或 DÉSACCORD。检查视频画面以解决分歧，并保留准确的命令、包名、设置和错误信息。
5. **构建并验证** — 将说明交给 skill-creator 生成技能，再用真实场景运行一次。

## 所需条件

- Claude Code
- 用于分析 YouTube 视频的 watch:watch 技能
- 用于构建结果的 skill-creator 技能
- Gemini（可选；工作流程支持仅使用 Claude）

## 安装

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

然后在 Claude Code 中运行 /reload-plugins 重新加载插件。

## 使用

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "整个项目" "一个 Claude Code 技能"
```

## 生成的文件

- `notes/lecture-claude.md` — Claude 的六部分视频分析
- `notes/lecture-gemini.md` — Gemini 的两次独立分析（如可用）
- `notes/SPEC.md` — 交叉核对后的说明和待解决问题
- 在所选输出目录中生成的技能

## 仓库结构

- `README.md` — 英文项目主页
- `README.<locale>.md` — 按语言代码命名的翻译页面
- `SKILL.md` — 仓库中的技能源文件副本
- `.claude/skills/youtube-vers-agent/SKILL.md` — Claude Code 项目技能路径中的安装副本；与根目录副本保持同步

## 许可证

本项目采用 MIT 许可证，详见 LICENSE。
