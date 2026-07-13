---
tags: [index]
---

# Explorations 색인

파일명이 `YYYYMMDD-HHMMSS-슬러그.md`라 폴더 뷰에서 이름순 정렬 = 최신순 정렬이 된다. 그래도 개수가 늘면 아래 Dataview 표가 제일 빠르다 — `출처`/`생성일`/`원본` 컬럼으로 바로 훑거나 정렬해서 찾는다.

```dataview
TABLE WITHOUT ID
    link(file.link, title) AS "노트",
    source AS "출처",
    query AS "질문",
    created_at AS "생성일",
    origin AS "원본(채팅/문서)"
FROM "Wiki/Explorations"
WHERE file.name != "_INDEX"
SORT created_at DESC
```

## source 값 의미

| source | 의미 |
|---|---|
| `kb_query` | `/ask-vault`로 볼트 자체를 검색한 결과 |
| `research` | 딥리서치 스킬 등으로 웹을 조사한 결과 |
| `session` | 대화 세션 내 분석(카톡방 리포트 등 외부 자료 기반, 웹 검색 없음) |

`source:session` 노트는 보통 `origin` 필드에 원본 채팅/문서 경로가 달려 있다 (예: `[[v3/inputs/2026-07-04/hermes.txt]]`).
