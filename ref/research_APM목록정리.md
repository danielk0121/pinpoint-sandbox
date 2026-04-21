# APM 도구 목록 정리

## 사용해본 것들

| 도구 | 한 줄 특징 | 지원 언어 |
|------|-----------|-----------|
| **Elastic APM** | ELK 스택 기반 APM. 이미 Elasticsearch 사용 중인 팀에 자연스러운 선택 | Java, Go, Python, Node.js, Ruby, .NET, PHP, iOS, Android |
| **Scouter** | 국산 오픈소스. 경량, 실시간 Java 모니터링 특화 | Java (주력), Python (제한적) |
| **New Relic** | 글로벌 엔터프라이즈 SaaS APM. Datadog과 양대산맥 | Java, Go, Python, Node.js, Ruby, .NET, PHP, C, C++, iOS, Android |
| **Sentry** | 에러 트래킹 사실상 표준. APM 기능도 제공 | 거의 전 언어 (JS, Python, Java, Go, Ruby, PHP, .NET 등) |

---

## 관심 없는 것들

| 도구 | 비고 |
|------|------|
| **AppSignal** | 소규모 팀 대상 간단한 APM |

---

## 학습 대상

| 도구 | 회사 | 한 줄 특징 | 지원 언어 |
|------|------|-----------|-----------|
| **Pinpoint** | 네이버 (오픈소스) | 대규모 Java 분산 환경 특화. bytecode 계측으로 코드 수정 불필요 | Java (주력), PHP, Python, Node.js, Go |

---

## 모르는 것들

| 도구 | 회사 | 한 줄 특징 | 지원 언어 |
|------|------|-----------|-----------|
| **Datadog** | Datadog Inc. (미국, 2010) | 클라우드 네이티브 올인원 모니터링 플랫폼. APM 외 인프라·로그·보안 통합. 시장 점유율 1위 | Java, Go, Python, Node.js, Ruby, .NET, PHP, C++ |
| **Jaeger** | CNCF 오픈소스 (Uber 시작, 2015) | 분산 트레이싱 전용 오픈소스. OTel 표준 기반, 셀프호스팅 무료 | OTel SDK 경유 전 언어 |
| **Grafana Tempo** | Grafana Labs (미국, 2020) | Grafana 생태계 트레이싱 백엔드. 오브젝트 스토리지 기반 저비용 대용량 저장 | OTel SDK 경유 전 언어 |
| **Uptrace** | 오픈소스 프로젝트 (2021) | OTel 네이티브 오픈소스 APM. 트레이스·메트릭·로그 통합 | OTel SDK 경유 전 언어 |
| **Instana** | IBM (2015 창립, 2021 인수) | 자동 계측 엔터프라이즈 APM. 300개 이상 플랫폼 자동 감지 | Java, Go, Python, Node.js, Ruby, PHP, .NET 등 14개 |
| **Lightstep** | ServiceNow (2015 창립, 2023 인수) | OTel 공동 창시자가 설립. OTel 데이터 분석 특화 | OTel SDK 경유 전 언어 |
| **Groundcover** | groundcover (이스라엘, 2021) | eBPF 기반 자동 계측. 에이전트·코드 수정 없이 커널 레벨 수집 | 언어 무관 (eBPF 자동 수집) |
| **Helios** | Helios (이스라엘, 2021) | 비동기·이벤트 기반 시스템 트레이싱 특화 | OTel SDK 경유 (Java, Node.js, Python, Go 등) |
| **Aspecto** | Aspecto (이스라엘, 2020) | API·이벤트 드리븐 마이크로서비스 관찰성 특화. 전용 에이전트 없음 | OTel SDK 경유 (Java, Node.js, Python, Go 등) |
| **Last9** | Last9 (인도, 2021) | OTel 트레이스 기반 서비스 자동 감지. 비용 효율 강조 | OTel SDK 경유 전 언어 |
