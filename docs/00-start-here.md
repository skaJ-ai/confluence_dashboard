# 여기부터 시작

처음 따라할 때는 이 문서만 순서대로 보면 된다.

## 목표

Confluence에서 아래 구조를 만든다.

- 사업부별 상위 페이지
- 각 사업부 아래 개발과제 페이지
- 각 개발과제 페이지에 `페이지 속성` 매크로
- 첫 페이지에서 `페이지 속성 보고서` 매크로로 자동 수집

## 10분 요약

해야 할 일은 사실 4개뿐이다.

1. 루트 페이지와 사업부 페이지를 만든다.
2. 개발과제 페이지를 만들고 label 3개를 붙인다.
3. 개발과제 페이지 상단에 `페이지 속성` 표를 넣는다.
4. 첫 페이지에서 `페이지 속성 보고서`로 모아본다.

## 정말 최소로 따라하는 순서

### 1. 루트 페이지 만든다

페이지명:

```text
Agent 개발현황
```

### 2. 사업부 페이지 하나만 먼저 만든다

예를 들어 테스트용으로 `VD` 하나만 먼저 만든다.

```text
Agent 개발현황
└─ VD
```

### 3. 개발과제 페이지 하나 만든다

`VD` 페이지 아래에 아래 제목으로 새 페이지를 만든다.

```text
[채용] JD 초안 생성 에이전트
```

### 4. 레이블 3개 붙인다

이 페이지에 아래 3개 label을 붙인다.

```text
agent-task
vd
talent-acquisition
```

## 5. 페이지 속성 넣기

여기서 말하는 것은 Confluence의 속성 매크로다. 한글 UI에서는 보통 `페이지 속성`으로 이해하면 된다.

- 한글 설명명: `페이지 속성`
- 영문 매크로명: `Content Properties` 또는 `Page Properties`

매크로 검색창에서 안 보이면 `페이지 속성`, `content properties`, `page properties` 순으로 찾아본다.

페이지 본문 맨 위에 해당 매크로를 삽입하고, 그 안에 아래 2열 표를 넣는다.

| 항목 | 값 |
| --- | --- |
| 사업부 | VD |
| 구분 | 채용 |
| 과제명 | JD 초안 생성 에이전트 |
| 목적 | 채용 담당자의 JD 작성 시간을 줄이고 초안 품질을 높인다 |
| 담당 | 홍길동 |
| 상태 | 진행중 |
| 우선순위 | High |
| 완료예정일 | 2026-04-30 |
| 관련 링크 | Jira-123 |

### 6. 루트 페이지에 집계 표 넣는다

루트 페이지 `Agent 개발현황` 본문에서 아래 `페이지 속성 보고서` 매크로를 삽입하고 설정한다.

- 한글 설명명: `페이지 속성 보고서`
- 영문 매크로명: `Content Properties Report` 또는 `Page Properties Report`

매크로 검색창에서 안 보이면 `페이지 속성 보고서`, `content properties report`, `page properties report` 순으로 찾아본다.

| 한글 UI 항목명 | 입력값 |
| --- | --- |
| 레이블 | `agent-task` |
| 공간에서 | `현재 공간` |
| 표시할 열 | `사업부, 구분, 과제명, 상태, 담당, 우선순위, 완료예정일` |
| 제목 열 이름 | `과제 페이지` |
| 정렬 기준 | `사업부` |

여기까지 하면 첫 페이지에 방금 만든 개발과제 페이지가 자동으로 표에 잡혀야 한다.

## 안 보이면 체크할 것

아래 4개 중 하나가 빠진 경우가 많다.

- 과제 페이지에 `agent-task` 레이블이 없다.
- `페이지 속성` 매크로 안에 표를 넣지 않았다.
- 속성 컬럼명이 다른 페이지와 다르다.
- 첫 페이지에서 레이블 필터를 잘못 넣었다.
- `공간에서`가 `현재 공간`으로 잡혀 있지 않다.

루트 첫 페이지에 보고서를 넣는 구조라면 `상위 항목 포함`은 굳이 넣지 않는 편이 단순하다.

## 그 다음에 무엇을 보면 되는지

- 페이지 트리 전체 구조를 보려면 [01-space-structure.md](./01-space-structure.md)
- 레이블 전체 목록을 보려면 [02-label-and-property-rules.md](./02-label-and-property-rules.md)
- 구축 절차를 자세히 보려면 [03-confluence-build-guide.md](./03-confluence-build-guide.md)
- 한글 UI 항목명을 보려면 [04-korean-ui-glossary.md](./04-korean-ui-glossary.md)
- 과제 페이지 복붙용 템플릿은 [../templates/agent-task-page-template.md](../templates/agent-task-page-template.md)
- 집계 페이지 복붙용 템플릿은 [../templates/report-page-template.md](../templates/report-page-template.md)
