# APM 도구 목록 정리

## 사용해본 것들

- **Elastic APM**
- **Scouter**
- **New Relic**
- **Sentry**

---

## 관심 없는 것들

- **AppSignal**

---

## 학습 대상 (Pinpoint)

- **Pinpoint** — 네이버 개발 오픈소스 APM. 대규모 Java 분산 환경 특화, bytecode 계측으로 코드 수정 불필요
  - 지원 언어: Java (주력), PHP, Python, Node.js, Go

---

## 모르는 것들

- **Datadog**
  - 회사: Datadog Inc. (미국 뉴욕, 2010년 창립, 나스닥 상장)
  - 클라우드 네이티브 환경에 강한 올인원 모니터링 플랫폼. APM 외에 인프라, 로그, 보안까지 통합
  - 지원 언어: Java, Go, Python, Ruby, Node.js, .NET, PHP, C++

- **Jaeger**
  - 회사: CNCF 오픈소스 프로젝트 (Uber 내부에서 시작, 2017년 오픈소스화)
  - 분산 트레이싱 전용 오픈소스 백엔드. OpenTelemetry 표준 기반, 셀프호스팅 무료
  - 지원 언어: OTel SDK 경유로 모든 언어 지원 (Java, Go, Python, Node.js 등)

- **Grafana Tempo**
  - 회사: Grafana Labs (미국, 2019년 창립)
  - Grafana 생태계의 분산 트레이싱 백엔드. 오브젝트 스토리지 기반으로 저렴하게 대용량 트레이스 저장
  - 지원 언어: OTel SDK 경유로 모든 언어 지원

- **Uptrace**
  - 회사: Uptrace (오픈소스 프로젝트)
  - OpenTelemetry 기반 오픈소스 APM. 트레이스 + 메트릭 + 로그 통합, 셀프호스팅 가능
  - 지원 언어: OTel SDK 경유로 모든 언어 지원

- **Instana**
  - 회사: IBM (2015년 창립된 Instana를 2021년 IBM이 인수)
  - 자동 계측 기반의 엔터프라이즈 APM. 300개 이상 플랫폼 자동 감지, Kubernetes/컨테이너 환경 특화
  - 지원 언어: Java, Go, Python, Node.js, Ruby, PHP, .NET, .NET Core 등 14개 언어

- **Lightstep**
  - 회사: ServiceNow (OpenTelemetry 창시자들이 설립, 2023년 ServiceNow에 인수)
  - OpenTelemetry 공동 창시자가 만든 트레이싱 플랫폼. OTel 데이터 분석에 특화
  - 지원 언어: OTel SDK 경유로 모든 언어 지원

- **Groundcover**
  - 회사: groundcover (이스라엘, 2021년 창립)
  - eBPF 기반 자동 계측 APM. 에이전트나 코드 수정 없이 커널 레벨에서 텔레메트리 수집
  - 지원 언어: 언어 무관 (eBPF로 런타임 레이어에서 자동 수집)

- **Helios**
  - 회사: Helios (이스라엘 스타트업)
  - 비동기/이벤트 기반 시스템(메시지 큐, 백그라운드 잡)의 트레이싱에 특화된 개발자 친화적 플랫폼
  - 지원 언어: OTel SDK 경유 (Java, Node.js, Python, Go 등)

- **Aspecto**
  - 회사: Aspecto (이스라엘 스타트업)
  - API 및 이벤트 드리븐 마이크로서비스 관찰성에 특화. OTel 기반, 프로프라이어터리 에이전트 없음
  - 지원 언어: OTel SDK 경유 (Java, Node.js, Python, Go 등)

- **Last9**
  - 회사: Last9 (인도, 2021년 창립)
  - OpenTelemetry 트레이스 기반으로 서비스 자동 감지 및 의존성 맵 제공. 비용 효율 강조
  - 지원 언어: OTel SDK 경유로 모든 언어 지원
