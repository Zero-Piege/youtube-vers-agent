<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>Transforme tutoriais do YouTube em skills claras e verificadas para o Claude Code.</strong></p>

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

Informe um link do YouTube e um objetivo. A skill analisa o vídeo de forma independente com Claude e Gemini, reúne os resultados em notes/SPEC.md e cria e valida uma skill reutilizável para o Claude Code. O Gemini é opcional; sem ele, o resultado é identificado como baseado em uma única fonte.

## Como funciona

1. **Defina o pedido** — esclareça o que extrair do vídeo e o que criar. Para vídeos com mais de 20 minutos, escolha um trecho específico se for útil.
2. **Análise com Claude** — use o mecanismo local do watch:watch e salve a especificação de seis partes em notes/lecture-claude.md.
3. **Análise independente com Gemini** — repita a análise duas vezes sem mostrar as anotações do Claude e salve as duas respostas em notes/lecture-gemini.md. Se o Gemini não estiver disponível, continue só com Claude e marque o resultado como fonte única.
4. **Cruze os resultados** — classifique cada item em notes/SPEC.md como CONFIRMED, UNE SOURCE ou DÉSACCORD. Revise os quadros do vídeo para resolver divergências e preserve comandos, nomes de pacotes, configurações e mensagens de erro exatos.
5. **Crie e valide** — passe a especificação ao skill-creator, gere a skill e execute-a em um caso real.

## Requisitos

- Claude Code
- A skill watch:watch para analisar vídeos do YouTube
- A skill skill-creator para criar o resultado
- Acesso ao Gemini (opcional; o fluxo também funciona só com Claude)

## Instalação

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Depois, execute /reload-plugins no Claude Code para recarregar os plugins.

## Uso

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "o projeto inteiro" "uma skill do Claude Code"
```

## Arquivos gerados

- `notes/lecture-claude.md` — Análise do vídeo em seis partes feita pelo Claude
- `notes/lecture-gemini.md` — Duas análises independentes do Gemini, quando disponível
- `notes/SPEC.md` — Especificação cruzada e perguntas em aberto
- Skill gerada no diretório de saída escolhido

## Estrutura do repositório

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

## Licença

Este projeto é distribuído sob a licença MIT. Consulte LICENSE.
