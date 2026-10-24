# claude-rfp-triage

A Claude Code plugin to triage RFP and tender documentation for sources of complexity.

The triage reads RFP or tender documentation, looks for known drivers of solution complexity, and reports the drivers found with their risk levels and an overall risk verdict.
Every finding cites its location in the documents, so it can be checked against the source.
After the triage, you can find the levers that could reduce the risk, with the questions to ask the customer, and export the report as a PDF to share.

## Install

```
/plugin marketplace add hrytsenko/claude-rfp-triage
/plugin install rfp-triage@claude-rfp-triage
```

## Usage

```
/rfp-triage:triage-rfp <document-or-directory>...
```

Pass one or more documents, or directories that contain them.

```
/rfp-triage:clarify-rfp
```

Run it after the triage, in the same session, to find what to clarify with the customer to reduce the risk.

```
/rfp-triage:export-pdf <language>
```

Run it after the triage, in the same session, to save the report as a PDF to share.
If you found levers, they are included.
Optionally, pass a language to translate the report.

## Before you run

- **Model.** Use a high-tier model at high reasoning effort or above.
  The skill states goals and definitions and leaves the judgment to the model, so the quality of the triage depends on it.
- **Input.** Provide a curated set: every document that defines the scope, including annexes, addenda, and clarifications, and nothing else.
  Primary formats are PDF, DOCX, XLSX, and PPTX.
  The agent treats every document as relevant and reads each one in full, so unrelated files skew the findings and add time and cost, while missing ones make the triage misleading.
- **Limits.** Consider your team's capacity and experience separately.
  The triage judges only what the documents require, so it informs the bid decision rather than making it.

## Complexity drivers

- **Complexity Driver.** A known source of solution complexity, such as on-premises hosting, legacy integrations, strict availability targets, or mandatory security frameworks.
  It counts only in its troublesome form: hosting on managed cloud services, for example, is not a driver.
- **Risk Level.** Only High or Critical, since every driver found adds complexity: High adds effort and uncertainty, Critical may jeopardize delivery or the bid itself.
- **Overall Risk.** A verdict on how the drivers combine, not the highest level among them.
  From least to most severe: Predictable (a regular bid process absorbs them), Challenging (needs attention in the bid), Uncertain (needs due diligence before bidding), Unrealistic (infeasible as specified).

Full definitions are in [COMPLEXITY_DRIVERS.md](skills/triage-rfp/references/COMPLEXITY_DRIVERS.md).

## Triage report

- **Procurement** — the customer, the title and reference of the procurement, and what is being procured, so the report identifies what was triaged.
- **Executive Summary** — the overall risk verdict shown on the scale of all verdicts, and how the drivers found combine to justify it.
- **Complexity Drivers** — each driver found with its risk level, exact findings with document locations, and the complexity they add. Drivers absent from the documentation are not listed.
- **Sources** — the documents analyzed, each with its role in the procurement.

## Complexity levers

- **Constraint** — the scope, obligation, or dependency to bound, pin down, or shift to the customer.
- **Question** — the clarification question to ask the customer.
- **Assumption** — the answer that favors the bid, stated so that the bid can adopt it if the question goes unanswered.
- **Impact** — what the assumption would relieve if it holds.
- **Likelihood** — how likely the customer is to confirm the assumption.
- **Findings** — the findings of the triage report that the lever acts on.

## PDF report

- **First page** — the procurement, the executive summary, and a table of the drivers found with their risk levels.
- **Following pages** — the complexity drivers, each with its summary set apart in a block, then the complexity levers, if any, each with its question and assumption set apart in a block.
- **Last page** — the sources.

The content is that of the triage report and the levers, unchanged except for translation: quotes from the documents stay in their original language.
Risk levels and verdicts share one color scale by severity, and are always shown with their names.
