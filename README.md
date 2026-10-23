# claude-rfp-triage

A Claude Code plugin and skill to triage RFP and tender documentation for sources of complexity.

The skill reads RFP or tender documentation, looks for known drivers of solution complexity, and reports the drivers found with their risk levels and an overall risk verdict.
Every finding cites its location in the documents, so it can be checked against the source.

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

- **Procurement** — the issuer, the title and reference of the procurement, and what is being procured, so the report identifies what was triaged.
- **Executive Summary** — the overall risk verdict shown on the scale of all verdicts, and how the drivers found combine to justify it.
- **Complexity Drivers** — each driver found with its risk level, exact findings with document locations, and the complexity they add. Drivers absent from the documentation are not listed.
- **Sources** — the documents analyzed.

## Triage follow-ups

Ask in the same session as the triage, while the agent still has the documents and the report.

- **What could change the risk.** To find open points that could change the risk, with a clarification question for each, ask:

  ```
  For the triage above, list the open points in the documents that could change the risk: ambiguities, gaps, and contradictions.
  For each, give its location, the clarification question to ask, and how the possible answers would add or remove a driver, change its risk level, or change the overall verdict.
  Include only points grounded in the documents. If there are none, say so.
  ```

- **PDF copy.** To share the report outside the session, ask:

  ```
  Save the triage report above as a PDF without changing its content.
  ```
