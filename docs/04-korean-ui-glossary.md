# 한글 UI 용어 매핑

이 문서는 Confluence Data Center 한글 UI에서 실제로 찾게 되는 항목명을 빠르게 보는 용도다.

## 매크로 이름

| 한글 UI | 영문 이름 |
| --- | --- |
| 페이지 속성 | `Page Properties` |
| 페이지 속성 보고서 | `Page Properties Report` |

## 페이지 속성 보고서 설정 항목

| 한글 UI에서 찾을 말 | 영문 이름 |
| --- | --- |
| 레이블 | `Labels` |
| 부모 페이지 | `Parent page` |
| 상위 항목 포함 | `With ancestor` |
| 공간에서 | `In space` |
| 표시할 열 | `Columns to show` |
| 제목 열 이름 | `Title column heading` |
| 표시할 항목 수 | `Number of items to display` |
| 정렬 기준 | `Sort by` |
| 페이지 속성 ID | `Page Properties ID` |

## 이 설계에서 우선 쓰는 것

- 매트릭스 셀: `부모 페이지`
- 중간 하위 폴더가 있을 때만: `상위 항목 포함`
- 기본 검색 범위: `공간에서 = 현재 공간`
- 공통 필터: `레이블 = agent-task`

## 바로 기억할 것

- `정렬 기준`이 `Sort by`다.
- `표시할 열`이 `Columns to show`다.
- `제목 열 이름`이 제목 링크 열 이름이다.
- `부모 페이지`는 직계 자식만 집계한다.
- `상위 항목 포함`은 하위 트리 전체를 집계한다.

## 주의

- 같은 이름의 도메인 페이지가 여러 개발주체 아래에 있어도, 매크로에서 실제 페이지 객체를 선택하면 된다.
- 셀 집계에서는 `상위 항목 포함`보다 `부모 페이지`가 덜 헷갈린다.
