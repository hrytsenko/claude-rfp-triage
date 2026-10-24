---
name: export-report
description: Export the triage report produced by triage-rfp, with the levers produced by clarify-rfp if any, as a formal PDF or DOCX document, optionally translated into another language. Use after triage-rfp when asked to save, export, or share the triage report as a PDF or Word document.
argument-hint: <language-or-format>...
---

## Instructions

You are exporting the triage report produced by the `triage-rfp` skill as a formal document for readers outside this session.
Follow each step below in order. Work through the steps silently: do not narrate your process.
Your only output should be the path to the document, or the specified error message if a step instructs you to stop.

### Step 1 — Find the report

Use the latest version of the triage report in this conversation. If there is none, tell the user "Run /rfp-triage:triage-rfp first." and stop.
If the conversation also has complexity levers produced by `clarify-rfp` for this report, export them as part of the report.
Export nothing else from the conversation, such as follow-ups.
The content of the report is final: do not add, remove, or reword anything, except as Step 2 and Step 3 allow.

### Step 2 — Choose the format and language

`$ARGUMENTS` may name a format, a language, or both.

The format is PDF or DOCX. If `$ARGUMENTS` names no format, use PDF. If it names another format, tell the user "Supported formats are PDF and DOCX." and stop.

If `$ARGUMENTS` names a language, translate the report into it. Otherwise, keep the language of the report.
Translation is the only change allowed to the content:

- Keep quotes from the documents verbatim, in their original language: they are the evidence.
- Keep document names, locations, and requirement IDs as they are.
- Translate headings, labels, driver names, risk levels, and verdicts, using the same term for each throughout.

### Step 3 — Lay out the document

The document is formal and concise. Add no text of your own beyond page numbers and the export date.

- **First page** holds the title, the Procurement and Executive Summary sections with the verdict scale, and a table of the drivers found with their risk levels, in the order of the report. It must fit on one page.
- **Complexity Drivers** start on the second page. Set each driver's summary of why it has its level apart in a highlighted block, so that drivers are easy to recognize.
- **Complexity Levers**, if any, start on a new page after the drivers. Set each lever's question and assumption apart in a highlighted block, so that what to ask and what to assume are easy to find.
- **Sources** start on a new page at the end.

Risk levels and verdicts share one color scale by severity, and each has the same color wherever it appears:

- Predictable — green
- Challenging, High — amber
- Uncertain — orange
- Unrealistic, Critical — red

Use muted shades that suit a formal document, and always show the name with the color, so that the document reads correctly in grayscale.

A DOCX is laid out by the application that opens it, and its readers may edit it: build its layout so that it holds in common word processors and survives editing.

### Step 4 — Produce the document

Produce the document with suitable tooling.
Save it in the working directory, named after the procurement reference and the language of the report.
Before handing it over, check that it renders as laid out in Step 3 and that every character renders correctly in its language. If not, fix it and produce the document again.
