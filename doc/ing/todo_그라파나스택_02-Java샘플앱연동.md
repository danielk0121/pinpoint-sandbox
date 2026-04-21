# 2단계: Java 샘플 앱 연동

## 목표

Spring Boot 샘플 앱에 OTel Java Agent, Prometheus 메트릭, Loki 로그를 연동하여
Grafana에서 트레이스/메트릭/로그를 통합 조회한다.

---

## 사전 준비

- [ ] 1단계(로컬 환경 구축) 완료 확인
- [ ] Java 17+, Gradle 또는 Maven 설치 확인

---

## 작업 목록

### 샘플 앱 작성

- [ ] Spring Boot 프로젝트 생성
- [ ] 샘플 HTTP 엔드포인트 작성
  - `GET /hello` — 단순 응답
  - `GET /slow` — 의도적 지연 (시나리오 테스트용)
  - `GET /error` — 의도적 에러 발생 (시나리오 테스트용)

### 트레이싱 연동 (OTel Java Agent)

- [ ] OTel Java Agent jar 다운로드 (`opentelemetry-javaagent.jar`)
- [ ] 앱 실행 시 Agent 적용 옵션 설정
  - `OTEL_SERVICE_NAME`
  - `OTEL_EXPORTER_OTLP_ENDPOINT` → OTel Collector 주소
- [ ] Jaeger UI에서 트레이스 수집 확인

### 메트릭 연동 (Prometheus)

- [ ] `spring-boot-actuator` + `micrometer-registry-prometheus` 의존성 추가
- [ ] `/actuator/prometheus` 엔드포인트 노출 설정
- [ ] Prometheus에서 앱 스크랩 설정 추가 (`prometheus.yml`)
- [ ] Prometheus UI에서 JVM 메트릭 조회 확인 (`jvm_memory_used_bytes` 등)

### 로그 연동 (Loki)

- [ ] `loki-logback-appender` 의존성 추가
- [ ] `logback-spring.xml` Loki appender 설정
  - Loki 주소 설정
  - TraceID를 로그에 포함 설정 (`MDC` 활용)
- [ ] Loki에서 로그 수집 확인

### Grafana 통합 확인

- [ ] Grafana에서 Jaeger 트레이스 조회
- [ ] Grafana에서 Prometheus JVM 메트릭 조회
- [ ] Grafana에서 Loki 애플리케이션 로그 조회
- [ ] TraceID로 트레이스 → 로그 연계 조회 확인
