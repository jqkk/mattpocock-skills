# 한국어 번역본

`docs/engineering/` 와 `docs/productivity/` 의 스킬 문서를 한국어로 옮긴 것입니다. 원문은 그대로 두고 여기에 사본을 둡니다.

- 원문: `docs/<버킷>/<스킬>.md` (aihero.dev 에 발행되는 정본)
- 번역: `docs/ko/<버킷>/<스킬>.md` (읽기용 사본, 발행되지 않음)

원문과 번역이 어긋나면 원문이 맞습니다. 스킬이 바뀌면 원문을 먼저 고치고 여기를 다시 맞추십시오.

## 번역 규칙

- 스킬 이름과 슬래시 명령어(`/tdd`, `to-spec`, `ready-for-agent`)는 영어 그대로 둡니다. 실제로 타이핑하거나 트래커에 들어가는 문자열이라 번역하면 동작하지 않습니다.
- 전문용어는 첫 등장에 한국어 뒤 괄호로 영어를 답니다. 이음매(seam), 깊은 모듈(deep module), 예광탄(tracer bullet). 두 번째부터는 한국어만 씁니다.
- 링크 주소는 원문 그대로입니다. aihero.dev 와 github.com 에 한국어 페이지가 없으므로 바꾸면 깨집니다.
- 표의 행 수, 코드블록, 체크리스트 형식은 원문과 동일합니다.
- em-dash 를 쓰지 않습니다 (레포 공통 규칙).

## 제목 대응표

원문의 고정 뼈대를 이렇게 옮겼습니다. 자유 형식 중간 절의 제목은 스킬마다 달라서 그때그때 옮겼습니다.

| 원문 | 번역 |
| --- | --- |
| `## What it does` | `## 무엇을 하나` |
| `## When to reach for it` | `## 언제 꺼내 쓰나` |
| `## Prerequisites` | `## 사전 조건` |
| `## Common questions` | `## 자주 나오는 질문` |
| `## It's working if` | `## 제대로 동작하고 있다는 신호` |
| `## Where it fits` | `## 전체에서 어디에 있나` |

## 목차

### engineering (18)

- [ask-matt](engineering/ask-matt.md)
- [code-review](engineering/code-review.md)
- [codebase-design](engineering/codebase-design.md)
- [diagnosing-bugs](engineering/diagnosing-bugs.md)
- [domain-modeling](engineering/domain-modeling.md)
- [grill-with-docs](engineering/grill-with-docs.md)
- [implement](engineering/implement.md)
- [improve-codebase-architecture](engineering/improve-codebase-architecture.md)
- [prototype](engineering/prototype.md)
- [research](engineering/research.md)
- [resolving-merge-conflicts](engineering/resolving-merge-conflicts.md)
- [setup-matt-pocock-skills](engineering/setup-matt-pocock-skills.md)
- [tdd](engineering/tdd.md)
- [to-spec](engineering/to-spec.md)
- [to-tickets](engineering/to-tickets.md)
- [triage](engineering/triage.md)
- [wayfinder](engineering/wayfinder.md)
- [wizard](engineering/wizard.md)

### productivity (7)

- [grill-me](productivity/grill-me.md)
- [grilling](productivity/grilling.md)
- [handoff](productivity/handoff.md)
- [teach](productivity/teach.md)
- [to-questionnaire](productivity/to-questionnaire.md)
- [wait-what](productivity/wait-what.md)
- [writing-for-agents](productivity/writing-for-agents.md)
