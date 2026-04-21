# Grafana 스택 + Jaeger + Loki 학습 테스트

## 목표

로컬 셀프 호스팅 환경에서 Grafana + Prometheus + Jaeger + Loki 스택을 구축하고,
Java/Go 애플리케이션의 트레이싱/메트릭/로그를 통합 모니터링한다.

## 구성 목표

```
WAS (Java/Go 샘플 앱)
  → OTel Collector
    ├→ Jaeger      (트레이싱)
    ├→ Prometheus  (메트릭)
    └→ Loki        (애플리케이션 로그)

Grafana
  ├→ Jaeger 데이터소스
  ├→ Prometheus 데이터소스
  └→ Loki 데이터소스
```

---

## 단계별 작업

### 1단계: 로컬 셀프 호스팅 구축

- [x] Docker Compose 파일 작성 (Grafana, Prometheus, Jaeger, Loki, OTel Collector)
- [x] OTel Collector 설정 파일 작성
- [x] Prometheus 설정 파일 작성
- [x] Grafana 데이터소스 프로비저닝 설정
- [ ] 각 컴포넌트 기동 확인
  - [ ] Jaeger UI 접속 확인
  - [ ] Grafana UI 접속 확인
  - [ ] Prometheus UI 접속 확인
- [ ] Grafana 데이터소스 연결 테스트 (Jaeger, Prometheus, Loki)

### 2단계: Java 샘플 앱 연동

- [ ] 샘플 Java 앱 작성 (Spring Boot 또는 단순 HTTP 서버)
- [ ] OTel Java Agent 적용 (트레이싱 자동 계측)
- [ ] Prometheus 메트릭 노출 설정 (JVM, HTTP)
- [ ] Loki에 애플리케이션 로그 전송 설정
- [ ] Grafana에서 트레이스/메트릭/로그 통합 조회 확인

### 3단계: Go 샘플 앱 연동

- [ ] 샘플 Go 앱 작성
- [ ] OTel Go SDK 적용 (트레이싱 수동 계측)
- [ ] Prometheus 메트릭 노출 설정
- [ ] Loki에 애플리케이션 로그 전송 설정
- [ ] Grafana에서 트레이스/메트릭/로그 통합 조회 확인

### 4단계: 시나리오 테스트

- [ ] 느린 트랜잭션 발생 → Jaeger에서 트레이스 확인
- [ ] TraceID로 Loki 로그 연계 조회
- [ ] Grafana 대시보드 구성 (JVM 메트릭, 요청 수, 응답시간)
- [ ] 알림 설정 (응답시간 임계치 초과 시)
