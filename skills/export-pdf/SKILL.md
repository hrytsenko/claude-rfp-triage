---
name: export-pdf
description: Export the triage report produced by triage-rfp as a formal PDF, optionally translated into another language. Use after triage-rfp when asked to save, export, or share the triage report as a PDF.
argument-hint: <language>
---

## Instructions

You are exporting the triage report produced by the `triage-rfp` skill as a formal PDF for readers outside this session.
Follow each step below in order. Work through the steps silently: do not narrate your process.
Your only output should be the path to the PDF, or the specified error message if a step instructs you to stop.

### Step 1 — Find the report

Use the latest version of the triage report in this conversation. If there is none, tell the user "Run /rfp-triage:triage-rfp first." and stop.
Export only the triage report, not follow-ups or other content of the conversation.
The content of the report is final: do not add, remove, or reword anything, except as Step 2 and Step 3 allow.

### Step 2 — Choose the language

If `$ARGUMENTS` names a language, translate the report into it. Otherwise, keep the language of the report.
Translation is the only change allowed to the content:

- Keep quotes from the documents verbatim, in their original language: they are the evidence.
- Keep document names, locations, and requirement IDs as they are.
- Translate headings, labels, driver names, risk levels, and verdicts, using the same term for each throughout.

### Step 3 — Lay out the PDF

The PDF is formal and concise. Add no text of your own beyond page numbers and the export date.

- **First page** holds the title, the Procurement and Executive Summary sections with the verdict scale, and a table of the drivers found with their risk levels, in the order of the report. It must fit on one page.
- **Complexity Drivers** start on the second page. Set each driver's summary of why it has its level apart in a highlighted block, so that drivers are easy to recognize.
- **Sources** start on a new page after the drivers.

Risk levels and verdicts share one color scale by severity, and each has the same color wherever it appears:

- Predictable — green
- Challenging, High — amber
- Uncertain — orange
- Unrealistic, Critical — red

Use muted shades that suit a formal document, and always show the name with the color, so that the PDF reads correctly in grayscale.

### Step 4 — Produce the PDF

Produce the PDF with suitable tooling.
Save it in the working directory, named after the procurement reference and the language of the report.
Before handing it over, check that it renders as laid out in Step 3 and that every character renders correctly in its language. If not, fix it and produce the PDF again.
