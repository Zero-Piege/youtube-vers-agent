<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Gawing malinaw at napatunayan na mga Claude Code skill ang mga tutorial sa YouTube.</strong></p>

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

Magbigay ng link sa YouTube at layunin. Hiwalay na sinusuri ng skill ang video gamit ang Claude at Gemini, pinagsasama ang mga natuklasan sa notes/SPEC.md, at gumagawa at sumusubok ng magagamit-muli na Claude Code skill. Opsyonal ang Gemini; kung wala ito, mamarkahan ang resulta bilang mula sa iisang sanggunian.

## Daloy ng trabaho

1. **Linawin ang kahilingan** — tukuyin kung ano ang kukunin mula sa video at kung ano ang gagawin. Para sa video na lampas 20 minuto, pumili ng partikular na bahagi kung kailangan.
2. **Pagsusuri ni Claude** — gamitin ang lokal na engine ng watch:watch at itala ang anim-na-bahaging espesipikasyon sa notes/lecture-claude.md.
3. **Hiwalay na pagsusuri ng Gemini** — ulitin nang dalawang beses ang pagsusuri nang hindi ipinapakita ang mga tala ni Claude, at itala ang parehong sagot sa notes/lecture-gemini.md. Kung walang Gemini, magpatuloy gamit lang si Claude at markahang iisang sanggunian.
4. **Paghambingin ang mga natuklasan** — lagyan ng CONFIRMED, UNE SOURCE, o DÉSACCORD ang bawat item sa notes/SPEC.md. Suriing muli ang mga frame para lutasin ang hindi pagkakasundo at panatilihing eksakto ang mga command, pangalan ng package, setting, at mensahe ng error.
5. **Buuin at subukan** — ibigay ang espesipikasyon sa skill-creator, buuin ang skill, at patakbuhin ito sa totoong gamit.

## Mga kailangan

- Claude Code
- Ang watch:watch skill para suriin ang mga video sa YouTube
- Ang skill-creator skill para buuin ang resulta
- Access sa Gemini (opsyonal; puwedeng magpatuloy gamit lang si Claude)

## Pag-install

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Pagkatapos, patakbuhin ang /reload-plugins sa Claude Code para i-reload ang mga plugin.

## Paggamit

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "ang buong proyekto" "isang Claude Code skill"
```

## Mga nalikhang file

- `notes/lecture-claude.md` — Anim-na-bahaging pagsusuri ng video ni Claude
- `notes/lecture-gemini.md` — Dalawang hiwalay na pagsusuri ng Gemini kung mayroon
- `notes/SPEC.md` — Pinag-ugnay na espesipikasyon at mga bukas na tanong
- Skill na ginawa sa napiling output directory

## Ayos ng repository

- `README.md` — Pangunahing pahina ng proyekto sa Ingles
- `README.<locale>.md` — Mga salin na may code ng wika sa pangalan ng file
- `SKILL.md` — Kopyang sanggunian ng skill sa ugat ng repository
- `.claude/skills/youtube-vers-agent/SKILL.md` — Kopyang ini-install bilang project skill ng Claude Code at naka-sync sa nasa ugat

## Lisensya

Ipinamamahagi ang proyektong ito sa ilalim ng lisensyang MIT. Tingnan ang LICENSE.
