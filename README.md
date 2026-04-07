# Confluence Matrix Dashboard Starter

Confluence Data Center 9.2.15 기준으로 `Agent 개발현황` 첫 페이지에 자동 업데이트되는 매트릭스 대시보드를 만드는 시작 저장소다.

최종 설계는 아래와 같다.

- 첫 페이지에 `단일 매트릭스`를 둔다.
- 가로축은 `개발주체`다.
- 세로축은 `도메인`이다.
- 각 셀에는 해당 조건에 맞는 `Agent 과제 페이지 제목`이 자동으로 나온다.
- 구현은 기본 기능인 `페이지 속성`, `페이지 속성 보고서`, `레이블`, `페이지 트리`만 사용한다.

HTML 매크로는 Data Center에서 가능하지만 1차 구축에는 필요하지 않다.

## 확정된 축

가로축 `개발주체`

- `W/G`
- `VD`
- `DA`
- `MX`
- `NW`
- `의료기기`
- `SR`
- `CDO`
- `생기연`

세로축 `도메인`

- `인력운영`
- `제도`
- `임원조직`
- `노사`
- `조직문화`
- `채용`
- `총무`
- `집단지성`
- `보상/근태`

## 핵심 구조

페이지 트리는 아래처럼 간다.

```text
Agent 개발현황
├─ W/G
│  ├─ 인력운영
│  ├─ 제도
│  ├─ 임원조직
│  ├─ 노사
│  ├─ 조직문화
│  ├─ 채용
│  ├─ 총무
│  ├─ 집단지성
│  └─ 보상/근태
├─ VD
│  ├─ 인력운영
│  ├─ 제도
│  └─ ...
├─ DA
├─ MX
├─ NW
├─ 의료기기
├─ SR
├─ CDO
└─ 생기연
```

실제 Agent 과제 페이지는 각 `개발주체 > 도메인` 페이지 아래에 직접 만든다.

예:

```text
VD
└─ 채용
   ├─ JD 초안 생성 에이전트
   └─ 채용 Q&A 에이전트
```

```text
W/G
└─ 제도
   ├─ 규정 비교 에이전트
   └─ 제도 문서 요약 에이전트
```

## 이 저장소에서 정리한 것

- 페이지 트리 구조
- 레이블 규칙
- Agent 과제 페이지 템플릿
- 첫 페이지 매트릭스 구성 방법
- 한글 UI 항목명 기준 설정값

## 어디서부터 보면 되는지

처음이면 아래 순서로 보면 된다.

1. [docs/00-start-here.md](./docs/00-start-here.md)
2. [docs/01-space-structure.md](./docs/01-space-structure.md)
3. [docs/02-label-and-property-rules.md](./docs/02-label-and-property-rules.md)
4. [docs/03-confluence-build-guide.md](./docs/03-confluence-build-guide.md)
5. [docs/04-korean-ui-glossary.md](./docs/04-korean-ui-glossary.md)
6. [templates/agent-task-page-template.md](./templates/agent-task-page-template.md)
7. [templates/report-page-template.md](./templates/report-page-template.md)

## 운영 원칙

- Agent 페이지 제목 자체를 `과제명`으로 쓴다.
- 한 Agent는 `개발주체`를 반드시 1개 가진다.
- 한 Agent는 `도메인`을 반드시 1개 가진다.
- 트리는 `개발주체 > 도메인 > 과제` 순서로 고정한다.
- 매트릭스 셀 집계는 `레이블 + 부모 페이지` 조합을 우선 사용한다.

`부모 페이지`를 권장하는 이유:

- 트리 구조가 이미 `개발주체 + 도메인`을 표현한다.
- 여러 레이블을 조합하는 것보다 설정이 덜 헷갈린다.
- 같은 Space 안에서 오집계가 적다.

레이블은 여전히 필요하다.

- 전역 검색
- 보조 집계
- 나중에 다른 뷰 추가

## 레이블 한 줄 요약

- 공통: `agent-task`
- 개발주체: `owner-wg`, `owner-vd`, `owner-da`, `owner-gtr` ...
- 도메인: `dm-workforce`, `dm-policy`, `dm-talent-acquisition` ...

## 빠른 예시

`W/G > 채용 > JD 초안 생성 에이전트`

- 레이블
  - `agent-task`
  - `owner-wg`
  - `dm-talent-acquisition`

`생기연 > 제도 > 규정 비교 에이전트`

- 레이블
  - `agent-task`
  - `owner-gtr`
  - `dm-policy`

## 참고

- 페이지 속성 보고서는 제목 열을 기본으로 보여준다.
- 따라서 페이지 제목을 과제명으로 짓는 것이 중요하다.
- 셀 안에서는 `과제명`과 함께 최소한의 보조 열만 두는 편이 좋다.
