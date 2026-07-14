# MCP
> 관련 노트: 17개 | 마지막 갱신: 2026-07-14 16:32

## 개요

주요 키워드: **Claude** · **MCP** · **MCP를** · **직접** · **Code** · **작업을** · **다양한** · **핵심**

## 핵심 인사이트

- Claude Certified Architect 인증 시험 대비를 위한 핵심 정보 요약. Anthropic 파트너가 아니어도 프로덕션급 앱을 만들 수 있는 지식 습득 가능. 5가지…
- Anthropic에서 Claude Code를 Telegram과 Discord에서 제어할 수 있는 Channels 기능을 연구 프리뷰로 공개했습니다. 이를 통해 휴대폰에서 직접 Cl…
- Claude Code 해커톤 우승자가 Claude Code 활용 팁 70가지를 공유합니다. 마인드셋, Plan Mode, 컨텍스트 관리, 환경 설정, MCP, Hooks, Skil…
- Claude Code 사용 시 Obsidian과 연동하는 방법을 소개합니다. MCP를 사용하는 대신, Obsidian 설정을 통해 Claude Code가 로컬 마크다운 파일에 직접…
- Claude가 MCP를 통해 'Financial Datasets'와 연결되어 30년치 재무 데이터를 자연어로 즉시 불러와 분석 및 시각화가 가능해졌습니다. 이를 통해 투자자들은 데…

## Agent Insight
- 03-27에 개인/커뮤니티 단위 MCP 서버가 폭발적으로 등장(Financial Datasets, Docker MCP, n8n, Playwright, iOS 앱스토어 제출, Penpot, Notion/WordPress/Canva/ElevenLabs)한 뒤, 04-28 Anthropic이 MCP를 공식 표준으로 공개하며 200개 이상 서버를 정리하는 흐름으로 이어진다. 즉 풀뿌리 확산이 먼저였고 표준화는 뒤따랐다.
- 04-28 표준화 이후 05월 노트들(n8n-MCP의 JSON 실시간 검증, 환경변수 lazy load로 토큰 절감)은 '더 많은 MCP 연결'이 아니라 '오버헤드 감소·정확성 검증'으로 관심사가 옮겨간 것을 보여준다 — 확산기에서 성숙기로의 전환.
- 동시에 "MCP를 쓰는 대신 직접 접근"(Obsidian 로컬 파일 직접 연동, Docker MCP의 필요시 로드/언로드)이라는 반례가 반복 등장한다. MCP 확산과 컨텍스트/토큰 비용 절감 요구가 정면으로 충돌하는 긴장이다.
- 실무 시사점: MCP 서버를 상시 전부 로드하지 말고, Docker MCP나 lazy-load 패턴처럼 작업 단위로 붙였다 떼는 구조를 우선 적용하고, 로컬 파일 접근처럼 MCP 없이도 되는 경우엔 MCP를 쓰지 않는 편이 토큰 효율상 유리하다.

## 관련 개념

[[Concepts/Claude-Code|Claude Code]] | [[Concepts/github.com|github.com]] | [[Concepts/Anthropic|Anthropic]] | [[Concepts/AI-코딩|AI 코딩]] | [[Concepts/Claude|Claude]]

## 출처 노트 (17개, 최근순)

