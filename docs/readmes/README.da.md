<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Gør YouTube-vejledninger til tydelige og verificerede Claude Code-skills.</strong></p>

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

Angiv et YouTube-link og et mål. Skillen analyserer videoen uafhængigt med Claude og Gemini, samler resultaterne i notes/SPEC.md og opbygger og validerer derefter en genanvendelig Claude Code-skill. Gemini er valgfri; uden Gemini markeres resultatet som baseret på én kilde.

## Sådan fungerer det

1. **Afklar opgaven** — fastlæg, hvad der skal udtrækkes fra videoen, og hvad der skal bygges. Ved videoer over 20 minutter kan du vælge et bestemt afsnit.
2. **Claude-analyse** — brug den lokale watch:watch-motor, og gem specifikationen med seks dele i notes/lecture-claude.md.
3. **Uafhængig Gemini-analyse** — gentag analysen to gange uden at vise Claudes noter, og gem begge svar i notes/lecture-gemini.md. Hvis Gemini ikke er tilgængelig, fortsæt kun med Claude, og markér resultatet som én kilde.
4. **Sammenhold resultaterne** — mærk hvert punkt i notes/SPEC.md med CONFIRMED, UNE SOURCE eller DÉSACCORD. Gennemgå videobilleder igen for at løse uenigheder, og bevar nøjagtige kommandoer, pakkenavne, indstillinger og fejlmeddelelser.
5. **Byg og validér** — giv specifikationen til skill-creator, opret skillen, og kør den på en reel brugssituation.

## Krav

- Claude Code
- watch:watch-skillen til analyse af YouTube-videoer
- skill-creator-skillen til at bygge resultatet
- Adgang til Gemini (valgfri; forløbet kan fortsætte med kun Claude)

## Installation

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Kør derefter /reload-plugins i Claude Code for at genindlæse plugins.

## Brug

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "hele projektet" "en Claude Code-skill"
```

## Genererede filer

- `notes/lecture-claude.md` — Claudes videoanalyse i seks dele
- `notes/lecture-gemini.md` — To uafhængige Gemini-analyser, hvis de er tilgængelige
- `notes/SPEC.md` — Den sammenholdte specifikation og åbne spørgsmål
- En genereret skill i den valgte outputmappe

## Repository-struktur

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## Licens

Projektet er udgivet under MIT-licensen. Se LICENSE.
