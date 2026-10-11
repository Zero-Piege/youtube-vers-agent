<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Gjør YouTube-opplæringer om til tydelige, verifiserte ferdigheter og arbeidsflyter for flere KI-agenter.</strong></p>

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

Dette repositoriet støtter flere agentplattformer. Denne siden beskriver arbeidsflyten for Claude Code; portable formater og oppsett for Codex, Gemini CLI, GitHub Copilot, ChatGPT og OpenAI API finner du i [plattformveiledningen](../../docs/platforms/README.md).

Oppgi en YouTube-lenke og et mål. Ferdigheten analyserer videoen uavhengig med Claude og Gemini, samler funnene i notes/SPEC.md og lager og validerer deretter en gjenbrukbar Claude Code-ferdighet. Gemini er valgfritt; uten Gemini merkes resultatet som basert på én kilde.

## Slik fungerer det

1. **Avklar oppgaven** — finn ut hva som skal hentes fra videoen, og hva som skal bygges. For videoer over 20 minutter kan du velge et bestemt utdrag.
2. **Claude-analyse** — bruk den lokale watch:watch-motoren og lagre spesifikasjonen med seks deler i notes/lecture-claude.md.
3. **Uavhengig Gemini-analyse** — gjenta analysen to ganger uten å vise Claudes notater, og lagre begge svarene i notes/lecture-gemini.md. Hvis Gemini ikke er tilgjengelig, fortsett bare med Claude og merk resultatet som én kilde.
4. **Sammenlign funnene** — merk hvert punkt i notes/SPEC.md med CONFIRMED, UNE SOURCE eller DÉSACCORD. Se gjennom videorammene på nytt for å løse uenigheter, og behold nøyaktige kommandoer, pakkenavn, innstillinger og feilmeldinger.
5. **Bygg og valider** — gi spesifikasjonen til skill-creator, lag ferdigheten og kjør den på et reelt bruksområde.

## Krav

- Claude Code
- watch:watch-ferdigheten for YouTube-videoanalyse
- skill-creator-ferdigheten for å lage resultatet
- Tilgang til Gemini (valgfritt; arbeidsflyten kan fortsette med bare Claude)

## Installasjon

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Kjør deretter /reload-plugins i Claude Code for å laste inn programtilleggene på nytt.

## Bruk

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "hele prosjektet" "en Claude Code-ferdighet"
```

## Genererte filer

- `notes/lecture-claude.md` — Claudes videoanalyse i seks deler
- `notes/lecture-gemini.md` — To uavhengige Gemini-analyser når de er tilgjengelige
- `notes/SPEC.md` — Den sammenstilte spesifikasjonen og åpne spørsmål
- En generert ferdighet i den valgte utdatamappen

## Lagerstruktur

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## Lisens

Prosjektet er utgitt under MIT-lisensen. Se LICENSE.
