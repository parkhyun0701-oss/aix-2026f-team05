# AI 협업 기록 / AI Collaboration Log

작성 원칙: 프롬프트 나열이 아니라 **판단 근거**를 남긴다.
Principle: record your **reasoning**, not just prompts.

---

## [이슈 #__] 제목 / Title

**목표(스펙) / Spec**
- 입력 Input:
- 처리 Processing:
- 출력 Output:
- 실패 조건 Failure:

**요청한 프롬프트 요지 / Prompt (summary)**

**결과에 대한 판단 / Decisions**
- 채택한 부분과 이유 / Accepted, because:
- 수정한 부분과 이유 / Changed, because:
- 폐기한 부분과 이유 / Rejected, because:

**검증 방법 / How it was verified**

---
(이슈 단위로 반복 / repeat per issue)

--
## 2026-09-11 · 메모 검색 기능 (2주차 활동)
### A조

**지시**
text메모 검색 기능 만들어줘. 제목이랑 본문에서 키워드로 찾을 수 있게.

**채택 여부**
미채택 (계층 분리 미준수, 응답 포맷 미준수, SQL/백엔드 로직 누락 및 user_id 조건 부재로 인한 본인 메모 검색 실패)

**참고**
파일 및 컨텍스트를 전혀 제공하지 않아 단순 클라이언트 JS 단일 파일만 생성됨.


