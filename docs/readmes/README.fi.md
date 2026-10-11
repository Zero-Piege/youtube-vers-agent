<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Muunna YouTube-oppaat selkeiksi ja tarkistetuiksi Claude Code -taidoiksi.</strong></p>

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

Anna YouTube-linkki ja tavoite. Taito analysoi videon itsenäisesti Clauden ja Geminin avulla, kokoaa havainnot tiedostoon notes/SPEC.md ja luo sekä tarkistaa uudelleenkäytettävän Claude Code -taidon. Gemini on valinnainen; ilman sitä tulos merkitään yhden lähteen varaan perustuvaksi.

## Näin se toimii

1. **Rajaa pyyntö** — selvitä, mitä videosta halutaan poimia ja mitä rakentaa. Yli 20 minuutin videosta voi valita tietyn osuuden.
2. **Claude-analyysi** — käytä watch:watchin paikallista moottoria ja tallenna kuusiosainen määrittely tiedostoon notes/lecture-claude.md.
3. **Geminin itsenäinen analyysi** — tee sama analyysi kahdesti näyttämättä Geminille Clauden muistiinpanoja ja tallenna molemmat vastaukset tiedostoon notes/lecture-gemini.md. Jos Gemini ei ole käytettävissä, jatka vain Claudella ja merkitse lähteeksi yksi lähde.
4. **Vertaa havaintoja** — merkitse jokainen notes/SPEC.md-kohde tunnisteella CONFIRMED, UNE SOURCE tai DÉSACCORD. Tarkista videoruudut uudelleen ristiriitojen ratkaisemiseksi ja säilytä täsmälliset komennot, pakettien nimet, asetukset ja virheilmoitukset.
5. **Rakenna ja tarkista** — anna määrittely skill-creatorille, luo taito ja suorita se aidossa käyttötapauksessa.

## Vaatimukset

- Claude Code
- watch:watch-taito YouTube-videoiden analysointiin
- skill-creator-taito tuloksen rakentamiseen
- Gemini-käyttöoikeus (valinnainen; työn voi tehdä myös vain Claudella)

## Asennus

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Lataa seuraavaksi Claude Code -liitännäiset uudelleen suorittamalla /reload-plugins.

## Käyttö

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "koko projekti" "Claude Code -taito"
```

## Luodut tiedostot

- `notes/lecture-claude.md` — Clauden kuusiosainen videoanalyysi
- `notes/lecture-gemini.md` — Geminin kaksi itsenäistä analyysiä, jos saatavilla
- `notes/SPEC.md` — Ristiintarkistettu määrittely ja avoimet kysymykset
- Valittuun tuloshakemistoon luotu taito

## Tietovaraston rakenne

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## Lisenssi

Tämä projekti julkaistaan MIT-lisenssillä. Katso LICENSE.
