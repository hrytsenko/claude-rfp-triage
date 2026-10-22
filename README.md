# claude-rfp-triage

A Claude Code plugin and skill to triage RFP and tender documentation for sources of complexity.

The skill reads RFP or tender documentation, looks for known drivers of solution complexity, and reports the drivers found with their risk levels.

## Install

```
/plugin marketplace add hrytsenko/claude-rfp-triage
/plugin install rfp-triage@claude-rfp-triage
```

## Usage

```
/rfp-triage:triage-rfp <document-or-directory>...
```

## Before you run

- **Model.** The skill is written for high-tier models at high reasoning effort or above.
  It states goals and definitions and leaves the judgment to the model, so the quality of the triage depends on it.
- **Input.** Provide a curated set: every document that defines the scope, including annexes, addenda, and clarifications, and nothing else.
  Primary formats are PDF, DOCX, XLSX, and PPTX.
  The agent treats every document as relevant and reads each one in full, so unrelated files skew the findings and add time and cost, while missing ones make the triage misleading.

## Output

- **Executive Summary** — the overall risk verdict (Predictable, Challenging, Uncertain, or Unrealistic) shown on the scale of all verdicts, and how the drivers found combine to justify it.
- **Complexity Drivers** — each driver found with its risk level (High or Critical), exact findings with document locations, and the complexity they add. Drivers absent from the documentation are not listed.
- **Sources** — the documents analyzed.

## Drivers

Drivers, risk levels, and overall risk verdicts are defined in [COMPLEXITY_DRIVERS.md](skills/triage-rfp/references/COMPLEXITY_DRIVERS.md).
