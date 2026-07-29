---
source: session
query: "bl(Bailian CLI)이 우리 프로젝트의 Alibaba Model Studio MCP/CLI랑 뭐가 다른지, 같이 써도 충돌 안 나는지, Token Plan 업그레이드하면 OCR/TTS가 되는지"
created_at: 2026-07-23T12:21:40.000Z
origin: "대화 중 사용자가 다른 채팅방(카잣둠 발화 기준, 새벽 2시경)에서 공유한 bl(Bailian CLI) 소개 로그를 직접 붙여넣음 — 저장된 원본 파일 없음"
related:
  - "[[2026-07-21_Alibaba-Cloud-Model-Studio-Token-Plan]]"
  - "[[20260721-235147-gjc-랑-alibaba-연결하듯이-omp를-연결하는-방법을-찾아]]"
  - "[[2026-07-21_gjc-Alibaba-TokenPlan-연동]]"
publish: false
---

# bl(Bailian CLI) vs 우리 Alibaba Model Studio MCP/CLI 비교

> [!question] 질문
> "카잣둠이 새벽 2시경 Bailian CLI(bl 명령어)를 소개하며 시작됐다..." 로 시작하는 채팅방 로그를 근거로 —
> 1. bl이 `D:\AI\260721-AlibabaModelStudioMCP` 프로젝트의 MCP 서버·CLI랑 다른 것인지
> 2. gjc에 설치하면 gjc에서만 쓰는 건지, CLI라서 어디서나 되는지
> 3. 같이 써도 충돌 안 나는지, 그럼 우리 것 안 써도 되는 거 아닌지
> 4. Token Plan을 다른 요금제로 업그레이드하면 OCR/TTS가 되는지

## TL;DR

- **bl은 완전히 다른 도구다.** Alibaba(또는 커뮤니티)가 배포하는 별도 npm 패키지(`bailian-cli`)로, 이미지·영상뿐 아니라 TTS·ASR·웹서치·RAG·장기메모리까지 10개+ 기능을 하나의 CLI로 묶고 `npx skills add`로 여러 코딩 에이전트에 자동 연결해주는 범용 브리지다. 우리 프로젝트(`mcp_server.py` MCP 서버 6 tool + `cli/alibaba` 독립 CLI)는 이미지·영상·채팅만 다루는, 직접 만들고 실제 API로 검증한 좁은 범위의 도구다.
- **설치는 gjc 전용이 아니라 전역이다.** `npm install -g`로 깔리는 일반 바이너리라 gjc든 Claude Code든 어떤 에이전트의 bash에서도 `bl ...`을 그대로 칠 수 있다. `npx skills add`는 "설치 범위"가 아니라 각 에이전트가 알아서 먼저 나서서 bl을 호출하게 만드는 자동화 스위치일 뿐이다.
- **같이 써도 기술적 충돌은 없다.** 바이너리명(`alibaba` vs `bl`), MCP 네임스페이스와 Skill 메커니즘, 결과물 저장 경로, 인증 정보 저장 위치가 전부 다르다. 다만 이미지/영상처럼 기능이 겹치는 영역에서는 Claude가 어느 경로를 쓸지 애매해질 수 있고, 같은 Token Plan 계정 쿼터를 공유해서 사용량 구분이 어려워질 수 있다.
- **완전 대체는 아니다.** omp/gjc는 bl의 공식 지원 목록(Qwen Code/Cursor/Claude Code/Cline/Kilo Code/OpenCode)에 없어서, bl을 도입해도 `cli/alibaba`는 계속 필요하다. 이미지/영상은 우리 쪽이 이미 실제 API로 검증까지 끝난 상태라 그대로 유지하는 게 낫고, bl은 TTS/RAG/장기메모리처럼 우리한테 없는 기능을 보완하는 용도로 검토하는 게 합리적이다.
- **Token Plan은 등급을 올려도 OCR/TTS/STT가 안 된다.** 공식 문서(help.aliyun.com, alibabacloud.com)를 확인한 결과, 개인판(Lite/Standard/Pro)·팀판(Standard/Pro/Max 좌석) 어느 등급의 "지원 모델" 표에도 `qwen-vl-ocr`/`qwen-tts`/`paraformer` 계열이 없다. 등급 차이는 사용량 한도(Credits)뿐이라 상위 등급으로 올려도 모델이 추가되지 않는다. 이는 MCP 서버 개발 중 실측했던 `404 Model not exist`(Token Plan 자체의 한계)라는 결론과 정확히 일치한다.

