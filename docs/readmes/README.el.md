<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Μετατρέψτε τα βίντεο του YouTube σε σαφείς, επαληθευμένες δεξιότητες και ροές εργασίας για πολλούς AI agent.</strong></p>

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

Αυτό το αποθετήριο υποστηρίζει πολλές πλατφόρμες agent. Αυτή η σελίδα περιγράφει τη ροή εργασίας του Claude Code· οι φορητές μορφές και η ρύθμιση για Codex, Gemini CLI, GitHub Copilot, ChatGPT και OpenAI API βρίσκονται στον [οδηγό πλατφορμών](../../docs/platforms/README.md).

Δώστε έναν σύνδεσμο YouTube και έναν στόχο. Η δεξιότητα αναλύει ανεξάρτητα το βίντεο με Claude και Gemini, συγκεντρώνει τα ευρήματα στο notes/SPEC.md και στη συνέχεια δημιουργεί και επαληθεύει μια επαναχρησιμοποιήσιμη δεξιότητα Claude Code. Το Gemini είναι προαιρετικό· χωρίς αυτό, το αποτέλεσμα επισημαίνεται ως βασισμένο σε μία πηγή.

## Πώς λειτουργεί

1. **Ορισμός του αιτήματος** — διευκρινίστε τι πρέπει να εξαχθεί από το βίντεο και τι πρέπει να δημιουργηθεί. Για βίντεο άνω των 20 λεπτών μπορείτε να επιλέξετε συγκεκριμένο απόσπασμα.
2. **Ανάλυση με Claude** — χρησιμοποιήστε την τοπική μηχανή του watch:watch και αποθηκεύστε την προδιαγραφή έξι μερών στο notes/lecture-claude.md.
3. **Ανεξάρτητη ανάλυση με Gemini** — επαναλάβετε την ίδια ανάλυση δύο φορές χωρίς να δείξετε τις σημειώσεις του Claude και αποθηκεύστε και τις δύο απαντήσεις στο notes/lecture-gemini.md. Αν το Gemini δεν είναι διαθέσιμο, συνεχίστε μόνο με Claude και σημειώστε ότι υπάρχει μία πηγή.
4. **Διασταύρωση ευρημάτων** — χαρακτηρίστε κάθε στοιχείο στο notes/SPEC.md ως CONFIRMED, UNE SOURCE ή DÉSACCORD. Ελέγξτε ξανά τα καρέ για να λύσετε διαφωνίες και διατηρήστε ακριβείς εντολές, ονόματα πακέτων, ρυθμίσεις και μηνύματα σφάλματος.
5. **Δημιουργία και επαλήθευση** — δώστε την προδιαγραφή στο skill-creator, δημιουργήστε τη δεξιότητα και δοκιμάστε την σε πραγματική περίπτωση.

## Απαιτήσεις

- Claude Code
- Η δεξιότητα watch:watch για ανάλυση βίντεο YouTube
- Η δεξιότητα skill-creator για τη δημιουργία του αποτελέσματος
- Πρόσβαση στο Gemini (προαιρετική· υπάρχει και ροή μόνο με Claude)

## Εγκατάσταση

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Έπειτα εκτελέστε /reload-plugins στο Claude Code για να φορτώσετε ξανά τα πρόσθετα.

## Χρήση

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "ολόκληρο το έργο" "μια δεξιότητα Claude Code"
```

## Αρχεία που δημιουργούνται

- `notes/lecture-claude.md` — Η ανάλυση βίντεο έξι μερών του Claude
- `notes/lecture-gemini.md` — Οι δύο ανεξάρτητες αναλύσεις Gemini, εφόσον είναι διαθέσιμο
- `notes/SPEC.md` — Η διασταυρωμένη προδιαγραφή και οι ανοιχτές ερωτήσεις
- Η δεξιότητα που δημιουργείται στον επιλεγμένο φάκελο εξόδου

## Δομή αποθετηρίου

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## Άδεια

Το έργο διατίθεται με άδεια MIT. Δείτε το LICENSE.
