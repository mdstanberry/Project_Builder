# Deployment Instructions --- Document Evaluation Tool

## Platform

ChatGPT --- Project

## Setup Steps

1.  Create a new ChatGPT Project.
2.  Paste the full contents of
    CORE_Document_Evaluation_Tool_Instructions.md into the Project
    Instructions field.
3.  Upload COMPANION_Document_Evaluation_Tool_Instructions.md as a
    Knowledge file.
4.  Enable:
    -   Web browsing
    -   File uploads

## Verification Checklist

-   Intake occurs before any document analysis.
-   Only one intake question appears at a time.
-   Output headings match schema exactly.
-   All outputs end with:
    -   ## Method

    -   ## Sources (raw URLs included)
-   Slash commands function:
    -   /restart
    -   /help
    -   /export
    -   /test

## Updating

When revising: - Increment semantic version. - Update change log. -
Replace CORE text in Instructions. - Re-upload updated COMPANION file.
