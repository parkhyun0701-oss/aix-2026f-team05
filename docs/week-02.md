# 2주차 활동지 / Week 2 Worksheet

# 2주차 활동지 — 코딩 에이전트와 컨텍스트

| | |
| :-- | :-- |
| 팀명 | 5(오)류해결팀|
| 작성일 | 2026.09.09|
| 참여자 | 박현, 최윤성, 한승엽, 이제빈|

---

## 0. 준비

 `memo-seed` 저장소를 엽니다. 다음 파일이 있는지 확인하세요.

- [o] `schema.sql`
- [o] `service.js`
- [o] `routes.js`
- [o] `CONVENTIONS.md`

---

## 1. 조 나누기

팀을 두 조로 나눕니다. (4인 → 2:2 / 3인 → 1:2)

| 조 | 참여자 |
| :-- | :-- |
| A조 | 이제빈, 박현 |
| B조 | 최윤성, 한승엽|

**두 조는 같은 과제를 동시에 수행합니다.** 서로의 화면을 보지 마세요.

### 오늘의 과제 (두 조 공통)

> 메모 검색 기능을 추가하라. 제목과 본문에서 키워드로 찾을 수 있어야 한다.

---

## 2. 에이전트에게 준 것

### A조 — 이것만 붙여넣습니다

```
메모 검색 기능 만들어줘. 제목이랑 본문에서 키워드로 찾을 수 있게.
```

파일은 **하나도 주지 않습니다.**

### B조 — 네 칸을 모두 채웁니다

```
[지시]
메모 검색 기능을 추가해줘. 제목과 본문에서 키워드로 검색된다.

[규약]
(CONVENTIONS.md 내용 전체를 붙여넣기)

[근거]
(schema.sql, service.js, routes.js 내용 전체를 붙여넣기)

[종료조건]
- GET /memos/search?q=키워드 로 호출된다
- 제목 또는 본문에 키워드가 포함된 메모만 반환한다
- 본인 메모만 반환한다
- q가 비어 있으면 400과 { ok: false, error } 를 반환한다
```

### 실제로 붙여넣은 것 (원문 그대로, 요약 금지)

```
[지시]
메모 검색 기능을 추가해줘. 제목과 본문에서 키워드로 검색된다.

[규약]
(# 프로젝트 규약

이 문서는 코드를 작성할 때 지켜야 할 규칙입니다.

## 계층 분리

- `routes.js`는 HTTP 요청과 응답만 다룹니다. SQL을 직접 쓰지 않습니다.
- 데이터베이스 접근은 `service.js`에만 둡니다.

## 응답 형식

모든 응답은 다음 두 형태 중 하나입니다.

```json
{ "ok": true,  "data": ... }
{ "ok": false, "error": "ERROR_CODE" }

에러 코드는 대문자와 밑줄로 씁니다. (예: `MEMO_NOT_FOUND`)

## 명명 규칙

- 함수명은 동사로 시작합니다. `list`, `get`, `create`, `update`, `remove`
- 데이터베이스 컬럼은 스네이크 케이스를 씁니다. `user_id`, `created_at`
- 자바스크립트 변수는 카멜 케이스를 씁니다. `userId`, `createdAt`

## 입력 검증

- 사용자 입력은 반드시 검증합니다.
- 검증에 실패하면 400과 함께 `{ ok: false, error }` 를 반환합니다.

## 권한

- 모든 조회와 수정은 **본인 소유 데이터로 한정**합니다.
- 모든 쿼리에 `user_id` 조건을 포함합니다.)

