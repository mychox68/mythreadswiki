# OpenAI
> 관련 노트: 21개 | 마지막 갱신: 2026-07-13 09:06

## 개요

주요 키워드: **AI** · **새로운** · **OpenAI가** · **작업을** · **오픈AI가** · **GPT** · **Codex** · **OpenAI**

## 핵심 인사이트

- OpenAI가 Workspace Agents를 발표하여 팀 단위의 업무를 효율적으로 처리할 수 있는 새로운 AI 에이전트를 도입했다. 이 에이전트는 Slack과 통합되어 팀의 대화…
- Cursor API를 OpenAI/Anthropic 형식으로 변환해주는 프록시 cursor2api가 등장했다. Cursor 백엔드를 활용하면서 기존 OpenAI/Anthropic …
- OpenAI가 새로운 실시간 음성 모델 3개(GPT-Realtime-2, GPT-Realtime-Translate, GPT-Realtime-Whisper)를 발표했습니다. 이 모델…
- OpenAI가 GPT-5.4를 활용하여 웹사이트를 디자인하는 노하우를 공개했습니다. AI 모델은 학습 데이터의 일반적인 패턴을 따르므로, 구체적인 프롬프트를 사용하여 원하는 디자인…
- OpenAI의 코덱스(Codex)에 '레코드 & 리플레이(Record & Replay)' 기능이 추가되어, 사용자가 작업을 시연하면 AI가 이를 학습하여 반복 작업을 자동으로 수행…

## Agent Insight
- 03-27(Skills Catalog, 130개 서브에이전트, 하네스 엔지니어링)에서 04월(Workspace Agents, Privacy Filter, GPT-5.5) 다수 기능 출시를 거쳐 05-17(OpenAI Deployment Company로 기업 운영 재설계), 06-03(Codex Python SDK, 비개발자용 Sites 기능)까지 이어지는 흐름은 OpenAI가 '모델 제공사'에서 '기업 AI 인프라 회사'로 전략을 확장해온 궤적을 보여준다.
- 개발자 대상 확장(Skills Catalog, 서브에이전트, Python SDK)과 비개발자 대상 노코드 확장(Sites, Workspace Agents)이 같은 시기 나란히 진행되는 것은 시장을 위아래에서 동시에 장악하려는 전략으로 읽힌다.
- 05-17 노트에서 Anthropic도 유사한 Deployment Company 전략을 채택했다고 언급된 점은, OpenAI-Anthropic 경쟁의 축이 모델 성능 비교에서 '기업 도입·전환 서비스' 경쟁으로 이동했음을 시사한다.
- 실무 시사점: Codex/Claude를 단순 코드 생성기로 쓰기보다, 하네스 엔지니어링 관점(AGENTS.md로 규칙 명문화, 위험 분류·자동 리뷰 루프, 재사용 가능한 스킬 카탈로그 구축)에서 에이전트가 일할 환경을 설계하는 데 실무 역량을 투자해야 한다.

## 관련 개념

[[Concepts/Codex|Codex]] | [[Concepts/AI|AI]] | [[Concepts/github.com|github.com]] | [[Concepts/AI-에이전트|AI 에이전트]] | [[Concepts/코딩|코딩]]

## 출처 노트 (21개, 최근순)

