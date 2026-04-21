# Go(Golang) 주요 APM 도구 조사

## 1. Go APM의 특수성

Go의 경량 동시성 모델(Goroutine)은 장점이면서 모니터링 관점에서 도전 과제이기도 하다.
일반적인 APM이 제공하는 thread 기반 추적이 Goroutine에는 적합하지 않으며, 아래 항목을 제대로 지원하는지 확인이 필요하다:

- Goroutine 수 및 상태 모니터링
- GC(Garbage Collection) 타이밍 및 빈도
- 비동기 처리 흐름 추적

또한 Java와 달리 **bytecode instrumentation이 불가능**하여, 대부분의 Go APM은 **코드에 직접 SDK를 임포트**하거나 **OpenTelemetry 표준**을 사용한다.

---

## 2. 오픈소스 / 셀프호스팅

### OpenTelemetry Go SDK + Jaeger

- **OpenTelemetry Go SDK**: https://github.com/open-telemetry/opentelemetry-go
- **Jaeger**: https://www.jaegertracing.io/
- 현재 Go 분산 트레이싱의 사실상 표준 조합
- 코드에 OTel SDK로 계측 후 Jaeger로 데이터 전송
- Jaeger는 오픈소스이며 CNCF 프로젝트로 관리됨
- 완전 무료, 셀프호스팅 가능
- Elastic APM, Grafana Tempo 등 다양한 백엔드로 교체 가능 (벤더 락인 없음)

```go
// 예시: OTel SDK로 span 생성
tracer := otel.Tracer("my-service")
ctx, span := tracer.Start(ctx, "my-operation")
defer span.End()
```

### Elastic APM Go Agent

- GitHub: https://github.com/elastic/apm-agent-go
- Elastic Stack(Elasticsearch + Kibana)과 통합
- Go 프레임워크(Gin, Echo, gRPC 등) 공식 지원
- 오픈소스이며 셀프호스팅 시 무료
- Elastic Cloud 사용 시 월 $95~(Observability 플랜)
- Elastic APM / Scouter 경험이 있다면 진입 장벽이 낮음

### Grafana Tempo

- 오픈소스 분산 트레이싱 백엔드
- OpenTelemetry 수신, Grafana에서 시각화
- Prometheus + Grafana 스택을 이미 쓰고 있다면 자연스러운 선택
- 셀프호스팅 무료, Grafana Cloud 사용 시 종량제

### Uptrace

- OpenTelemetry 기반 APM, 셀프호스팅 가능
- 오픈소스(셀프호스팅) 또는 클라우드(~$5/백만 스팬)
- Go 친화적인 UI와 문서 제공

### Pinpoint Go Agent

- GitHub: https://github.com/pinpoint-apm/pinpoint-go-agent
- 기존 Pinpoint 인프라를 사용 중이라면 Go 서비스도 통합 가능
- Java 에이전트 대비 기능 커버리지가 낮음
- 커뮤니티 규모가 위 도구들보다 작음

---

## 3. 상용 APM

### Datadog

- Go 공식 트레이싱 라이브러리 제공 (`dd-trace-go`)
- Gin, Echo, gRPC, database/sql 등 자동 계측 지원
- Goroutine 모니터링, 프로파일링(CPU/메모리) 기능 포함
- 비용: 호스트당 월 $31~(APM 플랜), 대규모 환경에서 비용이 빠르게 증가
- 기능이 가장 풍부하지만 비용도 가장 높음

### New Relic

- Go 에이전트 공식 지원
- Goroutine 수 및 메모리, GC 메트릭 수집
- 월 100GB 무료, 초과 시 GB당 과금
- 소규모 트래픽이라면 무료 범위 내에서 사용 가능

### Sentry

- 에러 트래킹 + 기본 성능 모니터링
- Go SDK 공식 지원
- APM 전문 도구보다는 에러 중심
- 월 $26~(Team 플랜), 소규모 팀에 적합

### AppSignal

- 간단한 설정, 개발자 친화적 UI
- Go 지원 포함
- 월 $19~, 소규모 프로젝트에 가성비 좋음

---

## 4. 도구 선택 가이드

- **Java와 동일한 Pinpoint 대시보드에서 통합 관리** → Pinpoint Go Agent
- **벤더 락인 없이 오픈소스로** → OpenTelemetry SDK + Jaeger 또는 Grafana Tempo
- **이미 Elastic Stack 사용 중** → Elastic APM Go Agent
- **올인원 상용 솔루션, 예산 여유 있음** → Datadog
- **에러 추적 + 간단한 APM, 소규모** → Sentry 또는 New Relic(무료 플랜)
- **Prometheus + Grafana 스택 사용 중** → Grafana Tempo

---

## 참고 자료

- [11 APM Tools for Go - Last9](https://last9.io/blog/apm-tools-for-golang/)
- [OpenTelemetry Go SDK](https://github.com/open-telemetry/opentelemetry-go)
- [Jaeger 공식 사이트](https://www.jaegertracing.io/)
- [Elastic APM Go Agent](https://github.com/elastic/apm-agent-go)
- [Datadog Go APM](https://www.datadoghq.com/apm/go-apm/)
- [Pinpoint Go Agent](https://github.com/pinpoint-apm/pinpoint-go-agent)
