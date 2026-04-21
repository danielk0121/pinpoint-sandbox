# APM 도구 비교

> 기준일: 2026-04-21
> 범례 — 셀프호스팅 난이도: ⭐ 쉬움 / ⭐⭐ 보통 / ⭐⭐⭐ 어려움

## 업계 인기도 수치 요약 (2025 기준)

- **시장 점유율 (상용 APM)**: Datadog 약 52% > New Relic 약 24% > Dynatrace 약 3% (데이터센터 관리 기준)
- **Datadog 매출**: 2025년 $3.3B (나스닥 상장, 고객 수 30,500+)
- **GitHub ★ (오픈소스)**: Sentry 43k > Jaeger 22k > Pinpoint 14k > Grafana Tempo 5k > Uptrace 4k > Scouter 2k
- **개발자 설문 (Stack Overflow 2025)**: Grafana+Prometheus(43%), Sentry(32%), New Relic(13%) 순 (AI 에이전트 모니터링 항목 기준)

---

## 사용해본 것들

### Elastic APM
- **서비스 시작**: 2016년 (Elastic Stack 5.0에 포함)
- **비용**: 오픈소스 무료. Elastic Cloud 사용 시 월 $95~(Observability 플랜)
- **클라우드 무료 체험**: Elastic Cloud 14일 무료 트라이얼 제공
- **셀프호스팅**: 가능 ⭐⭐ (Elasticsearch + APM Server + Kibana 구성 필요)
- **지원 언어**: Java, Go, Python, Node.js, Ruby, .NET, PHP, iOS, Android
- **업계 인기도**: 중상. ELK 스택 사용 팀에서 자연스럽게 채택. Elastic 전체 점유율 약 9%(IT 모니터링)
- **OTel 호환성**: 높음. OTel 데이터를 네이티브로 수신 가능

### Scouter
- **서비스 시작**: 2014년 (네이버 내부 개발, 오픈소스 공개)
- **비용**: 완전 무료 오픈소스 (Apache 2.0)
- **클라우드 무료 체험**: 해당 없음 (셀프호스팅 전용)
- **셀프호스팅**: 가능 ⭐ (단일 서버로 빠르게 구성 가능, Java 환경에 최적화)
- **지원 언어**: Java (주력), Python (제한적)
- **업계 인기도**: 낮음. 국내 일부 Java 백엔드 팀 중심. GitHub ★2,171. 글로벌 인지도는 거의 없음
- **OTel 호환성**: 낮음. OTel 표준 미지원, 자체 프로토콜 사용

### New Relic
- **서비스 시작**: 2008년
- **비용**: 월 100GB 무료(Full Platform User 1명 포함). 초과 시 GB당 과금
- **클라우드 무료 체험**: 영구 무료 플랜 존재 (신용카드 불필요)
- **셀프호스팅**: 불가 (SaaS 전용)
- **지원 언어**: Java, Go, Python, Node.js, Ruby, .NET, PHP, C, C++, iOS, Android
- **업계 인기도**: 높음. 글로벌 엔터프라이즈 시장 2위. 시장 점유율 약 24%. 개발자 설문 13%
- **OTel 호환성**: 높음. OTel 데이터 수신 및 네이티브 지원

### Sentry
- **서비스 시작**: 2010년
- **비용**: 무료 플랜 존재(5k 에러/월). 팀 플랜 월 $26~
- **클라우드 무료 체험**: 영구 무료 플랜 제공
- **셀프호스팅**: 가능 ⭐⭐ (Docker Compose 기반, 단 리소스 요구량 있음)
- **지원 언어**: JavaScript, Python, Java, Go, Ruby, PHP, .NET, iOS, Android 등 거의 전 언어
- **업계 인기도**: 매우 높음. 에러 트래킹 분야 사실상 표준. GitHub ★43,632. 개발자 설문 32%
- **OTel 호환성**: 중간. OTel SDK를 내부적으로 활용하나 APM 전문 도구는 아님

---

## 학습 대상

