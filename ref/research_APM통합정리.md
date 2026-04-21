# APM 도구 통합 정리

> 기준일: 2026-04-21
> 셀프호스팅 난이도: ⭐ 쉬움 / ⭐⭐ 보통 / ⭐⭐⭐ 어려움
> OTel 호환: ◎ 매우 높음 / ○ 높음 / △ 중간 / ✕ 낮음

---

## 사용해본 것들

| 도구 | 개발사 / 국가 | 시작 | 비용 | 클라우드 무료 | 셀프호스팅 | 지원 언어 | 인기도 | OTel |
|------|--------------|------|------|--------------|-----------|-----------|--------|------|
| **Elastic APM** | Elastic N.V. / 미국 | 2016 | 오픈소스 무료. Cloud 월 $95~ | 14일 트라이얼 | ⭐⭐ | Java, Go, Python, Node.js, Ruby, .NET, PHP, iOS, Android | 중상. 점유율 ~9% | ○ |
| **Scouter** | 네이버 (오픈소스) / 한국 | 2014 | 완전 무료 | 해당 없음 | ⭐ | Java (주력), Python (제한적) | 낮음. GitHub ★2k. 국내 일부 팀 | ✕ |
| **New Relic** | New Relic Inc. / 미국 | 2008 | 100GB/월 무료. 초과 GB당 과금 | 영구 무료 플랜 | 불가 (SaaS) | Java, Go, Python, Node.js, Ruby, .NET, PHP, C, C++, iOS, Android | 높음. 점유율 ~24% | ○ |
| **Sentry** | Functional Software / 미국 | 2010 | 무료 플랜(5k 에러/월). 팀 $26~/월 | 영구 무료 플랜 | ⭐⭐ | 거의 전 언어 (JS, Python, Java, Go, Ruby, PHP, .NET 등) | 매우 높음. GitHub ★43k. 설문 32% | △ |

---

## 모르는 것들

| 도구 | 개발사 / 국가 | 시작 | 비용 | 클라우드 무료 | 셀프호스팅 | 지원 언어 | 인기도 | OTel |
|------|--------------|------|------|--------------|-----------|-----------|--------|------|
| **Datadog** | Datadog Inc. / 미국 | 2010 | 무료 티어(5 호스트). APM $31~/호스트/월 | 14일 트라이얼 + 무료 티어 | 불가 (SaaS) | Java, Go, Python, Node.js, Ruby, .NET, PHP, C++ | 매우 높음. 점유율 ~52%(1위). 고객 30k+. 매출 $3.3B | ○ |
| **Dynatrace** | Dynatrace Inc. / 미국 (오스트리아 창립) | 2005 | 엔터프라이즈 라이선스 (문의). 15일 트라이얼 | 15일 트라이얼 | 불가 (SaaS + 엔터프라이즈 온프레미스 협의) | Java, Go, Python, Node.js, Ruby, .NET, PHP 등 전 언어 | 매우 높음. Gartner APM 부문 수년 연속 리더. Datadog/New Relic과 함께 상용 빅3 | ○ |
| **SigNoz** | SigNoz Inc. / 미국 (인도 창립) | 2021 | 오픈소스 무료. Cloud $199~/월 | 무료 플랜 | ⭐⭐ Docker Compose | OTel SDK 경유 전 언어 | 중상. GitHub ★20k+. 오픈소스 OTel 네이티브 APM 중 성장 1위 | ◎ |
| **Jaeger** | CNCF 오픈소스 (Uber 시작) / 미국 | 2015 | 완전 무료 | 해당 없음 | ⭐ Docker 단일 컨테이너 | OTel SDK 경유 전 언어 | 높음. GitHub ★22k. CNCF Graduated | ◎ |
| **Grafana Tempo** | Grafana Labs / 미국 | 2020 | 오픈소스 무료. Cloud 50GB/월 무료 | 영구 무료 플랜 | ⭐⭐ Prometheus + Grafana 스택 | OTel SDK 경유 전 언어 | 중상. GitHub ★5k. 설문 Grafana+Prometheus 43% | ◎ |
| **Pinpoint** | 네이버 (오픈소스) / 한국 | 2015 | 완전 무료. Naver Cloud는 유료 | Naver Cloud 체험 (요금 확인 필요) | ⭐⭐⭐ HBase + ZooKeeper 구성 | Java (주력), PHP, Python, Node.js, Go | 중간. GitHub ★14k. 일 200억 건 처리 | ✕ |

---

## 관심 없는 것들

