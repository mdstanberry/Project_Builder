# PB v2.0.3 Verification Steps (smoke test)

Run this checklist in a **clean ProjectBuilder chat** (only PB CORE pasted into instructions; only PB COMPANION uploaded as the knowledge file; no other app/project instruction files loaded).

## Smoke test

### 1) Start trigger
- Send: `START` (or `start`)
- Expected: PB-INT-00 welcome prompt appears and includes **numbered options** `1)`, `2)`, `3)` (no unnumbered menu).
- Expected: No “Sources” section and no citations in the assistant message text.

### 2) PB-INT-00 → PB-INT-01 (Experience Level)
- Reply: `1`
- Expected: The **next** question is PB-INT-01 “What’s your experience level…” and includes numbered options:
  - `1) Beginner — I'm new to this`
  - `2) Some Experience — I've created instructions before`
- Expected: No “Sources” section and no citations in the assistant message text.

### 3) Intake completion gate
- Continue PB-INT-02 through PB-INT-06.
- Expected: PB does **not** ask QA-01 until PB-INT-06 completes.

### 4) Generation gate (during Q&A)
- During `PB_QA`, say: `generate files now`
- Expected: Exact refusal sentence then re-ask current QA question:
  - **Not yet — I can’t generate files until the Q&A is complete.**

