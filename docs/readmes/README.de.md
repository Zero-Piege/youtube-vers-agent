<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Verwandle YouTube-Tutorials in klare, überprüfte Claude-Code-Skills.</strong></p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/badge/License-MIT-2ea44f?style=flat" alt="MIT License" /></a>
  <a href="https://github.com/Zero-Piege/youtube-vers-agent/stargazers"><img src="https://img.shields.io/github/stars/Zero-Piege/youtube-vers-agent?style=flat&logo=github" alt="GitHub stars" /></a>
  <a href="../../.claude/skills/youtube-vers-agent/SKILL.md"><img src="https://img.shields.io/badge/Claude%20Code-skill-cb785c?style=flat&logo=anthropic&logoColor=white" alt="Claude Code skill" /></a>
</p>

<p align="center">
  <a href="README.en.md">🇬🇧 English</a> · <a href="README.zh.md">🇨🇳 中文</a> · <a href="README.zh-TW.md">🇹🇼 繁體中文</a> · <a href="README.ja.md">🇯🇵 日本語</a> · <a href="README.pt.md">🇵🇹 Português</a> · <a href="README.pt-BR.md">🇧🇷 Português (Brasil)</a> · <a href="README.ko.md">🇰🇷 한국어</a><br />
  <a href="README.es.md">🇪🇸 Español</a> · <a href="README.de.md">🇩🇪 Deutsch</a> · <a href="README.fr.md">🇫🇷 Français</a> · <a href="README.he.md">🇮🇱 עברית</a> · <a href="README.ar.md">🇸🇦 العربية</a> · <a href="README.ru.md">🇷🇺 Русский</a> · <a href="README.pl.md">🇵🇱 Polski</a><br />
  <a href="README.cs.md">🇨🇿 Čeština</a> · <a href="README.nl.md">🇳🇱 Nederlands</a> · <a href="README.tr.md">🇹🇷 Türkçe</a> · <a href="README.uk.md">🇺🇦 Українська</a> · <a href="README.vi.md">🇻🇳 Tiếng Việt</a> · <a href="README.tl.md">🇵🇭 Tagalog</a> · <a href="README.id.md">🇮🇩 Bahasa Indonesia</a><br />
  <a href="README.th.md">🇹🇭 ไทย</a> · <a href="README.hi.md">🇮🇳 हिन्दी</a> · <a href="README.bn.md">🇧🇩 বাংলা</a> · <a href="README.ur.md">🇵🇰 اردو</a> · <a href="README.ro.md">🇷🇴 Română</a> · <a href="README.sv.md">🇸🇪 Svenska</a> · <a href="README.it.md">🇮🇹 Italiano</a><br />
  <a href="README.el.md">🇬🇷 Ελληνικά</a> · <a href="README.hu.md">🇭🇺 Magyar</a> · <a href="README.fi.md">🇫🇮 Suomi</a> · <a href="README.da.md">🇩🇰 Dansk</a> · <a href="README.no.md">🇳🇴 Norsk</a>
</p>

---

Gib einen YouTube-Link und ein Ziel an. Der Skill analysiert das Video unabhängig mit Claude und Gemini, führt die Ergebnisse in notes/SPEC.md zusammen und erstellt und überprüft einen wiederverwendbaren Claude-Code-Skill. Gemini ist optional; ohne Gemini wird das Ergebnis als Einzelquelle gekennzeichnet.

## Ablauf

1. **Auftrag klären** — festlegen, was aus dem Video übernommen und was erstellt werden soll. Bei Videos über 20 Minuten kann ein Abschnitt ausgewählt werden.
2. **Analyse mit Claude** — die lokale Engine von watch:watch verwenden und die sechsteilige Spezifikation in notes/lecture-claude.md speichern.
3. **Unabhängige Gemini-Analyse** — die Analyse zweimal wiederholen, ohne Claude die eigenen Notizen zu zeigen, und beide Antworten in notes/lecture-gemini.md speichern. Ist Gemini nicht verfügbar, nur mit Claude fortfahren und die Einzelquelle kennzeichnen.
4. **Ergebnisse abgleichen** — jeden Punkt in notes/SPEC.md als CONFIRMED, UNE SOURCE oder DÉSACCORD markieren. Bei Widersprüchen Videobilder erneut prüfen und genaue Befehle, Paketnamen, Einstellungen und Fehlermeldungen beibehalten.
5. **Erstellen und prüfen** — die Spezifikation an skill-creator übergeben, den Skill erzeugen und in einem echten Anwendungsfall ausführen.

## Voraussetzungen

- Claude Code
- Der Skill watch:watch zur Analyse von YouTube-Videos
- Der Skill skill-creator zum Erstellen des Ergebnisses
- Gemini-Zugriff (optional; ein Claude-only-Ablauf ist möglich)

## Installation

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Lade anschließend mit /reload-plugins die Claude-Code-Plugins neu.

## Verwendung

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "das ganze Projekt" "einen Claude-Code-Skill"
```

## Erzeugte Dateien

- `notes/lecture-claude.md` — Claudes sechsteiliger Videoanalyse
- `notes/lecture-gemini.md` — Zwei unabhängige Gemini-Analysen, sofern verfügbar
- `notes/SPEC.md` — Abgeglichene Spezifikation und offene Fragen
- Generierter Skill im ausgewählten Ausgabeverzeichnis

## Repository-Struktur

```text
README.md
docs/
└── readmes/
    ├── README.en.md
    └── README.<locale>.md
.claude/
└── skills/
    └── youtube-vers-agent/
        └── SKILL.md
```

## Lizenz

Dieses Projekt steht unter der MIT-Lizenz. Siehe LICENSE.
