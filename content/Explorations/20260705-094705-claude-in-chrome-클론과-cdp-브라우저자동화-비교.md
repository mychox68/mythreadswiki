---
source: research
query: "개발/디버그할 때 Claude와 Codex가 브라우저를 쓰는 최선의 방법은 무엇인가"
created_at: 2026-07-05T09:47:05.000Z
updated_at: 2026-07-05
origin: "[[v3/inputs/2026-07-04/hermes.txt]] (오전 10:35~10:41, 이 채팅방은 저의 일기장 입니다)"
related:
  - "[[GitHub-ChromeDevTools-chrome-devtools-mcp-Chrome-D-7db0c3b0-a0958cc4bbb8]]"
  - "[[u260327_yeopo92_ChromeDevTools_d27fce]]"
  - "[[u260422_cpa_chan27_Playwright와-Ch_d2f34b]]"
  - "[[u260327_lian.lab71_Chrome-Claude-_04bc29]]"
  - "[[u260422_masterkeyai_구글이-크롬-브라우저에-S_4824a0]]"
publish: false
---

# Claude·Codex 브라우저 자동화 — 뭘 쓰는 게 제일 좋은가

> [!question] 질문
> 개발/디버그할 때 Claude Code와 Codex가 브라우저를 쓰는 방법 중, **자동으로 잡혀서 바로 쓸 수 있는 최선의 툴**은 무엇인가? Claude in Chrome("보라색 탭")을 대체할 오픈소스 CDP/MCP 후보들과 비교했을 때, 뭐가 제일 나은가?

## 결론 (TL;DR)

**이미 갖고 있는 두 개가 정답이다. 추가 설치 불필요.**

