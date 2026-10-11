<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Transformă tutorialele YouTube în skill-uri Claude Code clare și verificate.</strong></p>

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

Oferă un link YouTube și un obiectiv. Skill-ul analizează videoclipul independent cu Claude și Gemini, reunește rezultatele în notes/SPEC.md, apoi creează și validează un skill Claude Code reutilizabil. Gemini este opțional; fără el, rezultatul este marcat ca provenind dintr-o singură sursă.

## Cum funcționează

1. **Clarifică cererea** — stabilește ce trebuie extras din videoclip și ce trebuie construit. Pentru videoclipurile mai lungi de 20 de minute poți alege un segment.
2. **Analiza Claude** — folosește motorul local watch:watch și salvează specificația în șase părți în notes/lecture-claude.md.
3. **Analiza independentă Gemini** — repetă analiza de două ori fără să-i arăți notițele lui Claude și salvează ambele răspunsuri în notes/lecture-gemini.md. Dacă Gemini nu este disponibil, continuă doar cu Claude și marchează sursa unică.
4. **Compară constatările** — etichetează fiecare element din notes/SPEC.md cu CONFIRMED, UNE SOURCE sau DÉSACCORD. Verifică din nou cadrele pentru a rezolva diferențele și păstrează comenzile, numele pachetelor, setările și mesajele de eroare exacte.
5. **Construiește și validează** — oferă specificația către skill-creator, generează skill-ul și rulează-l pe un caz real.

## Cerințe

- Claude Code
- Skill-ul watch:watch pentru analiza videoclipurilor YouTube
- Skill-ul skill-creator pentru construirea rezultatului
- Acces la Gemini (opțional; fluxul poate continua doar cu Claude)

## Instalare

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Apoi rulează /reload-plugins în Claude Code pentru a reîncărca pluginurile.

## Utilizare

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "întregul proiect" "un skill Claude Code"
```

## Fișiere generate

- `notes/lecture-claude.md` — Analiza video în șase părți realizată de Claude
- `notes/lecture-gemini.md` — Cele două analize independente Gemini, dacă sunt disponibile
- `notes/SPEC.md` — Specificația comparată și întrebările deschise
- Skill-ul generat în directorul de ieșire ales

## Structura depozitului

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

## Licență

Acest proiect este publicat sub licența MIT. Consultă LICENSE.
