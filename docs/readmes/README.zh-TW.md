<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>將 YouTube 教學轉化為清楚、經過核實的 Claude Code 技能。</strong></p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/badge/License-MIT-2ea44f?style=flat" alt="MIT License" /></a>
  <a href="https://github.com/Zero-Piege/youtube-vers-agent/stargazers"><img src="https://img.shields.io/github/stars/Zero-Piege/youtube-vers-agent?style=flat&logo=github" alt="GitHub stars" /></a>
  <a href="../../.claude/skills/youtube-vers-agent/SKILL.md"><img src="https://img.shields.io/badge/Claude%20Code-skill-cb785c?style=flat&logo=anthropic&logoColor=white" alt="Claude Code skill" /></a>
</p>

<p align="center">
  <a href="../../README.md">🇬🇧 English</a> · <a href="README.zh.md">🇨🇳 中文</a> · <a href="README.zh-TW.md">🇹🇼 繁體中文</a> · <a href="README.ja.md">🇯🇵 日本語</a> · <a href="README.pt.md">🇵🇹 Português</a> · <a href="README.pt-BR.md">🇧🇷 Português (Brasil)</a> · <a href="README.ko.md">🇰🇷 한국어</a><br />
  <a href="README.es.md">🇪🇸 Español</a> · <a href="README.de.md">🇩🇪 Deutsch</a> · <a href="README.fr.md">🇫🇷 Français</a> · <a href="README.he.md">🇮🇱 עברית</a> · <a href="README.ar.md">🇸🇦 العربية</a> · <a href="README.ru.md">🇷🇺 Русский</a> · <a href="README.pl.md">🇵🇱 Polski</a><br />
  <a href="README.cs.md">🇨🇿 Čeština</a> · <a href="README.nl.md">🇳🇱 Nederlands</a> · <a href="README.tr.md">🇹🇷 Türkçe</a> · <a href="README.uk.md">🇺🇦 Українська</a> · <a href="README.vi.md">🇻🇳 Tiếng Việt</a> · <a href="README.tl.md">🇵🇭 Tagalog</a> · <a href="README.id.md">🇮🇩 Bahasa Indonesia</a><br />
  <a href="README.th.md">🇹🇭 ไทย</a> · <a href="README.hi.md">🇮🇳 हिन्दी</a> · <a href="README.bn.md">🇧🇩 বাংলা</a> · <a href="README.ur.md">🇵🇰 اردو</a> · <a href="README.ro.md">🇷🇴 Română</a> · <a href="README.sv.md">🇸🇪 Svenska</a> · <a href="README.it.md">🇮🇹 Italiano</a><br />
  <a href="README.el.md">🇬🇷 Ελληνικά</a> · <a href="README.hu.md">🇭🇺 Magyar</a> · <a href="README.fi.md">🇫🇮 Suomi</a> · <a href="README.da.md">🇩🇰 Dansk</a> · <a href="README.no.md">🇳🇴 Norsk</a>
</p>

---

提供 YouTube 連結和目標後，這項技能會分別使用 Claude 與 Gemini 分析影片，將結果整理到 notes/SPEC.md，再建置並驗證可重複使用的 Claude Code 技能。Gemini 為選用；無法使用時會註明結果僅來自單一來源。

## 工作流程

1. **釐清需求** — 確認要從影片擷取什麼，以及要建置什麼。影片超過 20 分鐘時，可指定重點片段。
2. **Claude 分析** — 使用 watch:watch 的本機引擎，並將六部分建置規格儲存至 notes/lecture-claude.md。
3. **Gemini 獨立分析** — 不提供 Claude 筆記，獨立分析兩次，並將兩份結果儲存至 notes/lecture-gemini.md。Gemini 無法使用時，改用 Claude 並標記為單一來源。
4. **交叉核對** — 在 notes/SPEC.md 將每項標記為 CONFIRMED、UNE SOURCE 或 DÉSACCORD。重新檢查影片畫面以解決歧異，並保留精確的指令、套件名稱、設定與錯誤訊息。
5. **建置與驗證** — 將規格交給 skill-creator 產生技能，並以實際案例執行一次。

## 需求

- Claude Code
- 用於分析 YouTube 影片的 watch:watch 技能
- 用於建置結果的 skill-creator 技能
- Gemini（選用；流程支援僅使用 Claude）

## 安裝

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

接著在 Claude Code 執行 /reload-plugins 重新載入外掛程式。

## 使用

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "整個專案" "一個 Claude Code 技能"
```

## 產生的檔案

- `notes/lecture-claude.md` — Claude 的六部分影片分析
- `notes/lecture-gemini.md` — Gemini 的兩次獨立分析（如可用）
- `notes/SPEC.md` — 交叉核對後的規格與待解問題
- 在所選輸出目錄中產生的技能

## 儲存庫結構

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## 授權

本專案採用 MIT 授權，詳見 LICENSE。
