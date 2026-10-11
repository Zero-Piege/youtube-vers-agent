# youtube-vers-agent

로컬 Claude + Gemini를 통한 이중 소스 검증 및 사양 교차 참조를 통해 YouTube 튜토리얼을 Claude Code 스킬로 변환하는 Claude Code 스킬입니다.

## 설명

이 스킬은 다음을 통해 YouTube 튜토리얼 콘텐츠를 구조화된 Claude Code 스킬로 변환합니다:
1. 비디오 트랜스크립트에서 주요 개념 및 절차 추출
2. 이중 소스 검증(비디오 + 문서)을 통한 정보 검증
3. Claude Code 관례를 따른 올바르게 형식화된 SKILL.md 파일 생성
4. 참조 교차 참조를 통한 정확성 및 완전성 보장

## 언제 사용해야 하는가

다음과 같은 경우 이 스킬을 사용합니다:
- 교육용 YouTube 콘텐츠를 재사용 가능한 Claude Code 스킬로 변환
- 개발 도구, 프레임워크 또는 방법론에 대한 튜토리얼 비디오를 기반으로 스킬 생성
- 공식 문서와의 대조를 통한 스킬 정확성 보장
- 비디오 학습 리소스에서 검증된 스킬 라이브러리 구축

## 스킬 워크플로우

### 1. 비디오 분석 단계
- watch 스킬을 사용하여 YouTube 비디오를 처리하고 트랜스크립트 및 주요 프레임을 추출
- 비디오에서 제시된 주요 주제, 절차 및 코드 예시 식별
- 학습 목표 및 결과 구조화

### 2. 이중 소스 검증
- 각 주요 개념/절차에 대해 context7-mcp 또는 find-docs 스킬을 사용하여 공식 문서 참조
- 비디오 콘텐츠를 권위 있는 소스와 교차 참조
- 차이점 또는 버전 차이 기록
- 코드 예시가 시연대로 작동하는지 검증

### 3. 스킬 생성
- Claude Code 관례를 따른 올바르게 형식화된 SKILL.md 파일 생성
- 명확한 설명, 사용 지침 및 단계별 워크플로 포함
- 검증에 사용된 비디오 소스 및 문서 소스 참조
- 검증된 절차를 기반으로 적절한 도구 추천 추가

### 4. 품질 보증
- 언급된 코드 예시 또는 절차 테스트
- 스킬이 Claude Code 스킬 형식 표준을 따르는지 검증
- 스킬이 실행 가능하고 검증 가능한 지침을 제공하는지 확인

## 출력

적절한 .claude/skills/ 디렉토리에 완전한 SKILL.md 파일을 생성하며, 이 파일은:
- 스킬의 목적 및 적용성을 명확히 정의
- 특정 사용 지침 제공
- 검증 가능한 워크플로 개요
- 이중 소스 검증에 사용된 소스 참조
- Claude Code 스킬 관례 준수

## 필수 도구

- watch: YouTube 비디오 콘텐츠 처리용
- context7-mcp 또는 find-docs: 공식 문서에 대한 이중 소스 검증용
- Bash: 파일 작업 및 스킬 생성용

## 설치

1. 이 저장소를 클론:
   ```bash
   git clone https://github.com/Zero-Piege/youtube-vers-agent
   ```

2. 스킬을 Claude Code 스킬 디렉터리에 복사:
   ```bash
   cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
   ```

3. 플러그인 새로 고침:
   ```bash
   /reload-plugins
   ```

## 사용법

설치 후 YouTube URL을 제공하고 구축할 내용을 지정하여 스킬을 사용할 수 있습니다:

```
/youtube-vers-agent [YouTube URL] [추출할 내용] [구축할 내용]
```

예시:
```
/youtube-vers-agent https://youtu.be/zke3bTtvmLo 전체 프로젝트 Claude Code 스킬
```

## 사용 예시

React 컴포넌트 생성 YouTube 튜토리얼을 Claude Code 스킬로 변환:
1. watch 스킬을 사용하여 비디오 트랜스크립트 및 핵심 포인트 추출
2. context7-mcp를 사용하여 React 컴포넌트 생성 패턴을 공식 React 문서와 대조
3. Claude Code에서 React 컴포넌트 생성의 검증된 절차를 포함하는 SKILL.md 생성
4. 사용한 YouTube 튜토리얼 및 React 문서에 대한 참조 포함

## 검증 표준

생성된 모든 스킬은 다음을 충족해야 합니다:
- 최소 두 개의 독립적인 소스(비디오 + 문서)를 참조
- 구체적이고 실행 가능한 단계 포함
- 명확한 사용 지침 제공
- 확립된 Claude Code 스킬 형식 준수
- 테스트 가능한 검증된 절차 포함

## 라이선스

MIT 라이선스 - 세부 사항은 [LICENSE](LICENSE) 파일 참조