# RAG
> 관련 노트: 11개 | 마지막 갱신: 2026-06-12 02:15

## 개요

주요 키워드: **RAG** · **에이전트** · **문서** · **데이터** · **Claude** · **개발** · **검색** · **구조를**

## 핵심 인사이트

- OpenRAG는 문서 파서, 벡터 검색 엔진, 워크플로 오케스트레이터, 프론트엔드를 통합한 오픈소스 RAG 플랫폼입니다. Docling을 사용하여 문서 구조를 보존하며 파싱하고, …
- Claude Code를 활용한 코드 설계 팁으로, AI가 회사 문맥을 이해하도록 문서 구조를 만들고, 설계 스킬을 사전에 설정하는 방법을 소개한다. 회사 목표, 배경, 제약 조건 …
- Google Research의 TurboQuant 알고리즘을 RAG에 적용한 'pyturboquant'가 출시되었습니다. 이 덕분에 기존 31GB의 인덱스 공간이 단 4GB로 줄어…
- 구글이 텍스트, 이미지, 비디오, 오디오, 문서 등 다양한 데이터를 하나의 공간에서 처리하는 'Gemini Embedding 2'를 공개했습니다. 이는 네이티브 멀티모달 방식으로,…
- LangGraph 에이전트 개발 시 루프 문제를 시각적으로 해결해주는 LangGraphics가 출시되었습니다. 복잡한 설정 없이 컴파일된 그래프를 watch()로 감싸면 에이전트 …

## Agent Insight
> 추후 Phase 3-B에서 LLM으로 채워짐

## 관련 개념

[[Concepts/AI|AI]] | [[Concepts/github.com|github.com]] | [[Concepts/AI-코딩|AI 코딩]] | [[Concepts/Claude-Code|Claude Code]] | [[Concepts/LangGraph|LangGraph]]

## 출처 노트 (11개, 최근순)

