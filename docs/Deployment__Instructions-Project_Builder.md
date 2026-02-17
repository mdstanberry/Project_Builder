# Deployment Instructions — Project Builder
**Applies to:** `CORE_ProjectBuilder_Instructions.md` (v2.0.3-core) + `COMPANION_ProjectBuilder_Instructions.md` (v2.0.3-companion)  
**Effective date:** 2026-02-16  

---

## Overview

These instructions explain how to deploy **Project Builder** into your chosen platform(s) without changing the platform-neutral CORE and COMPANION content.

## Files to deploy

- **Paste into platform instructions (CORE only):**
  - `docs/CORE_ProjectBuilder_Instructions.md`
- **Upload as knowledge files (do not paste):**
  - `docs/COMPANION_ProjectBuilder_Instructions.md`
  - `docs/Deployment_Instructions_Template.md`

## Deployment placement rule (all platforms) (authoritative)

- **CORE is the only content pasted** into the platform’s **Project Instructions / System Instructions** field.
- **COMPANION is never pasted** into the instructions field. It must be **uploaded as a knowledge file**.
- `Deployment_Instructions_Template.md` must be **uploaded as a knowledge file** (Project Builder uses it to generate customized deployment instructions for new projects).

## Pre-flight checks (recommended)

### Confirm the files exist

Run this in **PowerShell on Windows**, in your repo folder `Project_Builder`.

This command lists the three required files so you can confirm paths and names.

```powershell
Get-Item .\docs\CORE_ProjectBuilder_Instructions.md, .\docs\COMPANION_ProjectBuilder_Instructions.md, .\docs\Deployment_Instructions_Template.md
```

### Check CORE size (important for ChatGPT/Gemini/Copilot)

Run this in **PowerShell on Windows**, in your repo folder `Project_Builder`.

This command prints the CORE character count so you can confirm it is within platform limits (hard limit: **8000 characters**).

```powershell
(Get-Content -Raw .\docs\CORE_ProjectBuilder_Instructions.md).Length
```

## Platform setup

### ChatGPT — Project

1. Create a new **ChatGPT Project** (or open an existing one).
2. Open the Project’s **Instructions** (or “Project instructions”) field.
3. **Paste CORE only**:
   - Paste the full contents of `docs/CORE_ProjectBuilder_Instructions.md`
4. Open **Project files** (knowledge/files area).
5. **Upload knowledge files**:
   - Upload `docs/COMPANION_ProjectBuilder_Instructions.md`
   - Upload `docs/Deployment_Instructions_Template.md`
6. Save.

### ChatGPT — Custom GPT

1. Create or edit a **Custom GPT**.
2. In the **Instructions** field, **paste CORE only**:
   - Paste the full contents of `docs/CORE_ProjectBuilder_Instructions.md`
3. In **Knowledge** (files), **upload**:
   - `docs/COMPANION_ProjectBuilder_Instructions.md`
   - `docs/Deployment_Instructions_Template.md`
4. Save/update the GPT.

### Claude — Project

1. Create or open a **Claude Project**.
2. In **Project instructions**, **paste CORE only**:
   - Paste the full contents of `docs/CORE_ProjectBuilder_Instructions.md`
3. In **Project knowledge / documents**, **upload**:
   - `docs/COMPANION_ProjectBuilder_Instructions.md`
   - `docs/Deployment_Instructions_Template.md`
4. Save.

### Gemini — GEMS

1. Create or edit a **GEM**.
2. In the **Instructions** area, **paste CORE only**:
   - Paste the full contents of `docs/CORE_ProjectBuilder_Instructions.md`
3. In the **knowledge/files/sources** area (whatever Gemini calls it), **upload**:
   - `docs/COMPANION_ProjectBuilder_Instructions.md`
   - `docs/Deployment_Instructions_Template.md`
4. Save.

### Microsoft Copilot — Agent

1. Create or edit an **Agent** (Copilot Studio or your organization’s Copilot agent tool).
2. In **System instructions** (or equivalent), **paste CORE only**:
   - Paste the full contents of `docs/CORE_ProjectBuilder_Instructions.md`
3. In **Knowledge / resources / files**, **upload**:
   - `docs/COMPANION_ProjectBuilder_Instructions.md`
   - `docs/Deployment_Instructions_Template.md`
4. Save.

---

## Verification tests (smoke tests)

Run these after deployment to confirm Project Builder behavior matches the CORE/COMPANION rules.

### T-01 Start trigger works (PB intake starts cleanly)

**Action:** Start a new conversation and send:
- `start`

**Expected:**
- You see the **PB-INT-00 Welcome** prompt with options `1)`, `2)`, `3)`.
- It does **not** ask any other questions in the same message.

### T-02 One-question rule (intake does not “double ask”)

**Action:** Reply `1` (Create a new Project).  

**Expected:**
- It asks only the **Experience Level** question next (with options `1)` and `2)`).

### T-03 No “Sources” during PB intake / Q&A

**Action:** Continue intake for 1–2 questions.  

**Expected:**
- No “## Sources” section appears during PB intake or PB Q&A.
- No citations appear during PB intake or PB Q&A.

### T-04 `/help` is non-destructive and re-asks the current question

**Action:** During intake, type:
- `/help`

**Expected:**
- It shows a short help text, then re-asks the same current intake question (so you can still answer it).

### T-05 File-generation gating works

**Action:** During intake or PB Q&A, try:
- “Generate the files now.”

**Expected:**
- It does not generate CORE/COMPANION/deployment files early, and it continues with the current required question.

### T-06 Deployment instructions use the template

**Action:** Complete a small end-to-end build (intake + Q&A) for a tiny example project, then ask to proceed until it generates deployment instructions.  

**Expected:**
- The generated deployment instructions include platform sections and repeat the placement rule: **paste CORE only, upload COMPANION as knowledge**.

---

## Troubleshooting

### It ignores the rules or seems inconsistent

- Start a **brand new conversation** and run T-01 again (`start`).
- Confirm only CORE is in the platform instructions field (no COMPANION pasted there).
- Re-upload `docs/COMPANION_ProjectBuilder_Instructions.md` and `docs/Deployment_Instructions_Template.md` as knowledge files.

### It cannot generate deployment instructions or “forgets” the template

- Confirm `docs/Deployment_Instructions_Template.md` is uploaded as a knowledge file.
- If the platform has multiple “knowledge” areas, ensure it is uploaded to the one your agent/project can actually read.

---

## Updating Project Builder later

When you revise Project Builder:

- Update the files in your repo (CORE and/or COMPANION).
- Increment semantic versions as required (COMPANION Section A and CORE rules).
- In your platform:
  - Replace the pasted **CORE** text in the instructions field.
  - Re-upload the updated **COMPANION** file and the updated template file (if it changed).

