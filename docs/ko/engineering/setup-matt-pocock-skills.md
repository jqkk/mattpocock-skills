## 무엇을 하나

`setup-matt-pocock-skills` 는 레포 하나에 대해 세 가지 질문에 답합니다. 이슈가 어디에 사는가, 분류 라벨은 뭐라고 부르는가, 도메인 문서는 어디에 앉는가. 그 답들을 `docs/agents/` 아래 마크다운 파일로 기록합니다.

레포마다 달라지는 것은 그 파일들뿐입니다. 스킬 자체는 어디서나 동일합니다. 실행할 때 `docs/agents/issue-tracker.md` 를 읽고 거기 적힌 대로 합니다. 그래서 이 묶음이 GitHub 에 묶여 있지 않고, 다른 곳을 가리키게 하려고 스킬 파일을 고칠 일이 없습니다. "스킬들을 우리 이슈 트래커에 연결해줘" 라고 불러도, 프로그래밍으로 연결할 수 있는 것이라면 무엇이든 스킬 변경 없이 동작합니다.

이것은 프롬프트로 굴러가는 스킬이지 결정론적 스크립트가 아닙니다. 당신의 `git remote`, 기존 `CLAUDE.md`, 기존 `CONTEXT.md` 를 읽고, 발견한 것을 제안하고, 무언가를 쓰기 전에 당신의 확인을 기다립니다.

## 언제 꺼내 쓰나

