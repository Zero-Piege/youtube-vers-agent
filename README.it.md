<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Trasforma i tutorial di YouTube in skill Claude Code chiare e verificate.</strong></p>

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

Fornisci un link YouTube e un obiettivo. La skill analizza il video in modo indipendente con Claude e Gemini, raccoglie i risultati in notes/SPEC.md e crea e convalida una skill Claude Code riutilizzabile. Gemini è facoltativo; se non è disponibile, il risultato viene indicato come basato su un’unica fonte.

## Come funziona

1. **Definire la richiesta** — chiarire cosa estrarre dal video e cosa realizzare. Per i video oltre i 20 minuti, si può indicare un segmento preciso.
2. **Analisi con Claude** — usare il motore locale di watch:watch e salvare la specifica in sei parti in notes/lecture-claude.md.
3. **Analisi indipendente con Gemini** — ripetere l’analisi due volte senza mostrare a Gemini gli appunti di Claude e salvare entrambe le risposte in notes/lecture-gemini.md. Se Gemini non è disponibile, proseguire con Claude e indicare la fonte singola.
4. **Confrontare i risultati** — etichettare ogni elemento in notes/SPEC.md come CONFIRMED, UNE SOURCE o DÉSACCORD. Ricontrollare i fotogrammi per risolvere le divergenze e mantenere esatti comandi, nomi dei pacchetti, impostazioni e messaggi di errore.
5. **Creare e convalidare** — passare la specifica a skill-creator, generare la skill ed eseguirla su un caso reale.

## Requisiti

- Claude Code
- La skill watch:watch per analizzare i video di YouTube
- La skill skill-creator per creare il risultato
- Accesso a Gemini (facoltativo; è previsto anche un flusso con il solo Claude)

## Installazione

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Poi esegui /reload-plugins in Claude Code per ricaricare i plugin.

## Uso

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "l’intero progetto" "una skill Claude Code"
```

## File generati

- `notes/lecture-claude.md` — L’analisi video di Claude in sei parti
- `notes/lecture-gemini.md` — Le due analisi indipendenti di Gemini, se disponibile
- `notes/SPEC.md` — La specifica confrontata e le domande aperte
- La skill generata nella cartella di output scelta

## Struttura del repository

- `README.md` — Pagina iniziale del progetto in inglese
- `README.<locale>.md` — Pagine tradotte indicate dal codice della lingua
- `SKILL.md` — Copia di riferimento della skill nella radice del repository
- `.claude/skills/youtube-vers-agent/SKILL.md` — Copia installabile per le skill del progetto Claude Code, mantenuta sincronizzata con quella nella radice

## Licenza

Questo progetto è distribuito con licenza MIT. Vedi LICENSE.
