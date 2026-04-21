# Pinpoint Sandbox

Naver Pinpoint APM 학습 및 테스트 환경입니다.

Pinpoint는 Java 분산 애플리케이션의 성능을 모니터링하는 오픈소스 APM 도구로,
서비스 간 호출 관계 추적, 응답시간 분석, JVM 메트릭 수집 등을 제공합니다.

## 목적

- Pinpoint 구성 요소(Collector, Web, Agent) 설치 및 설정 학습
- 샘플 애플리케이션에 Agent 연동 테스트
- 분산 트레이싱 및 모니터링 기능 탐구

## 구조

```
pinpoint-sandbox/
├── doc/
│   ├── ing/    # 진행 중인 작업
│   ├── hold/   # 보류 중인 작업
│   └── done/   # 완료된 작업
└── ...
```

## 참고

- [Pinpoint GitHub](https://github.com/pinpoint-apm/pinpoint)
- [Pinpoint 공식 문서](https://pinpoint-apm.gitbook.io/pinpoint/)
