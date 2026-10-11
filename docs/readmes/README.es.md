<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Convierte tutoriales de YouTube en skills claras y verificadas para Claude Code.</strong></p>

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

Proporciona un enlace de YouTube y un objetivo. La skill analiza el vídeo de forma independiente con Claude y Gemini, reúne los resultados en notes/SPEC.md y crea y valida una skill reutilizable para Claude Code. Gemini es opcional; si no está disponible, el resultado se marca como de una sola fuente.

## Cómo funciona

1. **Definir la petición** — aclarar qué extraer del vídeo y qué construir. En vídeos de más de 20 minutos, se puede elegir un segmento.
2. **Análisis con Claude** — usar el motor local de watch:watch y guardar la especificación de seis partes en notes/lecture-claude.md.
3. **Análisis independiente con Gemini** — repetir el análisis dos veces sin mostrar las notas de Claude y guardar ambas respuestas en notes/lecture-gemini.md. Si Gemini no está disponible, continuar solo con Claude y marcar el resultado como de una sola fuente.
4. **Contrastar los resultados** — etiquetar cada elemento de notes/SPEC.md como CONFIRMED, UNE SOURCE o DÉSACCORD. Revisar fotogramas para resolver desacuerdos y conservar comandos, nombres de paquetes, ajustes y mensajes de error exactos.
5. **Crear y validar** — entregar la especificación a skill-creator, generar la skill y ejecutarla en un caso real.

## Requisitos

- Claude Code
- La skill watch:watch para analizar vídeos de YouTube
- La skill skill-creator para crear el resultado
- Acceso a Gemini (opcional; el flujo permite continuar solo con Claude)

## Instalación

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Después, ejecuta /reload-plugins en Claude Code para volver a cargar los plugins.

## Uso

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "todo el proyecto" "una skill de Claude Code"
```

## Archivos generados

- `notes/lecture-claude.md` — Análisis del vídeo en seis partes de Claude
- `notes/lecture-gemini.md` — Dos análisis independientes de Gemini, si está disponible
- `notes/SPEC.md` — Especificación contrastada y preguntas pendientes
- Skill generada en el directorio de salida elegido

## Estructura del repositorio

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

## Licencia

Este proyecto se distribuye con la licencia MIT. Consulta LICENSE.
