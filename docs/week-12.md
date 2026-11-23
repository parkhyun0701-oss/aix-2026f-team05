# 12주차 활동지 / Week 12 Worksheet

**개발 착수 / Starting development**

- 작성일 / Date: 2026-11-18 (작업 기간 11/16 월 오후 ~ 11/18 수)
- 참여자 / Present: 박현, 이제빈, 최윤성, 한승엽

---

## ① 착수 점검표 / Start checklist

수업 시작 후 10분 안에 확인합니다. 체크되지 않은 항목이 있으면 그것부터 해결하고 개발을 시작합니다.
*Check within the first 10 minutes. Fix any unchecked item before you start coding.*

- [x] 초기 파일이 저장소에 올라와 있다 / Initial files are in the repository
- [x] 7주차 이슈가 GitHub에 등록되어 있고 담당자가 지정되어 있다 / Week 7 issues are on GitHub with owners
- [x] 팀원 모두 같은 환경에서 실행된다 / Everyone can run it in the same environment
- [x] 브랜치 규칙을 정했다 / Branch rule agreed — 이슈 하나에 브랜치 하나, 이름은 `종류/기능번호-짧은이름`(예: `feat/F17-dnd`). `main` 직접 push 금지, PR 1명 승인 뒤 Squash and merge. 명세는 A가 `docs/spec-v22` 브랜치로 고침. P3 PR은 P2 확인 목록(#23)이 끝난 뒤 합침(conventions 9번)

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
| 10주차 | 막힘 진단 · 데모 시나리오 초안 | PR #40 render.js, #41 history.js, #42 forgotten.js, #43 plan.js, #44 background.js, #45 folders.js, #46 forgottenFolder.js, #47 search.js, #48 명세 v18, #49 샘플 세트, P1 화면 완성, `demo-w11` 태그 | A · B · C · D |
| 11주차 | **MVP 완료 · 중간 데모** | P2 기능 PR(#50~#81)을 main에 합침, 명세 v19~v21 | A · B · C · D |
| 12주차 | 핵심 경로 테스트 | 먼저 P2 확인 목록 #23 마무리 · 명세 v22(F17 드래그 이동, F18 내 정보와 꾸미기, F16 제외) · P3 구현: F17 #19(PR #82), F18 새 기능 · 웹스토어 제출 준비(S1~S8) | A · B · C · D |
| 13주차 | **배포 · 실행 패키지** | 11/24~25 P3 기능 고정 후 웹스토어에 한 번 제출(제출 뒤에는 제출본을 고치지 않음), P3 확인 목록 #24, 실행 패키지·README 정리 | A (제출) · 전원 확인 |

> 일정이 맞지 않으면 기능을 줄입니다. 뺀 기능은 5주차 Won't 목록에 옮깁니다.
> *If it doesn't fit, cut scope and move the feature to your Week 5 Won't list.*

이번 주에 뺀 기능 (5주차 Won't 목록에 옮김)
- F16 세부 폴더 제안: 지금 필요 없음. 요구사항 3줄은 지우지 않고 우선순위만 '제외'로 바꾸고, topic.js N35도 함께 '제외'. 이슈 #12와 `feat/F16-topic` 브랜치는 v22 뒤 정리
- 내 정보 창의 이메일·이름 표시: 새 권한이 필요해서 하지 않음. 그래서 P3는 새 권한이 하나도 없음
- 다크 모드: 라이트만 함
- F17 중 폴더 끌기, 독 순서 바꾸기, 앱 위에 앱을 놓아 폴더 만들기, 모든 북마크 안에서 순서 바꾸기(여러 폴더를 펼친 목록이라 크롬 순서로 저장할 수 없음)

데모(11/30 주) 전에 웹스토어 승인이 나지 않으면 개발자 모드로 설치해 데모하고, 대시보드의 "심사 중" 화면을 보여 준다.

---

## ③ 이번 주 목표 이슈 / This week's issues

| # | 제목 Title | 담당 Owner | 완료 Done |
|---|---|---|---|
| — | 명세 v22: F17 10줄(3줄 고침·7줄 추가), F18 14줄 추가, F16 '제외', 저장 항목 appearance·profilePhoto·wallpaperPhoto, dnd.js N36을 함수 3개로 | A | [ ] |
| #19 | F17 끄는 쪽: dnd.js makeDraggable, 모든 북마크의 점 6개 손잡이, 끄는 동안 표시 (F17-01·04·06~09) — PR #82 | D | [ ] |
| — | F17 놓는 쪽: folders.js 폴더 타일에 넣기, 팝업 안 순서 바꾸기·하위 폴더에 넣기, 놓을 수 없는 곳·지금 폴더 처리 (F17-01~03·05) | C | [ ] |
| — | F17 끄는 동안 화면 다시 그리기 미루기 (F17-10): render.js scheduleRerender(D), folders.js(C) | D · C | [ ] |
| — | F18 꾸미기 저장 함수 setAppearance·setPhoto·loadPhotos, 이 PC에만 저장, 없는 값은 기본값 (F18-12·14) | A | [ ] |
| — | F18 헤더 계정 동그라미, 화면 보이기 전 꾸미기 적용 applyAppearance (F18-01·13) | D | [ ] |
| — | F18 색 8벌·배경·글꼴 CSS, 대체 이미지 SVG·배경 사진·글꼴 파일 (F18-06·07·11) | D | [ ] |
| — | F18 내 정보 창 view/profile.js: 동기화 켜짐/꺼짐, 북마크 수·폴더 수, 마지막 정리 날짜 (F18-02·03), 먼저 `syncing` 값 실행 확인 | B | [ ] |
| — | F18 프로필·배경 사진 고르기·줄이기·지우기, "사진을 쓸 수 없어요" (F18-04·05·08·09·10) | B | [ ] |
| — | 웹스토어 제출 준비: 방침 3·4·6절 고침(S1·S8), 개인정보 보호 관행 신고(S5), 스토어 설명(S6), 권한별 이유(S7), 개발자 계정 | A | [ ] |
| — | 배경 사진·글꼴·대체 이미지 출처와 라이선스, docs/credits.md (S2~S4) | D · A | [ ] |
| #12 | topic.js 세부 폴더 제안: F16 제외로 정리 | C | [ ] |
| #24 | P3 확인 목록을 v22 줄(F17 10줄, F18 14줄)로 바꾸기 | C · D | [ ] |

P3 담당은 회의에서 정할 담당 제안(Q4)대로 적음. F17·F18이 모두 D 파일에 몰려서 나눔.

---

## ④ 오늘 진행한 것 / Progress today

- P3 범위 확정(11/16): F17 드래그 이동 + F18 내 정보와 꾸미기, F16 제외. 새 권한 없음(manifest 그대로 bookmarks·storage·favicon·search, 선택 topSites). 내 정보 창은 북마크 동기화 켜짐/꺼짐, 북마크 수·폴더 수, 마지막 정리 날짜만 보여 줌. 꾸미기와 사진은 이 PC(storage.local)에만 저장
- 명세 v22 정리본 최종 검토(11/17): 코드와 대조해 4곳을 고침. (1) F17-02 같은 폴더 안 +1은 moveBookmark가 이미 하므로 다시 더하지 않음 (2) 팝업 안 순서는 화면 순번이 아니라 크롬 index로 넘김 (3) 끄는 동안 화면을 다시 그리지 않고 끝난 뒤 한 번 그림(F17-10으로 올림) (4) 내 정보 창은 헤더가 아니라 #dialogs에 두고, 사진 두 키는 load() 밖에서 따로 읽음
- 웹스토어 배포 검토: 새 권한이 없고 데이터를 밖으로 보내지 않아 P3 때문에 막히는 정책은 없음. 다만 대시보드의 개인정보 보호 관행을 "없음"으로 신고하면 안 됨(북마크·웹 기록을 다룬다고 신고). 방침·출처·스토어 설명·권한 이유를 제출 전에 맞춤
- 제출 일정 결정(11/17): P3까지 만든 뒤 한 번에 제출. 이번 주(~11/22)에 개발자 계정, 스토어 설명·스크린샷, 신고, 방침, 출처를 준비하고 11/24~25 기능 고정 후 제출. 제출 전에 초안 상태로 올려 설치 오류부터 확인
- D: F17 끄는 쪽 PR #82 올림(dnd.js 손잡이·놓을 곳 표시, 시안대로 끌기 모양, 11/18)
- C: P3 명세와 디자인 시안 대조. v22에 더할 것 정리: 앞에서 뒤로 끌 때 한 칸 밀리는 순서 계산 고치기, 관리자 폴더·고르지 않은 쪽 폴더·[새 폴더] 칸을 놓을 수 없는 곳에 넣기, folders.js 자체 다시 그리기도 끄는 동안 미루기
- 다음: 회의(Q2 헤더 동그라미, Q4 담당, Q5 SortableJS 안 씀, Q6 배경 사진 위 가독성, Q7 Pretendard·나눔명조, Q8 기본 그림) 뒤 명세 v22 PR 그날 합치기, F18-03 `syncing` 값이 동기화를 켜고 끌 때 바뀌는지 크롬 두 프로필로 확인, store.js 함수·색 8벌 CSS, 화면, 배포 준비

### P3 구현 완료와 웹스토어 배포 (추가)

- **P3 기능 구현 완료:** F17 드래그 이동(끄는 쪽 dnd.js, 놓는 쪽 folders.js, 끄는 동안 다시 그리기 미루기)과 F18 내 정보와 꾸미기(헤더 계정 동그라미, 내 정보 창, 색·배경·글꼴 꾸미기, 프로필·배경 사진)를 모두 만들어 main에 합침. 새 권한은 추가하지 않음
- **웹스토어 제출(11/22):** 계획(11/24~25)보다 앞당겨 P3까지 들어간 main `7d00a90`(#102)의 `extension/`을 version 1.0.0으로 묶어 제출. 개인정보처리방침·출처(credits)·스토어 설명·스크린샷 5장·권한별 이유·개인정보 보호 관행 신고를 함께 맞춤
- **심사 승인·게시:** 크롬 웹스토어 심사를 통과해 공개 게시됨. 다른 컴퓨터에서도 웹스토어 페이지로 바로 설치해 새 탭에서 동작하는 것을 확인함 → 데모는 개발자 모드가 아니라 웹스토어 설치본으로 진행 가능
- **배포 링크:** https://chromewebstore.google.com/detail/jlmohochknbdbdlpobbmiepajnldifle
- 다음: P3 확인 목록 #24 마무리, 실행 패키지·README에 웹스토어 링크 추가, 데모(11/30 주) 시나리오를 설치본 기준으로 정리. 버그를 고치면 version 1.0.1로 따로 제출

- [ ] 이번 활동에서 AI를 사용했다면 `PROMPTS.md`에 기록했습니다 / Logged any AI use in `PROMPTS.md`
