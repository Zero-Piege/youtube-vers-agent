<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Zamieniaj samouczki YouTube w przejrzyste i sprawdzone umiejętności Claude Code.</strong></p>

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

Podaj link do YouTube i cel. Umiejętność niezależnie analizuje film za pomocą Claude i Gemini, łączy wyniki w notes/SPEC.md, a następnie tworzy i sprawdza umiejętność Claude Code do ponownego użycia. Gemini jest opcjonalne; bez niego wynik zostaje oznaczony jako oparty na jednym źródle.

## Jak to działa

1. **Doprecyzowanie zadania** — ustal, co wyodrębnić z filmu i co zbudować. W przypadku filmów dłuższych niż 20 minut można wskazać konkretny fragment.
2. **Analiza Claude** — użyj lokalnego silnika watch:watch i zapisz sześcioczęściową specyfikację w notes/lecture-claude.md.
3. **Niezależna analiza Gemini** — wykonaj tę samą analizę dwa razy bez udostępniania notatek Claude i zapisz obie odpowiedzi w notes/lecture-gemini.md. Jeśli Gemini jest niedostępne, kontynuuj tylko z Claude i oznacz wynik jako pochodzący z jednego źródła.
4. **Porównanie ustaleń** — oznacz każdy element w notes/SPEC.md jako CONFIRMED, UNE SOURCE lub DÉSACCORD. Sprawdź ponownie klatki filmu, aby rozstrzygnąć rozbieżności, i zachowaj dokładne polecenia, nazwy pakietów, ustawienia oraz komunikaty błędów.
5. **Budowanie i walidacja** — przekaż specyfikację do skill-creator, wygeneruj umiejętność i uruchom ją na rzeczywistym przykładzie.

## Wymagania

- Claude Code
- Umiejętność watch:watch do analizy filmów YouTube
- Umiejętność skill-creator do utworzenia wyniku
- Dostęp do Gemini (opcjonalny; dostępny jest tryb tylko z Claude)

## Instalacja

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Następnie uruchom /reload-plugins w Claude Code, aby ponownie załadować wtyczki.

## Użycie

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "cały projekt" "umiejętność Claude Code"
```

## Tworzone pliki

- `notes/lecture-claude.md` — Sześcioczęściowa analiza filmu wykonana przez Claude
- `notes/lecture-gemini.md` — Dwie niezależne analizy Gemini, jeśli jest dostępne
- `notes/SPEC.md` — Uzgodniona specyfikacja i otwarte pytania
- Wygenerowana umiejętność w wybranym katalogu wyjściowym

## Struktura repozytorium

- `README.md` — Angielska strona główna projektu
- `README.<locale>.md` — Tłumaczenia oznaczone kodem języka w nazwie pliku
- `SKILL.md` — Referencyjna kopia umiejętności w katalogu głównym repozytorium
- `.claude/skills/youtube-vers-agent/SKILL.md` — Instalowalna kopia umiejętności projektu Claude Code, synchronizowana z kopią główną

## Licencja

Projekt jest udostępniany na licencji MIT. Zobacz LICENSE.
