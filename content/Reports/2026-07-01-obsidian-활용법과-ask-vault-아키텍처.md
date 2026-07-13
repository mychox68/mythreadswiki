---
source: session
type: report
created_at: 2026-07-01
tags: [옵시디언, PKM, 지식관리, ask-vault, 아키텍처, RAG, Claude-Code]
publish: false
---

# Obsidian 활용법 비교 & ask-vault 아키텍처 (2026-07-01)

> [!summary] 요약
> 웹 베스트프랙티스와 이 볼트를 비교하고, 유료 API RAG 플러그인(`threads-query`)을 무(無)API
> Claude Code 스킬(`/ask-vault`)로 대체하기로 결정한 세션 기록. 볼트의 유일한 빈칸이던
> "LLM 정제 레이어"(각 개념의 `Agent Insight`, 설계상 Phase 3-B)를 이 스킬로 채운다.

## 1. 웹 베스트프랙티스 (2026)

- **CODE** — Capture(수집) → Organize(정리) → Distill(정제) → Express(표현)의 반복 루프.
- **PARA** — Projects / Areas / Resources / Archives + Inbox 로 "행동 가능성" 기준 분류.
- **폴더 vs 링크** — 폴더는 물리적 분리(노트는 폴더 1곳에만). 진짜 조직은 **MOC(Maps of Content) + `[[링크]]` + 태그**. 한 노트가 여러 MOC에서 링크될 수 있어 다차원 구조가 됨.
- **2026 AI 트렌드** — Claude Code 를 볼트에 붙여 수백 개 노트를 즉시 교차참조. AI가 orphan(어느 MOC에도 안 걸린) 노트를 스캔·분류·연결. → 즉 **AI가 정제/연결 레이어를 대신 유지**하는 것이 핵심 진화.

관련 개념: [[Concepts/옵시디언|옵시디언]] · [[Concepts/지식-관리|지식 관리]] · [[Concepts/RAG|RAG]] · [[Concepts/Claude-Code|Claude Code]] · [[Concepts/MCP|MCP]]

## 2. 이 볼트 진단 (실측 2026-07-01)

| 레이어 | 폴더 | .md | 상태 |
|---|---|---|---|
| 수집 | Groups/Threads | 900 | 🟢 넘침 |
| 수집 | Groups/Sources | 425 | 🟢 진행 |
| 정제(자동) | **Wiki** | 636 | 🟢 Concepts/Topics/Explorations/Reports — 사실상 MOC/연결 레이어 |
| 연결(폴더) | MOC · Zettelkasten | 0 · 0 | ⚪ 비어있음(기능은 Wiki가 대체) |
| PARA | Projects/Areas/Resources/Archives | 5/0/3/0 | 🟡 거의 미사용 |

**핵심 진단:** 수집(1,325) + 자동 지식베이스(Wiki 636, 개념·토픽 링크망)까지는 이미 상위권.
남들이 수동으로 파는 MOC를 자동 생성으로 갖춘 상태. **유일한 빈칸은 각 `Wiki/Concepts/*.md`에
설계만 해두고 비워둔 `## Agent Insight`(주석: "추후 Phase 3-B에서 LLM으로 채워짐") = LLM 정제 레이어.**

## 3. 결정

- **`threads-query` 플러그인 은퇴.** 이미지의 그 AI 채팅 UI(본인 제작, author `mychox68`)는 OpenAI API로 RAG를 돌려 질의마다 종량 과금됨. `.obsidian/community-plugins.json`에서 비활성화(폴더는 보존 → 되돌리기 가능).
- **`/ask-vault` 글로벌 스킬로 대체.** 위치 `C:\Users\HOME\.claude\skills\ask-vault\SKILL.md` — 모든 폴더/프로젝트에서 호출. 검색 = Grep 다중 키워드 패스 + 직접 읽기 + 추론(임베딩·OpenAI API 불필요), 생성 = Claude Code 구독. 저장 포맷은 플러그인 출력과 바이트 호환(차이는 frontmatter `provider: claude-code` 뿐).
- **임베딩 불필요 근거:** 검색기가 LLM이면 언어를 이해하므로 동의어 확장 + 후보 읽고 판단으로 의미검색을 대체. 단어가 전혀 안 겹치는 개념적 유사 노트를 놓치면 그때 업그레이드 신호 → 이미 보유한 `.smart-env` 임베딩(9,784개) 재사용 가능(추가 과금 0).

### 흐름도

```
[어느 폴더든] /ask-vault "질문"
   ├─ 1. D:\obsidian 검색 (Grep 다중 키워드, 무료)
   ├─ 2. Claude가 [[출처]] 인용해 종합
   ├─ 3. "Wiki에 저장?" → 예 → Wiki\Explorations\<yyyyMMdd-HHmmss>-<슬러그>.md
   ├─ 4. (선택) 관련 Concept의 Agent Insight 칸 채우기 (Phase 3-B)
   └─ 5. 📊 토큰 사용량(추정) 표시
```

## 4. /ask-vault 사용법

- 호출: 아무 폴더에서 `/ask-vault <질문>` 또는 "볼트에 물어봐 …".
- 답변 뒤 저장 여부를 물음 → 저장 시 `Wiki/Explorations/`에 기존과 동일 포맷 노트 생성.
- 매 답변 끝에 **토큰 사용량(추정, 글자수 기반)** 표시 — 읽은 컨텍스트 / 답변 / 합계, 그리고 옛 OpenAI 종량 대비 러프 비교(선택).

## 5. Phase 3-B 완료

이 세션에서 61개 `Wiki/Concepts/*.md`의 `Agent Insight` 빈칸을 각 노트의 개요·핵심 인사이트·출처 노트를
근거로 일괄 합성해 채움. 이제 개념 노트가 "원문 요약 + LLM 종합 인사이트" 두 층을 모두 가짐.

## Sources (web)

- [Obsidian AI Second Brain Complete Guide 2026 — NxCode](https://www.nxcode.io/resources/news/obsidian-ai-second-brain-complete-guide-2026)
- [Obsidian + AI: Second Brain That Works in 2026 — HundredTabs](https://hundredtabs.com/blog/obsidian-ai-second-brain-2026)
- [Folders vs MOCs vs Tags — Shuvangkar Das](https://blog.shuvangkardas.com/obsidian-note-organization/)
- [Maps of Content — Obsidian Rocks](https://obsidian.rocks/maps-of-content-effortless-organization-for-notes/)
- [Obsidian AI 플러그인 비교 — Code Culture](https://codeculture.store/blogs/developer-culture/obsidian-ai-plugin-comparison-2025)
- [Smart Connections vs Copilot 비용 — smartconnections.app](https://smartconnections.app/obsidian-copilot/)
