# 9주차 활동지 / Week 9 Worksheet

**개발 착수 / Starting development**

- 작성일 / Date: 2026-10-28
- 참여자 / Present: 박현, 이제빈, 최윤성, 한승엽
- 개발링크: https://github.com/aix-team-5/aix_BaroLink_bookmark

---

## ① 착수 점검표 / Start checklist

수업 시작 후 10분 안에 확인합니다. 체크되지 않은 항목이 있으면 그것부터 해결하고 개발을 시작합니다.
*Check within the first 10 minutes. Fix any unchecked item before you start coding.*

- [ㅇ] 초기 파일이 저장소에 올라와 있다 / Initial files are in the repository
- [ㅇ] 7주차 이슈가 GitHub에 등록되어 있고 담당자가 지정되어 있다 / Week 7 issues are on GitHub with owners
- [ㅇ] 팀원 모두 같은 환경에서 실행된다 / Everyone can run it in the same environment
- [ㅇ] 브랜치 규칙을 정했다 / Branch rule agreed — 

---

## ② 개발 일정 / Development schedule

5주차 **작업 순서**와 7주차 **이슈·마일스톤**을 바탕으로 이슈를 주차별로 배치합니다.
*Place your issues week by week, based on the Week 5 work order and Week 7 issues and milestones.*

- 11주차에 MVP가 동작해야 합니다. / Fill backwards from the deadlines.
- 선행 이슈가 끝나기 전에 뒤 이슈를 넣지 않습니다. / Never schedule an issue before the ones it depends on.
- 한 사람에게 몰리지 않았는지 확인합니다. / Check that no one is overloaded.
- P1(11주 중간 데모)은 9~11주차 안에 모두 끝내고, P2는 #22(P1 확인 목록)가 닫힌 12주차부터 `-p2` 브랜치로 시작합니다.

| 주차 Week | 수업 일정 Class | 끝낼 이슈 # Issues to close | 담당 Owner |
|---|---|---|---|
| 9주차 | 개발 착수 | **[P1] 바닥 통로와 분류 규칙**<br>#1 `manifest.json`<br>#2 `bookmarks.js` (F01-01~05·07, F02, F03-01~03, F07)<br>#3 `store.js` (F01-06, F04, F06, F07-05, F13)<br>#7 `classify.js` (F05-01~03·08) | 팀원 A: #1, #2, #3<br>팀원 B: #7 |
| 10주차 | 막힘 진단 · 데모 시나리오 초안 | **[P1] 계산 파일과 화면 조각 모두 합치기**<br>#4 `organize.js` (F07-01~04·08~09, F13-03~08)<br>#5 `view/history.js` 정리 결과 안내 (F07-03)<br>#8 `forgotten.js` (F04-01~03·12)<br>#9 `view/forgottenFolder.js` (F04-04~07·09~11)<br>#6 `background.js` P1 부분 (F01-06, F07-05)<br>#10 `categories.json` 확인 (F05-03)<br>#11 `plan.js` (F05-04~07·09)<br>#13 `view/folders.js` (F03-01~03)<br>#16 `ui.js` (F02-01·03)<br>#14 `newtab.html`, `newtab.css` (F12-01~04)<br>#17 `view/cards.js` (F06-01~03·05~06)<br>#15 `renderAll` 뼈대 먼저 올리기<br>데모 시나리오 초안 | 팀원 A: #4, #5<br>팀원 B: #8, #9, #6, #10<br>팀원 C: #11, #13<br>팀원 D: #16, #14, #17, #15 뼈대 |
| 11주차 | **MVP 완료 · 중간 데모** | **[P1] 연결, 확인, 데모**<br>#15 `render.js` 전체 연결 (F01-01·02·05, F12)<br>#18 `search.js` 웹 검색창 (F11-01~05)<br>#22 P1 확인 목록 닫기<br>데모 이틀 전부터 `fix`만 합치기, 데모 날 `demo-w11` 태그 | 팀원 D: #15, #18<br>#22: 전원 (A→B→C→D→A) |
| 12주차 | 핵심 경로 테스트 | **P2 시작**<br>#20 샘플 북마크 세트<br>#22에서 나온 `fix`<br>#5-p2 정리 기록 화면 (F13-01·02·09·10)<br>#6-p2 새 북마크, 직접 옮김 (F10, F07-06·07)<br>#11-p2 고정 후보, 새 폴더 제안 (F09, F10)<br>#18-p2 북마크 검색 (F14) | 팀원 C·B: #20<br>팀원 A: #5<br>팀원 B: #6<br>팀원 C: #11<br>팀원 D: #18 |
| 13주차 | **배포 · 실행 패키지** | **P2 이어서, 배포 준비**<br>#3-p2 고정됨(독) 저장 (F08)<br>#9-p2 [고정하기] (F04-08)<br>#13-p2 폴더 만들기·이름 바꾸기·삭제, 우클릭 이동 (F03-04~08, F15)<br>#17-p2 고정 제안 카드, [정리하기] 창 (F06-04·07, F09, F10)<br>#21 저장소 마무리 (README 실행법, 배포용 압축 파일) | 팀원 A: #3, #21<br>팀원 B: #9<br>팀원 C: #13<br>팀원 D: #17 |


> 일정이 맞지 않으면 기능을 줄입니다. 뺀 기능은 5주차 Won't 목록에 옮깁니다.
> *If it doesn't fit, cut scope and move the feature to your Week 5 Won't list.*

> **11주차 데모 시나리오:** 새 탭에 앱과 앱 폴더가 보임 → 첫 정리 카드에서 [정리하기] → 북마크바에 폴더가 생김 → [되돌리기]로 원래대로 → 잊고 있던 북마크를 발견해 열기

> **일정이 밀리면:** 13주차의 우클릭 이동(F15)부터 뺍니다. #12 `topic.js`, #19 `dnd.js`, #24 P3 확인 목록은 시간이 남으면 합니다.

> **일이 몰리는 사람:** 팀원 D는 P1 파일이 5개입니다. #16 `ui.js`를 가장 먼저 합치고 `renderAll` 뼈대를 먼저 올립니다. 팀원 A가 D의 PR 확인을 먼저 맡습니다.

---


---

## ③ 이번 주 목표 이슈 / This week's issues (9주차)

| # | 제목 Title | 담당 Owner | 완료 Done |
|---|---|---|---|
| #1 | `manifest.json` 권한, 새 탭 바꾸기, 서비스 워커 등록 (PR #28) | `parkhyun0701-oss` | ✅ |
| #2 | `bookmarks.js` 크롬 북마크 통로 (F01-01~05·07, F02-01~05, F03-01~03, F07-01~04·08~09) (PR #30) | `parkhyun0701-oss` | ✅ (P1) |
| #3 | `store.js` 저장 항목 통로 (F01-06, F04, F06, F07-05, F13-03~08) (PR #29) | `parkhyun0701-oss` | ✅ (P1) |
| #7 | `classify.js` 분류 규칙과 정확도 측정 (F05-01~03·08) (PR #37) | `hantmdduq` | ✅ |


---

## ④ 오늘 진행한 것 / Progress today

- [ ] 이번 활동에서 AI를 사용했다면 `PROMPTS.md`에 기록했습니다 / Logged any AI use in `PROMPTS.md`

---

> 수업 종료 시 커밋하세요 / Commit this at the end of class
> `git add docs/week-09.md && git commit -m "docs: 9주차 활동지 작성"`
