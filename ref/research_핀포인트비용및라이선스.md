# Pinpoint APM 비용 및 라이선스

## 1. 오픈소스 Pinpoint (셀프 호스팅)

Pinpoint는 **Apache License 2.0** 오픈소스 프로젝트로, 소프트웨어 자체는 **완전 무료**이다.

- 소스코드: https://github.com/pinpoint-apm/pinpoint
- 라이선스 원문: https://github.com/pinpoint-apm/pinpoint/blob/master/LICENSE

Apache 2.0 라이선스이므로 상업적 목적 사용, 수정, 재배포 모두 자유롭다.

### 셀프 호스팅 시 비용 구조

소프트웨어 비용은 없지만 인프라 구성에 비용이 발생한다:

- **HBase 클러스터**: 가장 큰 비용 요소. ZooKeeper 포함 최소 3~5대 권장
- **Collector 서버**: 트래픽에 따라 수평 확장
- **Pinpoint Web 서버**: 1대로도 운영 가능
- **운영 인력**: HBase 관리는 난이도가 높아 전담 인력이 필요할 수 있음

### 과거 라이선스 이슈 (해결 완료)

v2.0.0 이전에는 UI에서 상용 차트 라이브러리를 사용하여 상업적 운영 시 별도 라이선스 구매가 필요했다:

- **GoJS**: 서버맵(노드-엣지 그래프) 렌더링에 사용. 상용 라이선스 필요
- **amCharts**: Inspector 차트에 사용. 상용 라이선스 필요

**v2.0.0(2020년)부터 두 라이브러리를 모두 오픈소스 대체재로 교체**하여 이 이슈는 완전히 해결되었다.
현재는 상업적 목적으로도 추가 비용 없이 자유롭게 사용 가능하다.

참고 이슈:
- [GoJS 라이선스 문제 논의](https://github.com/pinpoint-apm/pinpoint/issues/1308)
- [v2.0.0 릴리즈 노트 (상용 의존성 제거)](https://github.com/pinpoint-apm/pinpoint/releases/tag/v2.0.0)

---

## 2. Pinpoint Cloud (네이버 클라우드 플랫폼)

네이버 클라우드 플랫폼(NCP)에서 Pinpoint를 매니지드 서비스로 제공한다.

- 서비스 페이지: https://www.ncloud.com/v2/product/management/pinpointCloud
- 인프라 구성, HBase 운영 부담 없이 Pinpoint를 바로 사용 가능

### 오픈소스 vs Pinpoint Cloud 비교

- **오픈소스 셀프 호스팅**
  - 비용: 인프라 비용만 발생 (소프트웨어 무료)
  - 장점: 완전한 제어권, 데이터 내부 보관
  - 단점: HBase 클러스터 직접 구성 및 운영, 초기 세팅 난이도 높음

- **Naver Cloud Pinpoint Cloud**
  - 비용: 사용량 기반 종량제 (NCP 요금 체계 적용)
  - 장점: 인프라/운영 부담 없음, 빠른 시작
  - 단점: NCP 환경에 종속, 데이터가 외부 클라우드에 저장

> 정확한 요금은 NCP 요금 계산기(https://www.ncloud.com/v2/charge/calc) 또는 영업팀 문의 필요

---

## 3. 상용 APM과 비용 비교 (참고)

- **Elastic APM**: Elastic Cloud 기준 월 $95~(Observability 플랜), 셀프 호스팅은 무료
- **Datadog APM**: 호스트당 월 $31~(APM 기준), 대규모 환경에서 비용이 빠르게 증가
- **New Relic**: 월 100GB 무료, 초과 시 GB당 과금
- **Pinpoint 오픈소스**: 소프트웨어 비용 없음. 인프라 비용만 발생

소규모~중규모 Java 백엔드 환경에서 비용 효율이 높은 선택지이다.

---

## 참고 자료

- [Pinpoint GitHub - LICENSE](https://github.com/pinpoint-apm/pinpoint/blob/master/LICENSE)
- [GoJS 라이선스 이슈 #1308](https://github.com/pinpoint-apm/pinpoint/issues/1308)
- [v2.0.0 릴리즈 노트](https://github.com/pinpoint-apm/pinpoint/releases/tag/v2.0.0)
- [Naver Cloud Pinpoint Cloud](https://www.ncloud.com/v2/product/management/pinpointCloud)
