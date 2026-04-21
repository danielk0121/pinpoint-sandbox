# 1단계: 로컬 셀프 호스팅 구축

## 목표

Docker Compose로 Grafana + Prometheus + Jaeger + Loki + OTel Collector를
로컬에서 기동하고, Grafana에서 각 데이터소스 연결까지 완료한다.

---

## 사전 준비

- [ ] Docker, Docker Compose 설치 확인
- [ ] 포트 충돌 여부 확인
  - Grafana: 3000
  - Prometheus: 9090
  - Jaeger UI: 16686
  - Jaeger OTLP gRPC: 4317
  - Loki: 3100
  - OTel Collector: 4317 (gRPC), 4318 (HTTP)

---

## 작업 목록

### Docker Compose 작성

작업 디렉토리: `grafana-stack/`

- [x] `grafana-stack/docker-compose.yml` 파일 생성
- [x] Grafana 서비스 정의
- [x] Prometheus 서비스 정의
- [x] Jaeger (all-in-one) 서비스 정의
- [x] Loki 서비스 정의
- [x] OTel Collector 서비스 정의
- [x] OTel Collector 설정 파일 작성 (`grafana-stack/otel-collector-config.yaml`)
  - 수신: OTLP gRPC/HTTP
  - 트레이싱 → Jaeger 전송
  - 메트릭 → Prometheus 전송
  - 로그 → Loki 전송
- [x] Prometheus 설정 파일 작성 (`grafana-stack/prometheus.yml`)
  - OTel Collector 메트릭 스크랩 설정
- [x] Grafana 데이터소스 프로비저닝 파일 작성 (`grafana-stack/grafana/provisioning/datasources/datasources.yaml`)

### 기동 및 접속 확인

- [ ] `cd grafana-stack && docker compose up -d` 실행
- [ ] 전체 컨테이너 정상 기동 확인 (`docker compose ps`)
- [ ] Jaeger UI 접속 확인 (http://localhost:16686)
- [ ] Grafana UI 접속 확인 (http://localhost:3000)
- [ ] Prometheus UI 접속 확인 (http://localhost:9090)
- [ ] Loki 헬스체크 확인 (http://localhost:3100/ready)

### Grafana 데이터소스 연결

- [x] Jaeger 데이터소스 추가 (프로비저닝으로 자동 설정)
- [x] Prometheus 데이터소스 추가 (프로비저닝으로 자동 설정)
- [x] Loki 데이터소스 추가 (프로비저닝으로 자동 설정)
- [ ] 각 데이터소스 연결 테스트 (Test & Save) — 기동 후 확인 필요

---

## 참고

- Jaeger all-in-one 이미지: `jaegertracing/all-in-one`
- Loki 이미지: `grafana/loki`
- OTel Collector 이미지: `otel/opentelemetry-collector-contrib`
- Grafana 기본 계정: admin / admin (GF_SECURITY_ADMIN_PASSWORD로 변경 가능)
- 데이터소스는 `grafana/provisioning/datasources/datasources.yaml`로 자동 프로비저닝됨
