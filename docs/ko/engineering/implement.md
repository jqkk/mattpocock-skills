## 무엇을 하나

`implement` 는 이미 정해진 일을 만듭니다. [티켓](https://www.aihero.dev/ai-coding-dictionary/ticket), [스펙](https://www.aihero.dev/ai-coding-dictionary/spec), 또는 방금 대화에서 합의한 계획을 가리키면, 코드를 쓰고, 이음매에서 [tdd](https://aihero.dev/skills-tdd) 를 굴리고, 가면서 타입 검사를 하고, 끝에 [code-review](https://aihero.dev/skills-code-review) 를 돌리고, 현재 브랜치에 커밋합니다.

계획을 절대 다시 열지 않습니다. 인터뷰도, 확인 질문 묶음도, 다른 접근법 제안도 없습니다. 상류에서 정해진 것이 입력이고, 이 스킬의 일 전부는 그것을 커밋으로 바꾸는 것입니다. 새 [에이전트](https://www.aihero.dev/ai-coding-dictionary/agent)에게 "이거 만들어" 라고 치는 것과의 차이가 바로 이것입니다. 그쪽은 만들면서 일을 태연히 다시 설계합니다.

## 언제 꺼내 쓰나

`/implement` 라고 직접 쳐서 부릅니다. 에이전트가 알아서 꺼내 쓰지 않습니다. `disable-model-invocation: true` 를 달고 출시되므로 다른 스킬도 이것을 부를 수 없습니다. [ask-matt](https://aihero.dev/skills-ask-matt) 이나 [to-tickets](https://aihero.dev/skills-to-tickets) 가 "그다음 티켓마다 `/implement`" 라고 말하는 곳은 전부 당신에게 하는 지시이지 에이전트가 시키지 않아도 할 일이 아닙니다.

그 일이 지금 어디에 있느냐가 이 스킬이 맞는지를 정합니다.

| 일이 있는 곳 | 꺼낼 것 |
| --- | --- |
| 트래커 위의 티켓 | `/implement #42`. [세션](https://www.aihero.dev/ai-coding-dictionary/session) 하나에 티켓 하나, 티켓 사이에 컨텍스트 [비우기](https://www.aihero.dev/ai-coding-dictionary/clearing) |
| 아직 안 쪼갠 스펙이고, 빌드가 여러 세션에 걸침 | 먼저 [to-tickets](https://aihero.dev/skills-to-tickets), 그다음 티켓마다 `/implement` |
| 스펙이 있고, 빌드가 작음 | 스펙을 상대로 바로 `/implement` |
| 방금 나눈 대화 안에만 있고, 아직 작음 | 같은 창에서 바로 `/implement` |
| 아직 아무 데도 안 적힘 | [grill-with-docs](https://aihero.dev/skills-grill-with-docs), 코드베이스가 없으면 [grill-me](https://aihero.dev/skills-grill-me) |
| 스펙 없이 테스트 먼저 만들고 싶은 구체적 동작 하나 | [tdd](https://aihero.dev/skills-tdd) 를 바로 |
| 이미 만들었고 점검받고 싶음 | [code-review](https://aihero.dev/skills-code-review) 를 바로 |

같은 세션 안에서 쓰는 경우는 따로 짚을 만합니다. 스킬 자신의 첫 줄이 그걸 다루지 않기 때문입니다. `SKILL.md` 는 "스펙이나 티켓" 이라고 말하는데, 이 표현이 [모델](https://www.aihero.dev/ai-coding-dictionary/model)을 존재하지 않는 파일을 찾아 나서게 밀어냅니다. 계획이 스레드 안에만 있다면 부를 때 그렇다고 말하십시오.

## 사전 조건

`implement` 는 당신이 지금 서 있는 브랜치에 커밋합니다. 브랜치를 만들지 않고, 묻지도 않습니다. 시작 전에 작업을 올리고 싶은 브랜치에 있는지 확인하십시오.

티켓이 [to-tickets](https://aihero.dev/skills-to-tickets) 에서 왔다면, 그것들이 사는 트래커는 [setup-matt-pocock-skills](https://aihero.dev/skills-setup-matt-pocock-skills) 가 설정한 것입니다. `code-review` 는 마무리에서 출발점이 된 스펙을 찾을 때 같은 설정을 읽습니다.

## 한 번 돌리면 무슨 일이 일어나나

한 번의 실행은 순서대로 다섯 박자입니다.

1. 티켓이나 스펙을 읽고 이음매를 파악합니다.
2. 미리 합의된 이음매에서 [tdd](https://aihero.dev/skills-tdd) 를 굴립니다. 한 번에 빨강-초록 조각 하나씩.
3. 자주 타입 검사를 하고, 가면서 개별 테스트 파일을 돌립니다.
4. 끝에 전체 테스트 묶음을 한 번 돌립니다.
5. [code-review](https://aihero.dev/skills-code-review) 를 돌리고, 현재 브랜치에 커밋합니다.

한 번의 실행이 티켓 하나를 다룹니다. [to-tickets](https://aihero.dev/skills-to-tickets) 가 만드는 티켓은 새 [컨텍스트 윈도](https://www.aihero.dev/ai-coding-dictionary/context-window) 하나에 들어가도록 크기가 잡힌 예광탄 수직 조각이라서, 의도된 리듬은 이렇습니다. 컨텍스트를 비우고, 티켓 하나를 구현하고, 커밋하고, 다시 비운다. 각 티켓이 자족적이라는 점이 이전 티켓의 컨텍스트를 버려도 되게 만듭니다.

## 미리 합의된 이음매

이 스킬이 딛고 선 개념은 **이음매**입니다. 안쪽에 손을 넣지 않고 동작을 관찰하는 공개 경계죠. 테스트는 이음매에 삽니다. 코드가 써지기 전에 합의된 이음매에서 작업하는 것이 테스트를 오래가게 만듭니다. 그 아래 구현을 다시 써도 테스트가 움직이지 않기 때문입니다.

"미리 합의된" 이라는 말이 실제로 일을 하고 있고, 동시에 이 스킬의 가장 약한 관절이기도 합니다. `implement` 안에는 이음매를 합의하는 장치가 없습니다. 묻는 쪽은 `tdd` 이고, 확인되지 않은 이음매에는 테스트 쓰기를 거부합니다. 그래서 실제로는 합의가 상류의 스펙에서 일어나거나, 실행의 첫 주고받기에서 일어납니다. 어디에서도 일어나지 않으면 그 전제 조건은 아예 발동하지 않고, 실행은 조용히 "그냥 코드 쓰기" 가 됩니다. 스펙에 이음매를 이름으로 적어두는 것이 그것을 막습니다.

## 자주 나오는 질문

**끝났는데 티켓이 여전히 열려 있고 인수 조건도 체크가 안 돼 있습니다.**

맞고, 예상된 일입니다. `implement` 에는 완료 단계가 없습니다. 커밋에서 끝나고 작업 항목을 건드리지 않습니다. GitHub Issues 와 로컬 마크다운 트래커 양쪽에서 확인됐으므로 트래커 연동 문제가 아닙니다. `code-review` 가 내놓은 지적에 대해서도 조치하지 않고, 출발점이 된 이슈의 `- [ ]` 상자에 체크하지도 않습니다. 티켓을 닫고 조건을 맞추는 일은 당신이 하십시오. 의존 사슬에서 이게 가장 아프게 옵니다. `to-tickets` 가 "막는 것이 전부 닫힌 티켓" 을 다음 작업 전선으로 정의하기 때문입니다. 아무것도 닫히지 않으면 아무것도 눈에 띄게 풀리지 않습니다.

**티켓 전부를 한꺼번에 가리키거나, 여러 개를 병렬로 돌릴 수 있나요?**

아닙니다. 한 번 부르면 티켓 하나입니다. 티켓 대기열을 일괄 처리하는 것과 [서브에이전트](https://www.aihero.dev/ai-coding-dictionary/subagent)로 퍼뜨리는 것 둘 다 반복해서 요청됐지만 둘 다 없습니다. 하나의 체크아웃에서 `/implement` 세션 여러 개를 나란히 돌리는 것은 지원되지 않는 정도가 아니라 더 나쁩니다. 어떤 현장 보고는 한 세션의 `git commit --amend` 가 다른 세션의 커밋에 떨어지고, stash 가 `refs/stash` 에서 사라지고, 커밋이 엉뚱한 브랜치에 올라간 일이 세 이슈에 걸쳐 하루 오후에 전부 일어났다고 적고 있습니다. 세션들이 작업 디렉터리 하나, 인덱스 하나, HEAD 하나를 공유합니다. git worktree 가 커뮤니티의 우회책인데, `refs/stash` 는 worktree 사이에서도 공유되므로 worktree 만으로는 stash 문제가 해결되지 않는다는 점을 유념하십시오. 오늘 병렬성을 원한다면 직접 조립해야 합니다.

**커밋 대신 풀 리퀘스트를 열게 할 수 있나요?**

기본으로는 안 됩니다. 현재 브랜치에 바로 커밋하는데, 이걸 너무 성급하다고 느끼는 사람이 여럿입니다. 동작을 확인할 기회를 갖기 전에 코드가 들어가 버리니까요. 설정 플래그도 PR 모드도 없습니다. 사람들은 부를 때 말로 덮어쓰거나("브랜치에 커밋하고 PR 을 열어줘") 스킬의 로컬 사본을 고쳐서 처리합니다.

**`code-review` 가 제 변경을 못 본다고 합니다.**

`code-review` 는 `git diff <고정점>...HEAD` 를 검토하는데, 여기서 스테이징된 변경과 작업 트리 변경은 빠집니다. `implement` 는 커밋 전에 그것을 돌리므로, 중간 커밋이 이미 있지 않은 한 그 차이에 검토할 것이 없습니다. 여러 사람이 보고했고 양쪽 다 안 고쳐졌습니다. 먼저 커밋하고, 분기한 지점을 기준으로 검토하십시오.

별개로, 실행 안에 리뷰가 들어 있는 것 자체를 의도적으로 원치 않는 사람들도 있습니다. 방금 쓴 코드를 리뷰하는 에이전트는 자기 해법 쪽으로 편향되기 때문입니다. 깨끗한 세션에서 고정점을 기준으로 [code-review](https://aihero.dev/skills-code-review) 를 돌리는 것은 정당한 대안이고, 그 스킬이 두 축을 별개 서브에이전트에서 돌리는 것도 같은 이유입니다.

**티켓 하나에 토큰 15만 개를 태웠습니다. 잘못 쓰고 있는 건가요?**

스킬을 잘못 쓴 게 아니라 티켓이 너무 클 가능성이 높습니다. 한 번의 실행은 코드베이스 탐색, 이음매마다의 빨강-초록 루프, 전체 테스트 묶음, 리뷰를 합니다. 그래서 만만치 않은 티켓이 [토큰](https://www.aihero.dev/ai-coding-dictionary/token) 10만 개를 넘기는 것은 뭔가 고장 난 신호가 아니라 정상입니다. 손잡이는 상류에 있습니다. [to-tickets](https://aihero.dev/skills-to-tickets) 에서 각각이 새 윈도 하나에 들어가도록 티켓 크기를 알맞게 잡으십시오. 티켓 하나가 계속 터진다면 [노력](https://www.aihero.dev/ai-coding-dictionary/effort) 수준을 올리지 말고 쪼개십시오.

**새 세션에서 `/implement #2` 를 했더니 전혀 상관없는 걸 작업했습니다.**

`#2` 는 에이전트가 볼 수 있는 아무 번호 목록에 대고 해석됩니다. 새 세션에서는 설정된 트래커가 아니라 할 일 파일, 체크리스트, 또는 다른 작업 목록일 수 있습니다. 해석이 실패 시 멈추는 게 아니라 자신만만하게 진행되므로, 시작한 뒤에야 실수가 드러납니다. 전체 참조를 넘기십시오. 이슈 URL 이나 `owner/repo#2` 형태로 주고, 시작 전에 제목을 되읽어 확인해 달라고 하십시오.

## 제대로 동작하고 있다는 신호

- 세션이 무엇을 만들지 당신에게 묻는 대신, 티켓이나 스펙을 읽고 무엇을 만들지 되짚어 말하며 시작합니다.
- 기록에 실제 `/tdd` 호출이 보입니다. 차이에 테스트가 나타나는 것만으로는 부족합니다.
- 실행 중에 타입 검사와 개별 테스트 파일이 반복해서 돌고, 끝 무렵에 전체 묶음이 한 번 돕니다.
- 당신이 계속하라고 재촉하지 않아도 현재 브랜치의 커밋까지 도달합니다.
- 차이가 티켓 하나 분량입니다. 여러 티켓을 쓸어 담은 것이 아니라 모든 계층을 관통하는 수직 조각입니다.

## 전체에서 어디에 있나

`implement` 는 주 사슬의 빌드 단계이고 끝에서 두 번째입니다.

```txt
grill-with-docs → to-spec → to-tickets → implement → code-review
```

이웃은 이것이 소비할 티켓을 만들어내고 순서를 정하는 차단 관계를 선언하는 [to-tickets](https://aihero.dev/skills-to-tickets), 각 이음매에서 내부적으로 굴리는 [tdd](https://aihero.dev/skills-tdd), 그리고 커밋 전에 돌리는 [code-review](https://aihero.dev/skills-code-review) 입니다. 계획 스킬들의 하류에 앉아 그것들을 신뢰합니다. 건네받은 것의 모양을 다시 검증하지 않으므로, 구조가 엉망인 지도나 수평으로 쌓인 티켓은 적힌 그대로 만들어집니다.

그 신뢰 때문에 [wayfinder](https://aihero.dev/skills-wayfinder) 는 자기 지도를 `implement` 로 바로 흘려보내지 않고 [to-spec](https://aihero.dev/skills-to-spec) 에서 사슬에 합류합니다. 지도에서 곧장 `implement` 로 가는 것은 그 일이 실제로 작은 것으로 드러났을 때만 하십시오.

어느 흐름에 있는지 모르겠으면 [ask-matt](https://aihero.dev/skills-ask-matt) 이 전체 묶음 위의 길잡이입니다.
