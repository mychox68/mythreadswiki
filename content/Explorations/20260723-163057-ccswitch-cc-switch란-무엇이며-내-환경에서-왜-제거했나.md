---
source: kb_query
query: "ccswitch.io(cc-switch)란 무엇이며 내 ai-profiles 환경에서 왜 제거했나"
created_at: 2026-07-23T07:30:57.803Z
provider: claude-code
sources: []
publish: false
---

# ccswitch.io(cc-switch)란 무엇이며 내 ai-profiles 환경에서 왜 제거했나

> [!question] 질문
> ccswitch.io(cc-switch)란 무엇이며 내 ai-profiles 환경에서 왜 제거했나

## 답변

### 1. cc-switch가 뭔가

`ccswitch.io` 는 **cc-switch**(farion1231/cc-switch)라는 오픈소스 **데스크톱 앱**의 공식 사이트다. Claude Code 하나만이 아니라 여러 AI 코딩 툴의 **설정(프로바이더/API)을 GUI로 갈아끼우는 통합 관리기**다. 설정 파일을 손으로 안 고치고 클릭 한 번으로 프로바이더를 전환하는 게 핵심.

- **지원 대상 (8개)**: Claude Code, Claude Desktop, Codex, Gemini CLI, Grok Build, OpenCode, OpenClaw, Hermes Agent.
- **주요 기능**: 프로바이더 전환(50+ 프리셋, 핫스위칭 + 페일오버 로컬 프록시), MCP·Skills 통합 관리, 시스템 트레이 즉시 전환, 사용량/토큰/비용 추적, 세션 매니저, 클라우드 동기화(Dropbox/OneDrive/iCloud/WebDAV).
- **데이터 위치**: `~/.cc-switch/` 한 폴더에 SQLite DB(`cc-switch.db`) + 백업 + 설정이 모인다.

### 2. 내 환경과의 충돌 리스크 (핵심)

cc-switch는 전환 시 **각 툴의 실제 설정 파일을 직접 덮어쓰고**, skills를 자기 방식으로 심볼릭 링크한다. 그런데 내 `~/.claude` 는 이미 **Junction → `.ai-profiles/profiles/claude/<하네스>/.claude`** 구조이고, 그 트리 전체를 **260506-ManageByAgentProfiles(Python) 도구가 SSOT로 관리**한다. cc-switch가 skills를 자기 저장소로 옮기거나 설정을 덮어쓰면 **관리자가 둘이 되어 충돌**한다. 특히 cc-switch 설정의 `skillStorageLocation: cc_switch` + `skillSyncMethod: auto` 조합이 그 지점.

### 3. 실제 점검 결과 — 피해는 없었다

어제(7/22) 잠깐 써서 뭔가 틀어진 것 같다는 의심으로 점검했으나:

- **claude `settings.json` 깨끗**: `env: {}` (API 키·base URL 주입 흔적 없음), statusLine도 wrapper 경로 정상.
- **skills 심볼릭 링크 전부 정상**: 여전히 `ai-profiles/shared` 와 `.agents/skills` 기준으로 링크됨. cc-switch 자기 skills 폴더(`~/.cc-switch/skills`)는 **아예 생성조차 안 됨** → skills sync는 한 번도 실행 안 됨.
- cc-switch가 남긴 건 **`GEMINI_API_KEY` 환경변수 충돌 감지 로그**(레지스트리 `HKCU\Environment`의 Gemini 키 발견) 하나뿐. claude 설정은 안 건드림.
- 어제 statusline이 안 뜬 건 cc-switch가 아니라 그때 직접 만진 부분이었고 이미 복구됨.

### 4. 제거 절차와 결과

MSI 설치본이었다(winget엔 미등록이라 레지스트리 GUID로 제거). 진행한 순서:

1. 프로세스 종료 — `taskkill /F /IM cc-switch.exe` (PID 12244)
2. MSI 제거 — 레지스트리 UninstallString의 GUID `{43804B6E-DDC1-4E17-9338-A21B70799BF3}` 로 `msiexec /X{GUID} /qn /norestart`
3. 데이터 폴더 삭제 — `Remove-Item -Recurse -Force "$env:USERPROFILE\.cc-switch"`

**최종 검증**: 설치 폴더 ✅ 삭제 / 데이터 폴더 ✅ 삭제 / 레지스트리 ✅ 삭제 / 프로세스 ✅ 없음. ai-profiles 체계 손상 없어 `assets.py link` 복구는 불필요했다.

### 5. 판단

여러 프로바이더·계정을 돌려쓰는 사람에겐 편한 툴이다. 하지만 나처럼 **ai-profiles junction + Python 관리도구로 설정 SSOT 체계가 이미 잡혀 있으면 관리자가 둘이 되어 충돌 소지만 생기므로**, 도입하지 않고 제거한 게 맞는 선택이다. 굳이 쓴다면 **Skills/MCP 관리 기능은 끄고**, 프로바이더 전환만 포터블 ZIP으로 임시 사용하는 선에서.

## 참고 노트

볼트 내부 근거 노트 없음(이 노트는 직전 대화 — 웹 조사 + 로컬 시스템 점검 — 를 정리한 것). 웹 출처만 아래에 링크.

## 웹 출처

- [farion1231/cc-switch (GitHub)](https://github.com/farion1231/cc-switch)
- [ccswitch.io 공식 문서](https://ccswitch.io/en/docs?section=getting-started)
