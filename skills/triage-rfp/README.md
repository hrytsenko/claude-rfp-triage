# Triage RFP

This skill reads RFP or tender documentation, looks for known drivers of solution complexity, and reports the drivers found with their risk levels.

## Usage

```
/rfp-triage:triage-rfp <document-or-directory>...
```

Primary formats: PDF, DOCX, XLSX, and PPTX. The agent may convert documents to text with tooling of its choice.

## Output

- **Executive Summary** — the overall risk verdict (Manageable, Concerning, Dangerous, or Prohibitive) and how the drivers found combine to justify it.
- **Complexity Drivers** — each driver found with its risk level (High or Critical), exact findings with document locations, and the complexity they add. Drivers absent from the documentation are not listed.
- **Sources** — the documents analyzed.

## Drivers

Drivers, risk levels, and overall risk verdicts are defined in `references/COMPLEXITY_DRIVERS.md`.
