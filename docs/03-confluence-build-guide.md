# Confluence Build Guide

## 1. Space 준비

1. 전용 Space를 하나 만든다.
2. 루트 페이지 `Agent 개발과제`를 만든다.
3. 그 아래에 사업부 상위 페이지를 만든다.

## 2. 개발과제 페이지 만들기

1. 사업부 페이지 아래에서 새 페이지를 만든다.
2. 제목은 `[구분] 과제명` 형식으로 쓴다.
3. 페이지에 아래 label 3개를 붙인다.
   - `agent-task`
   - 해당 사업부 label 1개
   - 해당 구분 label 1개
4. 본문 상단에 `Content Properties` 매크로를 넣는다.
5. 매크로 안에 2열 테이블을 만들고 `templates/agent-task-page-template.md` 내용대로 채운다.

## 3. 전체 집계 페이지 만들기

1. `00. 집계 현황` 아래에 `전체 개발과제 현황` 페이지를 만든다.
2. 페이지에 `Content Properties Report` 매크로를 넣는다.
3. 아래처럼 설정한다.

| 항목 | 값 |
| --- | --- |
| Labels | `agent-task` |
| Columns to show | `사업부, 구분, 과제명, 상태, 담당, 우선순위, 완료예정일` |
| Sort by | `사업부` 또는 `완료예정일` |
| Title column heading | `과제 페이지` |

이렇게 하면 모든 개발과제 페이지가 한 표에 자동 집계된다.

## 4. 사업부별 집계 페이지 만들기

예: `VD 개발과제 현황`

1. 새 페이지를 만든다.
2. `Content Properties Report` 매크로를 넣는다.
3. 아래처럼 설정한다.

| 항목 | 값 |
| --- | --- |
| Labels | `agent-task` |
| With ancestor | `VD` 사업부 페이지 |
| Columns to show | `구분, 과제명, 상태, 담당, 완료예정일` |
| Sort by | `구분` |

중간에 하위 분류 페이지가 생겨도 `With ancestor`면 같이 잡힌다.

## 5. 구분별 집계 페이지 만들기

예: `채용 과제 현황`

1. 새 페이지를 만든다.
2. `Content Properties Report` 매크로를 넣는다.
3. 아래처럼 설정한다.

| 항목 | 값 |
| --- | --- |
| Labels | `agent-task` 와 `cat-recruiting` |
| Columns to show | `사업부, 과제명, 상태, 담당, 완료예정일` |
| Sort by | `사업부` |

중요:

- OR가 아니라 AND로 잡으려면 Label 필터를 두 번 추가해서 각각 하나씩 넣는다.
- 예를 들어 `agent-task`와 `cat-recruiting`을 모두 만족시키려면 Label 필터 2개를 사용한다.

## 6. 권장 운영 방식

- 신규 과제는 반드시 사업부 페이지 아래에서 만든다.
- label 3개가 없으면 집계에서 빠질 수 있다.
- `Content Properties` 컬럼명은 템플릿 그대로 유지한다.
- 속성에 `사업부`, `구분`을 넣어도 label은 따로 유지한다.

## 7. 피벗형 표가 꼭 필요할 때

기본 기능만으로 완전 자동 피벗은 불편하다. 먼저 마스터 테이블을 만든 뒤, 정말 필요할 때만 아래 순서로 간다.

1. 수동 표를 먼저 만든다.
2. 행은 `구분`, 열은 `사업부`로 둔다.
3. 각 셀에 조건별 `Content Properties Report`를 넣는다.

다만 매크로 수가 많아져서 운영성이 떨어지므로 1차 버전에서는 권장하지 않는다.

