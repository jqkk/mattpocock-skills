## 무엇을 하나

`grill-with-docs` 는 당신과 [에이전트](https://www.aihero.dev/ai-coding-dictionary/agent)가 하나의 이해를 공유할 때까지 계획이나 설계에 대해 당신을 인터뷰하고, 그러는 동안 어휘와 어려운 결정들을 당신 레포에 기록합니다. [grill-me](https://aihero.dev/skills-grill-me) 가 돌리는 것과 같은 인터뷰(질문 한 묶음, 기다림, 다음 묶음)를 코드베이스를 향해 돌리는 것입니다.

이것은 **[상태를 가집니다](https://www.aihero.dev/ai-coding-dictionary/stateful)**. 다른 모든 캐묻기 스킬은 [세션](https://www.aihero.dev/ai-coding-dictionary/session)을 당신 머릿속에 남기지만, 이것은 디스크에 파일을 남깁니다. 용어가 정리되면 끝에 몰아서가 아니라 정리되는 그 순간 `CONTEXT.md` 에 들어갑니다. 결정이 세 관문을 통과하면 ADR 로 들어갑니다. 차이는 그것이 전부이고, 사람들이 이 스킬에서 겪는 문제 대부분의 출처이기도 합니다. 산출물이 진짜 레포 안의 진짜 파일이라서, 기대한 자리에 없을 수도 있고 여러 사람이 쓰면 어긋날 수도 있습니다.

## 언제 꺼내 쓰나

`/grill-with-docs` 라고 직접 쳐서 부릅니다. 에이전트가 알아서 꺼내 쓰지 않습니다.

레포 안에서, 변경 작업의 시작에, 계획이 아직 흐릿하고 그것을 부를 낱말이 정해지지 않았을 때 꺼내십시오. 한 세션짜리 도구입니다. 어느 캐묻기 스킬을 원하는지는 앞에 놓인 것에 달렸습니다.

| 당신이 가진 것 | 꺼낼 것 |
| --- | --- |
| 애초에 작업 디렉터리 안에서 일하고 있지 않음 | [grill-me](https://aihero.dev/skills-grill-me) |
| 레포가 있고, 한 세션에 정리할 수 있는 변경 | `grill-with-docs` |
| 한 세션에 담기에는 너무 큰 일 (새로 만드는 빌드, 큰 기능) | [wayfinder](https://aihero.dev/skills-wayfinder) |
| 도메인 문서가 전혀 없는 레포, 특정 기능도 정해지지 않음 | `grill-with-docs`. 변경이 아니라 레포 자체를 겨냥합니다 |
| 남의 머릿속 지식에 막혀 있는 결정 | [to-questionnaire](https://aihero.dev/skills-to-questionnaire) |

wayfinder 와의 갈림은 세션 수로 결정됩니다. 한 세션 계획이면 `/grill-with-docs`, 여러 세션 계획이면 `/wayfinder`.

## 사전 조건

이 스킬은 당신 레포에 쓰므로, 써도 안전한 곳에 있어야 합니다. 정리된 용어는 루트의 `CONTEXT.md` 용어집으로 가거나, 루트의 `CONTEXT-MAP.md` 가 레포를 다중 컨텍스트로 표시하고 있다면 해당 컨텍스트의 `CONTEXT.md` 로 갑니다. 결정은 `docs/adr/` 로 갑니다. 둘 다 필요할 때 만들어집니다. 첫 용어나 첫 결정이 굳어지기 전까지는 아무것도 존재하지 않으므로 미리 틀을 잡아둘 것이 없습니다.

다른 스킬 둘도 있어야 합니다. 자기 `SKILL.md` 가 그 둘에 위임하는 한 줄이기 때문입니다. [grilling](https://aihero.dev/skills-grilling) 이 인터뷰를 공급하고, [domain-modeling](https://aihero.dev/skills-domain-modeling) 이 기록을 공급합니다. `grill-with-docs` 만 설치하면 동작하지 않는 스킬을 갖게 됩니다.

## 남는 기록

세션에서 세 가지가 나오는데, 동등하지 않습니다.

| 무엇이 정리됐나 | 어디로 가나 |
| --- | --- |
| 용어: 어떤 것을 부르는 이 프로젝트만의 낱말 | `CONTEXT.md`, 그때그때, 정리되는 순간 |
| 되돌리기 어렵고, 맥락 없이는 의외이고, 실제 절충인 결정 | `docs/adr/` 아래의 ADR |
| 당신이 결정한 나머지 전부 | 대화, 그리고 그 외 어디에도 없음 |

사람들이 걸려 넘어지는 것은 세 번째 행입니다. `CONTEXT.md` 는 용어집이고 의도적으로 그렇게 유지됩니다. 구현 세부도, [스펙](https://www.aihero.dev/ai-coding-dictionary/spec)도, 메모도 없습니다. ADR 은 세 조건을 동시에 요구하므로 대부분의 결정은 자격이 없고 대부분의 세션은 ADR 을 하나도 만들지 않습니다. 더 날카로워진 용어집과 ADR 0개를 내놓은 세션은 설계대로 동작한 것이지만, 동의한 내용의 대부분이 동의한 그 [컨텍스트 윈도](https://www.aihero.dev/ai-coding-dictionary/context-window) 안에만 존재한다는 뜻이기도 합니다. 그 대화를 [비우지](https://www.aihero.dev/ai-coding-dictionary/clearing) 말고 그대로 [to-spec](https://aihero.dev/skills-to-spec) 에 넘기십시오.

용어집이 핵심입니다. 도메인 언어가 이 스킬이 실제로 만들고 있는 것입니다. 한 번 합의된 프로젝트 자신의 낱말이 있으면 당신과 에이전트와 동료들이 그것을 매번 다시 끌어내는 비용을 치르지 않습니다. 이것이 에이전트 성능을 사준다는 데 모두가 동의하지는 않는다는 점은 말해둘 만합니다. 가장 날카로운 공개 반론은, 용어와 그것을 풀어 쓴 평범한 문장이 [모델](https://www.aihero.dev/ai-coding-dictionary/model)에게서 같은 결과를 끌어내며, 어휘가 실제로 압축하는 것은 그것을 공유하는 사람들 사이의 소통이라는 것입니다. 그 관점에서도 용어집은 여전히 가치가 있습니다. 가치의 위치가 옮겨질 뿐입니다.

## 자주 나오는 질문

**이걸 쓸까요, `/wayfinder` 를 쓸까요?**
범위가 결정합니다. 한 세션에 정리할 수 있는 것에는 이것을 쓰고, 한 세션에 담기에 너무 큰 일에는 [wayfinder](https://aihero.dev/skills-wayfinder) 를 쓰십시오. 그쪽은 일을 먼저 결정 [티켓](https://www.aihero.dev/ai-coding-dictionary/ticket)들의 지도로 그립니다. wayfinder 는 더 느리고 빽빽하며, 범위가 잘 잡힌 기능에 그것을 꺼내는 것이 흔한 실수입니다. 이 스킬을 대체하지 않습니다. 지도에서 한 세션에 어울리는 부분에 대해서는 캐묻기 세션으로 내려올 수 있습니다.

**돌렸는데 `CONTEXT.md` 도 ADR 도 안 생겼습니다.**
알려진 원인이 둘입니다. 평범한 쪽은 자격을 갖춘 것이 없었다는 것입니다. ADR 은 세 관문을 전부 요구하고, 새 어휘가 없는 변경에 대한 세션은 정말로 쓸 것이 없습니다. 진짜 버그 쪽은, 이 스킬이 다른 조율 계층 안에서 돌 때(스펙 주도 개발 래퍼, 다중 에이전트 프레임워크, 남의 파이프라인에서 한 단계로 이것을 부르는 규칙) 인터뷰는 돌아가는데 파일을 쓰는 절반이 조용히 일어나지 않는다고 보고된 것입니다. 접수됐고 안 고쳐졌습니다. 그런 구성에 있다면 세션 출력을 믿기 전에 작업 디렉터리를 확인하십시오.

**추천도 없이 전부 한꺼번에 물어봤고 `CONTEXT.md` 는 언급조차 안 했습니다.**
의존 스킬 둘을 불러오지 못한 것입니다. `SKILL.md` 가 한 줄짜리 위임이라서, [grilling](https://aihero.dev/skills-grilling) 과 [domain-modeling](https://aihero.dev/skills-domain-modeling) 을 집어 들지 못한 에이전트는 캐묻기가 뭔지 추측하게 되고, 구분 없는 질문 더미가 나옵니다. 더 헷갈리는 경우는 부분적으로만 불러온 것입니다. `grilling` 은 불러왔는데 `domain-modeling` 은 아니면, 좋은 인터뷰를 받고 기록은 하나도 남지 않습니다. 모델과 [노력](https://www.aihero.dev/ai-coding-dictionary/effort) 수준에 따라 달라지고, 이 스킬에서 가장 많이 보고된 문제입니다. 의심되면 에이전트에게 어떤 스킬을 불러왔는지 직접 물어보십시오.

**제가 내린 다른 결정들은 다 어디 갔나요?**
대화 안에만 있습니다. 이 스킬에 대한 가장 본질적인 열린 불만입니다. 용어집은 스펙이 아니고, 대부분의 답은 ADR 자격이 없으며, 정리된 각 답을 스펙과 티켓과 테스트까지 이어주는 장부가 없습니다. 정확한 답(순서 보장, 하지 말아야 할 요구사항, 숫자 기본값)이 하류로 가면서 더 약한 문장으로 뭉개지고, 결과물은 당신이 실제로 결정한 것을 빠뜨린 채 완성돼 보일 수 있습니다. 오늘 쓸 수 있는 완화책은 세션을 그대로 유지해 [to-spec](https://aihero.dev/skills-to-spec) 에 바로 먹이는 것, 그리고 스펙이 당신의 답을 담았으리라 가정하지 말고 당신의 답과 대조해 다시 읽는 것입니다.

**문서가 전혀 없는 기존 레포에 이걸 써도 되나요?**
됩니다. ADR 도 도메인 언어도 설계 원칙도 없는 코드베이스에 맞는 스킬입니다. 불러서 "내 레포를 문서화하도록 도와줘" 라고 하십시오. 커뮤니티에서 많이 쓰는 방식은 `CONTEXT.md` 를 만들거나 고치기 위해 [improve-codebase-architecture](https://aihero.dev/skills-improve-codebase-architecture) 와 짝지어 쓰는 것입니다. 방향을 잡아줘야 한다고 예상하십시오. 코드를 읽고 발견한 것에 대해 물어볼 텐데, 코드베이스에 이미 있는 낱말 중 어느 것이 맞는지 말하는 사람은 당신입니다.

**세션이 끝나면 뭘 해야 하나요?**
이 스킬의 마무리 메시지는 열린 결말인 경향이 있고, 알려진 거친 부분입니다. 주 흐름에서의 답은 같은 대화 안에서 [to-spec](https://aihero.dev/skills-to-spec) 입니다. 변경이 곧바로 만들 만큼 작다면 대신 [implement](https://aihero.dev/skills-implement) 로 바로 가십시오.

**왜 이런 이름인가요?**
이 이름에 만족하는 사람은 없습니다. 동작을 더 정직하게 서술하는 `grill-domain-model` 로 바꾸자는 열린 제안이 있습니다. 진척된 것은 없습니다. 언젠가 이름이 바뀌면 문서 페이지도 따라 옮겨가고 URL 도 바뀝니다.

## 제대로 동작하고 있다는 신호

- `CONTEXT.md` 가 끝에 한 덩어리로 나타나는 대신 세션 *도중에* 용어 하나씩 바뀝니다.
- 용어집이 순수한 어휘(당신 프로젝트의 낱말과 빡빡한 정의)로 읽히고, 구현 세부나 스펙 같은 문장이 들어 있지 않습니다.
- 코드베이스가 답할 수 있는 질문은 당신에게 묻지 않고 코드베이스를 읽어서 답합니다.
- ADR 이 거의 또는 전혀 안 나오고, 나온 것들은 다시 논쟁하게 되면 짜증이 날 만한 결정들입니다.
- 당신이 쓴 낱말을 기존 용어집이 다르게 정의하고 있다는 이유로 이의를 제기합니다.

## 전체에서 어디에 있나

`grill-with-docs` 는 주 빌드 사슬의 맨 앞입니다.

```txt
grill-with-docs → to-spec → to-tickets → implement → code-review
```

무언가가 스펙으로 적히기 전에 옵니다. 공유된 이해와 정해진 어휘를 만들어내고, [to-spec](https://aihero.dev/skills-to-spec) 이 당신을 다시 인터뷰하지 않고 그것을 종합합니다. 가까운 이웃은 레포도 파일도 없이 같은 인터뷰를 하는 [grill-me](https://aihero.dev/skills-grill-me), 그리고 이 스킬이 굴리는 용어집과 ADR 규율인 [domain-modeling](https://aihero.dev/skills-domain-modeling) 입니다. 둘 다 [grilling](https://aihero.dev/skills-grilling) 이라는 기본 단위 위에 놓여 있습니다. 상류에는 [wayfinder](https://aihero.dev/skills-wayfinder) 가 한 세션에 담기에 너무 큰 일을 지도로 그리고, 지도의 일부를 이 스킬에 내려보낼 수 있습니다. 어떤 스킬이나 흐름이 맞는지 모르겠으면 [ask-matt](https://aihero.dev/skills-ask-matt) 가 안내합니다.
