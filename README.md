# Resume Tailoring — Verified LaTeX

This repository is the canonical source of truth for Sri Upanya Balu's resume-tailoring skill.

Contents:
- `SKILL.md` — behavior, truth rules, JD fit review, approval gating, project logic, and validation rules
- `resources/MASTER_RESUME.tex` — canonical one-page LaTeX resume
- `resources/VERIFIED_FACTS.md` — factual guardrails, verified metrics, tools, roles, and exclusions
- `resources/MISSION_CONTROL_CONTRACT.md` — approval-task, state, notification, and version schemas used by Mission Control

## Claude usage

Use the repository files as the skill source. A request can be as short as:

```text
Use my "Resume Tailoring — Verified LaTeX" skill for this job.

TARGET ROLE
<role>

JOB DESCRIPTION
<full JD>

Run the fit review and propose changes for approval.
```

## Canonical source of truth

Mission Control must fetch `SKILL.md`, `resources/MASTER_RESUME.tex`, `resources/VERIFIED_FACTS.md`, and `resources/MISSION_CONTROL_CONTRACT.md` from the repository default branch before each fit review or resume-generation run.

Mission Control must not maintain independent candidate facts or resume strategy that can silently drift from this repository. If the canonical files cannot be fetched, resume generation should fail visibly rather than silently fall back to stale resume content.

## Core rules

- 6+ years headline unless explicitly changed by Sri
- BMS GenAI work is developed, deployed, production/user-facing work; do not reduce it to prototype/POC language
- only verified facts and metrics may enter the resume
- WHO-style bullets where evidence supports them
- one-page canonical LaTeX layout
- projects are optional, 0–2 maximum, verified, JD-relevant, and non-duplicative
- job-search, resume-generation, and career-tracking tooling never belongs on the resume
- every material recommended change requires explicit approval before generation
