# Claude Code
> 관련 노트: 190개 | 마지막 갱신: 2026-05-11 20:27

## 개요

주요 키워드: **Claude** · **AI** · **Code** · **코드** · **소개합니다** · **클로드** · **다양한** · **개발**

## 핵심 인사이트

- 앤트로픽 해커톤 우승자의 Claude Code 실전 설정 가이드가 공개되었으며, Skills, Hooks, MCP 조합을 통해 생산성을 극대화하는 엔지니어링 기법을 소개합니다. C…
- Claude Code has been redesigned for desktop with features like running multiple sessions, an integra…
- GitHub Copilot Pro를 활용하여 Opus 4.6, Sonnet 4.6을 사용하는 대안을 소개하고, Copilot API를 Claude Code에 연동하는 방법도 설명합…
- Google이 AI 스킬 설계에 대한 5가지 디자인 패턴(Tool Wrapper, Generator, Reviewer, Inversion, Pipeline)을 공개했습니다. 각 패…
- Claude Code를 효과적으로 사용하는 방법은 '하네스' 구조에 있으며, 이는 생성자와 평가자 에이전트를 분리하여 AI의 코딩 및 디자인 능력을 향상시키는 방법이다. 앤트로픽은…

## Agent Insight
> 추후 Phase 3-B에서 LLM으로 채워짐

## 관련 개념

[[Concepts/AI-코딩|AI 코딩]] | [[Concepts/자동화|자동화]] | [[Concepts/github.com|github.com]] | [[Concepts/AI|AI]] | [[Concepts/AI-에이전트|AI 에이전트]]

## 출처 노트 (30개, 최근순)

