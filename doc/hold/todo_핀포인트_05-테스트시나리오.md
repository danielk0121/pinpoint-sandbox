# TODO 05: 테스트 시나리오 실습

> 실제 트래픽을 발생시켜 Pinpoint의 트레이싱/모니터링 기능을 검증한다.

## 목표

의도적인 시나리오를 만들어 Pinpoint가 어떻게 포착하는지 직접 확인한다.

## 전제 조건

- todo_02 (Docker 스택) 완료
- todo_03 (Agent 연동) 완료
- 테스트용 Spring Boot 앱 실행 중

## 시나리오 1: 정상 요청 추적

```bash
# 여러 번 요청 발생
curl http://localhost:8080/api/hello
```

**확인 포인트**:
- Server Map에 서비스 노드 생성
- Scatter Chart에 파란 점 생성
- Call Tree에서 Controller → Service → Repository 계층 확인

## 시나리오 2: 느린 쿼리 추적

```java
// 테스트용: Thread.sleep으로 느린 처리 시뮬레이션
// 또는 실제 slow query 발생
```

```bash
curl http://localhost:8080/api/slow
```

**확인 포인트**:
- Scatter Chart에서 Y축 높은 위치에 점 표시
- Call Tree에서 느린 구간(SQL 또는 메서드) 빨간 하이라이트

## 시나리오 3: 에러 추적

```bash
# 404, 500 에러 발생 요청
curl http://localhost:8080/api/error
```

**확인 포인트**:
- Scatter Chart에서 빨간 점 표시
- 트랜잭션 상세에서 Exception 스택 트레이스 확인

## 시나리오 4: 분산 트레이싱 (마이크로서비스)

앱 A → 앱 B HTTP 호출 구성:

```
[앱 A: Agent 연동] --HTTP--> [앱 B: Agent 연동]
```

**확인 포인트**:
- Server Map에서 A → B 엣지 생성
- 트랜잭션 Call Tree에서 A의 span 안에 B 호출 span 포함
- TransactionId가 A/B 동일한지 확인 (헤더: `Pinpoint-TraceId`)

> Elastic APM의 `traceparent` 헤더와 같은 역할을 Pinpoint는 자체 헤더로 전파.

## 시나리오 5: SQL 모니터링

- DB 연동 앱에서 쿼리 실행
- Call Tree에서 `executeQuery` 구간에 실제 SQL 문 표시되는지 확인
- 바인딩 파라미터 마스킹 여부 확인 (민감 데이터 주의)

## 체크리스트

- [ ] 시나리오 1: 정상 요청 Call Tree 확인
- [ ] 시나리오 2: 느린 요청 Scatter Chart 위치 확인
- [ ] 시나리오 3: 에러 스택 트레이스 확인
- [ ] 시나리오 4: 분산 트레이싱 Server Map 엣지 확인
- [ ] 시나리오 5: SQL 구문 Call Tree에서 확인
