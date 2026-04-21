# TODO 02: Docker Compose로 Pinpoint 스택 실행

> 로컬에서 가장 빠르게 전체 스택을 띄우는 방법. Elastic Stack docker-compose와 유사한 접근.

## 목표

pinpoint-docker를 이용해 HBase + Collector + Web을 한 번에 실행한다.

## 사전 요구사항

- Docker Desktop 설치 및 실행
- 메모리 여유 권장: 최소 6GB (HBase가 무겁다)

## 실행 절차

### 1. 공식 docker 저장소 클론

```bash
git clone https://github.com/pinpoint-apm/pinpoint-docker.git
cd pinpoint-docker
```

### 2. 버전 확인 및 선택

```bash
# 최신 태그 확인
git tag | tail -10
# 예: git checkout 3.0.0
```

### 3. 스택 실행

```bash
docker-compose pull
docker-compose up -d
```

> HBase 초기화에 1~2분 걸린다. Collector/Web은 HBase가 준비될 때까지 재시작 반복이 정상.

### 4. 동작 확인

| 컴포넌트 | 확인 방법 |
|---------|---------|
| Pinpoint Web UI | http://localhost:8080 |
| Collector 상태 | `docker-compose logs pinpoint-collector` |
| HBase 상태 | `docker-compose logs pinpoint-hbase` |

### 5. 종료

```bash
docker-compose down
# 데이터까지 삭제하려면
docker-compose down -v
```

## 컨테이너 구성 확인

```bash
docker-compose ps
```

예상 컨테이너:
- `pinpoint-hbase`
- `pinpoint-collector`
- `pinpoint-web`
- `zoo1` (ZooKeeper)

## 체크리스트

- [ ] docker-compose up 후 Web UI 접속 성공
- [ ] 초기 화면에서 "No data" 상태 확인 (Agent 미연결 정상)
- [ ] 각 컨테이너 로그에서 에러 없는지 확인
