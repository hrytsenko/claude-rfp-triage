# AGENTS.md

Guidance for agents working on this repository.

## Design decisions

### Strong models are expected

The skills are meant to be executed by strong models with high reasoning effort, and they rely on their judgment.
The `triage-rfp` skill states the goal, the drivers, the risk levels, and the report format, and leaves the reasoning to the agent: how to apply a driver's definition, which edge cases to handle, and how to read and organize the documents.
The `clarify-rfp` skill states what a lever is, how to rank levers, and the output format, and leaves the reasoning to the agent: which levers to choose, how to phrase the questions and assumptions, and how to judge their impact and likelihood.
The `export-report` skill states the page layout, the color scale, and the limits on changing the report, and leaves the typography and page composition to the agent.

Do not add rules, thresholds, checklists, or examples that steer the agent where a strong model can decide on its own.
Explicit rules override the agent's judgment even when it would reason better, so add one only when it states an intent that cannot be inferred, such as a calibration choice or a scope boundary.

### Triage and clarification are separate skills

`triage-rfp` only identifies the complexity drivers and their risk; `clarify-rfp` finds the levers that could reduce it, working from the finished report.
Identifying drivers takes the agent's full attention, since it reads every document in full and checks every statement against every driver, and looking for levers in the same pass would divert attention from that.
The separation also keeps the risk assessment neutral: the triage states what the documents require, while levers argue for the bid, and an agent looking for ways to reduce a risk tends to rate it lower.

For the same reason, `clarify-rfp` works from the report alone and does not consult the drivers reference.
The report already explains why each driver adds complexity, why it has its risk level, and how the drivers combine into the overall risk, and these explanations are what levers act on.
Reassessing the drivers against their definitions in a pass that argues for the bid would bring back the bias the separation avoids.

Do not add levers, mitigations, or clarification questions to the triage.
Do not point `clarify-rfp` to the drivers reference or have it reassess the drivers, their risk levels, or the overall risk.

### No document tooling in the skills

The skills deliberately do not name tools for reading or producing PDF, DOCX, XLSX, PPTX, or other formats.
This follows from relying on strong models: choosing and running suitable tooling is left to the agent that executes the skill, based on what is available in its environment.
The skills only state the requirements: `triage-rfp` allows converting documents to text, keeping section headings, page numbers, table structure, and requirement IDs so that findings can be located; `export-report` states the layout and asks the agent to check the result.

Do not add specific tools, commands, or installation steps to the skills or the README.

## Versioning

When you change a skill itself, such as its `SKILL.md` or references, bump the minor version in `.claude-plugin/plugin.json`, for example from `0.2.0` to `0.3.0`, so that clients update it.
Bump it once per set of uncommitted changes: if the version already differs from the last commit, leave it as is.
Do not bump the version for changes that do not reach clients, such as READMEs or GitHub workflows.