### Pinpoint
- **서비스 시작**: 2015년 (2012년 네이버 내부 개발 시작)
- **비용**: 완전 무료 오픈소스 (Apache 2.0). Naver Cloud의 Pinpoint Cloud는 유료
- **클라우드 무료 체험**: Naver Cloud Pinpoint Cloud 체험 가능 (요금 별도 확인 필요)
- **셀프호스팅**: 가능 ⭐⭐⭐ (HBase + ZooKeeper + Collector + Web 구성, 리소스 많이 필요)
- **지원 언어**: Java (주력), PHP, Python, Node.js, Go
- **업계 인기도**: 중간. 국내외 대규모 Java 환경 사용. GitHub ★13,824. 네이버 내부 일 200억 건 처리
- **OTel 호환성**: 낮음. 자체 트레이싱 프로토콜 사용, OTel 공식 지원 미흡

---

## 모르는 것들

### Datadog
- **서비스 시작**: 2010년
- **비용**: 무료 티어(5 호스트, 1일 보존). APM 플랜 호스트당 월 $31~(연간)
- **클라우드 무료 체험**: 14일 무료 트라이얼 + 영구 무료 티어 제공
- **셀프호스팅**: 불가 (SaaS 전용)
- **지원 언어**: Java, Go, Python, Node.js, Ruby, .NET, PHP, C++, iOS, Android
- **업계 인기도**: 매우 높음. 상용 APM 시장 점유율 약 52%(1위). 고객 수 30,500+. 2025년 매출 $3.3B
- **OTel 호환성**: 높음. OTel 데이터 수신 지원, 단 자체 에이전트 병행 권장

### Jaeger
- **서비스 시작**: 2015년 (Uber 개발, 2017년 CNCF 편입)
- **비용**: 완전 무료 오픈소스 (Apache 2.0)
- **클라우드 무료 체험**: 해당 없음 (셀프호스팅 전용)
- **셀프호스팅**: 가능 ⭐ (Docker 단일 컨테이너로 빠른 시작 가능)
- **지원 언어**: OTel SDK 경유로 모든 언어 지원
- **업계 인기도**: 높음. 오픈소스 분산 트레이싱 사실상 표준. GitHub ★22,703. CNCF Graduated 프로젝트
- **OTel 호환성**: 매우 높음. v2.0부터 OTel이 핵심 기반으로 완전 통합

### Grafana Tempo
- **서비스 시작**: 2020년 (Grafana Labs)
- **비용**: 완전 무료 오픈소스. Grafana Cloud 사용 시 종량제(50GB/월 무료)
- **클라우드 무료 체험**: Grafana Cloud 영구 무료 플랜 제공
- **셀프호스팅**: 가능 ⭐⭐ (Prometheus + Grafana 스택과 함께 구성)
- **지원 언어**: OTel SDK 경유로 모든 언어 지원
- **업계 인기도**: 중상. Prometheus/Grafana 생태계와 빠르게 성장. GitHub ★5,206. 개발자 설문 Grafana+Prometheus 43%(1위)
- **OTel 호환성**: 매우 높음. OTel, Jaeger, Zipkin 포맷 모두 수신 가능

### Uptrace
- **서비스 시작**: 2021년
- **비용**: 오픈소스 무료(셀프호스팅). 클라우드 ~$5/백만 스팬
- **클라우드 무료 체험**: 클라우드 무료 플랜 존재
- **셀프호스팅**: 가능 ⭐ (Docker Compose로 간단히 구성)
- **지원 언어**: OTel SDK 경유로 모든 언어 지원
- **업계 인기도**: 낮음. GitHub ★4,173. 소규모 커뮤니티, 빠른 성장 중
- **OTel 호환성**: 매우 높음. OTel 네이티브 설계

### Instana
- **서비스 시작**: 2015년 (2021년 IBM 인수)
- **비용**: 호스트당 월 $75~. 무료 플랜 없음
- **클라우드 무료 체험**: 14일 무료 트라이얼 제공
- **셀프호스팅**: 불가 (SaaS. 단 온프레미스 엔터프라이즈 플랜은 별도 협의)
- **지원 언어**: Java, Go, Python, Node.js, Ruby, PHP, .NET, .NET Core 등 14개 언어
- **업계 인기도**: 중간. IBM 엔터프라이즈 고객 중심. 상용 APM 시장 약 3% 점유(Dynatrace와 유사 규모)
- **OTel 호환성**: 높음. OTel 데이터 수신 지원

