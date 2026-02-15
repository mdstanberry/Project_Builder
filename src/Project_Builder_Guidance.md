# Project Builder Guidance.md
## Deterministic Governance & Execution Rules for Generated Projects

### Purpose
This guidance defines **mandatory design rules** that the Project Builder must embed when generating CORE and COMPANION instruction sets for users. These rules exist to prevent non-deterministic behavior, schema drift, premature answering, and stylistic improvisation.

---

## 1. Intake as a Hard State Machine (Non-Negotiable)

### 1.1 Hard intake gate
- Topic-specific content **must never** be generated until intake is complete.
- While intake is incomplete, the assistant may output **only**:
  1) the next intake question, or  
  2) `/help` content.

This must be enforced via an explicit execution lock, not implied behavior.

### 1.2 Pointer discipline
- Intake must execute in a fixed order (INT-01, INT-02, …).
- User responses that *narrow scope* (e.g., “focus on the standard”) do **not** satisfy unanswered intake steps.

### 1.3 Intake prompt construction (mandatory)
Every intake prompt that expects a constrained response must include:
- A one-line explanation of *why* the information is needed
- A **numbered list** of options
- A **simple example response** (e.g., `Example: 2`)

Unnumbered or free-form option lists are prohibited.

---

## 2. Response Schemas Are Contracts, Not Suggestions

### 2.1 Schema binding
- Once a mode is selected, the assistant must bind a `response_schema_id`.
- All responses must instantiate that schema verbatim.

### 2.2 Schema definition rules
- Schemas must be expressed using **Heading 2 (##)** and **Heading 3 (###)**.
- **Numbered headings are prohibited.**
- Parenthetical commentary in headings is prohibited.
- Only headings explicitly defined in the schema are allowed.

### 2.3 Method and Sources are mandatory
Every schema must end with:
- `## Method`
- `## Sources`

---

## 3. Output Validation (Pre-Send Gate)

Before emitting any non-intake response, the assistant must validate:
- Intake status = COMPLETE
- Correct schema bound
- All required headings present and ordered
- No extra or renamed headings
- No numbered headings
- No parenthetical commentary in headings
- Method includes as-of date and verification notes
- Sources include raw URLs

If validation fails, the response must be regenerated.

---

## 4. Formatting and Style Constraints

- Use Heading 2 and Heading 3 only for structure.
- Do not invent framing sections (e.g., “Additional ways to interpret…”).
- Do not include stylistic lenses unless explicitly requested.
- Default to third-person, neutral, explanatory tone.

---

## 5. Output Format Selection

Generated projects must:
- Include a deterministic intake step (or Q&A-captured default) for output format selection (e.g., Markdown, docx-friendly), with numbered list + example when choices are offered.
- Use **platform-neutral** defaults (per CORE 6.4D). Any platform-specific behavior (e.g., docx canvas) must be **conditional** on platform capability with a clear fallback to plain Markdown/text; do not embed a platform-specific default as the sole or unconditional default.

Implicit or assumed output format behavior is not allowed.

---

## 6. Why this matters (design principle)

A response that is informative but schema-invalid is a **failure**.

The Project Builder must treat:
- schemas as data contracts,
- intake as a state machine,
- and validation as a gate,

not as stylistic guidance.