## 최종 결론 — bl 미설치 확정 (2026-07-23 후속 대화)

같은 세션에서 이어진 대화 끝에 **"bl은 설치 안 해도 된다"로 결정.** 근거:

### 기능별 비교표

| 항목 | bl | 우리 MCP (`mcp_server.py`) | 우리 CLI (`cli/alibaba`) |
|---|---|---|---|
| 채팅/텍스트 | ✅ | ✅ | ❌ |
| 이미지 생성/편집 | ✅ | ✅ (검증 완료) | ✅ (검증 완료) |
| 영상 생성 (t2v/i2v/r2v) | ✅ | ✅ (검증 완료) | ✅ (검증 완료) |
| TTS(음성합성) | ⚠️ 워크어라운드 필요 | ❌ Token Plan 미포함 | ❌ Token Plan 미포함 |
| STT/ASR | ❌ 시도했으나 실패 | ❌ Token Plan 미포함 | ❌ Token Plan 미포함 |
| OCR/Vision | 미확인 | ❌ Token Plan 미포함 | ❌ Token Plan 미포함 |
| 웹서치 | ✅ | ❌ (단, **Claude Code 자체 내장 WebSearch/WebFetch로 이미 대체됨**) | ❌ |
| RAG | ✅ | ❌ (대체 수단 없음 — **유일하게 순수한 갭**) | ❌ |
| 장기메모리 | ✅ | ❌ (단, **Claude Code 자체 세션 간 메모리 시스템으로 이미 상당 부분 대체됨**) | ❌ |

### 결정 근거

- 표면적으로는 bl에만 있는 기능이 웹서치·RAG·장기메모리 3개로 보였지만, 그중 **웹서치와 장기메모리는 Claude Code 자체에 이미 내장** 되어 있어(WebSearch/WebFetch 도구, 세션 간 파일 기반 메모리 시스템) bl을 깔 실익이 없음.
- 순수하게 새로 얻는 건 **RAG(사용자 문서 코퍼스 검색)** 하나로 좁혀지는데, 이거 하나 때문에 별도 npm 전역 패키지를 설치할 필요는 없다고 판단.
- 이미지/영상은 이미 우리 MCP/CLI가 실제 API로 검증까지 끝났고 bl보다 완성도가 높다고 판단됨(bl은 TTS 워크어라운드, STT 실패 등 거친 부분이 확인됨).
- 참고로 `npm install -g` 자체가 최근 npm 공급망 공격(Mini Shai-Hulud) 경고 대상이라는 점도 설치를 굳이 서두를 이유를 낮추는 요인.

**최종**: bl 미설치. 필요 기능이 새로 생기면(특히 RAG) 그때 재검토.

## 1. bl은 우리 mcp/cli와 다른 도구인가