### Lightstep (ServiceNow Cloud Observability)
- **서비스 시작**: 2015년 (2023년 ServiceNow 인수, 현재 ServiceNow Cloud Observability로 브랜드 변경)
- **비용**: 무료 플랜 존재(소규모). 유료 플랜 ~$100/월~
- **클라우드 무료 체험**: 무료 플랜 제공
- **셀프호스팅**: 불가 (SaaS 전용)
- **지원 언어**: OTel SDK 경유로 모든 언어 지원
- **업계 인기도**: 중간. OTel 창시자 설립으로 초기 주목받았으나 ServiceNow 인수 후 입지 약화
- **OTel 호환성**: 매우 높음. OTel 공동 창시자가 만든 제품

### Groundcover
- **서비스 시작**: 2021년 (이스라엘)
- **비용**: 무료 플랜 존재. 유료 플랜 $250/월~
- **클라우드 무료 체험**: 무료 플랜 제공
- **셀프호스팅**: 가능 (Kubernetes 클러스터 위에 설치, eBPF 기반)
- **지원 언어**: 언어 무관 (eBPF로 커널 레벨에서 자동 수집)
- **업계 인기도**: 낮음. 신생 스타트업
- **OTel 호환성**: 중간. OTel 데이터 수신 가능하나 자체 eBPF 계측이 주력

### Helios
- **서비스 시작**: 2021년 (이스라엘)
- **비용**: 무료 플랜 존재. 유료 플랜 $99/월~
- **클라우드 무료 체험**: 무료 플랜 제공
- **셀프호스팅**: 불가 (SaaS 전용)
- **지원 언어**: OTel SDK 경유 (Java, Node.js, Python, Go 등)
- **업계 인기도**: 낮음. 소규모 스타트업
- **OTel 호환성**: 높음. OTel 기반

### Aspecto
- **서비스 시작**: 2020년 (이스라엘)
- **비용**: 무료 개발자 플랜 존재. 유료 플랜 $49/월~
- **클라우드 무료 체험**: 무료 플랜 제공
- **셀프호스팅**: 불가 (SaaS 전용)
- **지원 언어**: OTel SDK 경유 (Java, Node.js, Python, Go 등)
- **업계 인기도**: 낮음. 소규모 스타트업
- **OTel 호환성**: 높음. OTel 전용 설계, 프로프라이어터리 에이전트 없음

### Last9
- **서비스 시작**: 2021년 (인도)
- **비용**: 유료. 플랜별 상이 (공식 사이트 문의)
- **클라우드 무료 체험**: 트라이얼 제공
- **셀프호스팅**: 불가 (SaaS 전용)
- **지원 언어**: OTel SDK 경유로 모든 언어 지원
- **업계 인기도**: 낮음. 신생 스타트업, 비용 효율 강조
- **OTel 호환성**: 높음. OTel 네이티브

---

## 한눈에 보기

- **무료로 PC에 셀프호스팅 가능한 것**: Pinpoint, Jaeger, Grafana Tempo, Uptrace, Elastic APM, Scouter, Sentry
- **클라우드 영구 무료 플랜 있는 것**: New Relic, Sentry, Grafana Cloud, Uptrace, Groundcover, Helios, Aspecto
- **SaaS 전용 (셀프호스팅 불가)**: Datadog, New Relic, Instana, Lightstep, Helios, Aspecto, Last9
- **OTel 완전 호환**: Jaeger, Grafana Tempo, Uptrace, Lightstep
- **OTel 미흡**: Pinpoint, Scouter
- **GitHub 스타 기준 인기도**: Sentry(43k) > Jaeger(22k) > Pinpoint(14k) > Grafana Tempo(5k) > Uptrace(4k) > Scouter(2k)
