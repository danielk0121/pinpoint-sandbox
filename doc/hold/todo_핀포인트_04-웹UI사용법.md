# TODO 04: Pinpoint Web UI 사용법

> Kibana APM UI / Scouter Web 경험 기반으로 Pinpoint UI 주요 화면 익히기.

## 목표

Pinpoint Web의 핵심 화면을 직접 탐색하고 각 기능의 용도를 파악한다.

## 주요 화면

### 1. Server Map (서비스 맵)

- **위치**: 메인 화면
- **기능**: 서비스 간 호출 관계를 노드-엣지 그래프로 자동 표현
- **Elastic APM 비교**: APM → Service Map과 동일
- **활용**:
  - 노드 클릭 → 해당 서비스의 요청 통계
  - 엣지 클릭 → 두 서비스 간 호출 상세
  - 시간 범위 조절로 특정 시간대 트래픽 패턴 확인

### 2. Inspector

- **위치**: 상단 메뉴 → Inspector
- **기능**: 선택한 앱의 JVM 메트릭 (Heap, GC, Thread, CPU)
- **Scouter 비교**: Scouter의 실시간 대시보드와 유사
- **활용**:
  - GC 빈도 및 힙 사용량 추이 확인
  - Active Thread 수 모니터링

### 3. Transaction List (트랜잭션 목록)

- **위치**: Server Map에서 노드 클릭 → Scatter Chart → 점 드래그 선택
- **기능**: 선택한 시간/응답시간 범위의 트랜잭션 목록
- **Elastic APM 비교**: APM → Transactions 목록과 유사
- **활용**:
  - 느린 요청만 드래그로 선택해서 상세 조회
  - Scatter Chart X축: 시간, Y축: 응답시간

### 4. Transaction Detail (트랜잭션 상세 / Call Tree)

- **위치**: 트랜잭션 목록 → 개별 트랜잭션 클릭
- **기능**: 하나의 요청에 대한 전체 Call Tree
- **Elastic APM 비교**: APM Trace 상세 화면 (워터폴 뷰)
- **Scouter 비교**: XLog 상세와 동일 개념
- **활용**:
  - SQL 쿼리, HTTP 호출, 메서드 실행시간 단계별 확인
  - 병목 구간 특정

### 5. Scatter Chart 활용 팁

```
Y축 높은 곳 (느린 요청) 드래그 → 느린 트랜잭션만 골라서 분석
에러 트랜잭션은 빨간 점으로 표시됨
```

## 체크리스트

- [ ] Server Map에서 연동한 앱 노드 확인
- [ ] Inspector에서 JVM 힙/GC 메트릭 확인
- [ ] Scatter Chart에서 트랜잭션 점 드래그로 목록 조회
- [ ] 개별 트랜잭션 Call Tree에서 SQL/HTTP 구간 확인
- [ ] 에러 트랜잭션 빨간 점 클릭 후 스택 트레이스 확인
