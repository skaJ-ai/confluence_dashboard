# Report Page Template

이 문서는 집계 페이지를 만들 때 바로 따라 넣는 설정값 모음이다.

## 1. 루트 페이지 전체 현황

페이지명 예:

```text
Agent 개발현황
```

매크로:

- `Content Properties Report`

설정값:

| 항목 | 값 |
| --- | --- |
| Labels | `agent-task` |
| With ancestor | `Agent 개발현황` |
| Columns to show | `사업부, 구분, 과제명, 상태, 담당, 우선순위, 완료예정일` |
| Title column heading | `과제 페이지` |
| Sort by | `사업부` |

## 2. 사업부별 현황

페이지명 예:

```text
VD 개발과제 현황
```

설정값:

| 항목 | 값 |
| --- | --- |
| Labels | `agent-task` |
| With ancestor | `VD` 페이지 |
| Columns to show | `구분, 과제명, 상태, 담당, 완료예정일` |
| Title column heading | `과제 페이지` |
| Sort by | `구분` |

## 3. 구분별 현황

페이지명 예:

```text
채용 과제 현황
```

설정값:

| 항목 | 값 |
| --- | --- |
| Labels | Label 필터 2개 사용: `agent-task`, `talent-acquisition` |
| Columns to show | `사업부, 과제명, 상태, 담당, 완료예정일` |
| Title column heading | `과제 페이지` |
| Sort by | `사업부` |

## 4. 사업부 + 구분 조합 현황

예:

```text
VD 채용 과제 현황
```

설정값:

| 항목 | 값 |
| --- | --- |
| Labels | Label 필터 2개 사용: `agent-task`, `talent-acquisition` |
| With ancestor | `VD` 페이지 |
| Columns to show | `과제명, 상태, 담당, 완료예정일` |
| Sort by | `완료예정일` |

## 5. 추천 집계 페이지 묶음

- 전체 개발과제 현황
- 사업부별 현황
- 구분별 현황
- 완료예정일 임박 과제
- 진행중 과제

`진행중 과제`처럼 상태 기반 뷰가 더 필요하면, 상태를 label로 추가하기보다 속성 컬럼으로 유지하고 리포트 페이지를 별도로 나누는 쪽이 보통 더 단순하다.
