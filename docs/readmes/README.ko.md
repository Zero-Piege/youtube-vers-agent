<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>YouTube 튜토리얼을 명확하고 검증 가능한 Claude Code 스킬로 바꿉니다.</strong></p>

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

YouTube 링크와 목표를 제공하면 Claude와 Gemini가 영상을 각각 독립적으로 분석하고 결과를 notes/SPEC.md에 정리합니다. 이를 바탕으로 재사용 가능한 Claude Code 스킬을 만들고 검증합니다. Gemini는 선택 사항이며, 사용할 수 없으면 단일 출처로 표시합니다.

## 작업 흐름

1. **요청 구체화** — 영상에서 무엇을 추출하고 무엇을 만들지 확인합니다. 20분이 넘는 영상은 필요한 구간을 지정할 수 있습니다.
2. **Claude 분석** — watch:watch의 로컬 엔진을 사용하고 6개 항목의 사양을 notes/lecture-claude.md에 저장합니다.
3. **Gemini 독립 분석** — Claude 메모를 공유하지 않고 같은 분석을 두 번 수행한 뒤 두 결과를 notes/lecture-gemini.md에 저장합니다. Gemini를 사용할 수 없으면 Claude만으로 진행하고 단일 출처라고 표시합니다.
4. **결과 교차 검토** — notes/SPEC.md의 각 항목을 CONFIRMED, UNE SOURCE, DÉSACCORD로 표시합니다. 불일치는 영상 프레임을 다시 확인하고 정확한 명령어, 패키지명, 설정, 오류 메시지를 보존합니다.
5. **생성 및 검증** — 사양을 skill-creator에 전달해 스킬을 만들고 실제 사례에서 실행합니다.

## 필수 항목

- Claude Code
- YouTube 영상 분석용 watch:watch 스킬
- 결과 생성을 위한 skill-creator 스킬
- Gemini 접근 권한(선택 사항, Claude만 사용하는 대체 흐름 지원)

## 설치

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

그런 다음 Claude Code에서 /reload-plugins를 실행해 플러그인을 다시 불러옵니다.

## 사용법

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "전체 프로젝트" "Claude Code 스킬"
```

## 생성 파일

- `notes/lecture-claude.md` — Claude의 6개 항목 영상 분석
- `notes/lecture-gemini.md` — 가능한 경우 Gemini의 독립 분석 2회
- `notes/SPEC.md` — 교차 검토된 사양과 미해결 질문
- 선택한 출력 디렉터리에 생성된 스킬

## 저장소 구성

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## 라이선스

이 프로젝트는 MIT 라이선스로 배포됩니다. LICENSE를 확인하세요.
