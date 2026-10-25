# Project Structure

`pixel-desk`의 폴더 구조와 각 폴더의 역할을 정의하는 기준 파일이다.

에이전트는 작업 전에 이 문서를 확인하고, 파일을 만들거나 이동할 때 아래 의미에 맞는 위치를 선택한다.

```text
pixel-desk/
├── AGENTS.md
├── PROJECT-STRUCTURE.md
├── .gitignore
├── .devcontainer/
│   ├── devcontainer.json
│   └── Dockerfile-java
├── .vscode/
│   └── settings.json
├── docs/
│   ├── 요구사항정의.ods
│   └── fixed/
│       └── 01.환경.md
├── agent/
│   └── tasks.md
├── source/
│   ├── frontend/                         # 현재 비어 있음
│   └── backend/
│       ├── build.gradle
│       ├── settings.gradle
│       ├── gradlew
│       ├── gradlew.bat
│       ├── gradle/
│       │   └── wrapper/
│       │       ├── gradle-wrapper.jar
│       │       └── gradle-wrapper.properties
│       └── src/
│           ├── main/
│           │   ├── java/dev/limc/desk/pixel_desk/
│           │   │   └── PixelDeskApplication.java
│           │   └── resources/
│           │       └── application.yaml
│           └── test/
│               └── java/dev/limc/desk/pixel_desk/
│                   └── PixelDeskApplicationTests.java
└── infra/                               # 현재 비어 있음
```

위 트리는 현재 프로젝트 파일을 기준으로 한다. `.git/`과 실행 환경에서 제공하는 빈 디렉터리인 `.agents/`, `.codex/`, `.aws/`는 생략한다. 빌드·실행 과정에서 생성되는 항목은 아래에 별도로 설명한다.

## 항목의 의미

- `AGENTS.md`: 에이전트가 프로젝트에서 따라야 하는 최소 작업 규칙
- `PROJECT-STRUCTURE.md`: 폴더 구조와 각 위치의 역할을 정의하는 기준 문서
- `.gitignore`: 빌드 결과물, Gradle 관련 폴더, 로그 등 Git 추적 제외 규칙
- `.devcontainer/`: Java 개발 컨테이너의 이미지, 포트, VS Code 확장 및 설정
- `.vscode/`: 프로젝트에 적용하는 VS Code 설정
- `docs/`: 프로젝트가 무엇을 만들고 어떻게 동작해야 하는지 설명하는 설계 문서
- `agent/`: 에이전트와 논의한 내용, 의사결정, 작업 메모를 기록하는 공간
- `source/`: 실제 애플리케이션 소스 코드의 최상위 폴더
- `infra/`: 애플리케이션 실행과 개발에 필요한 외부 환경 설정

## `source/` 하위 폴더

- `source/frontend/`: 사용자 화면과 상호작용을 담당하는 프론트엔드 코드
- `source/backend/`: API, 인증, 비즈니스 로직, 데이터 처리를 담당하는 백엔드 코드. 현재 Java 21, Spring Boot, Gradle 기반 기본 프로젝트가 있다.

## `source/backend/` 구성

- `build.gradle`: Java·Spring Boot 플러그인, Java 버전, 의존성 및 테스트 설정
- `settings.gradle`: Gradle 프로젝트 이름 설정
- `gradlew`, `gradlew.bat`: Unix 계열 및 Windows용 Gradle Wrapper 실행 스크립트
- `gradle/wrapper/`: Gradle Wrapper 실행 파일과 Gradle 배포 버전 설정
- `src/main/java/dev/limc/desk/pixel_desk/`: 백엔드 Java 코드. 현재 `PixelDeskApplication.java`가 애플리케이션 시작점이다.
- `src/main/resources/application.yaml`: 애플리케이션 이름, 가상 스레드 활성화, 로그 파일 경로 설정
- `src/test/java/dev/limc/desk/pixel_desk/`: 백엔드 테스트 코드. 현재 `PixelDeskApplicationTests.java`가 Spring 애플리케이션 컨텍스트 로딩을 확인한다.

### 로컬 생성 항목

다음 폴더는 현재 로컬에 존재하며 `.gitignore`로 Git 추적에서 제외된다.

- `source/backend/.gradle/`: Gradle의 프로젝트별 캐시와 작업 상태
- `source/backend/build/`: 컴파일 결과, 생성 코드, 리소스, 테스트 결과 및 보고서
- `source/backend/logs/`: 애플리케이션 실행 로그. 현재 설정의 로그 파일은 `application.log`이다.

현재 `.gitignore`의 `**/gradle` 규칙은 `source/backend/gradle/wrapper/`도 추적 대상에서 제외한다. 위 트리는 Git 추적 여부와 관계없이 실제 존재하는 Wrapper 파일을 포함한다.

## `docs/`의 문서

- `docs/요구사항정의.ods`: 프로젝트 요구사항을 정리하는 스프레드시트
- `docs/fixed/`: 확정한 설계와 결정 문서를 보관하는 폴더
- `docs/fixed/01.환경.md`: 백엔드 기술 스택, 환경 구성 및 선택 이유를 기록한 문서

## `agent/`의 기록

- `agent/tasks.md`: 진행 중인 작업과 다음 작업

## 개발 도구 설정

- `.devcontainer/devcontainer.json`: 개발 컨테이너 빌드 파일 지정, 8080 포트 전달, Java·Spring Boot 확장 및 편집기 설정
- `.devcontainer/Dockerfile-java`: Java 21 기반 개발 컨테이너 이미지 정의
- `.vscode/settings.json`: Java 컴파일 시 null 분석 설정

## `infra/`에 둘 설정

- Docker Compose, 데이터베이스, 웹 서버, 배포 등 애플리케이션 외부 환경에 필요한 설정
- 프론트엔드와 백엔드의 기능 코드는 이 폴더에 두지 않는다.

## 관리 규칙

- 폴더를 추가하거나 삭제하거나 이동하면 이 파일을 함께 수정한다.
- 파일의 주요 위치나 폴더의 역할이 바뀌면 이 파일을 함께 수정한다.
- 실제 폴더 구조와 이 문서의 내용이 항상 일치하도록 유지한다.