| 노트 | 저자 · 날짜 | 요약 |
|------|-------------|------|
| [[u260511_vyblor_Claude-Code의-환_24298c]] | `@vyblor` · 26-05-11 | Claude Code의 환경변수 설정 변경으로 초기 토큰 사용량을 크게 줄일 수 있다. lazy load 방식으로 필요할 때만 도구를 로드하여 효율을 높인다. 이는 대화의 지속 시간에 긍정적인 영향을 미치며, 특히 MCP 툴 사용자가 큰 혜택을 볼 수 있다. |
| [[u260507_conanssam_n8n-MCP는-AI가-생_b4d6cf]] | `@conanssam` · 26-05-07 | n8n-MCP는 AI가 생성한 Slack 메시지 보내기 프롬프트의 설정값을 실시간으로 검증하여 정확한 JSON을 제공하는 도구이다. 이 도구는 코드의 누락된 파라미터를 해결하고 효율적인 워크플로우 작성을 지원한다. AI의 역할이 단순한 코드 생성에서 도구 이해와 안전한 실행으로 변화하고 있다. |
| [[u260428_unclejobs.ai_Anthropic이-MCP_846d22]] | `@unclejobs.ai` · 26-04-28 | Anthropic이 MCP(Model Context Protocol)를 공개하며 AI 에이전트의 외부 시스템 통합을 표준화했습니다. MCP는 에이전트와 서비스 간의 연결을 단순화하고, 200개 이상의 MCP 서버를 지원합니다. 제시된 설계 원칙을 통해 엔드 유저 경험도 향상될 것으로 기대됩니다. |
| [[u260327_openclaw_ko_Playwright를-활용_012c83]] | `@openclaw_ko` · 26-03-27 | Playwright를 활용하여 브라우저 자동화 작업을 수행하는 방법을 소개합니다. Codex CLI를 통해 Playwright MCP 스킬을 설치하거나, 직접 설치하여 오픈클루에서 제공하는 기능을 사용할 수 있습니다. Playwright는 웹사이트 제어, 스크린샷, 가격 모니터링 등 다양한 자동화 작업을 가능하게 합니다. |
| [[u260327_toss.appsintoss_앱인토스-미니앱-개발-시-_c4a0bd]] | `@toss.appsintoss` · 26-03-27 | 앱인토스 미니앱 개발 시 앱인토스 팀에서 제공하는 AI 개발 가이드를 활용하면 효율적인 개발이 가능하다. 가이드에서는 MCP 서버 사용법, 앱인토스 공식 문서 기반 Skills, 문서 URL 인덱싱 방법을 제공한다. 빌드 에러를 줄이기 위해 공식 가이드 활용을 권장한다. |
| [[u260327_ai___touch_Claude-Code-사용_809c44]] | `@ai___touch` · 26-03-27 | Claude Code 사용 중 Codex, Gemini와 함께 사용하고 싶다는 아이디어에서 MCP를 직접 구현했습니다. MCP를 통해 모델 간 토론이 가능하며, 백그라운드 작업 ID 관리를 통해 비동기 요청 문제를 해결했습니다. Oh-my-claudecode를 참고하여 MCP를 개발하고 실전적인 접근 방식을 적용했습니다. |
| [[u260327_boris_cherny_Anthropic에서-Cl_971306]] | `@boris_cherny` · 26-03-27 | Anthropic에서 Claude Code를 Telegram과 Discord에서 제어할 수 있는 Channels 기능을 연구 프리뷰로 공개했습니다. 이를 통해 휴대폰에서 직접 Claude Code 세션을 제어하고, 작업을 비동기적으로 핸드오프하고 확인할 수 있습니다.  MCP 확장점을 통해 다양한 커뮤니케이션 채널로 확대될 예정이며, 코딩 워크플로우를 혁신할 것으로 기대됩니다. |
| [[u260327_devdesign.kr_Claude-Code-사용_d51ad9]] | `@devdesign.kr` · 26-03-27 | Claude Code 사용 시 Obsidian과 연동하는 방법을 소개합니다. MCP를 사용하는 대신, Obsidian 설정을 통해 Claude Code가 로컬 마크다운 파일에 직접 접근하도록 하여 토큰 낭비를 줄일 수 있습니다. 옵시디언 볼트 경로를 Claude 설정에 추가하고, 볼트 구조를 Claude Code에 알려주면 효율적인 노트 관리가 가능합니다. |
| [[u260327_geumverse_ai_Claude-Certifi_172c18]] | `@geumverse_ai` · 26-03-27 | Claude Certified Architect 인증 시험 대비를 위한 핵심 정보 요약. Anthropic 파트너가 아니어도 프로덕션급 앱을 만들 수 있는 지식 습득 가능. 5가지 도메인(Agentic Architecture, Tool Design & MCP, Claude Code 설정, Prompt & Structured Output, Context Management)별 핵심 내용 및 학습 순서 제시. |
| [[u260327_geumverse_ai_Claude-Certifi_70c593]] | `@geumverse_ai` · 26-03-27 | Claude Certified Architect 인증 시험 대비 핵심 내용을 요약한 게시글입니다. Claude Code, Agent SDK, API, MCP 4가지 핵심 역량을 중심으로 시험 도메인별 중요 사항과 학습 순서를 제시합니다. 인증 없이도 프로덕션급 앱을 만들 수 있도록 실질적인 지식 습득에 초점을 맞추고 있습니다. |
| [[u260327_qjc.ai_Claude-Code-해커_ef201b]] | `@qjc.ai` · 26-03-27 | Claude Code 해커톤 우승자가 Claude Code 활용 팁 70가지를 공유합니다. 마인드셋, Plan Mode, 컨텍스트 관리, 환경 설정, MCP, Hooks, Skills, TDD, 보안, 생산성 향상 등 다양한 팁을 제공합니다. Claude Code를 주니어 개발자처럼 대하고, 컨텍스트 관리에 신경 쓰고, 프로젝트 규칙을 설정하는 것이 중요하다고 강조합니다. |
| [[u260327_leehc_09_Docker-MCP를-사용_e37778]] | `@leehc_09` · 26-03-27 | Docker MCP를 사용하여 에이전트 컨텍스트를 효율적으로 관리하는 방법에 대한 게시글입니다. 필요할 때만 MCP를 로드하고 작업 완료 후 언로드하여 컨텍스트 윈도우 관리 및 토큰 절약이 가능합니다. Docker MCP를 통해 다양한 서비스 인증을 유지하며 300개 이상의 MCP를 연결하여 에이전트 성능을 유지할 수 있습니다. |
| [[u260327_choi.openai_Claude가-MCP를-통_04d1d2]] | `@choi.openai` · 26-03-27 | Claude가 MCP를 통해 'Financial Datasets'와 연결되어 30년치 재무 데이터를 자연어로 즉시 불러와 분석 및 시각화가 가능해졌습니다. 이를 통해 투자자들은 데이터 해석 및 자동화 워크플로우 구축에 집중할 수 있게 되었습니다. 하지만 댓글에서는 기존에 존재하던 서비스와 유사하며, 블룸버그 터미널을 대체하기에는 부족하다는 의견도 있습니다. |
| [[u260327_freainer_Claude-또는-Curs_ed0bcc]] | `@freainer` · 26-03-27 | Claude 또는 Cursor 사용자를 위한 생산성 향상 MCP 5가지 소개: FireSEO, Notion MCP, WordPress MCP, Canva MCP, ElevenLabs MCP. 각 MCP는 SEO 분석, 콘텐츠 관리, SEO 최적화 발행, 디자인 생성, 블로그-팟캐스트 변환 등의 기능을 제공. 링크는 댓글에 제공. |
| [[u260327_yeopo92_AI가-자연어-요청에-따라_dd7d6f]] | `@yeopo92` · 26-03-27 | AI가 자연어 요청에 따라 n8n 워크플로우를 직접 빌드해주는 MCP 서버가 등장했다. 이는 자율주행처럼 AI가 직접 실행하는 방식으로, 기존의 방법만 제시하는 방식과 차별화된다. 바이브코더에게 유용하며, 에이전트의 실행력 향상에 기여할 것으로 보인다. |
| [[u260327_homebodify_Figma-MCP-유료화에_3acd2f]] | `@homebodify` · 26-03-27 | Figma MCP 유료화에 대한 대안으로 Opensource인 Penpot을 소개하며, UI MCP 사용 시 Penpot을 추천하는 이유를 설명한다. Penpot은 Native Design Token 시스템을 사용하며, LLM 사용 비용만 지불하면 된다. MCP를 직접 만드는 경험도 추천한다. |
| [[u260327_seol.cc_Claude-Code를-활_ec6aa4]] | `@seol.cc` · 26-03-27 | Claude Code를 활용하여 iOS 앱스토어 제출 과정을 자동화하는 오픈소스 툴 MCP가 소개되었습니다. 서명 인증서 설정, 스크린샷 업로드 등 번거로운 작업을 '앱스토어에 제출해줘'라는 한 마디로 해결할 수 있습니다. 해당 툴은 Claude Code로 만들어졌으며 무료로 사용 가능합니다. |