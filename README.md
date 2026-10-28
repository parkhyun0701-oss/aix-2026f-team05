# 프로젝트명 / Project Name

> 한 줄 소개 — 누구의 어떤 문제를 해결하는가
> One line — whose problem does this solve?

**배포 URL / Live URL:** (13주차에 작성 / add in Week 13)

## 1. 문제 정의 / Problem Definition
- 사용자 / Users: PC 크롬에서 북마크를 쓰지만 폴더 정리는 하지 않는 대학생. (설문: 북마크 사용자 26명 중 16명(62%)이 폴더를 만들지 않음 / Chrome users who bookmark but don't organize into folders — 62% of bookmark users surveyed make no folders)
- 상황 / Situation: 크롬 별 버튼의 기본 저장 위치가 북마크바라, 북마크가 북마크바에 폴더 없이 쌓인다. 북마크 수는 대부분 50개 이하(84%)다. / Starred bookmarks pile up unorganized on the bookmarks bar; most users have under 50 bookmarks.
- 페인포인트 / Pain point: 북마크가 눈에 띄지 않아 **저장한 사실 자체를 잊고**, 저장한 **이름이 기억나지 않는다**. (설문 자유응답에서 반복) 찾는 데 걸리는 시간은 대부분 1분 이내라 "검색 속도"는 문제가 아니었다. / Bookmarks are out of sight, so users forget they saved them and forget the titles. Search speed was not the problem (most found items within a minute).
- 성공 기준 / Success criteria:
  - 잊은 북마크 발견: 테스트 참가자가 "잊고 있던 북마크" 폴더를 스스로 열어 보고, 잊고 있던 북마크를 알아본다. / Users open the "forgotten bookmarks" folder on their own and recognize items they had forgotten.
  - 분류 품질: 적용률·정확도·수정률이 첫 측정 후 팀이 정한 목표치를 넘는다. (현재 샘플 100개 중 89개 분류, 분류된 89개 전부 정답) / Classification coverage/accuracy/edit-rate exceed the team's target (currently 89/100 classified, all 89 correct).
  - 안전성: [정리하기] 전에는 크롬 북마크가 하나도 바뀌지 않고, 사용자 폴더와 요즘 쓰는 북마크는 그대로 남으며, [되돌리기]로 원래 폴더·순서로 돌아간다.

## 2. 사용자 확인 / User Validation
인터뷰 3명 요지 / Summary of three interviews:근거: 구글폼 설문(응답 48명, 북마크 사용자 26명)의 자유응답 6건과 선택지 결과를 대표 사례로 정리함. 개별 인터뷰 원문이 아니라 설문 응답 기반이다.
1. 북마크를 해 둔 사실 자체를 잊는다. 저장할 때는 "나중에 봐야지" 했지만 북마크 목록이 눈에 안 띄어 다시 열지 않는다. → 새 탭에 항상 보이게 하고, 오래 안 연 것은 "잊고 있던 북마크"로 먼저 꺼내 준다. 
2. 저장한 이름이 기억나지 않아 목록에서 찾기 어렵다. 썸네일 같은 미리보기가 있으면 좋겠다. → 이름 대신 **사이트 아이콘과 종류별 폴더**로 알아보게 한다. / Can't recall the saved title.
3. 폴더 정리가 귀찮아 북마크바에 그냥 쌓아 둔다(폴더 미사용 62%). → 북마크 수에 맞춰 **3~6개 폴더만** 한 번 확인 후 자동으로 만들고, 애매한 것은 숨기지 않는다.

## 3. 실행 방법 / How to Run
```bash
git clone <repo-url>
# 설치 / install
# 실행 / run
```
필요한 환경변수 / Required environment variables: `.env.example` 참고

## 4. 아키텍처 / Architecture
![architecture](docs/architecture.png)
> 서버·DB·AI가 없다. 두 부분으로 나뉜다: 새 탭이 열려 있을 때 동작하는 **새 탭 화면**과, 새 탭이 닫혀 있어도 북마크 알림을 받는 **백그라운드 서비스 워커**. 데이터는 크롬 북마크(원본)와 `chrome.storage.local`(이 PC 기록)뿐이다. 자세한 구조는 `docs/file-structure.md`.
- 표현 계층 / Presentation: `newtab.html` + `newtab.css` + `js/render.js`(화면 시작·전체 다시 그리기) + `js/view/*`(cards·folders·forgottenFolder·history) + `js/ui.js`(공통 조각) + `js/search.js`. 각 파일은 `newtab.html`의 자기 칸만 그린다. / HTML/CSS and view modules; each draws only its own slot.
- 로직 계층 / Logic: `js/classify.js`·`js/plan.js`·`js/forgotten.js`·`js/topic.js` — 크롬 API를 부르지 않고 입력만으로 계산한다(분류·폴더 계획·잊은 북마크 고르기). `js/organize.js`는 정리 적용·되돌리기를 실행한다. / Pure-computation rule modules + the organize/undo runner.
- 데이터 계층 / Data: `js/bookmarks.js`(크롬 북마크를 읽고 바꾸는 통로), `js/store.js`(`chrome.storage.local` 읽고 쓰기, 한 키는 한쪽만 씀), `background.js`(서비스 워커: 새 북마크·직접 옮김·삭제 기록), `data/categories.json`(분류표). / Bookmark gateway, storage gateway, service worker, and the category table.

## 5. 기술 스택과 선택 이유 / Tech Stack and Rationale
| Chrome Extension Manifest V3 (크롬 134+) | 크롬 북마크를 가져오기 없이 직접 읽고 새 탭을 대체해야 한다. 북마크바가 두 개로 보이는 크롬 134 동작까지 다루려고 최소 버전을 134로 둔다. / Needed to read Chrome bookmarks directly and replace the new tab page. |
| HTML·CSS·JavaScript (ES 모듈), 빌드 도구 없음 / no build tools | 네 명이 파일을 나눠 맡고 `extension/` 폴더째 바로 올려 확인한다. 빌드·번들러·TypeScript·프레임워크를 넣지 않아 설치 장벽과 충돌을 줄인다. / Four people split files and load the folder as-is; no bundler keeps setup trivial. |
| 백그라운드 서비스 워커 / service worker | 새 탭이 닫혀 있어도 사용자의 "직접 옮김"과 새 북마크를 감지해야 한다. / Detect manual moves and new bookmarks even when no tab is open. |
| 데이터: 크롬 북마크 + `chrome.storage.local` (서버·DB 없음) | 기기 간 동기화는 크롬 로그인 동기화가 맡는다. 자체 서버·DB는 범위를 키우고 개인정보 위험을 만든다. / Chrome sync handles cross-device; a custom backend would add scope and privacy risk. |
| 규칙 기반 분류 (AI 없음) / rule-based, no AI | 북마크에 민감 정보가 있어 외부 전송을 피한다. 규칙은 결과가 항상 같고 근거를 설명할 수 있으며 정확도를 반복 측정해 고칠 수 있다. / Avoids sending sensitive data out; deterministic and explainable. |
| SortableJS (파일 포함, P3) | 드래그 정렬에만 쓴다. CDN을 못 쓰므로(MV3 CSP) 폴더에 파일로 넣는다. / Local file only, used for P3 drag reorder. |
| GitHub Actions + CodeRabbit | PR마다 문법·빠진 함수·JSON 형태를 자동 검사하고 코드 리뷰를 받는다. / Automated checks and review on every PR. |
## 6. 팀 구성 / Team
| 이름(GitHub 아이디) Name (handle) | 담당 영역 Area | 주요 이슈 Issues |
|---|---|---|
| 박현 / Member A | 크롬 북마크·저장소 통로, 정리 적용·되돌리기, 정리 기록 화면 (manifest, bookmarks, store, organize, view/history) | #1, #2, #3, #4, #5 |
| 한승엽 / Member B | 서비스 워커, 분류·잊은 북마크(계산), 잊은 북마크 화면, 분류표 (background, classify, forgotten, view/forgottenFolder, categories.json) | #6, #7, #8, #9, #10 |
| 이제빈 / Member C | 정리 대상·폴더 계획(계산), 세부 폴더 제안, 내 폴더 화면 (plan, topic, view/folders) | #11, #12, #13 |
| 최윤성 / Member D | 새 탭 화면·공통 UI, 화면 시작·다시 그리기, 카드·검색·드래그 (newtab.html/css, render, ui, view/cards, search, dnd) | #14, #15, #16, #17, #18, #19 |

## 7. 라이선스 / License
MIT — 선택 이유 / Why:
