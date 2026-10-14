# Week 07 팀 활동지 / Team Activity

| 팀명 / Team | 작성일 / Date | 참여자 / Members |
|---|---|---|
| 오류해결팀 | 2026-10-14 | 박현, 이제빈, 최윤성, 한승엽  |

## 1. 아키텍처 다이어그램 / Architecture Diagram

손그림 사진을 올리고 링크하십시오 / Upload a photo and link it.
<img width="3600" height="2568" alt="시스템 아키텍처" src="https://github.com/user-attachments/assets/4513fbcc-c2a6-4980-9cc2-76e1ef2ff1d4" />


| 계층 / Layer | 모듈·파일 / Modules | 의존하지 않는 것 / Does not depend on |
|---|---|---|
| 표현 / Presentation | | |
| 로직 / Logic | | |
| 데이터 / Data | | |

## 2. 이슈 / Issues

> 이슈 = **앞으로 할 일** / An issue is work to be done.
> 개발할 때 커밋에 이슈 번호를 붙이고(`#3 알레르기 필터 추가`), 완료 조건을 만족하면 이슈를 닫습니다.
> Add the issue number to commits, and close the issue when its criteria are met.

| # | 제목 / Title | 라벨 / Label | 담당 / Assignee | 완료 조건 / Acceptance Criteria |
|---|---|---|---|---|
| # | 제목 / Title | 라벨 / Label | 담당 / Assignee | 완료 조건 / Acceptance Criteria |
|---|---|---|---|---|
| [#1](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/1) | manifest.json (권한 · 새 탭 · 서비스 워커 등록) | P1 | 박현 | 설치할 때 topSites 권한 경고가 없고, 새 탭이 확장 프로그램 화면으로 바뀌며, 서비스 워커가 오류 없이 등록된다 |
| [#2](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/2) | bookmarks.js (크롬 북마크 읽기 · 바꾸기 통로) | P1 | 박현 | 읽은 북마크 개수가 크롬 북마크 관리자와 같고, 같은 이름 폴더를 두 번 만들지 않으며, 폴더를 지워도 안의 북마크는 남는다 |
| [#3](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/3) | store.js (저장 항목 9개 통로) | P1 | 박현 | 저장 항목 9개가 기본값과 함께 읽히고, 고정은 8개를 넘지 않으며, 한 키를 새 탭과 서비스 워커가 함께 쓰지 않는다 |
| [#4](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/4) | organize.js (정리 적용 · 되돌리기) | P1 | 박현 | 북마크바 맨 뒤에 폴더가 생기고 정리 대상이 옮겨지며, 되돌리면 원래 폴더의 원래 순서로 돌아가고 그 정리가 만든 빈 폴더만 지워진다 |
| [#5](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/5) | view/history.js (정리 결과 안내 · 정리 기록) | P1 | 박현 | 정리 결과 안내와 [되돌리기]가 12초 동안 보이고, 누르면 크롬 북마크가 원래대로 돌아간다 |
| [#6](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/6) | background.js (서비스 워커 · 북마크 변경 기록) | P1 | 한승엽 | 새 탭이 닫혀 있어도 새 북마크가 기록되고, 사용자가 직접 옮긴 북마크만 manualMoves에 기록되며, 가져오기 중 북마크는 새 북마크로 기록하지 않는다 |
| [#7](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/7) | classify.js (카테고리 분류 규칙) | P1 | 한승엽 | 북마크 하나에 카테고리 하나와 근거가 붙고, 정답지 100개 기준 적용률 89% · 정확도 100%다 |
| [#8](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/8) | forgotten.js (잊고 있던 북마크 고르기) | P1 | 한승엽 | 30일 이상 안 연 북마크만 오래 안 연 순으로 후보가 되고, 고정 · "이제 안 봐도 됨" · javascript: 주소는 빠진다 |
| [#9](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/9) | view/forgottenFolder.js (잊고 있던 북마크 폴더 · 팝업) | P1 | 한승엽 | 후보가 있으면 폴더 줄 맨 앞에 개수 배지와 함께 보이고 팝업에 8개까지 보이며, 크롬 북마크에는 폴더가 생기지 않는다 |
| [#10](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/10) | categories.json (사이트 분류표 데이터) | P1 | 한승엽 | 같은 주소가 두 번 나오지 않고, category-definitions.md 10번과 내용이 같으며, 정답지로 잰 숫자가 문서와 같다 |
| [#11](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/11) | plan.js (정리 대상 · 폴더 계획 · 고정 후보) | P1 | 이제빈 | 사용자 폴더 · 요즘 쓰는 북마크 · 직접 옮긴 북마크가 빠지고, 폴더 수가 상한(3~6개)을 넘지 않으며 모든 폴더에 북마크가 3개 이상이다 |
| [#12](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/12) | topic.js (세부 폴더 제안) | P3 | 이제빈 | 북마크 3개 이상, 사이트 2곳 이상인 주제 단어만 세부 폴더로 제안되고, 조건에 못 미치면 빈 배열이 돌아온다 |
| [#13](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/13) | view/folders.js (폴더 줄 · 폴더 팝업 · 폴더 관리) | P1 | 이제빈 | 크롬 북마크 폴더가 미리보기 · 이름 · 개수와 함께 보이고, 폴더를 누르면 팝업이 열리며 폴더 안의 폴더로 들어가고 돌아올 수 있다 |
| [#14](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/14) | newtab.html · newtab.css (화면 뼈대 · 모양) | P1 | 최윤성 | 화면 뼈대의 순서가 시안과 같고, 480px 너비에서 가로 스크롤이 생기지 않으며, HTML 안에 직접 쓴 스크립트가 없다 |
| [#15](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/15) | render.js (화면 시작점 · 다시 그리기) | P1 | 최윤성 | 화면의 북마크 개수가 크롬 북마크 관리자와 같고, 북마크가 바뀌면 새로고침 없이 반영되며, Console에 오류가 없다 |
| [#16](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/16) | ui.js (공통 화면 조각) | P1 | 최윤성 | 파비콘이 있으면 색 타일 위에, 없으면 제목 첫 글자가 보이고, 안내 문구는 한 번에 하나만 보이며 아이콘 12종이 모두 그려진다 |
| [#17](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/17) | view/cards.js (첫 정리 카드 · 고정 제안 카드) | P1 | 최윤성 | 설치 후 첫 새 탭에 첫 정리 카드가 보이고, [정리하기]를 누르기 전에는 크롬 북마크가 바뀌지 않는다 |
| [#18](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/18) | search.js (웹 검색 · 북마크 검색) | P1 | 최윤성 | 주소면 그 주소로 가고 아니면 기본 검색엔진으로 검색하며, 빈 입력에서는 아무 일도 일어나지 않는다 |
| [#19](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/19) | dnd.js (끌어서 옮기기 · 순서 바꾸기) | P3 | 최윤성 | 끌어 폴더에 놓거나 순서를 바꾸면 크롬 북마크에 반영되고, 놓을 수 없는 곳에 놓으면 원래 자리로 돌아간다 |
| [#20](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/20) | 준비: 샘플 북마크 세트 (10개 미만 · 20개 · 30개) | P1 | 한승엽 · C | 세 세트가 tests/에 있고, 새 프로필에 가져오면 위치별 북마크 개수가 문서와 같다 |
| [#21](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/21) | 준비: 저장소 설정 마무리 | P1 | 박현 | main에 직접 올리면 거절되고, 승인 없이는 합칠 수 없으며, 팀원 네 명이 모두 첫 연습 PR을 합쳤다 |
| [#22](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/22) | 확인 목록 P1: 요구사항 62줄 | P1 | 박현 · B · C · D | 62줄이 모두 체크되고, 새 탭 표시 → [정리하기] → [되돌리기] → 잊고 있던 북마크 열기가 한 번에 끝까지 되며, demo-w11 태그를 붙였다 |
| [#23](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/23) | 확인 목록 P2: 요구사항 49줄 | P2 | 박현 · B · C · D | 49줄이 모두 체크되고, 최종 데모에서 P2 기능을 끊기지 않고 보여 주며, demo-w15 태그를 붙였다 |
| [#24](https://github.com/aix-team-5/aix_BaroLink_bookmark/issues/24) | 확인 목록 P3: 요구사항 6줄 | P3 | 이제빈 · D | 6줄이 모두 체크되고, P1 · P2 확인 목록을 다시 눌러 봐도 깨진 곳이 없다 |


## 3. 마일스톤 / Milestones

| 마일스톤 / Milestone | 마감 / Due | 포함 이슈 / Issues |
|---|---|---|
| MVP 완료 | 11주차 | |
| 실행 패키지 | 13주차 | |

> AI를 사용했다면 `PROMPTS.md`에 기록 / Log any AI use in `PROMPTS.md`
