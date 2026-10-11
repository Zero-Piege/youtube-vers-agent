<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Ubah tutorial YouTube menjadi skill Claude Code yang jelas dan terverifikasi.</strong></p>

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

Berikan tautan YouTube dan tujuan. Skill menganalisis video secara terpisah dengan Claude dan Gemini, merangkum temuan di notes/SPEC.md, lalu membuat dan memvalidasi skill Claude Code yang dapat digunakan kembali. Gemini bersifat opsional; tanpa Gemini, hasil ditandai berasal dari satu sumber.

## Cara kerja

1. **Perjelas permintaan** — tentukan apa yang perlu diambil dari video dan apa yang akan dibuat. Untuk video lebih dari 20 menit, pilih segmen tertentu bila perlu.
2. **Analisis Claude** — gunakan mesin lokal watch:watch dan simpan spesifikasi enam bagian di notes/lecture-claude.md.
3. **Analisis Gemini secara independen** — ulangi analisis yang sama dua kali tanpa memperlihatkan catatan Claude, lalu simpan kedua jawaban di notes/lecture-gemini.md. Jika Gemini tidak tersedia, lanjutkan hanya dengan Claude dan tandai sebagai satu sumber.
4. **Bandingkan temuan** — beri label CONFIRMED, UNE SOURCE, atau DÉSACCORD pada setiap butir di notes/SPEC.md. Tinjau ulang cuplikan video untuk menyelesaikan perbedaan dan pertahankan perintah, nama paket, pengaturan, serta pesan kesalahan secara tepat.
5. **Buat dan validasi** — berikan spesifikasi kepada skill-creator, buat skill, lalu jalankan pada kasus nyata.

## Persyaratan

- Claude Code
- Skill watch:watch untuk analisis video YouTube
- Skill skill-creator untuk membuat hasil
- Akses Gemini (opsional; alur hanya dengan Claude juga tersedia)

## Instalasi

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Selanjutnya jalankan /reload-plugins di Claude Code untuk memuat ulang plugin.

## Penggunaan

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "seluruh proyek" "skill Claude Code"
```

## File yang dihasilkan

- `notes/lecture-claude.md` — Analisis video enam bagian oleh Claude
- `notes/lecture-gemini.md` — Dua analisis Gemini yang independen jika tersedia
- `notes/SPEC.md` — Spesifikasi yang sudah dicocokkan dan pertanyaan terbuka
- Skill yang dibuat di direktori keluaran pilihan

## Struktur repositori

- `README.md` — Halaman utama proyek berbahasa Inggris
- `README.<locale>.md` — Halaman terjemahan dengan kode bahasa pada nama file
- `SKILL.md` — Salinan rujukan skill di akar repositori
- `.claude/skills/youtube-vers-agent/SKILL.md` — Salinan yang dipasang sebagai skill proyek Claude Code dan disinkronkan dengan salinan akar

## Lisensi

Proyek ini dirilis dengan Lisensi MIT. Lihat LICENSE.