| 노트 | 저자 · 날짜 | 요약 |
|------|-------------|------|
| [[u260422_feelfree_ai_Google-Researc_cf3a20]] | `@feelfree_ai` · 26-04-22 | Google Research의 TurboQuant 알고리즘을 RAG에 적용한 'pyturboquant'가 출시되었습니다. 이 덕분에 기존 31GB의 인덱스 공간이 단 4GB로 줄어들며, 실시간 인덱싱과 프라이버시 보호가 가능해졌습니다. LangChain은 이를 이미 지원 중이며, 효율적인 메모리 사용하는 RAG 구축에 필수적인 라이브러리로 평가됩니다. |
| [[u260412_ai_crazyman_AI-agent와-RAG를_b6d543]] | `@ai_crazyman` · 26-04-12 | AI agent와 RAG를 활용하면서 발생할 수 있는 데이터 문제에 대한 고찰이 소개되었다. 데이터 포인트를 책갈피처럼 관리하여 효율적인 검색 구조를 활용하는 방법이 제안되었다. Vectorless라는 새로운 접근법으로 기존 RAG의 한계를 보완하는 아이디어가 논의되었다. |
| [[u260407_choi.openai_안드레-카파시가-LLM을-_d47e84]] | `@choi.openai` · 26-04-07 | 안드레 카파시가 LLM을 활용하여 개인 지식 베이스를 구축하는 방법을 소개했습니다. 사용자가 제공한 원시 데이터로 LLM이 자동으로 위키를 생성하며, 문서를 요약하고 오류를 검증합니다. AI가 개인 지식 관리를 대신하게 되면서 새로운 시대가 도래하고 있습니다. |
| [[u260330_lian.lab71_Claude-Code를-활_b2de2e]] | `@lian.lab71` · 26-03-30 | Claude Code를 활용한 코드 설계 팁으로, AI가 회사 문맥을 이해하도록 문서 구조를 만들고, 설계 스킬을 사전에 설정하는 방법을 소개한다. 회사 목표, 배경, 제약 조건 등을 담은 문서를 Claude가 먼저 읽게 하고, 리서치 쿼리 분석 및 문서 랭킹과 같은 스킬을 정의하여 AI가 설계 방향을 잘 잡도록 돕는다. RAG 방식을 응용하여 Claude Code의 자연어 처리 능력을 극대화하는 것이 핵심이다. |
| [[u260327_feelfree_ai_Lubu-Labs에서-La_4b95a9]] | `@feelfree_ai` · 26-03-27 | Lubu-Labs에서 LangGraph 앱 개발 및 배포를 위한 '7가지 에이전트 스킬'을 공개했습니다. Claude Code나 Cursor 사용자에게 유용하며, LangSmith 연동을 통해 초기 셋업부터 프로덕션까지 지원합니다. MLOps 또는 RAG 개발자에게 특히 유용한 자료입니다. |
| [[u260327_github.trending_OpenRAG는-문서-파서_cb6b80]] | `@github.trending` · 26-03-27 | OpenRAG는 문서 파서, 벡터 검색 엔진, 워크플로 오케스트레이터, 프론트엔드를 통합한 오픈소스 RAG 플랫폼입니다. Docling을 사용하여 문서 구조를 보존하며 파싱하고, OpenSearch로 인덱싱하며, Langflow로 RAG 파이프라인을 커스터마이징할 수 있습니다. 엔터프라이즈 RAG 시장에서 PoC를 넘어 프로덕션 단계로 넘어가는데 유용한 도구이며, IBM watsonx.data에 통합될 예정입니다. |
| [[u260327_unclejobs.ai_Claude-Code에서-_58b331]] | `@unclejobs.ai` · 26-03-27 | Claude Code에서 명령어 한 줄로 웹사이트 크롤링하는 스킬이 등장했다. Cloudflare의 /crawl 엔드포인트를 활용하여 빠른 속도로 크롤링이 가능하며, 설치 및 사용법 또한 간단하다. RAG 파이프라인이나 모델 학습용 데이터 수집에 유용하게 활용될 수 있다. |
| [[u260327_bizmentor_kr_GitHub-Trendin_dd401d]] | `@bizmentor_kr` · 26-03-27 | GitHub Trending 1위는 AI 에이전트 컨텍스트 DB인 volcengine/OpenViking입니다. 에이전트의 기억, 자료, 스킬을 파일 시스템처럼 관리하여 문맥 관리 문제를 해결합니다. 여러 에이전트 운영팀, 업무 자동화 개발자, RAG/메모리 품질 문제를 겪는 팀에게 유용합니다. |
| [[u260327_choi.openai_구글이-텍스트-이미지-비디_69c20d]] | `@choi.openai` · 26-03-27 | 구글이 텍스트, 이미지, 비디오, 오디오, 문서 등 다양한 데이터를 하나의 공간에서 처리하는 'Gemini Embedding 2'를 공개했습니다. 이는 네이티브 멀티모달 방식으로, 데이터 간의 복잡한 관계 파악에 용이합니다. 이로 인해 영상 속 특정 대화 구간 검색 등 더욱 빠르고 정확한 서비스 구현이 가능해질 것입니다. |
| [[u260327_feelfree_ai_LangGraph-에이전트_e162f7]] | `@feelfree_ai` · 26-03-27 | LangGraph 에이전트 개발 시 루프 문제를 시각적으로 해결해주는 LangGraphics가 출시되었습니다. 복잡한 설정 없이 컴파일된 그래프를 watch()로 감싸면 에이전트 실행 과정을 실시간으로 시각화하여 확인할 수 있습니다. RAG나 에이전트 개발 시 디버깅 시간을 획기적으로 줄여줄 꿀템입니다. |
| [[u260327_joonlee0228_Cloudflare가-웹사_368bc6]] | `@joonlee0228` · 26-03-27 | Cloudflare가 웹사이트 전체를 크롤링하는 API 엔드포인트 /crawl을 오픈 베타로 출시했다. AI 학습 데이터 수집에 최적화되어 개발자에게는 유용하지만 콘텐츠 크리에이터에게는 저작권 침해 우려를 낳는다. 크롤링을 막는 새로운 서비스 판매 가능성도 제기되고 있다. |