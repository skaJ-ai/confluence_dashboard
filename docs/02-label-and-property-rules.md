# 레이블과 속성 규칙

## 기본 원칙

- `페이지 트리`는 탐색용이다.
- `레이블`은 매트릭스 셀 집계의 기준이다.
- `페이지 속성`은 보고서 표에서 보여줄 값이다.

중요:

- 이 설계에서 매트릭스 셀 집계는 `레이블 기반`이다.
- `부모 페이지`나 `상위 항목 포함`은 기본값이 아니다.

## 필수 레이블

한 Agent 페이지에는 아래 4종 레이블을 붙인다.

1. 공통 레이블
2. 개발주체 레이블
3. 도메인 레이블
4. 셀 전용 레이블

## 1. 공통 레이블

- `agent-task`

## 2. 개발주체 레이블

| 표시명 | 레이블 |
| --- | --- |
| W/G | `owner-wg` |
| VD | `owner-vd` |
| DA | `owner-da` |
| MX | `owner-mx` |
| NW | `owner-nw` |
| 의료기기 | `owner-medical-device` |
| SR | `owner-sr` |
| CDO | `owner-cdo` |
| 생기연 | `owner-gtr` |

## 3. 도메인 레이블

| 표시명 | 레이블 |
| --- | --- |
| 인력운영 | `dm-workforce` |
| 제도 | `dm-policy` |
| 임원조직 | `dm-executive-org` |
| 노사 | `dm-labor` |
| 조직문화 | `dm-culture` |
| 채용 | `dm-talent-acquisition` |
| 총무 | `dm-general-affairs` |
| 집단지성 | `dm-collective-intelligence` |
| 보상/근태 | `dm-reward-attendance` |

## 4. 셀 전용 레이블

형식:

```text
cell-{개발주체}-{도메인}
```

예:

| 셀 | 레이블 |
| --- | --- |
| W/G x 채용 | `cell-wg-talent-acquisition` |
| VD x 채용 | `cell-vd-talent-acquisition` |
| 생기연 x 제도 | `cell-gtr-policy` |

## 레이블 예시

`W/G > 제도 > 규정 비교 에이전트`

- `agent-task`
- `owner-wg`
- `dm-policy`
- `cell-wg-policy`

`VD > JD 초안 생성 에이전트`

- `agent-task`
- `owner-vd`
- `dm-talent-acquisition`
- `cell-vd-talent-acquisition`

## 권장 페이지 속성 컬럼

`페이지 속성` 표에는 아래 컬럼을 권장한다.

| 컬럼 | 설명 |
| --- | --- |
| 개발주체 | `W/G`, `VD`, `DA` 등 |
| 도메인 | `채용`, `제도`, `조직문화` 등 |
| 상태 | 아이디어 / 검토중 / 진행중 / 완료 / 보류 |
| 담당 | 실무 담당자 |
| 우선순위 | High / Medium / Low |
| 완료예정일 | 목표 날짜 |
| 목적 | 해결하려는 문제 |
| 관련 링크 | Jira, Drive, Figma 등 |

`과제명`은 페이지 제목으로 관리한다.

## 왜 셀 전용 레이블이 필요한가

- 매트릭스 셀은 `개발주체 + 도메인`의 교차 조건이다.
- `페이지 속성 보고서` 셀을 가장 단순하게 만들려면 셀마다 전용 레이블 하나를 두는 것이 안전하다.
- 그래서 보고서 셀에서는 `레이블 = cell-...` 하나만 넣는 방식으로 맞춘다.

## 피해야 할 것

- 개발주체 레이블을 두 개 붙이는 것
- 도메인 레이블을 두 개 붙이는 것
- 셀 전용 레이블을 빼먹는 것
- 페이지 제목에 `[채용]` 같은 접두사를 붙이는 것
