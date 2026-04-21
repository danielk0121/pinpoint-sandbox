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

## 학습 대상

| 도구 | 개발사 / 국가 | 시작 | 비용 | 클라우드 무료 | 셀프호스팅 | 지원 언어 | 인기도 | OTel |
|------|--------------|------|------|--------------|-----------|-----------|--------|------|
| **Pinpoint** | 네이버 (오픈소스) / 한국 | 2015 | 완전 무료. Naver Cloud는 유료 | Naver Cloud 체험 (요금 확인 필요) | ⭐⭐⭐ HBase + ZooKeeper 구성 | Java (주력), PHP, Python, Node.js, Go | 중간. GitHub ★14k. 일 200억 건 처리 | ✕ |

---

## 모르는 것들

| 도구 | 개발사 / 국가 | 시작 | 비용 | 클라우드 무료 | 셀프호스팅 | 지원 언어 | 인기도 | OTel |
|------|--------------|------|------|--------------|-----------|-----------|--------|------|
| **Datadog** | Datadog Inc. / 미국 | 2010 | 무료 티어(5 호스트). APM $31~/호스트/월 | 14일 트라이얼 + 무료 티어 | 불가 (SaaS) | Java, Go, Python, Node.js, Ruby, .NET, PHP, C++ | 매우 높음. 점유율 ~52%(1위). 고객 30k+. 매출 $3.3B | ○ |
| **Jaeger** | CNCF 오픈소스 (Uber 시작) / 미국 | 2015 | 완전 무료 | 해당 없음 | ⭐ Docker 단일 컨테이너 | OTel SDK 경유 전 언어 | 높음. GitHub ★22k. CNCF Graduated | ◎ |
| **Grafana Tempo** | Grafana Labs / 미국 | 2020 | 오픈소스 무료. Cloud 50GB/월 무료 | 영구 무료 플랜 | ⭐⭐ Prometheus + Grafana 스택 | OTel SDK 경유 전 언어 | 중상. GitHub ★5k. 설문 Grafana+Prometheus 43% | ◎ |
| **Uptrace** | 오픈소스 프로젝트 / - | 2021 | 오픈소스 무료. Cloud ~$5/백만 스팬 | 무료 플랜 | ⭐ Docker Compose | OTel SDK 경유 전 언어 | 낮음. GitHub ★4k | ◎ |
| **Instana** | IBM (2015 창립, 2021 인수) / 독일→미국 | 2015 | $75~/호스트/월. 무료 플랜 없음 | 14일 트라이얼 | 불가 (엔터프라이즈 온프레미스 협의) | Java, Go, Python, Node.js, Ruby, PHP, .NET 등 14개 | 중간. IBM 엔터프라이즈 중심. ~3% | ○ |
| **Lightstep** | ServiceNow (2015 창립, 2023 인수) / 미국 | 2015 | 무료 플랜(소규모). 유료 ~$100~/월 | 무료 플랜 | 불가 (SaaS) | OTel SDK 경유 전 언어 | 중간. OTel 창시자 설립, 인수 후 입지 약화 | ◎ |
| **Groundcover** | groundcover / 이스라엘 | 2021 | 무료 플랜. 유료 $250~/월 | 무료 플랜 | ⭐⭐ Kubernetes + eBPF | 언어 무관 (eBPF 커널 레벨 자동 수집) | 낮음. 신생 스타트업 | △ |
| **Helios** | Helios / 이스라엘 | 2021 | 무료 플랜. 유료 $99~/월 | 무료 플랜 | 불가 (SaaS) | OTel SDK 경유 (Java, Node.js, Python, Go 등) | 낮음. 소규모 스타트업 | ○ |
| **Aspecto** | Aspecto / 이스라엘 | 2020 | 무료 플랜. 유료 $49~/월 | 무료 플랜 | 불가 (SaaS) | OTel SDK 경유 (Java, Node.js, Python, Go 등) | 낮음. 소규모 스타트업 | ○ |
| **Last9** | Last9 / 인도 | 2021 | 유료 (플랜별 문의) | 트라이얼 제공 | 불가 (SaaS) | OTel SDK 경유 전 언어 | 낮음. 신생 스타트업 | ○ |

---

## 관심 없는 것들

| 도구 | 개발사 / 국가 | 비고 |
|------|--------------|------|
| **AppSignal** | AppSignal / 네덜란드 | 소규모 팀 대상 간단한 APM. $19~/월 |

---

## 인기도 수치 요약

- 상용 APM 시장 점유율: Datadog ~52% > New Relic ~24% > Instana/Dynatrace ~3%
- GitHub ★: Sentry 43k > Jaeger 22k > Pinpoint 14k > Grafana Tempo 5k > Uptrace 4k > Scouter 2k
- 개발자 설문 (Stack Overflow 2025): Grafana+Prometheus 43% > Sentry 32% > New Relic 13%

---

## APM 추천 (Java/Go 중심, 셀프호스팅 또는 클라우드 무료 기준)

조건: PC 셀프호스팅 또는 클라우드 무료 티어, Java/Go 필수, Node/Python 선택, 업계 인지도 우선

### 1순위: New Relic
- Java, Go 완벽 지원
- 영구 무료 플랜 (100GB/월)
- 업계 인지도 2위 (~24%)
- 셀프호스팅 불필요, 바로 시작 가능

### 2순위: Grafana Tempo (+ Prometheus 스택)
- Java, Go, Node.js, Python 모두 OTel 경유 지원
- 클라우드 무료 50GB/월 또는 PC 셀프호스팅 가능
- 개발자 설문 1위 (43%)
- 단점: 구성 복잡도 있음

### 3순위: Jaeger
- PC 셀프호스팅 가장 쉬움 (Docker 단일 컨테이너)
- Java, Go OTel 경유 지원
- GitHub ★22k, CNCF Graduated
- 단점: 클라우드 무료 없음, 시각화 도구 별도 필요 (Grafana 등)
