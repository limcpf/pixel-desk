# Project Structure

`pixel-desk`의 폴더 구조와 각 폴더의 역할을 정의하는 기준 파일이다.

에이전트는 작업 전에 이 문서를 확인하고, 파일을 만들거나 이동할 때 아래 의미에 맞는 위치를 선택한다.

```text
pixel-desk/
├── AGENTS.md
├── PROJECT-STRUCTURE.md
├── docs/
├── agent/
├── source/
│   ├── frontend/
│   └── backend/
└── infra/
```

## 항목의 의미

- `AGENTS.md`: 에이전트가 프로젝트에서 따라야 하는 최소 작업 규칙
- `PROJECT-STRUCTURE.md`: 폴더 구조와 각 위치의 역할을 정의하는 기준 문서
- `docs/`: 프로젝트가 무엇을 만들고 어떻게 동작해야 하는지 설명하는 설계 문서
- `agent/`: 에이전트와 논의한 내용, 의사결정, 작업 메모를 기록하는 공간
- `source/`: 실제 애플리케이션 소스 코드의 최상위 폴더
- `infra/`: 애플리케이션 실행과 개발에 필요한 외부 환경 설정

## `source/` 하위 폴더

- `source/frontend/`: 사용자 화면과 상호작용을 담당하는 프론트엔드 코드
- `source/backend/`: API, 인증, 비즈니스 로직, 데이터 처리를 담당하는 백엔드 코드

## `docs/`에 둘 문서

- `docs/01-requirements.md`: 프로젝트 목표와 기능 요구사항
- `docs/02-design-spec.md`: 도트 스타일, 화면 구성, 상호작용 규칙
- `docs/03-architecture.md`: 기술 스택과 시스템 구조
- `docs/04-data-and-api.md`: 데이터 모델과 프론트엔드·백엔드 통신 규격
- `docs/05-roadmap.md`: 개발 순서와 완료 조건

## `agent/`에 둘 기록

- `agent/decisions.md`: 확정한 결정과 결정 이유
- `agent/tasks.md`: 진행 중인 작업과 다음 작업
- `agent/notes.md`: 논의 중인 내용과 임시 메모

## `infra/`에 둘 설정

- Docker Compose, 데이터베이스, 웹 서버, 배포 등 애플리케이션 외부 환경에 필요한 설정
- 프론트엔드와 백엔드의 기능 코드는 이 폴더에 두지 않는다.

## 관리 규칙

- 폴더를 추가하거나 삭제하거나 이동하면 이 파일을 함께 수정한다.
- 파일의 주요 위치나 폴더의 역할이 바뀌면 이 파일을 함께 수정한다.
- 실제 폴더 구조와 이 문서의 내용이 항상 일치하도록 유지한다.
