<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Alakítsd a YouTube-oktatóanyagokat világos, ellenőrzött Claude Code-készségekké.</strong></p>

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

Adj meg egy YouTube-linket és egy célt. A készség Claude és Gemini segítségével egymástól függetlenül elemzi a videót, az eredményeket a notes/SPEC.md fájlban egyesíti, majd újrafelhasználható Claude Code-készséget hoz létre és ellenőriz. A Gemini használata nem kötelező; nélküle az eredmény egyetlen forrásból származóként lesz megjelölve.

## Működés

1. **A kérés pontosítása** — tisztázd, mit kell kinyerni a videóból és mit kell létrehozni. A 20 percnél hosszabb videóknál kijelölhetsz egy konkrét szakaszt.
2. **Claude-elemzés** — használd a watch:watch helyi motorját, és mentsd a hat részből álló specifikációt a notes/lecture-claude.md fájlba.
3. **Független Gemini-elemzés** — végezd el kétszer ugyanazt az elemzést anélkül, hogy megmutatnád Claude jegyzeteit, majd mentsd mindkét választ a notes/lecture-gemini.md fájlba. Ha a Gemini nem érhető el, folytasd csak Claude-dal, és jelöld az egyetlen forrást.
4. **Eredmények összevetése** — a notes/SPEC.md minden elemét jelöld CONFIRMED, UNE SOURCE vagy DÉSACCORD címkével. Az eltérések tisztázásához ellenőrizd újra a videó képkockáit, és őrizd meg a pontos parancsokat, csomagneveket, beállításokat és hibaüzeneteket.
5. **Létrehozás és ellenőrzés** — add át a specifikációt a skill-creator számára, hozd létre a készséget, és futtasd egy valós eseten.

## Követelmények

- Claude Code
- A watch:watch készség YouTube-videók elemzéséhez
- A skill-creator készség az eredmény létrehozásához
- Gemini-hozzáférés (nem kötelező; csak Claude-dal is folytatható)

## Telepítés

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Ezután futtasd a /reload-plugins parancsot a Claude Code-ban a bővítmények újratöltéséhez.

## Használat

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "a teljes projekt" "egy Claude Code-készség"
```

## Létrehozott fájlok

- `notes/lecture-claude.md` — Claude hatrészes videóelemzése
- `notes/lecture-gemini.md` — A Gemini két független elemzése, ha elérhető
- `notes/SPEC.md` — Az összevetett specifikáció és a nyitott kérdések
- A kiválasztott kimeneti könyvtárban létrehozott készség

## A tároló felépítése

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

## Licenc

A projekt MIT licenc alatt érhető el. Lásd: LICENSE.