| 도구 | 개발사 / 국가 | 시작 | 비용 | 클라우드 무료 | 셀프호스팅 | 지원 언어 | 인기도 | OTel |
|------|--------------|------|------|--------------|-----------|-----------|--------|------|
| **AppDynamics** | Cisco (2008 창립, 2017 인수) / 미국 | 2008 | 엔터프라이즈 라이선스 (문의). 무료 플랜 없음 | 15일 트라이얼 | 불가 (SaaS + 엔터프라이즈 온프레미스 협의) | Java, Go, Python, Node.js, Ruby, .NET, PHP, C++ | 중상. 엔터프라이즈 Java/.NET 환경에서 오래된 인지도. Cisco Splunk와 통합 방향 | △ |
| **Instana** | IBM (2015 창립, 2021 인수) / 독일→미국 | 2015 | $75~/호스트/월. 무료 플랜 없음 | 14일 트라이얼 | 불가 (엔터프라이즈 온프레미스 협의) | Java, Go, Python, Node.js, Ruby, PHP, .NET 등 14개 | 중간. IBM 엔터프라이즈 중심. ~3% | ○ |
| **Lightstep** | ServiceNow (2015 창립, 2023 인수) / 미국 | 2015 | 무료 플랜(소규모). 유료 ~$100~/월 | 무료 플랜 | 불가 (SaaS) | OTel SDK 경유 전 언어 | 중간. OTel 창시자 설립, 인수 후 입지 약화 | ◎ |
| **Uptrace** | 오픈소스 프로젝트 / - | 2021 | 오픈소스 무료. Cloud ~$5/백만 스팬 | 무료 플랜 | ⭐ Docker Compose | OTel SDK 경유 전 언어 | 낮음. GitHub ★4k | ◎ |
| **Groundcover** | groundcover / 이스라엘 | 2021 | 무료 플랜. 유료 $250~/월 | 무료 플랜 | ⭐⭐ Kubernetes + eBPF | 언어 무관 (eBPF 커널 레벨 자동 수집) | 낮음. 신생 스타트업 | △ |
| **Helios** | Helios / 이스라엘 | 2021 | 무료 플랜. 유료 $99~/월 | 무료 플랜 | 불가 (SaaS) | OTel SDK 경유 (Java, Node.js, Python, Go 등) | 낮음. 소규모 스타트업 | ○ |
| **Aspecto** | Aspecto / 이스라엘 | 2020 | 무료 플랜. 유료 $49~/월 | 무료 플랜 | 불가 (SaaS) | OTel SDK 경유 (Java, Node.js, Python, Go 등) | 낮음. 소규모 스타트업 | ○ |
| **Last9** | Last9 / 인도 | 2021 | 유료 (플랜별 문의) | 트라이얼 제공 | 불가 (SaaS) | OTel SDK 경유 전 언어 | 낮음. 신생 스타트업 | ○ |
| **AppSignal** | AppSignal / 네덜란드 | - | $19~/월 | 해당 없음 | 불가 (SaaS) | Ruby, Elixir, Node.js, Python, JS | 낮음. 소규모 팀 대상 | - |

---

## 인기도 수치 요약

- 상용 APM 시장 점유율: Datadog ~52% > New Relic ~24% > Dynatrace/Instana ~3% (Gartner 기준 빅3: Datadog, New Relic, Dynatrace)
- GitHub ★: Sentry 43k > Jaeger 22k > SigNoz 20k+ > Pinpoint 14k > Grafana Tempo 5k > Uptrace 4k > Scouter 2k
- 개발자 설문 (Stack Overflow 2025): Grafana+Prometheus 43% > Sentry 32% > New Relic 13%

---

## APM 추천 (Java/Go 중심, 셀프호스팅 또는 클라우드 무료 기준)

조건: PC 셀프호스팅 또는 클라우드 무료 티어, Java/Go 필수, Node/Python 선택, 업계 인지도 우선
제외: Elastic APM, Scouter, New Relic, Sentry

### 1순위: Grafana Tempo (+ Prometheus 스택)
- Java, Go, Node.js, Python 모두 OTel 경유 지원
- 클라우드 무료 50GB/월 또는 PC 셀프호스팅 가능
- 개발자 설문 1위 (43%)
- 단점: 구성 복잡도 있음

### 2순위: Jaeger
- PC 셀프호스팅 가장 쉬움 (Docker 단일 컨테이너)
- Java, Go OTel 경유 지원
- GitHub ★22k, CNCF Graduated
- 단점: 트레이싱 전용 (메트릭/로그 없음), 시각화 도구 별도 필요 (Grafana 등)

---

