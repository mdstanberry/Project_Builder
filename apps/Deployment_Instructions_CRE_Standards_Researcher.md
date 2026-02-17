# Deployment Instructions --- CRE Standards Researcher

## Platform

ChatGPT --- Project or Custom GPT  
Claude --- Project  
Gemini --- GEMS  
Microsoft Copilot --- Agent  

## Setup Steps

1.  Create a new Project / GPT / GEM / Agent (platform of your choice).
2.  Paste the full contents of `CORE_CRE_Standards_Researcher_Instructions_v1.3.0.md` into the main **Instructions** / **System prompt** field.
3.  Upload or attach `COMPANION_CRE_Standards_Researcher_Instructions_v1.3.0.md` as a **Knowledge** file (or the closest equivalent in your platform UI).
4.  Enable:
    -   Web browsing / Internet access

## Verification Checklist

-   Intake occurs before any research content (no topic output until intake is complete).
-   Only one intake question appears at a time (one-question rule).
-   Intake prompts match the COMPANION verbatim blocks (numbering preserved).
-   After intake completes, outputs:
    -   Use only `##` and `###` headings (no numbered headings).
    -   Match the selected schema exactly (no extra headings).
    -   End with:
        -   `## Method`
        -   `## Sources`
-   Sources are accessible citations (raw URLs where applicable), and the assistant does not claim clause-level requirements without accessible citations.

## Updating

When revising:
-   Increment semantic version in CORE and COMPANION (and update effective date).
-   Replace the CORE text in the platform instructions field.
-   Re-upload the updated COMPANION knowledge file.
