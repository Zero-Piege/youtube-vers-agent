<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Zet YouTube-tutorials om in duidelijke, gecontroleerde Claude Code-skills.</strong></p>

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

Geef een YouTube-link en een doel op. De skill analyseert de video onafhankelijk met Claude en Gemini, bundelt de bevindingen in notes/SPEC.md en bouwt en controleert een herbruikbare Claude Code-skill. Gemini is optioneel; zonder Gemini wordt het resultaat als afkomstig uit één bron gemarkeerd.

## Werkwijze

1. **De opdracht afbakenen** — bepalen wat uit de video moet worden gehaald en wat er gebouwd wordt. Bij video's langer dan 20 minuten kun je een specifiek fragment kiezen.
2. **Analyse met Claude** — gebruik de lokale engine van watch:watch en sla de specificatie in zes delen op in notes/lecture-claude.md.
3. **Onafhankelijke analyse met Gemini** — voer dezelfde analyse twee keer uit zonder Claude's notities te delen en sla beide antwoorden op in notes/lecture-gemini.md. Is Gemini niet beschikbaar, ga dan alleen met Claude verder en markeer het als één bron.
4. **Bevindingen vergelijken** — label elk onderdeel in notes/SPEC.md als CONFIRMED, UNE SOURCE of DÉSACCORD. Controleer videoframes opnieuw bij meningsverschillen en behoud exacte opdrachten, pakketnamen, instellingen en foutmeldingen.
5. **Bouwen en controleren** — geef de specificatie aan skill-creator, genereer de skill en voer die uit op een echte casus.

## Vereisten

- Claude Code
- De watch:watch-skill voor YouTube-videoanalyse
- De skill skill-creator om het resultaat te bouwen
- Toegang tot Gemini (optioneel; er is ook een Claude-only-route)

## Installatie

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Voer daarna /reload-plugins uit in Claude Code om de plugins opnieuw te laden.

## Gebruik

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "het hele project" "een Claude Code-skill"
```

## Gegenereerde bestanden

- `notes/lecture-claude.md` — Claudes videoanalyse in zes delen
- `notes/lecture-gemini.md` — Twee onafhankelijke Gemini-analyses, indien beschikbaar
- `notes/SPEC.md` — De vergeleken specificatie en open vragen
- Een gegenereerde skill in de gekozen uitvoermap

## Indeling van de repository

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

## Licentie

Dit project is uitgebracht onder de MIT-licentie. Zie LICENSE.