## Jaeger 특징 및 규모 확장

### Jaeger가 제공하는 것
- 트레이스 수집 (Collector)
- 트레이스 저장 (외부 스토리지 연동)
- 트레이스 조회 UI

### Jaeger가 없는 것
- 메트릭 (CPU, 메모리, JVM 등)
- 로그
- 대시보드/알림

### 규모 확장 단계

**1단계 — 소규모 (시작)**
- all-in-one 단일 컨테이너로 운영
- 인메모리 저장소 사용

**2단계 — 저장소 교체 (가장 먼저)**
- Elasticsearch / OpenSearch — 가장 많이 쓰임, 검색 성능 우수
- Cassandra — 대용량 쓰기에 강함, 클러스터 확장 용이
- Kafka (버퍼) — 트래픽 폭증 시 수집 버퍼로 앞단에 추가

**3단계 — 컴포넌트 분리 (중규모)**
- `jaeger-collector` — 트레이스 수집 전담, 수평 확장 가능
- `jaeger-query` — UI/API 전담
- `jaeger-agent` 또는 OTel Collector — 각 WAS 사이드카

**4단계 — OTel Collector 도입 (권장)**
- WAS → OTel Collector → Jaeger Collector 구조
- 수집 파이프라인을 Jaeger와 분리
- 백엔드를 Grafana Tempo 등으로 교체해도 앱 코드 변경 없음
- 필터링/샘플링/라우팅 로직을 Collector에서 처리

### 샘플링 전략
- 소규모: const 샘플링 (100% 수집)
- 중규모: probabilistic 샘플링 (예: 10%)
- 대규모: adaptive 샘플링 — 트래픽에 따라 자동 조절

### Jaeger 한계 및 전환 시점
트레이싱 전용이라 규모가 커지면 풀 APM 스택으로 전환 고려:
- Grafana Tempo + Prometheus + Loki 스택 (OTel 경유라 마이그레이션 용이)
- 또는 New Relic / Datadog 유료 전환

---

## 통합 세트 APM 비교

Jaeger는 트레이싱만 담당하며 메트릭/로그/시각화는 별도 조합 필요.
아래는 트레이스+메트릭+로그+시각화를 통합 제공하는 APM 목록.

### Grafana Stack (오픈소스, 셀프호스팅 가능)
- 구성: Tempo(트레이스) + Prometheus(메트릭) + Loki(로그) + Grafana(시각화)
- 셀프호스팅 가능, 클라우드 무료 플랜 있음
- 업계 표준에 가까움 (개발자 설문 43%)
- 단점: 컴포넌트를 직접 조합해야 함

### Elastic APM (오픈소스, 셀프호스팅 가능)
- 구성: APM Server + Elasticsearch + Kibana — Docker Compose로 한 번에 구성
- Java, Go, Node.js, Python 등 지원
- 단점: 메모리 요구량 높음 (Elasticsearch)

### Pinpoint (오픈소스, 셀프호스팅)
- 트레이스 + 메트릭 + 시각화 일체형
- Java 주력, Go/Python/Node.js 제한적 지원
- 단점: HBase + ZooKeeper 구성 필요, 셀프호스팅 난이도 높음

### New Relic (SaaS)
- 모두 포함된 SaaS, 설치 없음
- 영구 무료 플랜 (100GB/월)
- 단점: 셀프호스팅 불가

### Datadog (SaaS)
- 모두 포함된 SaaS, 업계 점유율 1위 (~52%)
- 단점: 셀프호스팅 불가, 규모 커지면 비용 높음

---

## 최종 APM 스택 결론 (Java/Go 중심)

### 추천 조합: Grafana + Prometheus + Jaeger (+ Loki)

- Jaeger — 트레이싱 전담. Tempo보다 기능 풍부 (서비스 의존성 그래프, UI 등), Go/Java 레퍼런스 압도적
- Prometheus — 메트릭 전담 (JVM, 런타임, 인프라)
- Grafana — 시각화 통합. Jaeger와 Prometheus를 데이터소스로 직접 지원
- Loki — 애플리케이션 로그 수집 (선택). `logger.info()`, `logger.error()` 등 개발자가 코드에서 찍는 로그

### 구성도

```
WAS (Java/Go)
  → OTel Collector
    ├→ Jaeger      (트레이싱)
    ├→ Prometheus  (메트릭)
    └→ Loki        (애플리케이션 로그, 선택)

Grafana
  ├→ Jaeger 데이터소스
  ├→ Prometheus 데이터소스
  └→ Loki 데이터소스 (선택)
```

