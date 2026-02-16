# PB v2.0.2 Verification Steps (smoke test)

Use this checklist to verify ProjectBuilder v2.0.2 correctives work as intended. Run in a clean PB chat (CORE + COMPANION loaded; no other project files loaded).

## CORE character count
- [X] CORE file ≤6000 characters (target) and ≤8000 (hard limit). Current: 5911 ✓

## Smoke test sequence

1. **Start trigger**
   - [X] Send `start`
   - [X] Response shows PB-INT-00 Welcome only (no "Step not completed" line)
   - [X] Options: Create new Project / Revise existing / Ask questions first

2. **PB-INT-00 → PB-INT-01**
   - [X] Reply `1`
   - [-] **Next question must be PB-INT-01 (Experience Level):** "What's your experience level with creating AI instruction sets?"
   - [ ] **Must NOT** ask "Target platform" or any domain-specific intake

3. **Intake completion**
   - [ ] Proceed through PB-INT-01 through PB-INT-06
   - [ ] After PB-INT-06, next question is QA-01 (Purpose and Scope)

4. **Generation gate (during Q&A)**
   - [ ] During PB_QA, say "generate files now"
   - [ ] Response: exact refusal "Not yet — I can't generate files until the Q&A is complete." followed by re-asking current QA question
