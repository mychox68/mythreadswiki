# AWS
> 수동 작성 노트(세션 기반, `build_wiki_concepts.py` 자동 파이프라인 아님) · 최초 작성: 2026-07-05 · 볼트 내 직접 소스 2개 + 일반 지식

## 개요

**AWS(Amazon Web Services)** 는 아마존이 운영하는 세계 최대 클라우드 플랫폼. 200개 이상의 서비스를 제공하며, [[Explorations/20260705-114727-s3-amplify-vercel-백엔드-배포-논쟁|S3·Amplify·Vercel 배포 논쟁 노트]]에 나온 S3·Elastic Beanstalk·RDS·Lightsail이 전부 AWS 서비스 중 일부다.

## 핵심 서비스 지도 (배포 관점)

| 분류 | 서비스 | 역할 |
|---|---|---|
| 컴퓨트 (원시 단위) | EC2 | 가상 서버. Elastic Beanstalk·Lightsail이 이 위에 얹혀서 관리 부담을 줄여줌 |
| PaaS | Elastic Beanstalk | EC2+오토스케일링+로드밸런서를 자동 구성, 코드만 올리면 배포 |
| VPS (단순 가상서버) | Lightsail | AWS판 단순화 서버 상품 — DigitalOcean Droplet과 같은 포지션 |
| 객체 스토리지 | S3 | 파일/이미지 저장의 업계 표준. 강점은 생태계 통합, 약점은 egress fee |
| 관리형 DB | RDS | 백업·패치·복제를 AWS가 대행하는 관계형 DB |
| 서버리스 함수 | Lambda | 서버 없이 함수 단위로 실행, 사용한 만큼만 과금 |
| NoSQL | DynamoDB | 완전관리형 키-값/문서 DB |
| 프론트 호스팅 | Amplify | AWS 생태계 통합형 프론트 호스팅. Next.js 최신 기능 지원은 Vercel보다 한 세대 늦다는 평 |

## 왜 복잡하게 느껴지나

- 서비스가 200개 이상이라 "AWS를 배운다"는 사실상 개별 서비스를 하나씩 배우는 것에 가깝다 — 한 덩어리 지식이 아니다.
- 같은 목적("서버 하나 띄우기")도 EC2(직접 관리) / Lightsail(단순화) / Elastic Beanstalk(자동화 PaaS) / Lambda(서버리스)처럼 추상화 수준이 다른 여러 선택지가 있다.
- 초심자에게 반복되는 조언은 "전부 알 필요 없다, 지금 필요한 조합(예: Beanstalk+RDS+S3)부터 완주하고 나머지는 필요할 때 그때그때 배우라"는 쪽으로 수렴한다 (자세한 배경은 [[Explorations/20260705-114727-s3-amplify-vercel-백엔드-배포-논쟁|배포 논쟁 노트]] 참고).

## 관련 개념

[[Concepts/Vercel|Vercel]] | [[Concepts/Supabase|Supabase]] | [[Concepts/클라우드|클라우드]]

## 참고 노트 (볼트 내 실제 소스)

| 노트 | 저자·날짜 | 요약 |
|---|---|---|
| [[Top-50+-AWS-Services-Explained-in-10-Minutes-dbe5b8a88f7a]] | Fireship · 2026-06-28(임포트) | AWS는 200개 이상 서비스를 제공하는 세계 최대 클라우드 플랫폼. EC2·S3·Lambda·DynamoDB·RDS 등 핵심 서비스를 10분 안에 소개 |
| [[AWS-Summit-Seoul-5983cb95203c]] | - · 2026-06-28(임포트) | AWS가 매년 여는 클라우드 컨퍼런스 "AWS 서밋 서울" 소개 페이지 |

볼트 안에 AWS를 직접 다룬 노트는 아직 이 2개뿐이라, 다른 Concepts 노트(Vercel·Supabase 등)처럼 수십 개 노트를 모아 패턴을 뽑는 "Agent Insight" 단계는 아직 생략함 — 관련 노트가 쌓이면 추가.

## 다음에 하나씩 쪼갤 것

- [ ] Elastic Beanstalk 단독 개념 노트 (PaaS 상세)
- [ ] S3 / egress fee 단독 개념 노트
- [ ] RDS 단독 개념 노트
- [ ] Lightsail 단독 개념 노트
