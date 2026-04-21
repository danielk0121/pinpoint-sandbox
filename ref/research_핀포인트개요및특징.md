# Pinpoint APM 개요 및 주요 특징

## 1. Pinpoint란?

Pinpoint는 네이버에서 2012년부터 개발하여 2015년 오픈소스로 공개한 **대규모 분산 시스템용 APM(Application Performance Management)** 도구이다.

Google의 [Dapper 논문](https://research.google/pubs/pub36356/)에서 영감을 받아 설계되었으며, 수십~수백 개의 서버로 구성된 n-tier 분산 환경에서 트랜잭션 흐름을 추적하고 성능 병목을 찾는 것을 목적으로 한다.

- GitHub: https://github.com/pinpoint-apm/pinpoint
- 공식 문서: https://pinpoint-apm.gitbook.io/pinpoint/

---

## 2. 다른 APM과 비교

- **Elastic APM**: Elasticsearch 기반 저장, OpenTelemetry 호환, 멀티 언어 지원에 강점
- **Scouter**: 국산 오픈소스, 경량, 실시간 모니터링 중심, 소규모 환경에 적합
- **Pinpoint**: HBase 기반 대용량 저장, 코드 무수정 bytecode 계측, 대규모 Java 환경 특화

---

## 3. 핵심 특징

### 3-1. 코드 수정 없는 계측 (Bytecode Instrumentation)

에이전트를 `-javaagent` 옵션으로 붙이기만 하면 되며, 애플리케이션 코드를 전혀 수정할 필요가 없다.

클래스 로딩 시점에 bytecode를 조작하여 메서드의 `before()` / `after()` 시점에 자동으로 트레이싱 로직을 주입한다.

### 3-2. 분산 트랜잭션 추적

RPC 호출 헤더에 추적 태그를 심어 서비스 간 요청 흐름을 end-to-end로 연결한다.

추적에 사용되는 3가지 핵심 데이터 구조:
- **Span**: 하나의 RPC 처리 단위. 내부 메서드 호출(SpanEvent)들을 포함
- **Trace**: 동일한 TransactionId를 공유하는 Span들의 집합. 하나의 요청 전체
- **TraceId**: `TransactionId + SpanId + ParentSpanId` 조합으로 구성
  - TransactionId: 전체 요청을 식별하는 전역 고유 ID (Elastic의 `trace.id`와 동일 개념)
  - SpanId: 개별 서비스 처리 단위 ID
  - ParentSpanId: 부모 Span 참조 (-1이면 최초 진입점)

### 3-3. 자동 서비스 토폴로지 감지

서비스 간 호출 관계를 별도 설정 없이 자동으로 감지하여 Server Map으로 시각화한다.

### 3-4. 수평 확장성

대규모 서버 그룹을 지원하도록 설계되어 있으며, Collector와 HBase를 수평 확장하면 수천 대 규모도 처리 가능하다.

---

## 4. 아키텍처 구성 요소

```
[Java App + Pinpoint Agent]
          ↓ UDP / gRPC
  [Pinpoint Collector]
          ↓
  [HBase + ZooKeeper]
          ↑
  [Pinpoint Web UI]
```

- **Pinpoint Agent**
  - JVM에 `-javaagent`로 부착
  - 트랜잭션 데이터를 비동기 UDP로 Collector에 전송 (앱 성능 영향 최소화)
  - 지원 언어: Java, PHP, Python

- **Pinpoint Collector**
  - Agent로부터 데이터 수신 및 HBase 저장 처리
  - 수평 확장 가능

- **HBase**
  - Pinpoint 전용 데이터 저장소
  - 대용량 시계열 write에 최적화 (Elasticsearch 대비 write 처리량 우위)
  - ZooKeeper로 클러스터 관리
  - 최신 버전에서는 Inspector 데이터를 Apache Pinot에 저장하는 방향으로 진화 중

- **Pinpoint Web**
  - HBase에서 데이터를 조회하여 시각화
  - Server Map, Scatter Chart, Call Tree, Inspector 제공

---

## 5. 주요 UI 기능

- **Server Map**
  - 서비스 간 호출 관계를 노드-엣지 그래프로 자동 시각화
  - 노드 클릭 시 해당 서비스의 트랜잭션 수, 응답시간 통계 확인

- **Scatter Chart (Request/Response)**
  - X축: 시간, Y축: 응답시간
  - 영역 드래그로 특정 트랜잭션만 골라 상세 조회 가능
  - 에러 트랜잭션은 빨간 점으로 표시

- **Call Tree**
  - 하나의 요청에 대한 전체 메서드 호출 계층 구조
  - SQL 쿼리, HTTP 호출, 각 메서드의 실행 시간 포함
  - 코드 레벨의 병목 구간 특정 가능

- **Realtime Active Thread Chart**
  - 애플리케이션 내 활성 스레드 수를 실시간 모니터링

- **Inspector**
  - JVM Heap, GC, CPU 사용률, TPS, JVM 인자 등 상세 메트릭
  - Scouter의 실시간 대시보드와 유사한 역할

---

## 6. 성능 최적화 설계

대용량 환경에서도 오버헤드를 최소화하기 위해 아래 기법을 사용한다:

- **비동기 UDP 전송**: 데이터 전송이 앱 스레드를 블로킹하지 않음
- **Thrift 바이너리 인코딩**: 빠른 직렬화/역직렬화
- **가변 길이 인코딩**: 8바이트 정수를 1~10바이트로 압축
- **Constant Table**: 반복되는 API 문자열이나 SQL을 ID로 치환하여 전송량 절감
- **샘플링**: 대용량 트래픽 환경에서 1~5% 샘플링으로 HBase 부하 조절

---

## 7. 지원 플러그인 (주요)

- 웹 프레임워크: Spring MVC, Spring Boot, Spring WebFlux
- WAS: Tomcat, Jetty, Netty, Undertow
- DB: MySQL, PostgreSQL, MongoDB, Redis, HBase
- 메시징: Kafka, RabbitMQ
- RPC: gRPC, HTTP Client (Apache, OkHttp 등)
- 전체 목록: https://github.com/pinpoint-apm/pinpoint/tree/master/plugins

---

## 참고 자료

- [Pinpoint GitHub](https://github.com/pinpoint-apm/pinpoint)
- [Pinpoint 공식 문서 - Overview](https://pinpoint-apm.gitbook.io/pinpoint/want-a-quick-tour/overview)
- [Technical Overview of Pinpoint (Wiki)](https://github.com/pinpoint-apm/pinpoint/wiki/Technical-Overview-Of-Pinpoint)
- [Google Dapper 논문](https://research.google/pubs/pub36356/)
