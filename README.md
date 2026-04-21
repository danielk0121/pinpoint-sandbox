# APM Sandbox

Java/Go APM 도구 학습 및 테스트 환경입니다.

## 학습 대상 APM

### 진행 중: Grafana 스택 + Jaeger + Loki

- Grafana + Prometheus + Jaeger + Loki 조합으로 Java/Go 통합 모니터링
- 로컬 셀프 호스팅 환경에서 구축 및 테스트
- 작업 문서: `doc/ing/todo_그라파나스택학습.md`

### 보류: Pinpoint

- Naver 오픈소스 APM, Java 특화 올인원 구성
- 작업 문서: `doc/hold/todo_핀포인트_*.md`

## 구조

```
pinpoint-sandbox/
├── doc/
│   ├── ing/    # 진행 중인 작업
│   ├── hold/   # 보류 중인 작업
│   └── done/   # 완료된 작업
└── ref/        # 리서치 문서
```