| 구분 | bl (Bailian CLI) | 우리 프로젝트 |
|---|---|---|
| 배포 주체 | Alibaba/커뮤니티가 배포하는 npm 패키지(`bailian-cli`) | 이 저장소에서 직접 구현 |
| 설치 | `npm install -g bailian-cli` (전역) | MCP 서버는 `claude mcp add`, CLI는 `~/.local/bin/alibaba` 수동 설치 |
| 연동 방식 | `npx skills add modelstudioai/cli --all -g` — 각 에이전트 Skills 디렉토리에 "언제 bl을 호출할지" 자동 등록 | MCP 프로토콜(`mcp__alibaba-model-studio__*`, Claude Code 전용) + omp/gjc용 독립 bash CLI |
| 지원 에이전트 | Qwen Code, Cursor, Claude Code, Cline, Kilo Code, OpenCode | Claude Code(MCP) + omp/gjc(CLI, bash 실행 전용 슬래시 커맨드 구조라 MCP 경로 자체가 없음) |
| 기능 범위 | 이미지·영상 생성/편집, TTS(CosyVoice), ASR(FunAudio), 웹서치, RAG, 장기메모리 등 10개+ | chat, `generate_image`(+editing), `generate_image_async`, `generate_video`(t2v/i2v/r2v), `poll_task`, `list_models` — 6개 tool만 |
| 검증 상태 | TTS/STT는 워크스페이스 전용 키 제약으로 `bl omni --base-url` 우회 필요, STT는 파일 업로드 실패로 끝내 성공 못 함(카잣둠 공유 로그 기준) | 6개 tool·CLI 서브커맨드 전부 실제 API 호출로 검증 완료(이미지·영상은 다운로드까지 확인) |

**결론**: 겹치는 부분(이미지/영상)도 있지만 구현 주체·프로토콜·기능 범위가 다른 별개 도구. bl이 범위는 넓지만 완성도(특히 TTS/STT)는 아직 거칠고, 우리 쪽은 좁지만 실측 검증이 끝난 상태.

## 2. gjc에 설치하면 gjc 전용인가

아니다. `bl`은 npm 전역 설치라서 바이너리 자체는 시스템 어디서나 실행 가능하다. `npx skills add`로 하는 건 "설치 범위 제한"이 아니라 특정 에이전트가 **알아서 먼저** bl을 호출하도록 만드는 스위치일 뿐 — 스킬이 등록 안 된 에이전트도 bash로 `bl ...`을 직접 치면 똑같이 동작한다.

(장기 메모리 기능 자체가 어느 저장소에 귀속되는지는 별개 문제 — bl 소스를 직접 본 적이 없어 확정할 수 없고, 계정/워크스페이스 단위 클라우드 저장이면 에이전트 무관하게 공유되고 로컬 파일 캐시면 머신 단위로 갈릴 것이라는 추정만 가능. 확인하려면 `bl memory --help`나 실측 필요.)

## 3. 같이 써도 충돌 안 나나 / 우리 것 안 써도 되나

