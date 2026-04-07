# Confluence Dashboard Starter

사내망 Confluence에서 `Agent 개발과제`를 기본 기능만으로 자동 집계하기 위한 시작 저장소다.

이 저장소는 다음 상황을 기준으로 작성했다.

- 사업부별 상위 페이지를 두고
- 그 아래에 개발과제 페이지를 자식으로 만들고
- 각 개발과제 페이지에 `Content Properties`와 `label`을 넣고
- 집계 페이지에서 `Content Properties Report`로 자동 수집한다

Confluence Cloud 기준으로 작성했지만, Data Center에서도 `Page Properties / Page Properties Report` 이름만 다르고 구조는 거의 같다.

## 이 저장소로 할 수 있는 것

- 사업부별 페이지 트리 구조를 바로 따라 만들 수 있다
- label 규칙을 그대로 가져다 쓸 수 있다
- 개발과제 페이지 템플릿을 복붙해서 바로 만들 수 있다
- 마스터 테이블, 사업부별 테이블, 구분별 테이블 설정값을 바로 따라할 수 있다

## 폴더 구성

- `docs/01-space-structure.md`: 페이지 트리 구조안
- `docs/02-label-and-property-rules.md`: label / 속성 규칙
- `docs/03-confluence-build-guide.md`: 실제 구축 순서
- `templates/agent-task-page-template.md`: 개발과제 페이지 템플릿
- `templates/report-page-template.md`: 집계 페이지 템플릿

## 가장 먼저 할 일

1. `docs/01-space-structure.md`를 보고 Space 구조를 만든다.
2. `docs/02-label-and-property-rules.md`의 label 체계를 확정한다.
3. 각 개발과제 페이지를 `templates/agent-task-page-template.md`로 생성한다.
4. 집계 페이지를 만들고 `templates/report-page-template.md`대로 `Content Properties Report`를 설정한다.

## 권장 운영 원칙

- 사업부는 `페이지 트리`로 관리한다.
- 구분은 `label`과 `속성값`으로 같이 관리한다.
- 보고용 표는 `과제 1건 = 1행` 구조를 기본으로 한다.
- 완전한 피벗형 매트릭스 표가 필요해도 1차 구축은 마스터 테이블부터 한다.

## 빠른 예시

페이지 트리 예시:

```text
Agent 개발과제
├─ AX&CI Lab
│  ├─ [인력운영] 인터뷰 코파일럿
│  └─ [채용] JD 초안 생성 에이전트
├─ VD
│  ├─ [보상/근태] 근태 문의 응답 에이전트
│  └─ [조직문화] 사내 제안 분류 에이전트
└─ MX
   └─ [총무] 공용 자산 문의 에이전트
```

라벨 예시:

- `agent-task`
- `bu-vd`
- `cat-recruiting`

속성 예시:

- 사업부: `VD`
- 구분: `채용`
- 상태: `진행중`
- 담당: `홍길동`

## 주의

- `With parent`는 직계 자식만 잡는다.
- `With ancestor`는 해당 상위 페이지 아래 전체 하위 트리를 잡는다.
- 사업부 페이지 아래 중간 분류 페이지를 둘 가능성이 있으면 `With ancestor`를 우선 사용한다.
- 기본 리포트만으로 `가로=사업부 / 세로=구분` 완전 피벗 표를 한 번에 만드는 건 불편하다.

## 추천 시작 구조

- 루트 페이지: `Agent 개발과제`
- 사업부 페이지: `AX&CI Lab`, `VD`, `DA`, `MX`, `NW`, `의료기기`, `SR`, `CDO`, `생기연`
- 공통 구분:
  - 인력운영
  - 제도
  - 임원조직
  - 노사
  - 조직문화
  - 채용
  - 총무
  - 집단지성
  - 보상/근태

