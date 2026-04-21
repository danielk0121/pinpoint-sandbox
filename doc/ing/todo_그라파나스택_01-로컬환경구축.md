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

- [ ] `grafana-stack/docker-compose.yml` 파일 생성
- [ ] Grafana 서비스 정의
- [ ] Prometheus 서비스 정의
- [ ] Jaeger (all-in-one) 서비스 정의
- [ ] Loki 서비스 정의
- [ ] OTel Collector 서비스 정의
- [ ] OTel Collector 설정 파일 작성 (`grafana-stack/otel-collector-config.yaml`)
  - 수신: OTLP gRPC/HTTP
  - 트레이싱 → Jaeger 전송
  - 메트릭 → Prometheus 전송
  - 로그 → Loki 전송
- [ ] Prometheus 설정 파일 작성 (`grafana-stack/prometheus.yml`)
  - OTel Collector 메트릭 스크랩 설정

### 기동 및 접속 확인

- [ ] `cd grafana-stack && docker compose up -d` 실행
- [ ] 전체 컨테이너 정상 기동 확인 (`docker compose ps`)
- [ ] Jaeger UI 접속 확인 (http://localhost:16686)
- [ ] Grafana UI 접속 확인 (http://localhost:3000)
- [ ] Prometheus UI 접속 확인 (http://localhost:9090)
- [ ] Loki 헬스체크 확인 (http://localhost:3100/ready)

### Grafana 데이터소스 연결

- [ ] Jaeger 데이터소스 추가
- [ ] Prometheus 데이터소스 추가
- [ ] Loki 데이터소스 추가
- [ ] 각 데이터소스 연결 테스트 (Test & Save)

---

## 참고

- Jaeger all-in-one 이미지: `jaegertracing/all-in-one`
- Loki 이미지: `grafana/loki`
- OTel Collector 이미지: `otel/opentelemetry-collector-contrib`
