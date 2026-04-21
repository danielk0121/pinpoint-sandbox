# 3단계: Go 샘플 앱 연동

## 목표

Go 샘플 앱에 OTel Go SDK, Prometheus 메트릭, Loki 로그를 연동하여
Grafana에서 트레이스/메트릭/로그를 통합 조회한다.

---

## 사전 준비

- [ ] 1단계(로컬 환경 구축) 완료 확인
- [ ] Go 1.21+ 설치 확인

---

## 작업 목록

### 샘플 앱 작성

- [ ] Go HTTP 서버 프로젝트 생성
- [ ] 샘플 HTTP 엔드포인트 작성
  - `GET /hello` — 단순 응답
  - `GET /slow` — 의도적 지연 (시나리오 테스트용)
  - `GET /error` — 의도적 에러 발생 (시나리오 테스트용)

### 트레이싱 연동 (OTel Go SDK)

- [ ] OTel Go SDK 의존성 추가
  - `go.opentelemetry.io/otel`
  - `go.opentelemetry.io/otel/exporters/otlp/otlptrace/otlptracegrpc`
  - `go.opentelemetry.io/contrib/instrumentation/net/http/otelhttp`
- [ ] TracerProvider 초기화 (OTLP gRPC exporter → OTel Collector)
- [ ] HTTP 핸들러에 OTel 미들웨어 적용 (`otelhttp.NewHandler`)
- [ ] 주요 함수에 수동 스팬 추가
- [ ] Jaeger UI에서 트레이스 수집 확인

### 메트릭 연동 (Prometheus)

- [ ] `prometheus/client_golang` 의존성 추가
- [ ] 기본 메트릭 등록 (HTTP 요청 수, 응답시간, 에러율)
- [ ] `/metrics` 엔드포인트 노출
- [ ] Prometheus에서 앱 스크랩 설정 추가 (`prometheus.yml`)
- [ ] Prometheus UI에서 메트릭 조회 확인

### 로그 연동 (Loki)

- [ ] 구조화 로그 라이브러리 적용 (`log/slog` 또는 `zap`)
- [ ] Loki HTTP API로 로그 전송 설정
- [ ] 로그에 TraceID 포함 설정 (OTel context에서 추출)
- [ ] Loki에서 로그 수집 확인

### Grafana 통합 확인

- [ ] Grafana에서 Jaeger 트레이스 조회
- [ ] Grafana에서 Prometheus 메트릭 조회
- [ ] Grafana에서 Loki 애플리케이션 로그 조회
- [ ] TraceID로 트레이스 → 로그 연계 조회 확인
