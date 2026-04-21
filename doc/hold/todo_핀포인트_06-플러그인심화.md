# TODO 06: 커스텀 플러그인 / 설정 심화 (보류)

> 기본 학습 완료 후 진행. Pinpoint Agent 플러그인 확장 및 고급 설정.

## 목표

기본 제공 플러그인 외에 커스텀 메서드 추적 설정을 추가한다.

## 주요 주제

### 특정 메서드 수동 추적

`pinpoint.config`에서 추가 설정:
```properties
# 특정 클래스/메서드를 추적 대상에 추가
profiler.include=com.example.MyService.myMethod
```

### Annotation 기반 추적

```java
@Trace  // Pinpoint 제공 어노테이션
public void myMethod() { ... }
```

### 샘플링 비율 조정

```properties
# 100% 샘플링 (부하 주의)
profiler.sampling.rate=1
# 10% 샘플링
profiler.sampling.rate=10
```

> Elastic APM의 `transaction_sample_rate`와 동일 개념.

### 플러그인 목록 확인

지원 프레임워크/라이브러리:
- Spring MVC, Spring Boot, Spring WebFlux
- Tomcat, Jetty, Netty
- MySQL, PostgreSQL, MongoDB, Redis
- gRPC, Kafka, RabbitMQ
- 기타: https://github.com/pinpoint-apm/pinpoint/tree/master/plugins

## 체크리스트

- [ ] `@Trace` 어노테이션으로 커스텀 메서드 추적 확인
- [ ] 샘플링 비율 변경 후 Scatter Chart 데이터 밀도 변화 확인
- [ ] 지원 플러그인 목록 검토
