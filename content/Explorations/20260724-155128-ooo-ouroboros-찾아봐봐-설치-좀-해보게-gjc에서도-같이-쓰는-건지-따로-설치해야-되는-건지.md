---
source: kb_query
query: "ooo (ouroboros) 찾아봐봐 설치 좀 해보게 gjc에서도 같이 쓰는 건지 따로 설치해야 되는 건지"
created_at: 2026-07-24T06:51:28.490Z
provider: claude-code
sources:
  - "[[GitHub-Q00-ouroboros-Agent-OS-Stop-prompting.-Star-abe6cdaa-02b619eb80e4]]"
publish: false
---

# ooo (ouroboros) 찾아봐봐 설치 좀 해보게 gjc에서도 같이 쓰는 건지 따로 설치해야 되는 건지

> [!question] 질문
> ooo (ouroboros) 찾아봐봐 설치 좀 해보게 gjc에서도 같이 쓰는 건지 따로 설치해야 되는 건지

## 답변

**Ouroboros는 지금 Claude Code(omc 하네스)에는 이미 설치돼 있다** — 플러그인 `ouroboros@ouroboros` v0.50.5가 `claude plugin install`로 들어와 있고(2026-07-20), MCP 서버(`mcp__ouroboros__*`)도 세션에 붙어 있는 상태 (참고: [노트 1]).

**GJC는 별도 설치가 필요하다.** Claude Code 플러그인 설치는 GJC로 자동 전파되지 않는다.

- `gjc mcp` 명령어 자체 문서에 "Claude Code / Codex / OpenCode 등의 라이브 MCP 설정을 상속하지 않는다"고 명시돼 있음 (`gjc mcp add/list/remove`는 독립 저장소).
- 실제로 `gjc mcp list` 결과 등록된 MCP 서버 0개.
- 지금 gjc 버전(v0.11.7)은 "storage-only" 상태라, MCP를 등록해도 일반 gjc 세션이 자동으로 로드하지 않음.

다만 Ouroboros 쪽엔 **GJC 전용 런타임 어댑터**가 이미 준비돼 있다 (플러그인 캐시 안 `docs/runtime-guides/gjc.md`). 이건 MCP 등록이 아니라 GJC를 서브프로세스(`gjc --mode rpc`)로 구동하는 별개 통합 방식이다.

### GJC에 붙이려면

```bash
pip install ouroboros-ai        # 이 머신엔 pip 패키지 자체가 안 깔려 있음 (Claude Code 플러그인 버전만 있음)
ouroboros setup --runtime gjc   # gjc 사이드에 ooo 브릿지 확장(<agent-dir>/extensions/ouroboros-ooo-bridge) 설치
```

이러면 GJC 세션 안에서 `ooo interview ...` 같은 명령을 쓸 수 있게 된다. 확인 시점 기준 이 브릿지도 설치 안 된 상태 (`~/.gjc/agent`에 extensions 폴더 자체가 없음).

즉 **"같이 쓰는 것"이 아니라 "각 하네스마다 따로 설치/셋업"** 구조. Claude Code는 이미 끝났고, GJC는 `pip install ouroboros-ai` + `ouroboros setup --runtime gjc`가 필요하다.

## 참고 노트

| 노트 | 태그 | 요약 |
|------|------|------|
| [[GitHub-Q00-ouroboros-Agent-OS-Stop-prompting.-Star-abe6cdaa-02b619eb80e4]] | `web` `AI` `GITHUB.COM` `Harness` | Ouroboros는 비구조적 프롬프트 대신 명세 기반으로 AI 코딩 워크플로우를 지원하는 에이전트 OS. 여러 AI CLI와 통합 가능. |
