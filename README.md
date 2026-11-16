

# CHICKEN FIGHT

> **한 발로 버티고, 상대를 밀어내라!**

전통 놀이 닭싸움을 모티브로 한 **4인 온라인 PvP 파티 브롤러**입니다.<br>
이동과 충전 점프로 상대의 균형을 무너뜨리고, 4라운드 누적 점수로 최종 승자를 결정합니다.

## 시연 영상

<!-- 대표 이미지와 시연 영상 링크를 추가하세요. -->
<a href="https://drive.google.com/file/d/1tKShvgaapBr7XYgLBqbtT7CRoU_LJiuE/view?usp=sharing">
  <img width="640" alt="Chicken Fight 시연 영상 보기" src="https://github.com/user-attachments/assets/c4e6c2dc-64d5-42bb-9f2e-f74150e4c12e" />
</a>

<!--
| 스파링 광장 | 도심 옥상 |
| :---: | :---: |
| 이미지 추가 예정 | 이미지 추가 예정 |

| 댐 정비장 | 놀이동산 |
| :---: | :---: |
| 이미지 추가 예정 | 이미지 추가 예정 |
-->

## 목차

- [게임 개요](#게임-개요)
- [팀원 소개](#팀원-소개)
- [아키텍처 설계](#아키텍처-설계)
- [프로젝트 폴더 구조](#프로젝트-폴더-구조)
- [주요 클래스 구조](#주요-클래스-구조)
- [브랜치 전략](#브랜치-전략)
- [애셋 라이선스 및 저작권](#애셋-라이선스-및-저작권)
- [프로젝트 자료](#프로젝트-자료)

## 게임 개요

### 소개

한 발로 균형을 유지하며 상대와 부딪히는 닭싸움을 온라인 경쟁 게임으로 구현했습니다.<br>
간단한 조작을 기반으로 충돌 방향, 점프 타이밍, 지형 활용에 따라 승부가 달라지는 플레이를 목표로 합니다.

| 항목 | 내용 |
| --- | --- |
| 장르 | 3D · Party Brawler · Online PvP |
| 플랫폼 | Windows PC |
| 플레이 인원 | 4인 |
| 경기 방식 | 개인전 · 4라운드 · 누적 점수 |
| 개발 기간 | 2026.09 ~ 2026.11 |

### 주요 특징

- **균형과 충돌 중심의 전투:** 이동·충전 점프로 상대를 밀고, 반대 방향 입력으로 균형 회복
- **4라운드 누적 경쟁:** 생존 순위에 따라 점수를 획득하고 최종 순위 결정
- **서로 다른 전투 공간:** 평면 광장, 수직 옥상, 장애물 전투장, 시소 무대
- **인터랙티브 로비:** 매칭 대기 중 캐릭터 조작과 점프 연습
- **온라인 플레이:** Epic 로그인, 닉네임 설정, 4인 매칭 및 EOS 세션 연결

### 핵심 시스템

| 시스템 | 주요 기능 |
| --- | --- |
| 캐릭터 조작 | WASD 이동·기울기 조절, 자동 제자리 점프, 충전 점프 |
| 충돌·균형 | 충돌에 따른 밀림과 기울기 변화, 균형 회복, 넘어짐·탈락 |
| 경기 진행 | 맵 4개를 무작위 순서로 중복 없이 진행, 생존 순위 판정, 점수 집계, 최종 결과 |
| 맵·장애물 | 이동 발판, 회전 장애물, 통나무, 물줄기, 시소 전투판 |
| 플레이 피드백 | 플레이어 식별, 점프 충전 게이지, 균형 위험 효과·방향 화살표 |

라운드 점수는 **1위 5점 / 2위 3점 / 3위 1점 / 4위 0점**입니다.<br>
결과표는 누적 점수순으로 표시하며, 현재 구현에서는 동점 시 공동 순위로 처리합니다.

### 개발 환경

| 구분 | 기술·도구 |
| --- | --- |
| 게임 엔진 | Unreal Engine 5.8 |
| 클라이언트 | C++ · Blueprint |
| UI | UMG · Widget Blueprint |
| 온라인 서비스 | Epic Online Services |
| 백엔드 | AWS 기반 인증·프로필·매칭 API |
| 버전 관리 | Git · GitHub |
| 기획·협업 | Notion · Figma · FigJam · GitHub Projects |

### 프로젝트 실행

- 프로젝트 파일: `ChickenFight.uproject`
- Editor 빌드 타깃: `DKUEndGameEditor`
- Runtime 모듈: `DKUEndGame`
- 시작 맵: `/Game/Frontend/Lvl_CF_MainMenu`

온라인 기능 실행에는 별도의 EOS 로컬 설정이 필요합니다.

- [로그인·로컬 설정 안내](Docs/Network/LoginEntry.md)
- [EOS 연결·테스트 안내](Docs/Network/EOSRound1Session.md)

## 팀원 소개

<!-- 실제 담당과 GitHub 링크를 작성하세요. 행은 팀 구성에 맞게 추가·삭제하세요. -->

| 팀원 | 담당 | 주요 기여 | GitHub |
| --- | --- | --- | --- |
| 안지성 | PM · 게임 기획 · 레벨 디자인 · UX/UI | 핵심 조작·전투·점수 규칙 설계, 맵 4종과 연습 로비 제작,<br>UX/UI 설계·구현, 개발 우선순위·일정 및 협업 관리 | [<img src="https://github.com/j1sung.png?size=120" width="100"/>](https://github.com/j1sung) |
| 김호영 | 클라이언트 · 서버 | 캐릭터 조작·전투 시스템, Unreal 리슨 서버 로직 및 멀티플레이 동기화 | [<img src="https://github.com/sunsi-game.png?size=120" width="100"/>](https://github.com/sunsi-game) |
| 정규민 | 클라이언트 · 서버 | Unreal 리슨 서버 로직 및 멀티플레이 동기화 | [<img src="https://github.com/KyuminChung.png?size=120" width="100"/>](https://github.com/KyuminChung) |
| 김은재 | 백엔드 · 네트워크 | 외부 인증·프로필·매칭 API, AWS 인프라 구축·배포 및 운영 | [<img src="https://github.com/Developer-EJ.png?size=120" width="100"/>](https://github.com/Developer-EJ) |

## 아키텍처 설계

### 온라인 경기 흐름

```mermaid
flowchart LR
    Menu[메인 메뉴] --> Login[Epic 로그인·<br/>프로필]
    Login --> Lobby[연습 로비]
    Lobby --> Queue[4인 매칭]
    Queue --> Session[EOS 세션 연결]
    Session --> Rounds[4라운드 경기]
    Rounds --> Result[최종 결과]
    Result --> Lobby
```

### 역할 분리

| 계층 | 역할 |
| --- | --- |
| UI | 사용자 입력, 접속·매칭 상태, 경기 정보 표시 |
| GameInstance Subsystem | 인증·매칭·세션 처리, 맵 간 경기 정보 유지 |
| GameMode | 서버의 경기 시작, 탈락 판정, 라운드 진행·점수 집계 |
| GameState·PlayerState | 경기 상태와 플레이어 정보를 클라이언트에 복제 |
| Character·Component | 캐릭터 조작, 충돌·균형 처리, 플레이어 표시 |
| Blueprint·레벨 | 에셋 연결, 기믹 구성, 배치·수치 조정 |

클라이언트의 입력과 UI 요청을 서버의 경기 상태·판정과 구분합니다.<br>
맵 전환 시 유지해야 하는 경기 정보는 GameInstance 수명의 Subsystem에서 관리합니다.

상세 설계는 [게임플레이](Docs/Gameplay/Overview.md), [네트워크](Docs/Network/Overview.md), [UI](Docs/UI/Overview.md) 문서를 참고하세요.

## 프로젝트 폴더 구조

주요 폴더를 발췌한 구조입니다.

```text
📂 ChickenFight
├── 📄 ChickenFight.uproject
├── 📂 Config                 # 프로젝트·입력·온라인 설정
├── 📂 Content
│   ├── 📂 Frontend           # 메인메뉴·기존 LAN 아레나 맵
│   ├── 📂 Map                # 연습 로비·라운드 맵
│   ├── 📂 Characters         # 캐릭터·애니메이션
│   ├── 📂 Input              # 입력 액션·매핑
│   ├── 📂 UI                 # 위젯·폰트·UI 리소스
│   └── 📂 LD_Gym             # 레벨 에셋·장애물
├── 📂 Source
│   └── 📂 DKUEndGame
│       ├── 📂 Character      # 캐릭터·균형·표시
│       ├── 📂 Gameplay       # 게임플레이 기믹
│       ├── 📂 Network        # 인증·매칭·세션·경기 진행
│       ├── 📂 UI             # UI 동작
│       ├── 📂 Testing        # 테스트용 액터·게임모드
│       └── 📂 Tests          # 자동화 테스트
├── 📂 Backend-Infra          # 백엔드·인프라
├── 📂 Tools                  # 에디터·네트워크 개발 도구
└── 📂 Docs                   # 설계·설정·개발 문서
```

## 주요 클래스 구조

| 영역 | 주요 클래스 | 책임 |
| --- | --- | --- |
| 캐릭터 | `AChickenCharacter` | 이동·점프·충돌·균형·넘어짐 |
| 플레이어 표시 | `UCFPlayerPresentationComponent` | 이름표·점프 게이지·위험 HUD |
| 메뉴 상태 | `UCFFrontendSubsystem` | 타이틀·로그인·닉네임 UI 상태 관리 |
| 인증·프로필 | `UCFEntrySubsystem` | 로그인·프로필 요청·로비 진입 |
| 매칭 | `UCFMatchmakingSubsystem` | 매칭 티켓 요청·조회·취소 |
| 세션 연결 | `UCFMatchSessionSubsystem` | EOS 세션 생성·검색·참가 |
| 경기 규칙 | `ACFRoundGameMode` · `ACFWaitingGameMode` | 경기 시작·탈락·라운드·점수 관리 |
| 경기 상태 | `ACFWaitingGameState` | 경기 단계·생존자·점수 복제 |
| 맵 간 정보 | `UCFMatchRuntimeSubsystem` | 맵 순서·플레이어 식별·점수 유지 |

C++은 주요 로직과 네트워크 상태를 처리하며,
Blueprint는 레벨·기믹 구성과 에셋 연결, 조정 가능한 설정에 사용합니다.<br>
UI는 C++ 위젯과 Widget Blueprint를 함께 사용합니다.

## 브랜치 전략

기능 개발과 테스트 작업을 별도 브랜치에서 진행하고, 검증한 변경사항을 `dev`에 통합합니다.

```mermaid
flowchart LR
    Work["<b>작업 브랜치</b><br/>기능 개발 · 수정"]
    Test["<b>테스트 브랜치</b><br/>서버 연결<br/>멀티플레이 검증"]
    Join(( ))
    Dev["<b>dev</b><br/>통합 · 검증"]
    Main["<b>main</b><br/>버전 관리"]

    Work --- Join
    Test --- Join
    Join -->|PR| Dev
    Dev -->|버전 통합 PR| Main

    style Work fill:#EAF2FF,stroke:#6195D6,color:#1F2937
    style Test fill:#FFF3DF,stroke:#D9A441,color:#1F2937
    style Join fill:#64748B,stroke:#64748B
    style Dev fill:#E7F5EC,stroke:#4F9B6C,color:#1F2937,stroke-width:2px
    style Main fill:#FFE8E2,stroke:#D97962,color:#1F2937,stroke-width:2px
```

| 브랜치 | 용도 |
| --- | --- |
| 작업 브랜치 | 기능 개발·수정 |
| 테스트 브랜치 | 서버 연결·멀티플레이 등 테스트와 관련 수정 |
| `dev` | 개발·테스트 결과 통합 및 검증 |
| `main` | 버전 단위 통합 |

- 기능 개발은 작업 브랜치에서 진행하고 PR을 통해 `dev`에 반영합니다.
- 서버 연결·멀티플레이 검증 등은 별도 테스트 브랜치에서 진행하고, 필요한 수정사항을 PR로 `dev`에 반영합니다.
- 버전 통합 시 `dev`에서 `main`으로 PR을 생성합니다.
- PR에는 변경 내용과 검증 결과를 작성합니다.
- 구현·설정 변경에 필요한 문서는 코드와 함께 관리합니다.

## 애셋 라이선스 및 저작권

외부 리소스는 각 제작자가 지정한 라이선스를 따릅니다.

<!-- 사용한 외부 리소스의 출처와 라이선스를 확인해 작성하세요. -->

| 구분 | 리소스 | 출처 | 라이선스·비고 |
| --- | --- | --- | --- |
| 폰트 | Inter | [Inter](https://rsms.me/inter/) | [라이선스 원문](Content/UI/MainMenu/Fonts/Inter-LICENSE.txt) |
| 3D 애셋 | 배경·오브젝트 | GPT·Codex를 활용하여 Unreal Engine에서 자체 제작 | 프로젝트 제작 리소스 |
| 애니메이션 | 캐릭터 동작 | GPT·Codex를 활용하여 Unreal Engine에서 자체 제작 | 프로젝트 제작 리소스 |
| 음원·효과음 | 배경음·동작 효과음 | GPT·Codex를 활용한 자체 제작 | 프로젝트 제작 리소스 |

<!-- 프로젝트 코드의 라이선스는 팀 합의 후 별도로 명시하세요. -->

## 프로젝트 자료

- 📄 [프로젝트 결과 보고서](https://docs.google.com/document/d/1sYPFTVFm0Dg2Fjk_jDDc7KS09rd3cR_Wt3WgujIIvI4/edit?tab=t.0)
- 📚 [개발 문서 목차](Docs/index.md)

### 프로젝트 포스터
<!-- 완성된 포스터 이미지를 여기에 추가 -->
<img width="300" alt="image" src="https://github.com/user-attachments/assets/9cac725e-2a42-4566-8be7-eff76ba9dbef" />
