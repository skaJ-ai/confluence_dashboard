# Confluence Matrix Dashboard Starter

Confluence Data Center 9.2.15 기준으로 `Agent 개발현황` 첫 페이지에 자동 업데이트되는 매트릭스 대시보드를 만드는 시작 저장소다.

최종 설계는 아래와 같다.

- 첫 페이지에 `단일 매트릭스`를 둔다.
- 가로축은 `개발주체`다.
- 세로축은 `도메인`이다.
- 각 셀에는 해당 조건에 맞는 `Agent 과제 페이지 제목`이 자동으로 나온다.
- 구현은 기본 기능인 `페이지 속성`, `페이지 속성 보고서`, `레이블`, `페이지 트리`만 사용한다.
- 매트릭스 셀 집계는 `레이블 기준`으로 한다.

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
│  ├─ Agent 과제 페이지들
├─ DA
├─ MX
├─ NW
├─ 의료기기
├─ SR
├─ CDO
└─ 생기연
```

중요:

- `W/G` 밑에는 도메인별 하위 페이지를 둔다.
- `VD`, `DA` 같은 사업부 밑에는 도메인 페이지를 굳이 만들지 않는다.
- 사업부 과제의 도메인 구분은 `도메인 레이블`로 처리한다.

이렇게 하는 이유:

- 같은 Space 안에서 같은 제목의 페이지를 반복해서 만들 수 없기 때문이다.
- 예를 들어 `W/G > 채용`과 `VD > 채용`을 동시에 둘 수 없다.
- 따라서 매트릭스 집계는 페이지 트리보다 `레이블`에 의존해야 한다.

## 셀 전용 레이블

각 매트릭스 셀을 대표하는 레이블을 하나씩 만든다.

예:

- `W/G x 채용` 셀: `cell-wg-talent-acquisition`
- `VD x 채용` 셀: `cell-vd-talent-acquisition`
- `생기연 x 제도` 셀: `cell-gtr-policy`

각 Agent 과제 페이지에는 아래처럼 레이블을 붙인다.

- 공통: `agent-task`
- 개발주체: `owner-vd`, `owner-wg` ...
- 도메인: `dm-policy`, `dm-talent-acquisition` ...
- 셀 전용: `cell-vd-policy`, `cell-wg-talent-acquisition` ...

그리고 첫 페이지 매트릭스 셀의 `페이지 속성 보고서`는 해당 `cell-...` 레이블 하나만 보고 집계한다.

## 어디서부터 보면 되는지

처음이면 아래 순서로 보면 된다.

1. [docs/00-start-here.md](./docs/00-start-here.md)
2. [docs/01-space-structure.md](./docs/01-space-structure.md)
3. [docs/02-label-and-property-rules.md](./docs/02-label-and-property-rules.md)
4. [docs/03-confluence-build-guide.md](./docs/03-confluence-build-guide.md)
5. [docs/04-korean-ui-glossary.md](./docs/04-korean-ui-glossary.md)
6. [templates/agent-task-page-template.md](./templates/agent-task-page-template.md)
7. [templates/report-page-template.md](./templates/report-page-template.md)
