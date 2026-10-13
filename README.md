# 김다연 (Kim Dayeon)

[이메일](mailto:danhandev@gmail.com) · [기술 블로그](https://danhandev.tistory.com/)

---

## Projects

### 코어뱅크 — 헥사고날 아키텍처 기반 코어뱅킹 서버
`2026.07 ~ 진행중` · 7인 팀 (신한DS 금융SW 과정 연계) · **상품 · 상품가입 도메인 담당**
Java 21 · Spring Boot 4 · MySQL · Flyway · Querydsl · ArchUnit · Testcontainers

- 상품 도메인을 엔티티부터 Querydsl 동적 목록 조회 API까지 엔드투엔드로 구현하고, 상품가입 도메인을
  약관동의 이력까지 포함해 17개 파일 · 704줄 규모로 신설했습니다.
- 도메인과 JPA 엔티티가 결합된 **레이어 위반 33개 파일**을 찾아 리팩터링하고, ArchUnit으로 헥사고날
  의존 방향을 자동 검증하는 테스트를 도입해 같은 위반이 다시 들어오지 못하게 막았습니다.
- 담당 외 영역(계좌 · 자동이체 · 인증 · CI) PR 8건을 리뷰하고 3건에 수정 요청 후 재검토했습니다.

→ [corebank-tech/corebank-server](https://github.com/corebank-tech/corebank-server)

### 앳크루 — 크리에이터 포트폴리오 · 구인 매칭 플랫폼
`2026.06 ~ 진행중` · 백엔드 단독
Java 21 · Spring Boot 4 · Spring Modulith · MariaDB · Elasticsearch · Cloudflare R2 / Worker

- 라이트 운영에서 확인한 도메인 간 강결합을 해소하기 위해 도메인 모델부터 다시 정의하고,
  모듈형 모놀리식(Spring Modulith)으로 모듈 경계를 강제했습니다. 신규 도메인 5종 · 37개 엔드포인트를
  REST Docs 문서화 테스트와 함께 구현했습니다.
- 운영 중인 서비스의 5개 모듈 영속성 계층을 **API 계약 변경 없이 MongoDB → MariaDB(JPA)로 전환**하고,
  테스트를 126개에서 310개로 확장해 검증했습니다.
- 이미지 처리 이벤트 경합으로 게시글이 PENDING에 영구히 갇히는 동시성 버그를 재현 테스트로 잡아내고
  비관적 락으로 수정했습니다.
- Google(Firebase ID Token)과 이메일(BCrypt) 인증을 분리한 이중 인증 구조에서 enumeration 공격,
  timing attack, TOCTOU 경쟁 조건을 각각 에러 통합 · 더미 연산 · 원자적 삭제로 방어했습니다.

### 라이트 — 웹툰 작가 포트폴리오 서비스
`2023.11 ~ 현재` · 5인 팀 · **백엔드 단독 담당** · 일평균 사용자 1,000명
Java 17 · Spring Boot 3 · MongoDB · Docker · Nginx · AWS · Grafana Loki · k6

- 작품 목록 조회의 MongoDB 실행계획을 분석해 복합 인덱스를 적용, **스캔 문서 수 10,188건 → 30건**.
- 북마크 폴더 조회의 전체 fetch 구조를 projection과 페이지 단위 조회로 분리해
  747개 폴더 기준 **28,279ms → 263ms**.
- 고용량 이미지 목록 지연을 썸네일 생성 + CDN 연동으로 분리해 **1,015ms → 20ms**.
- 캠페인 체크아웃을 20스레드 병렬 처리로 전환해 988명 처리 **346초 → 17초**.
- 회원가입 동시 요청으로 중복 계정이 생기는 문제를 재현하고 이메일 단위 잠금으로 방지했습니다.

→ [트러블슈팅 기록](https://danhandev.tistory.com/)

### K-SpamGuard — 한국어 인스타그램 스팸 탐지 (개인)
`2026.05` · 단독 · Java 21 · Spring Boot · 헥사고날 아키텍처 · Flyway · Testcontainers

초성 분리 · 숫자 치환 등 한국어 스팸 우회 패턴을 정규화 파이프라인과 룰 엔진으로 걸러내는 구조를
PRD부터 아키텍처 · 위협모델까지 직접 설계했습니다. 룰 기반이며 실사용자는 없는 설계 검증용 프로젝트입니다.

→ [danhandev/k-spamguard](https://github.com/danhandev/k-spamguard)

---

## Research

- **MDPI *Sensors*** (2024, Vol.24 No.2, Art. 592) — "Rowhammer Attacks in Dynamic Random-Access
  Memory and Defense Methods", 7인 공저 중 **제1저자**.
  [DOI: 10.3390/s24020592](https://doi.org/10.3390/s24020592)
- **한국정보보호학회 CISC-S'23 우수논문상** — "DDR4 DRAM의 소프트웨어 기반 Rowhammer 기법과
  전자파 오류주입 기반 Ehammer 기법에 관한 연구", 공동저자.
- 홍익대학교 [SCALAR Lab](https://scalar-hongik.github.io/) 학부연구원 (2023.02 ~ 2025.12)

---

## Experience

| 기간 | 활동 |
|---|---|
| 2026.05 ~ 2026.08 | 신한DS 금융SW 풀스택 개발자 양성 과정 7기 |
| 2025.03 ~ 2025.12 | 멋쟁이사자처럼 대학 13기 — [신한카드 협업 사내 위키 서비스](https://github.com/Likelion-Hongik-Business-Project/ShinhanCard-BE) 백엔드 |
| 2025.10 ~ 2025.11 | [또바기](https://github.com/GoSonGim/ttobaki-BE) — AI 아바타 발화 재활 서비스 백엔드 (2인, 커밋 69%) |
| 2023.11 ~ 현재 | 라이트 백엔드 개발·운영 |
| 2023.02 ~ 2025.12 | 홍익대학교 SCALAR Lab 학부연구원 |
| 2022.07 ~ 2023.09 | [GDSC Hongik](https://github.com/gdg-hongik-univ) 1기 창립 Core Member — DevTalk Seminar 10회 운영, 공식 저장소 최다 기여(31건) |
| 2022.03 ~ 2023.03 | 알고리즘 학회 HI-ARC 학술부 운영진 |
| 2021.03 ~ 2023.03 | 홍익 개발 커뮤니티 [BlazingDevs](https://github.com/BlazingDevs) 운영진 |

**자격** 정보처리기사 (2024.12) · SQLD (2026.03) · OPIc IH (2026.01)

---

## Stack

**Language** Java 21 / 17, Python, SQL
**Framework** Spring Boot 4 / 3, Spring Modulith, Spring Security, Spring Data JPA, Querydsl
**Data** MySQL, MariaDB, MongoDB, Elasticsearch, Redis, Flyway
**Test** JUnit 5, Testcontainers, ArchUnit, Spring REST Docs, k6
**Infra** Docker, GitHub Actions, AWS(EC2·S3), Cloudflare R2 / Worker, Nginx, Grafana Loki
