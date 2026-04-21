# APM Sandbox

## 목적

- APM 도구 학습 및 테스트
- 셀프 호스팅 환경 구축 먼저, 이후 클라우드 SaaS 서비스 테스트
- Grafana 스택, Naver Pinpoint 2개를 순차적으로 학습

### 학습 단계

- 1단계: 로컬 설치 학습 테스트 — 맥북 로컬에 Docker로 스택 구성, 기본 동작 이해
- 2단계: 클라우드 사용 테스트 — 클라우드 무료 플랜 또는 관리형 서비스로 전환, 운영 편의성 확인
- 3단계: 실사용 운영환경과 유사하게 재구성 학습 테스트 — 컴포넌트 분리, 스케일링, 샘플링 전략 등 실제 운영 구성 재현

## 현황

### doc/ — 작업 문서

- `doc/ing/todo_그라파나스택_00-개요.md` — 전체 구성 목표 및 4단계 작업 목록
- `doc/ing/todo_그라파나스택_01-로컬환경구축.md` — Docker Compose 구성, 컴포넌트 기동, Grafana 데이터소스 연결
- `doc/ing/todo_그라파나스택_02-Java샘플앱연동.md` — Spring Boot + OTel Agent 트레이싱/메트릭/로그 연동
- `doc/ing/todo_그라파나스택_03-Go샘플앱연동.md` — Go + OTel SDK 트레이싱/메트릭/로그 연동
- `doc/ing/todo_그라파나스택_04-시나리오테스트.md` — 느린 트랜잭션, TraceID 로그 연계, 대시보드, 알림
- `doc/hold/todo_핀포인트_*.md` — Pinpoint 학습 작업 6개 (보류)

### ref/ — 리서치 문서

- `ref/research_APM통합정리.md` — APM 도구 전체 비교, Grafana 스택 결론, SigNoz 비교, 로컬 환경 고려사항
- `ref/research_고랭APM도구조사.md` — Go 언어 APM 도구 조사
- `ref/research_핀포인트개요및특징.md` — Pinpoint 개요
- `ref/research_핀포인트비용및라이선스.md` — Pinpoint 비용/라이선스

### 현재 상태

리서치 완료. Grafana + Prometheus + Jaeger + Loki 스택으로 방향 확정.
작업 문서(01~04단계) 준비 완료. 1단계 로컬 환경 구축부터 실행 가능한 상태.

---

## 학습 순서

### 1순위: Grafana 스택 (진행 중)

- 구성: Grafana + Prometheus + Jaeger + Loki
- 작업 문서: `doc/ing/todo_그라파나스택학습.md`

### 2순위: Pinpoint (보류)

- 구성: Naver 오픈소스 APM, Java 특화 올인원
- 작업 문서: `doc/hold/todo_핀포인트_*.md`

## 구조

```
pinpoint-sandbox/
├── doc/
│   ├── ing/    # 진행 중인 작업
│   ├── hold/   # 보류 중인 작업
│   └── done/   # 완료된 작업
└── ref/        # 리서치 문서
```
