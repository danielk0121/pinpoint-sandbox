# APM Sandbox

## 목적

- APM 도구 학습 및 테스트
- 셀프 호스팅 환경 구축 먼저, 이후 클라우드 SaaS 서비스 테스트
- Grafana 스택, Naver Pinpoint 2개를 순차적으로 학습

### 학습 단계

- 1단계: 로컬 설치 학습 테스트 — 맥북 로컬에 Docker로 스택 구성, 기본 동작 이해
- 2단계: 클라우드 사용 테스트 — 클라우드 무료 플랜 또는 관리형 서비스로 전환, 운영 편의성 확인
- 3단계: 실사용 운영환경과 유사하게 재구성 학습 테스트 — 컴포넌트 분리, 스케일링, 샘플링 전략 등 실제 운영 구성 재현

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