[근거]
(-- memo-seed 데이터베이스 스키마

CREATE TABLE users (
  id         INTEGER PRIMARY KEY,
  email      TEXT NOT NULL UNIQUE,
  name       TEXT NOT NULL,
  created_at TEXT NOT NULL
);

CREATE TABLE memos (
  id         INTEGER PRIMARY KEY,
  user_id    INTEGER NOT NULL,
  title      TEXT NOT NULL,
  body       TEXT NOT NULL,
  created_at TEXT NOT NULL,
  FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE INDEX idx_memos_user ON memos(user_id);)

const db = require('./db');

/**
 * 사용자의 메모 목록을 최신순으로 조회한다.
 */
function listMemos(userId) {
  return db.all(
    `SELECT id, title, created_at
       FROM memos
      WHERE user_id = ?
      ORDER BY created_at DESC`,
    [userId]
  );
}

/**
 * 메모 한 건을 조회한다. 본인 메모가 아니면 null을 반환한다.
 */
function getMemo(userId, memoId) {
  return db.get(
    `SELECT id, title, body, created_at
       FROM memos
      WHERE id = ? AND user_id = ?`,
    [memoId, userId]
  );
}

/**
 * 메모를 생성한다.
 */
function createMemo(userId, title, body) {
  return db.run(
    `INSERT INTO memos (user_id, title, body, created_at)
     VALUES (?, ?, ?, datetime('now'))`,
    [userId, title, body]
  );
}

module.exports = { listMemos, getMemo, createMemo };

const express = require('express');
const service = require('./service');

const router = express.Router();

// 메모 목록 조회
router.get('/memos', async (req, res) => {
  const memos = await service.listMemos(req.user.id);
  res.json({ ok: true, data: memos });
});

// 메모 단건 조회
router.get('/memos/:id', async (req, res) => {
  const memo = await service.getMemo(req.user.id, req.params.id);

  if (!memo) {
    return res.status(404).json({ ok: false, error: 'MEMO_NOT_FOUND' });
  }

  res.json({ ok: true, data: memo });
});

// 메모 생성
router.post('/memos', async (req, res) => {
  const { title, body } = req.body;

  if (!title || !body) {
    return res.status(400).json({ ok: false, error: 'TITLE_AND_BODY_REQUIRED' });
  }

  const result = await service.createMemo(req.user.id, title, body);
  res.status(201).json({ ok: true, data: { id: result.lastID } });
});

module.exports = router;

[종료조건]
- GET /memos/search?q=키워드 로 호출된다
- 제목 또는 본문에 키워드가 포함된 메모만 반환한다
- 본인 메모만 반환한다
- q가 비어 있으면 400과 { ok: false, error } 를 반환한다
```

> 요약하지 마세요. 나중에 이 기록이 무엇이 결과를 만들었는지 확인하는 근거가 됩니다.

---

## 3. 결과 확인

### A
| | 확인 항목 | 결과 |
| :-: | :-- | :-- |
| ① | 실행 성공까지 걸린 시간 | 3분 |
| ② | 없는 함수·컬럼을 지어낸 개수 | 0개 (생성된 SQL 없음) |
| | → 지어낸 이름 | 없음 (백엔드 SQL 및 DB 컬럼 자체가 작성되지 않음) |
| ③ | `CONVENTIONS.md` 위반 개수 | 5개 |
| | → 무엇을 어겼는가 |  1. 계층 분리 미준수: routes.js,  service.js 계층 분리 없이 브라우저 클라이언트 JS 단일 파일로 작성됨 2.응답 형식 미준수: 규약된 { ok:true, data }, { ok: false, error }포맷 부재 3. 명명 규칙 미준수: list 등의 정해진 동사 함수명 대신 searchMemos 사용4. 입력 검증 미준수: 실패 시 400 에러 및 규약 에러 코드 반환 부재 5. 권한/SQL미준수: 백엔드 SQL 쿼리가 없으며, user_id를 통한 본인 데이터 제한 로직 부재 |
| ④ | 사람이 직접 고친 지점 | 0곳 |
| | → 어디를 어떻게 |없음 |
| ⑤ | **본인 메모만 반환되는가** | 아니오 (생성된 SQL 없음) |

### B
| | 확인 항목 | 결과 |
| :-: | :-- | :-- |
| ① | 실행 성공까지 걸린 시간 | 2분 |
| ② | 없는 함수·컬럼을 지어낸 개수 | 0개 |
| | → 지어낸 이름 | 정확히 사용 |
| ③ | `CONVENTIONS.md` 위반 개수 | 0개 |
| | → 무엇을 어겼는가 | 계층 분리, 에러 포맷, 동사,함수명 준수 |
| ④ | 사람이 직접 고친 지점 | 0곳 |
| | → 어디를 어떻게 | 없음 |
| ⑤ | **본인 메모만 반환되는가** | 예  |


### ⑤번을 반드시 확인하세요

생성된 SQL에 `user_id` 조건이 들어 있는지 보세요.

없다면 **코드는 정상 동작하지만 남의 메모까지 검색됩니다.** 에러도 나지 않습니다.

---

## 4. 두 조의 결과 비교

작업이 끝나면 두 조가 만든 코드를 나란히 놓고 함께 답하세요.

**4-1. 두 결과의 가장 큰 차이는 무엇입니까?**

```
가장 큰 차이는 '컨벤션(CONVENTIONS.md) 준수율'과 '기능의 완성도(백엔드/DB 로직 및 데이터 보안 구현 여부)'입니다.

1. 컨벤션 준수 및 품질: A조는 위반 항목이 5개에 달했으나, B조는 위반 항목이 0개로 컨벤션을 완벽히 준수했습니다.
2. 백엔드 및 DB 구현 여부: A조는 백엔드 SQL 및 DB 컬럼 자체를 생성하지 못하고 클라이언트 JS 단일 파일로만 작성되어 '본인 메모만 반환'하는 핵심 보안/비즈니스 로직(user_id 조건) 구현에 실패했습니다. 반면 B조는 정확한 함수/컬럼명을 사용하고 `user_id` 조건을 올바르게 포함하여 본인의 메모만 정확히 반환되도록 완성했습니다.
3. 소요 시간: B조(2분)가 A조(3분)보다 더 짧은 시간 안에 정확한 코드를 작성했습니다.
```

**4-2. A조의 실패는 모델 탓입니까, 우리가 주지 않은 탓입니까? 근거를 들어 적으세요.**

```
우리가 필요한 정보나 제약조건을 충분히 주지 않은 탓(프롬프트 및 컨텍스트 제공 미흡)입니다.

[근거]
1. 동일한 AI 모델 계열을 사용했음에도 불구하고, 컨벤션과 요구사항을 정확히 전달받은 B조는 0개의 위반과 완벽한 SQL 로직을 생성해 낸 반면, A조는 컨벤션을 5개나 위반했습니다.
2. A조의 위반 내용을 보면 계층 분리(routes/service), 응답 포맷({ ok: true }), 명명 규칙, 입력 검증, user_id 제한 등 프로젝트의 고유 규칙에 대한 지시를 전달받지 못해 단순한 클라이언트 단일 파일만 생성했습니다.
3. 따라서 모델의 능력이 부족했다기보다는, 모델이 따라야 할 프로젝트 맥락(CONVENTIONS.md 및 DB 스키마 등)을 사전에 명확히 주지 않았기 때문에 발생한 실패입니다.
```

**4-3. B조가 준 자료 중 결과를 가장 크게 바꾼 것 하나를 꼽는다면 무엇입니까? 왜 그렇게 생각합니까?**

```
'CONVENTIONS.md(코딩 및 아키텍처 규약 문서)'입니다.

[이유]
A조와 B조의 결정적인 차이는 단순 코드 동작 여부가 아니라 '프로젝트 구조(계층 분리), 응답 포맷, 명명 규칙, 보안/권한 조건(user_id 기반 데이터 제한)'을 지켰는가에 있습니다. 
A조는 이 규약이 없어 백엔드 레이어 자체를 누락하고 클라이언트 코드만 작성하는 치명적인 결과를 낳았지만, B조는 CONVENTIONS.md를 제공함으로써 AI가 백엔드 계층 분리부터 user_id 기반의 DB 쿼리 및 에러 포맷까지 완벽하게 인식하고 구현하도록 유도했습니다.
```

---

## 5. PROMPTS.md 기록

위 2번의 프롬프트 원문을 저장소의 `PROMPTS.md`에 추가하고 커밋하세요.

```markdown
## 2026-__-__ · 메모 검색 기능 (2주차 활동)

**지시**
(붙여넣은 프롬프트 원문)

**채택 여부**
(전체 채택 / 일부 채택 — 무엇을 어떻게 수정했는지 / 미채택)

**참고**
(있으면)
```

- [ ] `PROMPTS.md`에 추가하고 커밋했습니다

---

## 6. 제출 확인

- [ ] 이 활동지를 저장소에 커밋했습니다
- [ ] `PROMPTS.md`를 커밋했습니다