| 노트 | 저자 · 날짜 | 요약 |
|------|-------------|------|
| [[u260713_choi.openai_오픈AI가-GPT-5.6-_16d869]] | `@choi.openai` · 26-07-13 | 오픈AI가 GPT 5.6 출시와 관련하여 AMA를 진행하였습니다. 새로운 모델은 Sol, Terra, Luna로 나뉘어 있으며, 각 모델의 사용 목적과 성능이 다릅니다. 또한, 사용자의 피드백을 반영한 개선 사항도 다수 공유되었습니다. |
| [[u260713_unclejobs.ai_OpenAI의-코덱스-Co_5220cf]] | `@unclejobs.ai` · 26-07-13 | OpenAI의 코덱스(Codex)에 '레코드 & 리플레이(Record & Replay)' 기능이 추가되어, 사용자가 작업을 시연하면 AI가 이를 학습하여 반복 작업을 자동으로 수행할 수 있게 되었다. 이 기능은 설명 대신 보여주는 방식으로, 사용자 맞춤형 작업 설명서를 생성한다. 현재는 macOS에서만 사용 가능하며, 유럽 일부 지역에서는 제한되었다. |
| [[u260603_choi.openai_오픈AI가-Codex-Py_24f793]] | `@choi.openai` · 26-06-03 | 오픈AI가 Codex Python SDK를 공개하였습니다. 이제 개발자들은 Python 애플리케이션에 Codex를 내장하여 복잡한 프로토콜 없이 다양한 기능을 구현할 수 있게 되었습니다. 오픈AI는 AI 운영체제로의 확장과 함께 개발자들이 생태계 위에서 제품을 만들도록 지원하고 있는 것으로 보입니다. |
| [[u260603_choi.openai_오픈AI가-Codex의-대_4ff7b1]] | `@choi.openai` · 26-06-03 | 오픈AI가 Codex의 대규모 업데이트를 발표하며 스타트업 생존에 영향을 미칠 것으로 보인다. 'Sites' 기능으로 비개발자도 손쉽게 웹앱을 생성할 수 있어 기존 노코드 도구들과의 경쟁이 치열해질 전망이다. 오픈AI의 목표는 사내 모든 툴과 워크플로우를 자사 플랫폼 내에서 처리할 수 있는 종합 업무 포털 구축으로 확장되고 있다. |
| [[u260517_choi.openai_OpenAI가-OpenAI_a58469]] | `@choi.openai` · 26-05-17 | OpenAI가 OpenAI Deployment Company를 출범하여 기업의 운영 방식을 AI 중심으로 재설계하는 서비스를 시작했습니다. 대형 컨설팅 회사들과 협력해 FDE를 통해 AI 도입을 지원하고 있으며, 앤트로픽 또한 유사한 전략을 채택하고 있습니다. 이는 AI 회사들이 조직 구조를 변화시키는 새로운 시대의 시작을 알리고 있습니다. |
| [[u260511_ddongddangddi_최근-대시보드의-LLM-백_37f8af]] | `@ddongddangddi` · 26-05-11 | 최근 대시보드의 LLM 백엔드를 DeepSeek API에서 Codex SDK로 변경하였다. 이로 인해 API 호출 비용이 무료가 되며, 개인 ChatGPT Plus 구독으로 인증할 수 있다. OpenAI가 제공하는 새로운 인증 방법으로 사용이 편리해졌다. |
| [[u260511_unclejobs.ai_OpenAI가-새로운-실시_29b3aa]] | `@unclejobs.ai` · 26-05-11 | OpenAI가 새로운 실시간 음성 모델 3개(GPT-Realtime-2, GPT-Realtime-Translate, GPT-Realtime-Whisper)를 발표했습니다. 이 모델들은 각각 음성 에이전트, 실시간 통역, 실시간 받아쓰기 기능을 수행합니다. 음성 앱이 이제 단순한 STT와 TTS의 조합이 아니라, 더욱 인터랙티브한 사용자 경험을 제공하게 되었습니다. |
| [[u260505_choi.openai_오픈AI가-Codex에-새_ddd5ef]] | `@choi.openai` · 26-05-05 | 오픈AI가 Codex에 새로운 펫 기능을 추가했습니다. 이 기능은 개발자가 작업 중에도 AI의 상태를 실시간으로 보여주며, 귀여운 애니메이션 펫을 통해 사용자와의 친밀함을 높입니다. 사용자는 기본 펫을 선택하거나 맞춤형 펫을 생성할 수 있습니다. |
| [[u260428_choi.openai_OpenAI가-Worksp_0bfad9]] | `@choi.openai` · 26-04-28 | OpenAI가 'Workspace Agents'를 발표하며 에이전트 중심의 생태계를 구축하고 있습니다. 이 에이전트들은 조직의 워크플로우에서 협업하며 다양한 툴에 접근할 수 있습니다. 팀원들은 메신저와 ChatGPT를 통해 이 에이전트를 함께 사용할 수 있습니다. |
| [[u260428_choi.openai_오픈AI는-GPT-5.5-_8b6842]] | `@choi.openai` · 26-04-28 | 오픈AI는 GPT-5.5 모델을 발표하며 성능을 한 번에 정리한 내용을 공유했습니다. 이미지 생성 모델 Images 2.0도 출시되어 최신 정보를 반영한 인포그래픽이나 수학 문제 해결 이미지 생성이 가능해졌습니다. 새로운 AI 기능들이 빠르게 도입되고 있어 AI 생태계가 급속도로 확장되고 있습니다. |
| [[u260428_choi.openai_오픈AI가-개인정보-보호를_2ee5f3]] | `@choi.openai` · 26-04-28 | 오픈AI가 개인정보 보호를 위한 무료 오픈소스 모델 'Privacy Filter'를 발표했습니다. 이 모델은 개인 식별 정보를 자동으로 찾아 제거하며, 내부망에서도 빠르게 작동합니다. 이는 데이터 보안 문제를 해결하고 기업의 AI 도입을 촉진할 전략으로 평가됩니다. |
| [[u260428_unclejobs.ai_OpenAI가-Worksp_9faece]] | `@unclejobs.ai` · 26-04-28 | OpenAI가 Workspace Agents를 발표하여 팀 단위의 업무를 효율적으로 처리할 수 있는 새로운 AI 에이전트를 도입했다. 이 에이전트는 Slack과 통합되어 팀의 대화 속에서 직접 업무를 수행하며, 다양한 템플릿을 통해 반복적인 작업을 자동화할 수 있다. 특히, 내부 통제 장치와 Prompt injection 방어 기능이 추가되어 기업 사용에 적합하게 설계되었다. |
| [[u260422_choi.openai_오픈AI의-Codex가-C_a69e72]] | `@choi.openai` · 26-04-22 | 오픈AI의 Codex가 'Chronicle' 기능을 도입하여 작업 화면을 분석하고 기억합니다. 이 기능은 개발자가 과거 작업을 쉽게 이어갈 수 있도록 돕습니다. 이제 맥락 단절 문제를 해결하여 작업 효율성이 높아질 것으로 기대됩니다. |
| [[u260422_choi.openai_오픈AI가-Euphony-_2e0ab4]] | `@choi.openai` · 26-04-22 | 오픈AI가 'Euphony'라는 시각화 도구를 오픈소스로 공개했습니다. 이 도구는 챗봇 대화 데이터와 Codex 세션 로그를 분석하는 데 도움을 줍니다. 개발자들은 이 툴을 사용하여 AI의 사고 과정을 보다 직관적으로 이해하고 최적화할 수 있게 됩니다. |
| [[u260403_tilnote_하네스-엔지니어링-Harn_751829]] | `@tilnote` · 26-04-03 | 하네스 엔지니어링(Harness Engineering)은 OpenAI 엔지니어들이 AI 에이전트를 효율적으로 활용하여 프로그래밍을 대체하는 방법론이다. 이를 통해 생산성을 높이고, 에이전트가 원활하게 작업할 수 있는 환경을 설계하는 것이 중요하다. 2026년에는 코딩 실력이 아닌 환경 설계 능력이 핵심 역량으로 자리 잡을 것이다. |
| [[u260327_qjc.ai_AI가-코드를-작성하는-시_7764a0]] | `@qjc.ai` · 26-03-27 | AI가 코드를 작성하는 시대에, 리포지토리를 안전하게 관리하는 'Harness Engineering' 기법을 소개합니다. 위험도 분류, 자동 리뷰, 증거 수집 등 단계를 거치는 자동화된 루프를 통해 사람이 개입하는 시점을 최소화합니다. 다양한 도구를 활용하여 AI 코드의 안정성을 확보하고 효율성을 높일 수 있습니다. |
| [[u260327_yeopo92_Cursor-API를-Op_76e787]] | `@yeopo92` · 26-03-27 | Cursor API를 OpenAI/Anthropic 형식으로 변환해주는 프록시 cursor2api가 등장했다. Cursor 백엔드를 활용하면서 기존 OpenAI/Anthropic SDK 코드를 수정 없이 재활용 가능하다. Claude Code 도구 지원 및 이미지 처리 기능도 포함되어 Cursor 구독 개발자에게 유용하며 API 비용 절감 효과를 기대할 수 있다. |
| [[u260327_kjconsulting_tea_OpenAI가-Codex-_08f7e2]] | `@kjconsulting_team` · 26-03-27 | OpenAI가 Codex 에이전트용 Skills Catalog를 GitHub에 공개했습니다. 이는 코딩 에이전트가 재사용 가능한 검증된 스킬들을 모아둔 오픈소스 저장소입니다. AI 에이전트의 '스킬 생태계' 표준화를 향한 OpenAI의 첫 공식 움직임으로 보입니다. |
| [[u260327_feelfree_ai_OpenAI가-에이전트-빌_60872f]] | `@feelfree_ai` · 26-03-27 | OpenAI가 에이전트 빌딩을 위한 새로운 기초를 공개하며, 수시간 동안 안정적으로 워크플로우를 이어가는 10가지 팁을 공유했습니다. Skills와 Shell을 활용하여 복잡한 작업을 핸들링하는 구체적인 방법이 제시되었습니다. MLOps나 에이전트 개발자에게 유용한 정보이며, 실무에 바로 적용 가능한 내용이 많습니다. |
| [[u260327_choi.openai_OpenAI-Codex를-_cbc7ed]] | `@choi.openai` · 26-03-27 | OpenAI Codex를 위한 130개 이상의 맞춤형 서브 에이전트 모음이 깃허브에 공개되었습니다. 각 에이전트는 독립적으로 작업을 수행하여 결과물의 품질과 속도를 향상시킵니다. AI 시대 경쟁력은 AI를 얼마나 구조적으로 잘 설계된 팀으로 만드느냐에 달려있다는 내용입니다. |
| [[u260327_aicoffeechat_OpenAI가-GPT-5._3e83e8]] | `@aicoffeechat` · 26-03-27 | OpenAI가 GPT-5.4를 활용하여 웹사이트를 디자인하는 노하우를 공개했습니다. AI 모델은 학습 데이터의 일반적인 패턴을 따르므로, 구체적인 프롬프트를 사용하여 원하는 디자인을 얻어야 합니다. 디자인 시스템 정의, 시각적 레퍼런스 제공, 스토리텔링 구조 활용, '하지 마' 규칙 설정 등의 실전 프롬프트 기법을 통해 더 나은 결과를 얻을 수 있습니다. |