`/setup-matt-pocock-skills` 라고 직접 쳐서 부릅니다. [에이전트](https://www.aihero.dev/ai-coding-dictionary/agent)가 알아서 꺼내 쓰지 않습니다. 의도적으로 호출 불가로 표시되어 있어서 다른 스킬도 대신 부를 수 없습니다.

레포당 한 번, 다른 엔지니어링 스킬을 처음 쓰기 전에 꺼내십시오. [triage](https://aihero.dev/skills-triage), [to-spec](https://aihero.dev/skills-to-spec), [to-tickets](https://aihero.dev/skills-to-tickets), [wayfinder](https://aihero.dev/skills-wayfinder) 가 이슈가 어디로 가는지 추측하기 시작하거나 트래커에 없는 라벨을 붙인다면, 여기서 설정이 안 된 것입니다. 프로젝트가 절반쯤 진행된 레포도 돌리기 좋은 자리입니다. 이 스킬은 이미 있는 것을 읽고, 앞서 한 작업은 하나도 낭비되지 않습니다.

## 사전 조건

돌리는 레포 안에 씁니다.

| 쓰는 것 | 위치 |
| --- | --- |
| `issue-tracker.md` | `docs/agents/` |
| `domain.md` | `docs/agents/` |
| `triage-labels.md` | `docs/agents/`, `triage` 스킬이 설치된 경우에만 |
| `## Agent skills` 블록 | `CLAUDE.md` / `AGENTS.md` 중 이미 존재하는 쪽 |

전부 커밋되는 마크다운입니다. 사용자 수준이나 전역 모드는 없습니다. 설정이 레포 안에 살기 때문에 레포마다 자기 사본을 갖습니다.

## 세 가지 결정

각 항목을 권장 답으로 먼저 제시하고, 탐색으로 이미 정해진 것은 건너뜁니다. 대부분의 실행은 확인 두 번이면 끝납니다.

| 결정 | 무엇을 제안하나 | 실제로 언제 묻나 |
| --- | --- | --- |
| **이슈 트래커** | 당신의 `git remote` 에 맞는 것 | 항상. 이것이 유일한 진짜 선택입니다 |
| **분류 라벨** | 표준 이름 다섯 개 유지 (`needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`) | `triage` 스킬이 설치된 경우에만 |
| **도메인 문서** | 단일 컨텍스트: 루트에 `CONTEXT.md` 하나와 `docs/adr/` | 모노레포 신호를 발견했을 때만. 그때는 다중 컨텍스트 `CONTEXT-MAP.md` 를 제안합니다 |

트래커 선택지입니다.

| 선택지 | 이슈가 사는 곳 | 필요한 것 |
| --- | --- | --- |
| **GitHub** | 레포의 GitHub Issues | `gh` CLI |
| **GitLab** | 레포의 GitLab Issues | `glab` CLI |
| **로컬 마크다운** | 이 레포의 `.scratch/<기능>/` 아래 파일 | 없음. 원격 저장소 자체가 필요 없습니다 |
| **기타** | 당신이 말하는 곳 | 작업 방식을 서술한 당신의 한 문단 |

앞의 셋은 스킬에 템플릿으로 실려 있어서 그대로 동작합니다. 로컬 마크다운은 차선책이 아니라 일급 선택지입니다. 원격 저장소가 없는 1인 프로젝트도 완전히 지원됩니다. 되풀이할 만한 단서가 하나 있습니다. GitHub 를 쓰고 있다면 로컬 마크다운을 쓰지 마십시오. 둘은 겹쳐 쓰는 층이 아니라 대안입니다.

"기타" 도 껍데기가 아닙니다. Jira, Linear, Azure DevOps, Beads 가 모두 동작하는 이유가 그것입니다. 당신이 작업 방식을 서술하면, 스킬이 그 문장을 `docs/agents/issue-tracker.md` 에 기록하고, 하류 스킬들이 그 문장을 따릅니다. 커뮤니티는 이미 이렇게 해왔습니다. [MCP](https://www.aihero.dev/ai-coding-dictionary/mcp) 위의 Jira 변형, `gh` 처럼 생긴 Gitea CLI, 손으로 만든 로컬 대시보드 같은 것들입니다.

## 자주 나오는 질문

**꼭 GitHub 를 써야 하나요?**

아닙니다. GitHub, GitLab, `.scratch/` 아래 로컬 마크다운이 전부 완성된 템플릿으로 실려 나오고, 나머지는 "기타" 경로로 동작합니다. 기록에서 가장 많이 반복된 질문이고, 대략 이런 말들이었습니다. *"깃허브에 꽉 묶여 있음"*, *"GitLab / Jira 써도 되나"*, *"Azure DevOps 는?"*. 매번의 답은 트래커가 스킬의 성질이 아니라 설정에서의 답이라는 것입니다.

**스킬을 업데이트한 뒤에 다시 돌려야 하나요?**

v1.1 직후 직접 물었을 때의 답은 "예" 였습니다. 스킬 자신의 마무리 메시지는 더 부드럽습니다. 트래커를 바꾸거나 처음부터 다시 할 때만 다시 돌리면 된다고 말합니다. 둘 다 근거가 있고 차이가 나는 이유도 실재합니다. 씨앗 템플릿이 버전 사이에 바뀌므로, 옛 릴리스가 쓴 `docs/agents/issue-tracker.md` 는 지금 그것을 읽는 스킬들에 대해 낡아질 수 있습니다. 하류 스킬이 문서가 다르게 설명하는 동작을 하기 시작한다면, 다시 돌리는 것이 싼 해결책입니다.

**`CLAUDE.md` 에 썼는데 저는 Codex 를 씁니다.**

알려진 구멍이고 아직 열려 있습니다. 파일 선택 규칙이 "`CLAUDE.md` 가 있으면 그것을, 없으면 `AGENTS.md` 를 고친다" 입니다. 어떤 [하네스](https://www.aihero.dev/ai-coding-dictionary/harness)가 돌고 있는지가 아니라 어떤 파일이 있는지를 봅니다. Claude Code 에서 남은 `CLAUDE.md` 가 있는 레포는 Codex 가 절대 읽지 않는 곳에 `## Agent skills` 블록을 받게 됩니다. 우회책 둘이 돌아다닙니다. 블록을 손으로 `AGENTS.md` 로 옮기거나, `AGENTS.md` 를 정본으로 두고 `CLAUDE.md` 를 그것을 가리키는 한 줄로 만드는 것입니다. 두 파일이 다 없으면 스킬이 고르지 않고 어느 것을 만들지 묻는데, 알아서 정할 줄 알았던 사람들이 여기서 헷갈렸습니다.

**분류 라벨을 만들어주지 않았습니다.**

만들지 않습니다. `docs/agents/triage-labels.md` 는 *대응표*입니다. 당신 트래커의 어떤 문자열이 표준 역할 다섯에 대응하는지를 `/triage` 에게 알려줍니다. `gh label create` 를 돌리지 않습니다. 새 GitHub 레포에서는 라벨이 정말로 아직 없고, 이것은 여러 번 버그로 접수됐습니다. 이어지는 두 가지입니다.

- 당신 트래커가 이미 표준 이름을 쓰고 있다면 그 대응표는 항등표이고 설정할 것이 없습니다. 빠진 단계가 아니라 의도된 일반적인 경우입니다.
- [wayfinder](https://aihero.dev/skills-wayfinder) 의 `wayfinder:map` 과 `wayfinder:<유형>` 라벨도 여기서 만들어지지 않고, `gh issue create --label <없는것>` 은 라벨을 만들지 않고 그대로 실패합니다. GitHub 레포에서 wayfinder 를 처음 돌리기 전에 손으로 만드십시오.

**다른 스킬들의 동작([캐묻기](https://www.aihero.dev/ai-coding-dictionary/grilling) 빈도, 질문 형식, 말투)을 여기서 설정할 수 있나요?**

아닙니다. 세 가지만 설정합니다. 트래커, 라벨, 문서 배치. 사용자별 선호의 보금자리로 만들어달라는 직접적인 요청이 있었고, 한결같은 답은 스킬이 의견을 고수한다는 것입니다. *"설정은 죽음이다."* 선호는 모든 스킬이 이미 읽는 당신의 `CLAUDE.md` 에 평범한 지시로 넣으십시오.

**레포마다 커밋하지 말고 `~/.claude` 에 설정을 둘 수 있나요?**

오늘은 안 됩니다. 여러 레포에 걸쳐 이 스킬들을 쓰는 사람이 정확히 이것을 요청한 열린 이슈가 있고, 사용자 수준 모드는 없습니다. 레포마다 자기 `docs/agents/` 를 지닙니다.

**다른 스킬을 설정하는 스킬이라니 이상하지 않나요?**

오래된 불만 하나가 그렇다고 말합니다. *"다른 스킬을 설정하는 스킬을 두는 건 내게 맞게 느껴지지 않는다. LLM 이 자기 스킬을 설정한다는 뜻이니까."* 절충은 실재하고 인정된 것입니다. 설정 단계의 대안은 이슈를 건드리는 모든 스킬에 트래커 지시를 복제해 넣는 것입니다. 산출물이 들여다보고 고칠 수 있는 마크다운이라는 점이 완화책입니다. 쓴 파일을 전부 읽고 손으로 바꿀 수 있고, 일상적인 손질은 바로 그것이지 다시 돌리는 것이 아닙니다.

## 제대로 동작하고 있다는 신호

- `docs/agents/issue-tracker.md` 와 `docs/agents/domain.md` 가 있고, `triage` 가 설치돼 있으면 `triage-labels.md` 도 있습니다.
- 당신 하네스가 실제로 읽는 지시 파일에 `## Agent skills` 절이 나타나고, 그 파일들 각각을 가리키는 한 줄 요약이 달려 있습니다.
- 제안한 트래커가 당신이 실제로 쓰는 원격 저장소와 맞고, 라벨 문자열이 트래커에 실제로 존재하는 라벨과 맞습니다.
- 그 뒤로 `/to-tickets` 가 이슈가 어디 사는지 묻지 않고 발행하고, `/triage` 가 라벨을 지어내지 않고 붙입니다.
- 스킬 파일 자체는 하나도 바뀌지 않았습니다. 설정이 `SKILL.md` 를 고쳤다면 뭔가 잘못된 것입니다.

## 전체에서 어디에 있나

`setup-matt-pocock-skills` 는 엔지니어링 흐름의 **한 번만 하는 설정**이고, 사슬의 한 단계가 아니라 나머지 전부가 전제하는 선행 조건입니다. 이웃은 이 파일들을 읽는 쪽들입니다. 여기 적힌 라벨 어휘를 적용하는 [triage](https://aihero.dev/skills-triage), 여기서 이름 붙인 트래커에 발행하는 [to-spec](https://aihero.dev/skills-to-spec) 과 [to-tickets](https://aihero.dev/skills-to-tickets), 그리고 지도와 자식 [티켓](https://www.aihero.dev/ai-coding-dictionary/ticket)이 어떻게 저장되는지 알기 위해 같은 트래커 파일의 "Wayfinding operations" 절을 읽는 [wayfinder](https://aihero.dev/skills-wayfinder) 입니다. 여기서 기록한 도메인 문서 배치는 나중에 [domain-modeling](https://aihero.dev/skills-domain-modeling) 이 채웁니다. 그쪽은 용어나 결정이 실제로 정리될 때 `CONTEXT.md` 와 ADR 을 필요에 따라 만들므로, 설정 직후 비어 있는 레포가 정상 상태입니다. 다음에 어떤 스킬을 꺼낼지는 [ask-matt](https://aihero.dev/skills-ask-matt) 이 전체 묶음을 안내합니다.
