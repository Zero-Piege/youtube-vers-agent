<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Gör YouTube-handledningar till tydliga och verifierade Claude Code-skills.</strong></p>

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

Ange en YouTube-länk och ett mål. Skillen analyserar videon oberoende med Claude och Gemini, sammanför resultaten i notes/SPEC.md och skapar och validerar sedan en återanvändbar Claude Code-skill. Gemini är valfritt; utan Gemini märks resultatet som baserat på en enda källa.

## Så fungerar det

1. **Avgränsa uppgiften** — bestäm vad som ska hämtas ur videon och vad som ska byggas. För videor som är längre än 20 minuter kan du välja ett särskilt avsnitt.
2. **Claude-analys** — använd den lokala watch:watch-motorn och spara specifikationen i sex delar i notes/lecture-claude.md.
3. **Oberoende Gemini-analys** — gör samma analys två gånger utan att visa Claude-anteckningarna och spara båda svaren i notes/lecture-gemini.md. Om Gemini saknas fortsätter du med Claude och markerar resultatet som en enda källa.
4. **Jämför resultaten** — märk varje punkt i notes/SPEC.md med CONFIRMED, UNE SOURCE eller DÉSACCORD. Granska videobilder igen för att lösa skillnader och behåll exakta kommandon, paketnamn, inställningar och felmeddelanden.
5. **Bygg och validera** — lämna specifikationen till skill-creator, skapa skillen och kör den på ett verkligt användningsfall.

## Krav

- Claude Code
- watch:watch-skillen för YouTube-videoanalys
- skill-creator-skillen för att skapa resultatet
- Åtkomst till Gemini (valfritt; det går att fortsätta med bara Claude)

## Installation

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Kör sedan /reload-plugins i Claude Code för att läsa in plugin-programmen igen.

## Användning

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "hela projektet" "en Claude Code-skill"
```

## Skapade filer

- `notes/lecture-claude.md` — Claudes videoanalys i sex delar
- `notes/lecture-gemini.md` — Två oberoende Gemini-analyser när de är tillgängliga
- `notes/SPEC.md` — Den jämförda specifikationen och öppna frågor
- En genererad skill i den valda utdatakatalogen

## Lagringsplatsens struktur

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## Licens

Projektet distribueras under MIT-licensen. Se LICENSE.