| 노트 | 저자 · 날짜 | 요약 |
|------|-------------|------|
| [[u260511_the.claudeist_Claude-Code를-활_880cff]] | `@the.claudeist` · 26-05-11 | Claude Code를 활용하는 방법에서 질문법이 중요하다는 점을 강조한다. '가능한 가설을 세우는 것'과 '환경 변수 확인'이 업무 완결성을 높이는 핵심 전략이다. 이러한 접근법으로 해결책을 찾을 확률이 높아진다. |
| [[u260511_vyblor_Claude-Code의-환_24298c]] | `@vyblor` · 26-05-11 | Claude Code의 환경변수 설정 변경으로 초기 토큰 사용량을 크게 줄일 수 있다. lazy load 방식으로 필요할 때만 도구를 로드하여 효율을 높인다. 이는 대화의 지속 시간에 긍정적인 영향을 미치며, 특히 MCP 툴 사용자가 큰 혜택을 볼 수 있다. |
| [[u260507_kudi.uxui_클로드-코드와-다양한-도구_2e1969]] | `@kudi.uxui` · 26-05-07 | 클로드 코드와 다양한 도구를 활용하여 디자인 수정을 효율적으로 진행하는 방법에 대해 논의하고 있다. 사용자들은 에이전트와의 상호작용을 통해 구체적인 수정 요청을 원하는 것으로 보인다. 여러 가지 도구와 영상이 공유되며, 경험과 팁을 나누고 있다. |
| [[u260505_choi.openai_Claude-Code의-새_24787c]] | `@choi.openai` · 26-05-05 | Claude Code의 새로운 기능으로 모바일 앱과 Remote Control을 통해 긴 작업 중에도 푸시 알림을 받을 수 있게 되었다. 이를 통해 사용자는 터미널 창을 닫고도 작업을 계속할 수 있다. 사용자들의 반응이 긍정적이다. |
| [[u260505_id.capstone_클로드코드를-고도화하는-5_16e1da]] | `@id.capstone` · 26-05-05 | 클로드코드를 고도화하는 5가지 플러그인을 소개합니다. 각 플러그인은 개발 과정의 다양한 측면에서 효율성을 높이는 데 도움을 줍니다. 브레인스토밍, 실시간 문서 확인, 정책 관리 등을 통해 사용자 경험을 개선합니다. |
| [[u260505_teum_soul_Claude-Code가-유_8f1550]] | `@teum_soul` · 26-05-05 | Claude Code가 유출되어 누군가 로컬 데스크탑 앱으로 개발했습니다. 공식 버전은 API 과금 및 UI가 부족하지만, 새로운 앱은 여러 기능을 추가했습니다. 주석 달린 소스를 통해 모델의 작동 방식을 더 잘 이해할 수 있습니다. |
| [[u260505_the.claudeist_Claude-Code의-P_e50a17]] | `@the.claudeist` · 26-05-05 | Claude Code의 Pro 제한을 피하는 방법에 대한 4가지 팁을 소개합니다. 하이브리드 라우팅과 보조 사수(코워커) 셋업을 통해 비용 효율성을 극대화합니다. 반복 작업은 보조 모델에게 맡겨 메인 모델의 자원을 아끼는 전략이 중요합니다. |
| [[u260505_think.5x_code-review-gr_1bbe4d]] | `@think.5x` · 26-05-05 | code-review-graph는 코드를 수정할 때 영향을 받는 파일만을 받아들이고, 변경 영향 범위를 시각화하여 리뷰 및 리팩터링 시 토큰 비용을 절감합니다. 평균적으로 8.2배의 토큰 절감이 가능하며, 23개 이상의 언어를 지원합니다. MIT 오픈소스로 대형 모노레포와 레거시 코드베이스에 쉽게 적용할 수 있습니다. |
| [[u260505_unclejobs.ai_CCS-Claude-Cod_76ec9d]] | `@unclejobs.ai` · 26-05-05 | CCS(Claude Code Switch)는 다양한 AI 모델을 통합하여 사용하는 어댑터입니다. GPT-5.4의 성능이 향상되었으나, 요금제에 따른 한도 리셋 문제와 약관 준수의 중요성이 강조됩니다. 사용자에게 안전한 사용 방법과 위험성을 설명하고 있습니다. |
| [[u260505_vyblor_Claude-Code를-이_412832]] | `@vyblor` · 26-05-05 | Claude Code를 이용해 AI 이미지와 영상 모델을 동시에 운용할 수 있게 되었다. 이를 통해 콘텐츠 자동화의 진입장벽이 낮아지고 있다. Chase AI는 이 툴로 GitHub trending 콘텐츠를 자동화하여 구독자를 늘리고 있다. |
| [[u260505_vyblor_Graphify의-그래프-_2d3e93]] | `@vyblor` · 26-05-05 | Graphify의 그래프 인덱싱을 사용하면 Claude Code 파일 읽기 시 필요한 토큰을 71.5배 줄일 수 있습니다. 특히 큰 레포에서 그 효과가 더욱 두드러지며, 컨텍스트의 여유가 생겨 정확도도 상승합니다. 오픈소스이며 Claude Code와 호환되는 도구입니다. |
| [[u260428_choi.openai_앤트로픽이-Claude-C_310353]] | `@choi.openai` · 26-04-28 | 앤트로픽이 Claude Code에 '/ultrareview' 기능을 추가하여 다수의 버그 탐지 에이전트를 클라우드에서 동시에 실행해 코드를 리뷰합니다. 이에 대한 일부 불만도 있지만, 자동화 영역으로의 변화가 강조되고 있습니다. 해당 기능은 Pro 및 Max 구독자에게 일정 기간 무료로 제공됩니다. |
| [[u260428_sinbum_ai_CLAUDE.md-파일이-_d32ee3]] | `@sinbum_ai` · 26-04-28 | CLAUDE.md 파일이 LLM 코딩 실수 개선을 위해 만들어졌다. 주요 원칙은 가정을 없애고, 간소화하며, 필요한 부분만 수정하고, 목표 중심으로 실행하는 것이다. 이 파일을 통해 Claude Code와 Cursor의 행동이 최적화된다. |
| [[u260428_unclejobs.ai_Claude-Code의-최_45eb6a]] | `@unclejobs.ai` · 26-04-28 | Claude Code의 최신 업데이트는 세션 관리를 개선하는 다양한 기능을 도입했습니다. Session recap 기능이 추가되어 사용자에게 자동 요약을 제공하며, 세션 이름 붙이기, AI 자동 제목 생성, 예약 태스크 복원 등도 포함됩니다. 이로 인해 헤비 유저들이 더 효율적으로 작업을 관리할 수 있게 되었습니다. |
| [[u260422_atelic.io_Claude-Code와-C_a24cb0]] | `@atelic.io` · 26-04-22 | Claude Code와 Codex를 최적화하기 위한 다양한 설정을 공유하고, 자동 삽입 텍스트, 토큰 비용 감소 방법 등을 설명한다. 특히, 환경 설정과 커넥터 사용의 효율성을 강조하고 있다. 이러한 조정을 통해 프로젝트 성능을 향상시키고 비용 관리에 유리한 전략을 제시한다. |
| [[u260422_choi.openai_앤트로픽이-Claudia-_4c17c0]] | `@choi.openai` · 26-04-22 | 앤트로픽이 Claudia AI 모델 'Claude Code'를 업데이트하여 여러 세션 병렬 실행, 통합 터미널 기능 등을 추가했습니다. 이는 개발자들이 동시에 여러 작업을 쉽게 관리할 수 있도록 돕습니다. 또한 다양한 AI 도구들의 지능화 및 자동화 기능이 더욱 향상되었습니다. |
| [[u260422_kjconsulting_tea_Claude-Code의-새_bf60c8]] | `@kjconsulting_team` · 26-04-22 | Claude Code의 새로운 기능인 'claude-mem'을 통해 코딩 세션의 모든 활동을 자동으로 저장하고 장기 기억으로 관리할 수 있습니다. 이를 통해 프로젝트의 복잡한 역사에 대한 설명 없이도 필요한 정보를 즉시 제공받을 수 있습니다. 업데이트된 클로드 데스크탑은 이전 작업 내용을 확인하고 적용하는 데 유용합니다. |
| [[u260422_lucas_flatwhite_Claude-Code에-대_d22b4b]] | `@lucas_flatwhite` · 26-04-22 | Claude Code에 대한 발표 내용이 전사 세미나에서 공유되었습니다. 발표는 다양한 주제와 실제 사례를 포함하여 총 89장의 슬라이드로 구성되어 있었습니다. 이와 같은 유익한 공유가 증가하고 있습니다. |
| [[u260422_ai.guru.kim_코덱스는-불필요한-문장을-_95b35e]] | `@ai.guru.kim` · 26-04-22 | 코덱스는 불필요한 문장을 제거하여 응답을 간결하게 만들어줍니다. 출력 토큰을 65% 줄이며, 응답 속도를 향상시킵니다. 클로드 코드나 코덱스에 설치할 수 있으며, 사용을 추천합니다. |
| [[u260415_atelic.io_Claude-Code의-컨_6525b1]] | `@atelic.io` · 26-04-15 | Claude Code의 컨텍스트 사용률, 세션 비용 및 요금제 잔여량을 실시간으로 보여주는 상태바 플러그인을 소개합니다. 설치가 간단하고, 사용자 맞춤형 레이아웃 구성이 가능합니다. 기본 기능 외에도 다양한 추가 기능을 제공해 작업의 효율성을 높여줍니다. |
| [[u260415_choi.openai_앤트로픽이-Claude-C_a999ba]] | `@choi.openai` · 26-04-15 | 앤트로픽이 Claude Code에 '루틴' 기능을 추가하여 자동화를 지원합니다. 이를 통해 사용자는 지정된 시간이나 이벤트에 따라 클로드가 백그라운드에서 작업을 수행하도록 설정할 수 있습니다. 코드 리뷰와 버그 수정도 자동으로 진행되어 효율성이 크게 향상됩니다. |
| [[u260415_choi.openai_앤트로픽이-데스크톱용-Cl_f6b50d]] | `@choi.openai` · 26-04-15 | 앤트로픽이 데스크톱용 'Claude Code'를 개편하여 여러 클로드 세션을 동시에 사용할 수 있게 되었습니다. 새로운 기능으로 통합 터미널, 파일 편집, HTML과 PDF 미리보기가 추가되었고, 사용자 맞춤형 배치가 가능합니다. 이는 여러 작업을 동시에 수행할 때의 불편을 해소하는 데 기여할 것으로 보입니다. |
| [[u260415_choi.openai_최근-claude-code_2497ed]] | `@choi.openai` · 26-04-15 | 최근 'claude-code-best-practice' 프로젝트가 깃허브에서 높은 관심을 받고 있다. 이 프로젝트는 84개 이상 실전 팁과 설정 템플릿을 제공하며, 인기 워크플로우를 비교할 수 있는 자료도 포함되어 있다. 최적화된 개발 환경을 구축할 수 있도록 MIT 라이선스 아래 공개되었다. |
| [[u260415_claudeai_Claude-Code-ha_d67a9c]] | `@claudeai` · 26-04-15 | Claude Code has been redesigned for desktop with features like running multiple sessions, an integrated terminal, and file editing. Users can customize their workspace with a drag-and-drop layout. Feedback mentions the need for improvements in existing models and requests for Linux support. |
| [[u260415_dalgom.bami_디자인-시스템-구축에-있어_ae4edf]] | `@dalgom.bami` · 26-04-15 | 디자인 시스템 구축에 있어 AI의 도움을 활용하는 방법을 소개합니다. 특히, Pencil과 Claude Code를 결합하여 빠르게 프로토타입을 만들 수 있는 과정을 설명합니다. AI를 통해 미적 감각이 부족한 개발자도 효율적으로 디자인 시스템을 구축할 수 있습니다. |
| [[u260415_jetson_jh_Hermes-에이전트를-사_d84bc5]] | `@jetson_jh` · 26-04-15 | Hermes 에이전트를 사용하는 사용자들이 OAuth 관련 질문을 하고 있습니다. Claude Code를 로컬 머신에서 ACP로 사용할 수 있는 방법에 대한 패치도 공유되었습니다. 사용법은 댓글에 남길 예정입니다. |
| [[u260415_kk_fe_1_클로드-코드에서-사용되는-_9793e9]] | `@kk_fe_1` · 26-04-15 | 클로드 코드에서 사용되는 토큰의 비율을 확인할 수 있는 방법이 소개됩니다. 대화, 코딩, 탐색 및 디버깅을 포함한 다양한 사용 패턴이 언급되었습니다. 사용자들은 토큰 사용을 최적화하기 위해 이 기능을 활용할 것을 권장합니다. |
| [[u260415_unclejobs.ai_Waza라는-오픈소스-프로_e7d9f1]] | `@unclejobs.ai` · 26-04-15 | Waza라는 오픈소스 프로젝트는 AI 시대에 엔지니어가 갖춰야 할 8가지 습관을 마크다운 형식으로 제안합니다. Claude Code는 코드를 생성하는 AI로, 이 프로젝트는 코드 없이도 실용적인 결과를 제공합니다. 각 스킬은 문제 해결과 디자인, 디버깅 등 다양한 주제를 다루며, 간결한 작업 흐름을 지원합니다. |
| [[u260412_aychan3927_GPT-5.4를-Claud_c5644e]] | `@aychan3927` · 26-04-12 | GPT-5.4를 Claude Code에서 사용하기 위해 VibeProxy를 설치하는 방법을 공유합니다. 이를 통해 클로드코드의 모든 기능을 유지하면서 모델을 변경할 수 있습니다. 맥에서만 가능하며, 윈도우에 대한 대안도 존재합니다. |
| [[u260412_ck_06_01_Claude-Code에서-_ec9c3b]] | `@ck_06_01_` · 26-04-12 | Claude Code에서 AI가 잘못된 가정을 하여 발생하는 문제를 해결하기 위한 방법이 소개되었습니다. 설정 파일 CLAUDE.md를 이용하여 AI의 행동 규칙을 명시적으로 지정함으로써 일관된 결과를 이끌어낼 수 있습니다. 이 접근법은 AI 도구의 품질과 제약 조건 설계의 중요성을 강조합니다. |