### Loki 연계의 장점

Grafana에서 TraceID로 트레이스와 로그를 연결해서 조회 가능:
- Jaeger에서 특정 트랜잭션 느린 것 발견 → TraceID 클릭 → Loki에서 해당 요청의 애플리케이션 로그 바로 확인

### Grafana Tempo를 쓰지 않는 이유

Tempo는 "Grafana 생태계 안에서 트레이싱까지 한 번에"가 목적이나, 트레이싱 전문성은 Jaeger가 위.
Grafana는 Jaeger를 데이터소스로 직접 지원하므로 Tempo 없이도 동일한 통합 대시보드 구성 가능.

---

## SigNoz vs Grafana+Jaeger 스택 비교

두 선택지 모두 오픈소스 + 셀프호스팅 + OTel 네이티브 + 트레이스/메트릭/로그 통합이라는 같은 목적을 가진다.

### SigNoz

- 구성: 단일 애플리케이션 (ClickHouse 기반 백엔드 + 자체 UI)
- 설치: Docker Compose 한 번으로 전체 스택 기동
- 트레이스 + 메트릭 + 로그를 하나의 UI에서 통합 조회
- OTel 네이티브 설계 — SDK 연동 외 별도 에이전트 불필요
- 단점: ClickHouse 운영 필요, Grafana만큼 대시보드 유연성 낮음, 커뮤니티 규모가 Grafana 대비 작음

### Grafana + Jaeger + Prometheus + Loki 스택

- 구성: 4개 컴포넌트 각각 설치/운영 (Grafana, Jaeger, Prometheus, Loki)
- 트레이스(Jaeger), 메트릭(Prometheus), 로그(Loki)를 Grafana에서 데이터소스로 통합
- 각 컴포넌트가 업계 표준 수준의 성숙도 — 레퍼런스/플러그인 생태계 압도적
- 대시보드 유연성 최고 (Grafana)
- 단점: 컴포넌트가 많아 초기 구성/유지보수 복잡도 높음

### 비교 요약

- **간편하게 시작하고 싶다** → SigNoz (Docker Compose 하나로 끝)
- **유연성/생태계/레퍼런스가 중요하다** → Grafana+Jaeger 스택
- **학습 목적으로 각 컴포넌트를 이해하고 싶다** → Grafana+Jaeger 스택 (각 역할이 명확히 분리됨)
- **운영 환경에서 빠르게 도입하고 싶다** → SigNoz (관리 포인트 적음)

---

## 로컬 맥북 학습 환경 고려사항

### SigNoz의 ClickHouse는 로컬 학습에 적합한가

ClickHouse는 컬럼형 OLAP DB로 대용량 분석 쿼리에서 멀티코어를 적극 활용하도록 설계됐다.
로컬에서 기동은 되지만 학습 목적으로는 불필요하게 무겁다:

- 기본 메모리 사용량 높음 (최소 4GB+ 권장)
- SigNoz 전체 스택(ClickHouse + 백엔드 + 프론트엔드) 동시 기동 시 맥북 리소스 부담 큼
- 학습이 목적인데 ClickHouse 운영/튜닝까지 신경 써야 하는 부담

결론: **로컬 학습 환경에서는 Grafana+Jaeger 스택이 더 적합하다.**
SigNoz의 간편 설치 장점은 운영 환경 기준이고, 학습 환경에서는 컴포넌트가 분리된 Grafana 스택이 각 역할 이해에도 좋고 리소스 제어도 유리하다.

### Grafana 스택의 데이터 저장소

컴포넌트별로 저장소가 다르다:

- **Jaeger (트레이스)**
  - 기본: 인메모리 (재시작하면 사라짐, 테스트용)
  - 실사용: Elasticsearch / OpenSearch (가장 일반적), Cassandra
  - 학습용 추천: Badger (Jaeger 내장 로컬 파일 DB, 별도 설치 없음)

- **Prometheus (메트릭)**
  - 자체 내장 TSDB (로컬 디스크에 파일로 저장)
  - 별도 DB 불필요

- **Loki (로그)**
  - 기본: 로컬 파일시스템 (학습용으로 충분)
  - 실사용: S3 / GCS / MinIO 등 오브젝트 스토리지

- **Grafana (시각화)**
  - 대시보드 설정 저장용으로 SQLite 내장 (별도 DB 불필요)

결론: **학습 환경에서는 외부 DB 없이 완전히 구성 가능하다.**
Jaeger(Badger) + Prometheus(내장 TSDB) + Loki(로컬 파일) + Grafana(SQLite) 조합으로 충분하다.
