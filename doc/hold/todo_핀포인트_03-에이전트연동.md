# TODO 03: Pinpoint Java Agent 연동

> Elastic APM Java Agent처럼 `-javaagent` 옵션으로 붙인다. 코드 수정 없음.

## 목표

샘플 Java 앱(또는 Spring Boot)에 Pinpoint Agent를 붙여 Collector로 데이터를 전송한다.

## Agent 다운로드

```bash
# Pinpoint 릴리즈 페이지에서 버전에 맞는 agent 다운로드
# https://github.com/pinpoint-apm/pinpoint/releases

wget https://github.com/pinpoint-apm/pinpoint/releases/download/v3.0.0/pinpoint-agent-3.0.0.tar.gz
tar -xzf pinpoint-agent-3.0.0.tar.gz
```

> docker-compose 버전과 Agent 버전을 맞춰야 한다.

## Agent 디렉토리 구조

```
pinpoint-agent/
├── pinpoint-bootstrap-x.x.x.jar   ← javaagent로 지정하는 파일
├── pinpoint.config                  ← 핵심 설정 파일
├── profiles/
│   ├── release/
│   └── local/
└── plugin/                          ← 각 프레임워크별 instrumentation 플러그인
```

## pinpoint.config 핵심 설정

```properties
# Collector 주소 (docker-compose 기준 localhost)
profiler.transport.grpc.collector.ip=localhost

# 앱 이름 (Pinpoint Web의 서비스 맵에서 노드 이름이 됨)
profiler.applicationName=my-app

# 에이전트 ID (같은 앱의 인스턴스 구분용)
profiler.agentId=my-app-01
```

> Elastic APM의 `service.name`, `service.node.name`과 동일한 개념.

## JVM 실행 옵션

```bash
java \
  -javaagent:/path/to/pinpoint-agent/pinpoint-bootstrap-x.x.x.jar \
  -Dpinpoint.agentId=my-app-01 \
  -Dpinpoint.applicationName=my-app \
  -jar my-app.jar
```

## Spring Boot 예시 (gradle)

```bash
./gradlew bootRun --jvmArgs="\
  -javaagent:/path/to/pinpoint-bootstrap.jar \
  -Dpinpoint.agentId=my-app-01 \
  -Dpinpoint.applicationName=my-app"
```

## Docker 환경에서 앱 실행 시

Collector가 docker 네트워크 내에 있다면:
```properties
profiler.transport.grpc.collector.ip=pinpoint-collector
```

앱도 같은 docker network에 참여시키거나, `host` 네트워크 사용.

## 연동 확인

1. 앱 실행 후 HTTP 요청 몇 번 발생
2. Pinpoint Web UI → 좌측 앱 목록에 `my-app` 표시되면 성공
3. Inspector → JVM 메트릭, 트랜잭션 목록 확인

## 체크리스트

- [ ] Agent 버전과 Collector 버전 일치 확인
- [ ] pinpoint.config에서 applicationName / agentId 설정
- [ ] `-javaagent` 옵션으로 앱 실행
- [ ] Web UI에서 앱 노드 확인
- [ ] 샘플 요청 후 트랜잭션 추적 데이터 확인
