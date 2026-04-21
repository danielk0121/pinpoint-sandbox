# TODO 01: Pinpoint 아키텍처 이해

> Elastic APM / Scouter 경험자 기준으로 Pinpoint 구성 요소를 매핑해서 이해한다.

## 목표

Pinpoint의 핵심 컴포넌트와 데이터 흐름을 파악한다.

## 다른 APM과 비교

| 역할 | Elastic APM | Scouter | Pinpoint |
|------|-------------|---------|----------|
| 데이터 수집 에이전트 | APM Agent | Scouter Agent | Pinpoint Agent |
| 데이터 수신/처리 | APM Server | Scouter Server | Pinpoint Collector |
| 저장소 | Elasticsearch | 자체 파일 DB | HBase |
| 시각화 UI | Kibana / APM UI | Scouter Web | Pinpoint Web |

## Pinpoint 구성 요소

- **Pinpoint Agent**
  - Java 앱 JVM에 `-javaagent`로 붙임 (코드 수정 없음)
  - bytecode instrumentation 방식 (Elastic APM Java Agent와 동일 방식)
  - 트랜잭션 데이터를 Collector로 UDP/GRPC 전송

- **Pinpoint Collector**
  - Agent로부터 데이터를 받아 HBase에 저장
  - Scouter Server와 역할 유사

- **HBase**
  - Pinpoint 전용 저장소 (Elastic의 Elasticsearch 포지션)
  - ZooKeeper 기반으로 동작
  - 직접 쿼리보다는 Pinpoint Web을 통해 조회

- **Pinpoint Web**
  - 서비스 맵, 트랜잭션 상세, 응답시간 통계 UI 제공
  - Kibana APM UI와 유사한 역할

## 데이터 흐름

```
Java App + Agent
      ↓ (UDP / gRPC)
  Collector
      ↓
    HBase (ZooKeeper)
      ↑
  Pinpoint Web UI
```

## 핵심 개념

- **TransactionId**: 분산 요청 하나를 추적하는 고유 ID (Elastic의 trace.id와 동일 개념)
- **SpanId**: 개별 서비스 내 처리 단위 (Elastic의 span과 동일 개념)
- **Service Map**: 서비스 간 호출 관계를 자동으로 시각화 (Pinpoint의 대표 기능)

## 체크리스트

- [ ] Pinpoint GitHub README 훑어보기
- [ ] 위 컴포넌트 구성도 직접 그려보기
- [ ] HBase가 왜 Elasticsearch 대신 쓰이는지 이해하기 (시계열 대용량 write 최적화)
