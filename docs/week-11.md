# 11주차 활동지 / Week 11 Worksheet

**개발 착수 / Starting development**

- 작성일 / Date: 2026-11-16 (작업 기간 11/11 수 ~ 11/16 월)
- 참여자 / Present: 박현, 이제빈, 최윤성, 한승엽

---

## ① 착수 점검표 / Start checklist

수업 시작 후 10분 안에 확인합니다. 체크되지 않은 항목이 있으면 그것부터 해결하고 개발을 시작합니다.
*Check within the first 10 minutes. Fix any unchecked item before you start coding.*

- [x] 초기 파일이 저장소에 올라와 있다 / Initial files are in the repository
- [x] 7주차 이슈가 GitHub에 등록되어 있고 담당자가 지정되어 있다 / Week 7 issues are on GitHub with owners
- [x] 팀원 모두 같은 환경에서 실행된다 / Everyone can run it in the same environment
- [x] 브랜치 규칙을 정했다 / Branch rule agreed — 이슈 하나에 브랜치 하나, 이름은 `종류/기능번호-짧은이름`(예: `feat/F10-apply-new`). `main` 직접 push 금지 → PR → 1명 승인 → Squash and merge

---

## ② 개발 일정 / Development schedule

5주차 **작업 순서**와 7주차 **이슈·마일스톤**을 바탕으로 이슈를 주차별로 배치합니다.
*Place your issues week by week, based on the Week 5 work order and Week 7 issues and milestones.*

- 11주차에 MVP가 동작해야 합니다. / Fill backwards from the deadlines.
- 선행 이슈가 끝나기 전에 뒤 이슈를 넣지 않습니다. / Never schedule an issue before the ones it depends on.
- 한 사람에게 몰리지 않았는지 확인합니다. / Check that no one is overloaded.

