<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>YouTube のチュートリアルを、検証可能で分かりやすい Claude Code スキルに変換します。</strong></p>

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

YouTube のリンクと目的を渡すと、Claude と Gemini が動画を独立して分析し、結果を notes/SPEC.md にまとめます。その仕様から再利用可能な Claude Code スキルを作成し、検証します。Gemini は任意です。利用できない場合は単一ソースとして記録します。

## ワークフロー

1. **依頼を整理** — 動画から何を取り出し、何を作るか確認します。20 分を超える動画では、必要に応じて対象区間を指定します。
2. **Claude で分析** — watch:watch のローカルエンジンを使い、6 部構成の仕様を notes/lecture-claude.md に保存します。
3. **Gemini で独立分析** — Claude のメモを見せずに同じ分析を 2 回行い、両方の結果を notes/lecture-gemini.md に保存します。Gemini が利用できない場合は Claude のみで続行し、単一ソースと明記します。
4. **結果を照合** — notes/SPEC.md の各項目に CONFIRMED、UNE SOURCE、DÉSACCORD のいずれかを付けます。食い違いは動画のフレームを再確認し、正確なコマンド、パッケージ名、設定、エラーメッセージを残します。
5. **作成と検証** — 仕様を skill-creator に渡してスキルを作り、実際のケースで実行します。

## 必要なもの

- Claude Code
- YouTube 動画分析用の watch:watch スキル
- 成果物の作成に使う skill-creator スキル
- Gemini（任意。Claude のみでの代替手順に対応）

## インストール

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

続いて Claude Code で /reload-plugins を実行し、プラグインを再読み込みします。

## 使い方

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "プロジェクト全体" "Claude Code スキル"
```

## 生成されるファイル

- `notes/lecture-claude.md` — Claude による 6 部構成の動画分析
- `notes/lecture-gemini.md` — Gemini による 2 回の独立分析（利用可能な場合）
- `notes/SPEC.md` — 照合済み仕様と未解決の質問
- 選択した出力フォルダーに生成されるスキル

## リポジトリの構成

- `README.md` — 英語のプロジェクトトップページ
- `README.<locale>.md` — 言語コード別の翻訳ページ
- `SKILL.md` — リポジトリ内のスキル原本
- `.claude/skills/youtube-vers-agent/SKILL.md` — Claude Code のプロジェクトスキル用インストール先。ルートの原本と同期します

## ライセンス

本プロジェクトは MIT ライセンスで公開されています。詳細は LICENSE を参照してください。
