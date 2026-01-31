# Deployment Instructions Template
**Template Version:** v1.2.0-template  
**For use with:** Project Builder generated instruction files
**Change Log:** See `COMPANION_ProjectBuilder_Instructions.md` (Section: Change log)

---

This template is used by the Project Builder to generate customized deployment instructions. Placeholders (marked with `{{PLACEHOLDER}}`) are replaced with project-specific values during generation.

---

## Deployment Instructions — {{PROJECT_NAME}}

### 1. Overview

These instructions explain how to deploy your **{{PROJECT_NAME}}** instruction files to {{PLATFORM_NAME}}.

**Files to deploy:**
- `CORE_{{PROJECT_NAME}}_Instructions.md` — Governance and constraints
- `COMPANION_{{PROJECT_NAME}}_Instructions.md` — Execution logic
{{#IF_KNOWLEDGE_FILES}}
- Knowledge files: {{KNOWLEDGE_FILE_LIST}}
{{/IF_KNOWLEDGE_FILES}}

---

### 2. Platform Setup

{{#IF_CHATGPT}}
#### ChatGPT Project Setup

1. **Open ChatGPT** at chat.openai.com
2. **Navigate to Projects** (sidebar or menu)
3. **Create new Project** or select existing one
4. **Go to Project Settings**
5. **Upload instruction files:**
   - Click "Add files" or drag-and-drop
   - Upload `CORE_{{PROJECT_NAME}}_Instructions.md` first
   - Upload `COMPANION_{{PROJECT_NAME}}_Instructions.md` second
6. **Set custom instructions** (if platform requires separate text):
   - Copy the CORE file contents into the system instructions field
   - Or reference the uploaded file

{{#IF_KNOWLEDGE_FILES}}
7. **Upload knowledge files:**
   - Add each knowledge file listed above
   - Verify files are properly indexed
{{/IF_KNOWLEDGE_FILES}}

{{#IF_WEB_SEARCH}}
8. **Enable web search:**
   - Go to Project capabilities
   - Toggle on "Web browsing" or "Search"
{{/IF_WEB_SEARCH}}

9. **Save and test**
{{/IF_CHATGPT}}

{{#IF_CLAUDE}}
#### Claude Project Setup

1. **Open Claude** at claude.ai
2. **Navigate to Projects** (sidebar)
3. **Create new Project** or select existing one
4. **Add project instructions:**
   - Click "Set instructions" or "Edit project"
   - Upload or paste CORE file contents
5. **Add knowledge files:**
   - Click "Add content" or "Upload files"
   - Upload `COMPANION_{{PROJECT_NAME}}_Instructions.md`
{{#IF_KNOWLEDGE_FILES}}
   - Upload each knowledge file
{{/IF_KNOWLEDGE_FILES}}

{{#IF_WEB_SEARCH}}
6. **Note on web search:**
   - Claude Projects support web search when available
   - If not available, the Project will note limitations
{{/IF_WEB_SEARCH}}

7. **Save and test**
{{/IF_CLAUDE}}

---

### 3. File Upload Order

Upload files in this specific order for best results:

1. **CORE file first** — Establishes governance
2. **COMPANION file second** — Provides execution logic
3. **Knowledge files** — Reference materials (if applicable)

**Why order matters:** The AI reads files in order. CORE should be processed first to establish rules before execution logic.

---

### 4. Knowledge File Configuration

{{#IF_KNOWLEDGE_FILES}}
Your Project uses these knowledge files:

| File | Purpose | Update Frequency |
|------|---------|------------------|
{{KNOWLEDGE_FILE_TABLE}}

**Configuration tips:**
- Ensure files are in readable formats (MD, TXT, PDF)
- Keep files under platform size limits
- Update files when source information changes
{{/IF_KNOWLEDGE_FILES}}

{{#IF_NO_KNOWLEDGE_FILES}}
Your Project does not require knowledge files. If you add them later:
1. Reference them in the CORE file under "Operating file names"
2. Update the COMPANION file if they affect execution logic
{{/IF_NO_KNOWLEDGE_FILES}}

---

### 5. Test Cases

Run these tests to verify your Project works correctly:

#### T-01: Basic Functionality
**Action:** Start a new conversation and give a simple request related to {{PROJECT_PURPOSE}}.  
**Expected:** Project responds appropriately within its defined scope.

{{#IF_INTAKE}}
#### T-02: Intake Process
**Action:** Start a new conversation.  
**Expected:** Project asks the first intake question before providing main functionality.

#### T-03: Intake Completion
**Action:** Complete all intake questions.  
**Expected:** Project transitions to main functionality after last intake question.

#### T-04: Skip Attempt
**Action:** During intake, try to skip ahead (e.g., "Just give me the answer").  
**Expected:** Project explains it needs to gather information first and continues intake.
{{/IF_INTAKE}}

#### T-05: Boundary Respect
**Action:** Ask for something outside the Project's scope (based on prohibitions).  
**Expected:** Project politely declines and explains its limitations.

#### T-06: Output Format
**Action:** Request a typical task from the Project.  
**Expected:** Response follows the configured output style ({{OUTPUT_STYLE}}).

{{#IF_COMMANDS}}
#### T-07: Command Routing
**Action:** Try each configured command: {{COMMAND_LIST}}  
**Expected:** Each command triggers its defined behavior.
{{/IF_COMMANDS}}

{{#IF_WEB_SEARCH}}
#### T-08: Web Search
**Action:** Ask a question requiring current information.  
**Expected:** Project searches the web and cites sources.
{{/IF_WEB_SEARCH}}

---

### 6. Troubleshooting

#### Project ignores instructions
- **Check file upload:** Verify all files uploaded successfully
- **Check file format:** Ensure files are plain text/markdown
- **Re-upload:** Remove and re-add files
- **Platform cache:** Start a new conversation

#### Intake not working
- **Check COMPANION:** Verify intake sequence is defined
- **Check CORE:** Verify determinism rules reference intake
- **Test fresh:** Start completely new conversation

#### Wrong output format
- **Check CORE:** Verify output rules section
- **Check COMPANION:** Verify output contracts match expectations

#### Knowledge files not referenced
- **Check file names:** Must match exactly what's in CORE
- **Check file format:** PDFs may not be searchable
- **Re-upload:** Try converting to markdown/text

#### Commands not recognized
- **Check COMPANION:** Verify command routing section
- **Exact syntax:** Commands typically need exact match (e.g., `/restart` not `restart`)

---

### 7. Maintenance and Updates

#### Making changes manually
1. Edit the relevant file (CORE or COMPANION)
2. Increment the version number
3. Add a change log entry
4. Re-upload the updated file
5. Run test cases to verify

#### Using Project Builder for revisions
Instead of editing files manually, you can use the Project Builder to make changes:
1. Start a new chat with Project Builder
2. Select "Revise an existing Project"
3. Upload your current CORE and COMPANION files
4. Describe the changes you need
5. Review the revision plan
6. Approve and download updated files

This method ensures proper version increments and change log entries.

#### Version tracking
- Current CORE version: {{CORE_VERSION}}
- Current COMPANION version: {{COMPANION_VERSION}}

#### When to update CORE vs COMPANION
- **CORE:** Rules, constraints, prohibitions, definitions
- **COMPANION:** Workflows, sequences, execution logic, templates

---

### 8. Quick Reference

| Item | Value |
|------|-------|
| Project Name | {{PROJECT_NAME}} |
| Platform | {{PLATFORM_NAME}} |
| CORE File | `CORE_{{PROJECT_NAME}}_Instructions.md` |
| COMPANION File | `COMPANION_{{PROJECT_NAME}}_Instructions.md` |
| Has Intake | {{HAS_INTAKE}} |
| Has Web Search | {{HAS_WEB_SEARCH}} |
| Output Style | {{OUTPUT_STYLE}} |

---

## Appendix: Placeholder Reference

When generating deployment instructions, replace these placeholders:

| Placeholder | Description |
|-------------|-------------|
| `{{PROJECT_NAME}}` | Name of the user's project |
| `{{PLATFORM_NAME}}` | ChatGPT Project, Claude Project, or Both |
| `{{PROJECT_PURPOSE}}` | One-line description of project purpose |
| `{{OUTPUT_STYLE}}` | Brief, Moderate, or Verbose |
| `{{CORE_VERSION}}` | Version from generated CORE file |
| `{{COMPANION_VERSION}}` | Version from generated COMPANION file |
| `{{HAS_INTAKE}}` | Yes or No |
| `{{HAS_WEB_SEARCH}}` | Yes or No |
| `{{COMMAND_LIST}}` | Comma-separated list of commands |
| `{{KNOWLEDGE_FILE_LIST}}` | List of knowledge file names |
| `{{KNOWLEDGE_FILE_TABLE}}` | Markdown table of knowledge files |

Conditional blocks:
- `{{#IF_CHATGPT}}...{{/IF_CHATGPT}}` — Include for ChatGPT Projects
- `{{#IF_CLAUDE}}...{{/IF_CLAUDE}}` — Include for Claude Projects
- `{{#IF_KNOWLEDGE_FILES}}...{{/IF_KNOWLEDGE_FILES}}` — Include if knowledge files used
- `{{#IF_NO_KNOWLEDGE_FILES}}...{{/IF_NO_KNOWLEDGE_FILES}}` — Include if no knowledge files
- `{{#IF_INTAKE}}...{{/IF_INTAKE}}` — Include if intake process defined
- `{{#IF_WEB_SEARCH}}...{{/IF_WEB_SEARCH}}` — Include if web search enabled
- `{{#IF_COMMANDS}}...{{/IF_COMMANDS}}` — Include if custom commands defined
