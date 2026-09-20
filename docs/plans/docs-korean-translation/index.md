# docs 한국어 번역

## 요구사항

`docs/` 아래 25개 스킬 문서를 한국어로 옮깁니다.

- 배치: 원문 유지, `docs/ko/<bucket>/<skill>.md` 에 사본 생성
- 스킬 이름과 슬래시 명령어(`/tdd`, `to-spec`)는 영어 그대로
- 전문용어는 한국어 뒤 괄호로 영어 병기 (이음매(seam), 깊은 모듈(deep module))
- 링크는 원문 URL 유지 (aihero.dev, github.com)
- 표, 코드블록, 체크리스트 구조는 원문과 동일
- 제목은 한국어로 옮기되 원문과 1:1 대응 (대응표는 `docs/ko/README.md`)
- em-dash 금지 (레포 공통 규칙)

## 진행

### engineering (18)

- [x] tdd
- [x] ask-matt
- [x] code-review
- [x] codebase-design
- [x] diagnosing-bugs
- [x] domain-modeling
- [x] grill-with-docs
- [x] implement
- [x] improve-codebase-architecture
- [x] prototype
- [x] research
- [x] resolving-merge-conflicts
- [x] setup-matt-pocock-skills
- [x] to-spec
- [x] to-tickets
- [x] triage
- [x] wayfinder
- [x] wizard

### productivity (7)

- [x] grill-me
- [x] grilling
- [x] handoff
- [x] teach
- [x] to-questionnaire
- [x] wait-what
- [x] writing-for-agents

### 마무리

- [x] `docs/ko/README.md` (제목 대응표 + 갱신 규칙)

## 열린 질문

- `docs/ko/` 를 레포 `CLAUDE.md` 의 구조 규칙에 추가할지. 추가하면 스킬이 바뀔 때 두 벌을 갱신하라는 지시가 명문화됩니다. 아직 사용자 확인 전.