|                      | 자동 연결 방식                                                                                                              | 상태          |
| -------------------- | --------------------------------------------------------------------------------------------------------------------- | ----------- |
| **Claude Code 디버그용** | `chc` (`claude --chrome --dangerously-skip-permissions` alias) → Claude in Chrome (Beta) 확장과 native messaging으로 자동 연결 | ✅ 이미 설정됨    |
| **Codex 디버그용**       | "Control Chrome with Codex" 확장(1.1.5) → Codex 데스크톱 앱과 native messaging으로 자동 handshake                                 | ✅ 이미 설치·연결됨 |
| **Hermes Agent(WSL) 디버그용** | 순수 CDP WebSocket, `/browser connect`로 기존 브라우저에 연결 → [[#Hermes Agent 쪽 — CDP WebSocket 직접 연결]] 참고 | ⚠️ 확장 없이 되지만, 매번 `--remote-debugging-port` 브라우저 실행 + 연결이 필요해 완전 자동은 아님 |

두 경로 다 스크린샷·DOM·콘솔로그·네트워크 확인 + 클릭·타이핑·폼작성까지 커버하는 **native 통합**이다. MCP 서버(`chrome-devtools-mcp` 등)는 수동 설치(`claude mcp add`)가 필요하고 성격도 다르므로, "자동으로 잡혀서 쓰고 싶다"는 조건에는 native 경로가 정확히 맞는다 → **chrome-devtools-mcp는 성능 프로파일링·headless CI처럼 native가 못 하는 특수 상황에서만 추가로 고려**하면 된다.

MCP context 비용 걱정: `chc`와 Codex 확장은 **MCP가 아니라 무관**하다. 자세한 내용은 [[#MCP와 context 비용]] 참고.

---

## Claude 쪽 — `chc` (`claude --chrome`)

### 이미 쓰고 있는 것

PowerShell 프로필(`Microsoft.PowerShell_profile.ps1`)에 등록된 alias:

```powershell
function chc {
    claude --chrome --dangerously-skip-permissions
}
```

`claude --help`에 `--chrome: Enable Claude in Chrome integration`으로 명시된 **Claude Code 내장 플래그**다. MCP 서버가 아니라 별도 통합 경로.

| 항목                                  | 내용                                                                                                                                                    |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| 연결 방식                               | **Native Messaging** — Windows 레지스트리(`HKCU\Software\Google\Chrome\NativeMessagingHosts\`)에 호스트를 등록해 브라우저의 "Claude in Chrome (Beta)" 확장(1.0.79)과 직접 통신 |
| 가능한 것                               | 스크린샷, DOM 읽기, 콘솔 로그, 네트워크 요청 확인, 클릭·타이핑·폼 자동작성, 탭·창 관리, GIF 녹화, 에러 확인 후 실시간 코드 수정                                                                     |
| `--dangerously-skip-permissions` 의미 | 모든 도구 권한 확인 스킵. 원래는 클릭·타이핑 같은 상태 변경에 Plan Mode 승인 필요 — 이 플래그로 건너뜀. 신뢰 안 되는 사이트에서 프롬프트 인젝션 위험 존재                                                       |
| 지원 범위                               | Chrome/Edge만 (Brave/Arc/WSL 미지원), Anthropic 직접 플랜(Pro/Max/Team) 필요 — Bedrock/Vertex 등 제3자 제공자 불가                                                      |
| 출시 이력                               | 베타(2025-11) → 정식(2025-12) → 현재 GA(2026)                                                                                                               |

### 대안이 필요할 때만: `chrome-devtools-mcp`

`chc`는 "실제 로그인된 브라우저로 웹 자동화"에 최적화돼 있다. 반면 성능 트레이스, 구조화된 네트워크/콘솔 데이터, headless 격리 실행처럼 **`chc`가 못 하는 것**이 필요하면 `chrome-devtools-mcp`를 MCP로 추가한다.

|          | `chc` (native)                    | `chrome-devtools-mcp` (MCP)                          |
| -------- | --------------------------------- | ---------------------------------------------------- |
| 연결 방식    | Native Messaging + 브라우저 확장        | MCP 서버 (Puppeteer 기반 CDP)                            |
| 이미 갖고 있나 | ✅ 지금 바로 됨                         | ❌ 별도 설치 필요                                           |
| 강점       | 실사용 브라우저(로그인 세션) 그대로, 범용 자동화      | 성능 프로파일링, 구조화 디버깅, headless 반복실행                     |
| 약점       | Chrome/Edge만, 확장 의존, 프롬프트 인젝션 리스크 | 로그인 세션 기본 미공유(필요시 `--browserUrl`로 기존 브라우저에 붙는 것도 가능) |

**확인된 사실**: 사용자 전역 설정(`~/.claude.json`)에 chrome-devtools-mcp는 애초에 추가된 적이 없다 (등록된 MCP는 context7·magic·docs-langchain·MCP_DOCKER·codegraph·pencil 6개뿐). "몇 개 뺐다"는 기억과 별개로 이건 "처음부터 없었던 것"이다.

**추가하려면** (공식 README, v1.5.0):
```bash
claude mcp add chrome-devtools --scope user npx chrome-devtools-mcp@latest
```
또는 플러그인 형태(MCP+Skills 포함):
```
/plugin marketplace add ChromeDevTools/chrome-devtools-mcp
/plugin install chrome-devtools-mcp@chrome-devtools-plugins
```

`chrome-devtools-mcp` 자체는 6개 오픈소스 CDP/MCP 후보 중 가장 신뢰도 높은 선택이다 — Google Chrome DevTools 팀 공식, 45.9k★, 주간 릴리스, 196개 의존 프로젝트로 실사용 검증됨. (다른 5개 후보 비교는 [[#참고 오픈소스 CDP·MCP 엔진 후보 6개]] 참고)

---

## Codex 쪽 — "Control Chrome with Codex"

### 이미 쓰고 있는 것

`chrome://extensions/`에 설치·활성화된 OpenAI 공식 확장.

| 항목 | 내용 |
|---|---|
| 정식 이름 / 버전 | **Control Chrome with Codex**, 1.1.5 |
| 게시자 | **OpenAI 공식** (openai-chrome-devs@openai.com) |
| Chrome 웹스토어 | https://chromewebstore.google.com/detail/codex/hehggadaopoacecdllhhajmbjkdcmajg |
| 사용자 수 | 2,000,000명, 평점 3.8/5 (307개 평가) |
| 출시일 | 2026-05-07, Codex 데스크톱 앱의 Plugins 시스템과 함께 |
| 오픈소스 여부 | 비공개 — 소스/라이선스 공개 없음 |
| 연결 방식 | 웹스토어에서 받아도 Codex 데스크톱 앱과 **native messaging host**로 handshake해야 작동 (앱 없이는 무용) |
| 요구 권한 | `"Access the page debugger"`(=`chrome.debugger`), 모든 사이트 읽기/쓰기, 로그인된 모든 기기의 브라우징 기록, 북마크, 다운로드 관리, `"Communicate with cooperating native applications"`, `"View and manage your tab groups"` |
| 탭 처리 방식 | 스레드별 전용 탭 그룹 생성, 사용자의 활성 탭은 건드리지 않음 |

즉 Claude 쪽 `chc`와 구조적으로 거의 동형이다: **Extension + Native Messaging Host + chrome.debugger 기반 CDP 제어**. Codex 쪽도 별도 설치·설정 없이 데스크톱 앱과 자동 handshake되므로, 그대로 쓰면 된다.

### 기술 검증 — "보라색 탭"은 특별한 기술이 아니었다

원문(hermes.txt)은 "chrome.debugger + tabGroups API로 보라색 탭 구조가 이론상 가능하다"고 **추측**만 했었다. 이번 조사로 그 추측이 실제 사례로 뒷받침됐다.

| 주장 | 판정 |
|---|---|
| `chrome.tabGroups.Color`에 "purple" 존재 | ✅ 확인됨 — 공식 문서 기준 grey/blue/red/yellow/green/pink/purple/cyan/orange 9종 |
| `chrome.debugger` API가 확장에 CDP 접근 제공 | ✅ 확인됨 — `"debugger"` 권한 선언 시 사용 가능 (단 Accessibility/CSS/DOM/Network/Page/Runtime 등 제한된 도메인만) |
| Codex 확장이 실제로 이 두 API를 쓴다 | ✅ 확인됨 — 웹스토어 권한 목록에 `chrome.debugger`+`chrome.tabGroups` 명시 |
| Claude in Chrome도 같은 API로 구현됐다는 근거 | ⚠️ 미확인(추정) — Anthropic 공식 자료에 직접 명시된 근거는 없으나, OpenAI가 동일 목적으로 같은 API 조합을 실제 배포한 사례가 정황 증거를 강화함 |
| "보라색"이라는 특정 색상 사용 근거 | ⚠️ 미확인 — tab 그룹 자체는 확인되나 색상 선택 근거는 못 찾음 |

---

## Hermes Agent 쪽 — CDP WebSocket 직접 연결

사용자가 별도로 쓰는 Nous Research의 오픈소스 에이전트 CLI **Hermes Agent**(MIT, 2026-02 출시, 이 PC의 **WSL**에서 실행 중, `/home/mychox`). Claude/Codex와 달리 **브라우저 확장도 native messaging host도 쓰지 않고, 순수 CDP WebSocket**으로 붙는다.

| 항목 | 내용 |
|---|---|
| 연결 방식 | `--remote-debugging-port`로 띄운 기존 Chrome/Brave/Chromium/Edge에 `/browser connect`로 직접 WebSocket 연결. 확장 프로그램·native messaging 없음 |
| 핵심 도구 | `browser` 툴셋(browser_navigate, browser_click 등 — 모든 백엔드 공통), `browser-cdp` 툴셋(`browser_cdp`, `browser_dialog` — CDP 직접 연결 시에만 활성화), `computer_use` 툴셋(OS 레벨 픽셀 자동화, 별도) |
| 기본 동작 모드 | ① 클라우드(Browserbase 등 관리형 브라우저) ② 자가생성(로컬 Chromium 새로 띄움) ③ 기존 브라우저 재사용(`/browser connect`) — 세 가지 지원 |
| 로그인 세션 활용 | ③ 모드에서는 가능 (hangwin/mcp-chrome과 같은 원리) |
| 오픈소스 여부 | ✅ MIT — 6개 오픈소스 후보와 같은 카테고리. 원리상 `chrome-devtools-mcp`와 가장 비슷함(둘 다 raw CDP, Puppeteer 래핑 유무만 다름) |

### 세 경로 한눈에 비교

| | `chc` (Claude) | Control Chrome with Codex | Hermes Agent `browser-cdp` |
|---|---|---|---|
| 연결 방식 | Native Messaging + 브라우저 확장 | Native Messaging + 브라우저 확장 | 순수 CDP WebSocket (확장 없음) |
| 확장 설치 필요 | ✅ Claude in Chrome (Beta) | ✅ Control Chrome with Codex | ❌ |
| 기존 로그인 세션 사용 | ✅ | ✅ | ✅ (`/browser connect` 시) |
| 오픈소스 | ❌ | ❌ | ✅ MIT |
| "자동으로 잡혀있나" | ✅ `chc` alias만 실행하면 끝 | ✅ 앱이 자동 handshake | ⚠️ Chrome을 `--remote-debugging-port`로 직접 띄우고 `/browser connect` 해야 함 — 완전 자동은 아님. WSL↔Windows 경계 넘는 연결이라 신경 쓸 점 추가됨 |

즉 Hermes Agent는 "이미 자동으로 잡혀서 쓴다"는 조건에는 chc·Codex 확장보다 한 단계 손이 더 간다. 대신 오픈소스라 내부를 뜯어볼 수 있고, 브라우저 확장에 의존하지 않는다는 점이 다르다.

---

## 참고: 오픈소스 CDP·MCP 엔진 후보 6개

원래 hermes.txt 리서치가 다룬 "Claude in Chrome을 대체할 오픈소스 클론/엔진" 후보들 (2026-07-05 웹 재검증). `chc`·Codex 확장으로 충분하지 않을 때 참고.

| 프로젝트 | 실존/공식 여부 | Star | 라이선스 | 최근 활동 | 성격 |
|---|---|---|---|---|---|
| **noemica-io/open-claude-in-chrome** | 개인, README에 "clean-room reverse-engineered" 명시 | 144★ | MIT | 활발 | Claude in Chrome의 Extension+MCP+Native Messaging+CDP 구조 재현. 18개 MCP tools 동일, 공식 도메인 차단목록 제거됨. **Claude in Chrome UX 클론이 필요할 때 1순위** (단, 정품 아니므로 구조 참고용) |
| **ChromeDevTools/chrome-devtools-mcp** | Google 공식 | 45.9k★ | Apache-2.0 | 매우 활발 (v1.5.0) | 위 "Claude 쪽" 섹션 참고 — **범용 CDP/MCP 엔진 1순위** |
| **hangwin/mcp-chrome** | 개인 | 12k★ | MIT | 활발 | 기존 로그인 세션 그대로 활용, 20+ 도구. 강력하지만 HTTP 브릿지(12306) 노출로 세션 하이재킹 위험 |
| **BrowserMCP/mcp** | 개인/소규모 팀 | 6.8k★ | Apache-2.0 | 성숙도 낮음 | Playwright MCP 파생, 기존 브라우저 프로필 사용 |
| **nanobrowser** | 개인 | 13.4k★ | Apache-2.0 | 활발 | CDP 엔진 아님 — 멀티에이전트 자동화 확장(UX 참고용) |
| **williamkapke/kapture** | 개인 | 164★ | MIT | 활발 | DevTools 패널 없이도 백그라운드 동작, WebSocket 멀티클라이언트 |

---

## MCP와 context 비용

- `chc`(`--chrome`)와 "Control Chrome with Codex"는 **MCP가 아니다** — 둘 다 native/브라우저 확장 통합이라 별도 tool 스키마 뭉치를 등록하지 않는다. MCP 서버의 context 비용 문제와 무관.
- `chrome-devtools-mcp`는 **진짜 MCP 서버**라 붙이면 tool 스키마가 등록된다. 다만 이 하네스는 MCP 도구를 "deferred tool"로 처리해서, 연결돼 있어도 이름만 노출되고 실제 호출 전까진 전체 스키마가 로딩되지 않는 걸 이번 세션에서 확인함(WebSearch/WebFetch가 그 예). 하네스/클라이언트에 따라 이 방식이 아니면 진짜로 context를 먹을 수 있다.
- 사용자 전역 설정에 원래 있던 MCP는 context7·magic·docs-langchain·MCP_DOCKER·codegraph·pencil 6개뿐이고, chrome-devtools-mcp는 애초에 추가한 적이 없다.

---

## 참고 노트 (볼트 내 관련, 직접 겹치지는 않음)

| 노트 | 내용 |
|---|---|
| [[GitHub-ChromeDevTools-chrome-devtools-mcp-Chrome-D-7db0c3b0-a0958cc4bbb8]] | chrome-devtools-mcp GitHub 소스 자동 임포트 요약 |
| [[u260327_yeopo92_ChromeDevTools_d27fce]] | Threads 공유, ChromeDevTools 관련 |
| [[u260422_cpa_chan27_Playwright와-Ch_d2f34b]] | Playwright vs Chrome DevTools MCP 비교, CDP 직접 통신 설명 |
| [[u260327_lian.lab71_Chrome-Claude-_04bc29]] | Claude Code + Chrome 조합 소개 |
| [[u260422_masterkeyai_구글이-크롬-브라우저에-S_4824a0]] | 구글 Chrome Skills vs "클로드 인 크롬 유료 구독" 비교 언급 |

## 원본 출처 — 그리고 왜 6개 후보를 떠들었나

2026-07-04 헤르메스단 카톡방, "이 채팅방은 저의 일기장 입니다" 님이 오전 10:39에 공유한 리서치 원문 (`v3/inputs/2026-07-04/hermes.txt` 355~432행). 리포트에는 `hermes-topic-6`으로 요약됨.

**질문의 출발점이 사용자와 원래 다르다.** 원문 대화를 보면 그 사람들의 질문은 "지금 개발할 때 뭘 쓸까"가 아니었다:

1. **호기심/리버스엔지니어링 관심에서 시작.** "사카나 후구 울트라"(일본 오케스트레이션 AI)를 이것저것 써보다가 "후구로 좋은거 하나 찾아왔습니다"라며 던진 흥미거리였다 — "Claude in Chrome이 대체 어떻게 만들어졌길래 저런 게 되지?"에 대한 궁금증.
2. **유료 구독 접근 문제일 가능성.** 볼트 노트([[u260422_masterkeyai_구글이-크롬-브라우저에-S_4824a0]])에 "클로드 인 크롬 유료 구독"이라는 언급이 있고, 실제로 이번에 확인한 공식 문서상 `--chrome`은 Anthropic 직접 유료 플랜(Pro/Max/Team)이 있어야 쓸 수 있다. 유료 구독이 없는 사람에게는 오픈소스 클론이 "비슷한 걸 무료로 만들어보자"는 실질적 동기가 된다.
3. **자체 프로젝트에 심을 엔진을 고르던 중이었을 가능성.** 원문 끝에 "Yuna Browser Bridge가 감싸기 좋음"이라는 문장이 있다 — 자기만의 브라우저 자동화 에이전트("Yuna")를 만드는 프로젝트가 있고, 거기 들어갈 CDP 엔진을 비교하던 맥락으로 읽힌다. 이 경우엔 "Claude Code 디버깅용"이 아니라 "내 프로젝트에 넣을 엔진"이 필요한 것이므로 6개 후보 비교가 의미 있다.

즉 원문의 질문("Claude in Chrome을 대체할 오픈소스가 있나")과 사용자의 질문("chc가 이미 되는데 이거보다 나은 대체제가 있나")은 출발점 자체가 다르다 — 전자는 클론/자체 구축 관점, 후자는 이미 되는 걸 확인하는 실용적 관점이다.

## Sources

- https://github.com/noemica-io/open-claude-in-chrome
- https://github.com/ChromeDevTools/chrome-devtools-mcp
- https://github.com/hangwin/mcp-chrome
- https://github.com/BrowserMCP/mcp
- https://github.com/nanobrowser/nanobrowser
- https://github.com/williamkapke/kapture
- https://developer.chrome.com/docs/extensions/reference/api/tabGroups
- https://developer.chrome.com/docs/extensions/reference/api/debugger
- https://help.openai.com/en/articles/11369540-icodex-in-chatgpt
- https://chromewebstore.google.com/detail/codex/hehggadaopoacecdllhhajmbjkdcmajg
- https://developers.openai.com/codex/app/chrome-extension
- https://developers.openai.com/codex/app/browser
- https://code.claude.com/docs/en/chrome
- https://support.claude.com/en/articles/12902428-using-claude-in-chrome-safely
- https://github.com/NousResearch/hermes-agent
- https://hermes-agent.nousresearch.com/docs/developer-guide/browser-supervisor
- https://hermes-agent.nousresearch.com/docs/user-guide/features/browser/
