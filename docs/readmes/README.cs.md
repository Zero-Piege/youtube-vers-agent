<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Převádějte návody z YouTube na přehledné a ověřené dovednosti pro Claude Code.</strong></p>

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

Zadejte odkaz na YouTube a cíl. Dovednost nezávisle analyzuje video pomocí Claude a Gemini, spojí zjištění v notes/SPEC.md a vytvoří a ověří znovu použitelnou dovednost pro Claude Code. Gemini je volitelné; bez něj bude výsledek označen jako založený na jediném zdroji.

## Jak to funguje

1. **Upřesnění zadání** — určit, co z videa získat a co vytvořit. U videí delších než 20 minut lze vybrat konkrétní úsek.
2. **Analýza pomocí Claude** — použít místní engine watch:watch a uložit šestidílnou specifikaci do notes/lecture-claude.md.
3. **Nezávislá analýza Gemini** — dvakrát zopakovat stejnou analýzu bez sdílení poznámek Claude a obě odpovědi uložit do notes/lecture-gemini.md. Pokud Gemini není dostupné, pokračovat pouze s Claude a označit výsledek jako jediný zdroj.
4. **Porovnání zjištění** — každou položku v notes/SPEC.md označit CONFIRMED, UNE SOURCE nebo DÉSACCORD. Neshody řešit opětovnou kontrolou snímků a zachovat přesné příkazy, názvy balíčků, nastavení i chybové zprávy.
5. **Vytvoření a ověření** — předat specifikaci nástroji skill-creator, vytvořit dovednost a spustit ji na skutečném případu.

## Požadavky

- Claude Code
- Dovednost watch:watch pro analýzu videí z YouTube
- Dovednost skill-creator pro vytvoření výsledku
- Přístup ke Gemini (volitelný; lze pokračovat pouze s Claude)

## Instalace

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Poté v Claude Code spusťte /reload-plugins a znovu načtěte pluginy.

## Použití

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "celý projekt" "dovednost Claude Code"
```

## Vytvořené soubory

- `notes/lecture-claude.md` — Šestidílná analýza videa od Claude
- `notes/lecture-gemini.md` — Dvě nezávislé analýzy Gemini, pokud je k dispozici
- `notes/SPEC.md` — Propojená specifikace a otevřené otázky
- Vygenerovaná dovednost ve zvoleném výstupním adresáři

## Struktura repozitáře

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## Licence

Tento projekt je šířen pod licencí MIT. Viz LICENSE.
