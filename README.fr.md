<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Transformez des tutoriels YouTube en skills Claude Code clairs et vérifiés.</strong></p>

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

Fournissez un lien YouTube et un objectif. La skill analyse la vidéo séparément avec Claude et Gemini, rassemble les résultats dans notes/SPEC.md, puis crée et valide une skill Claude Code réutilisable. Gemini est facultatif ; sans lui, le résultat est signalé comme provenant d’une seule source.

## Fonctionnement

1. **Préciser la demande** — déterminer ce qu’il faut extraire de la vidéo et ce qu’il faut construire. Pour une vidéo de plus de 20 minutes, choisir un passage précis si besoin.
2. **Analyse par Claude** — utiliser le moteur local de watch:watch et enregistrer la spécification en six parties dans notes/lecture-claude.md.
3. **Analyse indépendante par Gemini** — refaire l’analyse deux fois sans lui montrer les notes de Claude, puis enregistrer les deux réponses dans notes/lecture-gemini.md. Si Gemini est indisponible, continuer avec Claude seul et signaler la source unique.
4. **Croiser les résultats** — classer chaque élément de notes/SPEC.md comme CONFIRMED, UNE SOURCE ou DÉSACCORD. Revoir les images pour trancher et conserver les commandes, noms de paquets, réglages et messages d’erreur exacts.
5. **Construire et valider** — transmettre la spécification à skill-creator, générer la skill et l’exécuter sur un cas réel.

## Prérequis

- Claude Code
- La skill watch:watch pour analyser les vidéos YouTube
- La skill skill-creator pour créer le résultat
- Un accès à Gemini (facultatif ; le parcours peut continuer avec Claude seul)

## Installation

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Rechargez ensuite les plugins de Claude Code avec /reload-plugins.

## Utilisation

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "tout le projet" "une skill Claude Code"
```

## Fichiers générés

- `notes/lecture-claude.md` — L’analyse vidéo de Claude en six parties
- `notes/lecture-gemini.md` — Les deux analyses indépendantes de Gemini, si disponible
- `notes/SPEC.md` — La spécification croisée et les questions ouvertes
- La skill créée dans le répertoire de sortie choisi

## Organisation du dépôt

- `README.md` — Page d’accueil du projet en anglais
- `README.<locale>.md` — Pages traduites identifiées par leur code de langue
- `SKILL.md` — Copie de référence de la skill à la racine du dépôt
- `.claude/skills/youtube-vers-agent/SKILL.md` — Copie installable pour les skills du projet Claude Code, synchronisée avec celle de la racine

## Licence

Ce projet est distribué sous licence MIT. Voir LICENSE.