| 주차 Week | 수업 일정 Class | 끝낼 이슈 # Issues to close | 담당 Owner |
|---|---|---|---|
| 9주차 | 개발 착수 | PR #28 manifest, #29 store.js, #30 bookmarks.js, #32 검증 매뉴얼, #33 명세 v16, #37 classify.js, #34 newtab 뼈대, #35 cards.js, #36 ui.js, #38 organize.js, #39 명세 v17 | A · B · C · D |
| 10주차 | 막힘 진단 · 데모 시나리오 초안 | PR #40 render.js, #41 history.js, #42 forgotten.js, #43 plan.js, #44 background.js, #45 folders.js, #46 forgottenFolder.js, #47 search.js, #48 명세 v18, #49 샘플 세트 → P1 화면 완성, `demo-w11` 태그 | A · B · C · D |
| 11주차 | **MVP 완료 · 중간 데모** | PR #50 명세 v19, #51·#52 화면 배경·아이콘, #53 pin/unpin, #54 suggestForNew, #55 setImporting, #56 안내 문구 확정, #57 renameFolder, #58 pickPinCandidates, #59 새 북마크 기록·가져오기 중 멈춤, #60 잊고 있던 북마크 고정, #61 정리 기록 화면, #64 명세 v20, #65 showToast container, #66 북마크 검색, #69 팝업 안내 수정 | A · B · C · D |
| 12주차 | 핵심 경로 테스트 | 열린 브랜치 합치기: F03 폴더 편집(#63), F10 새 북마크 정리(apply-new·organizedialog·new-folders), F15 우클릭 메뉴·삭제/되살리기, F08 독 편집, F09 고정 제안 카드 · P2 확인 목록 #23 | A · B · C · D |
| 13주차 | **배포 · 실행 패키지** | 웹스토어 배포 준비(`docs/store-prep`), 실행 패키지·README 정리, P3(F16·F17)는 남으면 Won't | A (배포) · 전원 확인 |

> 일정이 맞지 않으면 기능을 줄입니다. 뺀 기능은 5주차 Won't 목록에 옮깁니다.
> *If it doesn't fit, cut scope and move the feature to your Week 5 Won't list.*

---

## ③ 이번 주 목표 이슈 / This week's issues

| # | 제목 Title | 담당 Owner | 완료 Done |
|---|---|---|---|
| #50 | 우클릭 메뉴에 북마크 삭제·되돌리기 추가, 명세 v19 (F15) | A | [x] |
| #52 | 파비콘 있는 앱 아이콘 뒤 색 타일 겹침 수정 (F02-01) | D | [x] |
| #51 | 새 탭 배경 사진과 투명 섹션 카드 (F12) | D | [x] |
| #53 | 독에 고정·고정 해제 pin/unpin (F08-01·04·06) | A | [x] |
| #55 | 가져오기 중 표시 setImporting/isImporting (F01-07) | A | [x] |
| #57 | 폴더 이름 바꾸기 renameFolder (F03-05·07) | A | [x] |
| #54 | 새 북마크 추천 폴더 suggestForNew (F10-04·07) | B | [x] |
| #59 | 새 북마크 기록·옮기면 빼기·가져오는 동안 멈춤 (F10-01·08·09, F01-07) | B | [x] |
| #64 | 새 북마크 정리 창·applyPlan "new" 입력 확정, 명세 v20 (F10-05) | A | [x] |
| #60 | 잊고 있던 북마크 고정하기·모두 보기 (F04-05·08·09) | B | [x] |
| #56 | 정리 결과·되돌리기 안내 문구 확정 (F07-03·09, F13-05·08) | A | [x] |
| #61 | 정리 기록 화면 (F13-01·02·09·10) | A | [x] |
| #65 | 팝업 안에 안내 문구 showToast container (F02-04) | D | [x] |
| #66 | 북마크 검색 searchBookmarks와 결과 리스트 (F14-01~06) | D | [x] |
| #58 | 고정 후보 고르기 pickPinCandidates (F09-03·04·08·09) | C | [x] |
| #69 | 잊고 있던 북마크 팝업 안내 위치 수정 (F04-08) | B | [x] |
| #63 | 하위 폴더·폴더 만들기·이름 바꾸기·삭제 (F03-04~08) — 리뷰 반영 중 | C | [ ] |
| — | 새 북마크가 모이면 새 폴더 제안 suggestNewFolders (F10-06) | C | [ ] |
| — | 우클릭 메뉴 새 탭에서 열기·고정·폴더로 이동 (F15-01~05·10) | C | [ ] |
| — | 북마크 삭제·되살리기, 저장 기록 옮겨 적기 (F15-06~12) | A | [ ] |
| — | 새 북마크 정리 적용과 그대로 두기 기록 (F10-05) | A | [ ] |
| — | 독 고정 해제와 [+], 고정할 북마크 고르기 창 (F08-04·06, F09-05·06) | D | [ ] |
| — | 폴더를 못 만들 때 고정 제안 카드 (F06-07, F09-01~03·08·09) | D | [ ] |
| — | 새 북마크 정리 창과 '새로' 표시, 헤더 버튼 분기 (F10-01·02·04~07) | D | [ ] |
| — | 웹스토어 배포 준비 파일 추가 | A | [ ] |

---

## ④ 오늘 진행한 것 / Progress today

- MVP: P1 화면이 모두 main에 들어갔고 `demo-w11` 태그를 붙임(11/09, `79e0daf`). 11주차에는 P2 기능 PR 16개를 main에 합침(11/11~11/14)
- A: 새 북마크 정리 적용(F10-05) 브랜치에 main 반영, 이미 목적지 폴더에 있는 북마크는 '그대로 두기'로 세고 관리자 폴더는 빼도록 수정(`feat/F10-apply-new`, 11/16) · 웹스토어 배포 준비 문서 작성(`docs/store-prep`, 11/15)
- B: 새 북마크 기록·가져오기 중 멈춤(#59), 추천 폴더(#54), 잊고 있던 북마크 고정·모두 보기(#60·#69) 합침
- C: 고정 후보 고르기(#58) 합침 · 폴더 편집(#63) 리뷰 반영, 우클릭 메뉴(F15)·새 폴더 제안(F10-06) 브랜치 진행 중
- D: 북마크 검색(#66)·안내 문구 container(#65) 합침 · 독 편집(F08), 고정 제안 카드(F09), 새 북마크 정리 창(F10) 브랜치 올림(11/15)
- 다음: 열린 브랜치 9개 PR 리뷰·합치기 → P2 확인 목록(#23) 채우기

- [ ] 이번 활동에서 AI를 사용했다면 `PROMPTS.md`에 기록했습니다 / Logged any AI use in `PROMPTS.md`

---

> 수업 종료 시 커밋하세요 / Commit this at the end of class
> `git add docs/week-011.md && git commit -m "docs: 11주차 활동지 작성"`