**충돌 없음** — 바이너리명(`alibaba` vs `bl`), Claude Code 등록 방식(MCP 서버 vs Skill), 결과물 저장 경로(`D:\AI\260721-AlibabaModelStudioMCP\maas-output\` vs bl 자체 경로), 인증 정보 저장 위치(`C:\Users\HOME\.secrets\all-keys.env` 직접 읽기 vs `bl auth login`의 자체 설정 파일)가 전부 다르다.

**중복으로 인한 애매함** — 이미지/영상처럼 기능이 겹치는 영역에서는 Claude가 MCP tool과 bl skill 중 어느 경로를 쓸지 헷갈릴 수 있고, 같은 Token Plan 계정 쿼터를 공유해서 어느 도구가 얼마나 썼는지 사용량 추적이 어려워질 수 있다.

**완전 대체 불가한 이유** — omp/gjc는 bl 공식 지원 목록에 없다(`docs/decisions/004-standalone-cli-for-omp-gjc.md`에서 이미 omp/gjc 소스를 직접 읽어 "MCP도 못 타고 Skills 메커니즘도 없다"는 걸 확인한 상태). `cli/alibaba`를 없애면 omp/gjc는 도로 아무것도 못 쓰게 될 위험이 있다. 또 이미지/영상만 놓고 보면 우리 쪽이 이미 실제 API로 파이프라인 끝까지 검증됐고, 참고 레포보다 실측값이 더 정확했던 지점(r2v 미디어 타입)도 있었다.

**결론**: 완전 대체보다 "역할 분담"이 합리적. Claude Code에서 이미지/영상만 쓴다면 지금 것 유지, TTS/ASR/RAG/장기메모리처럼 우리한테 없는 기능이 필요하면 bl을 추가로 얹는 방향.

## 4. Token Plan 업그레이드하면 OCR/TTS 되나

**안 된다.** 공식 문서를 확인한 결과:

- Token Plan 개인판(Lite/Standard/Pro)·팀판(Standard/Pro/Max 좌석) 전부 "지원 모델" 표에 있는 건 텍스트(qwen3.8-max-preview, qwen3.7-max/plus, qwen3.6-flash, glm-5.2, deepseek-v4-pro)와 이미지/영상(wan2.7-image(-pro), happyhorse-1.1 계열)뿐.
- `qwen-vl-ocr`(OCR), `qwen-tts`/`qwen3-tts`(TTS), `paraformer`(STT) — 이 세 모델군은 개인판이든 팀판이든 **어느 등급 표에도 없다.**
- 등급 간 차이는 사용량 한도(Credits)뿐이고, 상위 등급으로 올려도 모델이 추가되지 않는다.
- 이는 이 프로젝트의 MCP 서버 개발 중 실측했던 `HTTP 404 {"code":"InvalidParameter","message":"Model not exist."}`(OCR/TTS/STT 세 모델명 전부 동일 결과) 결론과 정확히 일치 — 버그나 일시 제한이 아니라 **Token Plan이라는 상품 자체가 OCR/TTS/STT를 안 판다.**
- 실제로 쓰려면 Token Plan이 아니라 별도 **Pay-as-you-go(종량제)** 결제 방식으로 전환해야 한다. 정확한 절차는 콘솔(modelstudio.console.aliyun.com)에서 확인 필요.

## 참고 자료

- [help.aliyun.com/zh/model-studio/token-plan-overview](https://help.aliyun.com/zh/model-studio/token-plan-overview)
- [help.aliyun.com/zh/model-studio/token-plan-personal-overview](https://help.aliyun.com/zh/model-studio/token-plan-personal-overview)
- [alibabacloud.com/help/en/model-studio/token-plan-overview](https://www.alibabacloud.com/help/en/model-studio/token-plan-overview)
- [help.aliyun.com/zh/model-studio/qwen-vl-ocr](https://help.aliyun.com/zh/model-studio/qwen-vl-ocr)
- 프로젝트 실측 근거: `D:\AI\260721-AlibabaModelStudioMCP\context-notes.md`("확인됨 — 사용 불가" 절), `docs/decisions/004-standalone-cli-for-omp-gjc.md`
- 이 프로젝트의 learning map: `D:\obsidian\Projects\LearningMaps\d__ai__260721-alibabamodelstudiomcp\`(7. 대안 도구(bl/Bailian CLI) 비교 검토 항목에 같은 내용 요약 있음 — 이 노트가 전문, map/journal은 한 줄 요약)

## 참고 노트

| 노트 | 태그 | 요약 |
|------|------|------|
| [[2026-07-21_Alibaba-Cloud-Model-Studio-Token-Plan]] | `alibaba` `token-plan` `api` | Token Plan Base URL 2종, 사용 가능 모델 목록, MCP 서버 구현 기록 |
| [[20260721-235147-gjc-랑-alibaba-연결하듯이-omp를-연결하는-방법을-찾아]] | `omp` `gjc` `alibaba` | omp/gjc를 Alibaba Token Plan에 붙이는 방법(같은 계열 작업, 이 노트와 배경 공유) |
| [[2026-07-21_gjc-Alibaba-TokenPlan-연동]] | `gjc` `alibaba` `token-plan` | gjc를 Alibaba Token Plan 커스텀 provider로 붙인 전체 작업 기록 |
