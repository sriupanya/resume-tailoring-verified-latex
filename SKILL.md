---
name: resume-tailoring-verified-latex
description: Tailor Sri Upanya Balu's verified one-page LaTeX resume to a specific job while preserving factual accuracy, verified metrics, concise WHO-method bullets, ATS readability, and the canonical LaTeX layout. Includes quick-win skill checks, easy-to-learn JD skill detection, role-relevant personal project generation, a role fit review, and an approval-gated AI Job Mission Control workflow where every proposed change requires explicit user approval before it enters the resume.
---

# Resume Tailoring — Verified LaTeX

Use this skill whenever the user asks to tailor Sri Upanya Balu's resume for a specific job.

---

# APPROVAL AUTHORITY — READ FIRST

**NOTHING NEW MAY BE ADDED TO THE RESUME WITHOUT SRI'S EXPLICIT APPROVAL.**

This skill may ANALYZE and PROPOSE automatically. It may NOT silently IMPLEMENT.

The operating model is:

> **AI recommends → she approves → AI executes → she reviews → she approves the final resume.**

It is never:

> AI recommends → AI edits automatically → she discovers the changes afterward.

Approval is required for every one of these:

- resume wording changes
- reordered or reprioritized content, when the change is materially different
- newly surfaced skills
- easy-to-learn JD skills
- personal projects
- new positioning claims
- custom suggested bullets
- JD terminology that materially changes how her experience is represented

**Materially different** means a recruiter reading the two versions would take away a different impression of scope, seniority, focus, or capability. Pure mechanical work — fixing a typo, compressing whitespace, wrapping a line, keeping LaTeX valid — is not a material change and does not need a task.

Two rules that govern everything below:

1. **Approval is permission to implement a truthful proposed edit. It is never permission to invent evidence.** Every existing truth rule in this skill outranks every approval, including APPROVE ALL.
2. **Nothing defaults to approved.** Every generated recommendation carries `approval_required: true` and `default_approved: false`.

This approval layer sits *on top of* the existing rules in this file. It never relaxes them. Where an approval instruction and a truth rule appear to conflict, the truth rule wins.

## Canonical sources

Use these files as the source of truth:

- `resources/MASTER_RESUME.tex` — canonical one-page LaTeX structure and verified resume content
- `resources/VERIFIED_FACTS.md` — factual guardrails, verified metrics, known projects, skills, roles, dates, and explicit exclusions
- `resources/MISSION_CONTROL_CONTRACT.md` — field schemas for approval tasks, states, notifications, and version records (reporting format only; it never overrides a truth rule)

If a claim is not supported by these resources or explicitly supplied by the user in the current request, do not add it.

A job description is a TARGET, not evidence of candidate experience.

## Workflow order

Run every tailoring request in this order. The run splits into two phases separated by a hard approval gate.

### Phase 1 — Analysis (automatic, produces no resume)

1. Load canonical sources
2. Map the JD (see **Job-description mapping**) and classify every important requirement
3. Run the **Skill quick-win check** — including easy-to-learn JD skill detection — ask before adding anything
4. Draft, internally, the selection/reordering/rewording of verified experience that would best serve the role
5. Run the **Personal project fit analysis** — propose, never assume
6. Produce the **ROLE FIT REVIEW** with all three scores
7. Emit every recommendation as an independently approvable **Mission Control change task**
8. Set state `DECISION_READY_FOR_REVIEW` and stop

**STOP HERE.** Do not continue into resume generation unless Sri has explicitly configured automatic generation from already-approved changes. Wait for her approval choices.

### Phase 2 — Generation (only after approval)

9. Collect the approved task set, plus any custom instructions
10. Apply **Resume space management** and the **Space opportunity-cost test**
11. Run the **Interview defensibility check** on every new or revised claim
12. Generate `.tex` + PDF using approved changes only
13. Produce the **Validation report**, including all required sections and the **APPROVAL AUDIT**
14. Set state `RESUME_READY_FOR_REVIEW` and stop
15. Move to `APPROVED_FOR_APPLICATION` only on Sri's explicit final confirmation

Steps 3, 5, 6, and 7 are permanent steps. Run them on every tailoring request, even when the answer is "nothing to add" — in that case say so explicitly rather than skipping the section.

## Non-negotiable truth rules

Never invent, infer as fact, or inflate:

- skills or technologies
- tools or platforms
- projects
- metrics or percentages
- outcomes
- job responsibilities
- team size
- direct reports
- budget ownership
- product ownership
- strategic authority
- deployment scope
- leadership scope
- dates, titles, employers, locations, or education

Do not add a skill solely because the job description asks for it.

Transferable experience must remain transferable; never rewrite adjacent experience as direct platform/domain experience.

## Tailoring method

Tailor only by:

1. selecting the most relevant verified experiences
2. reordering bullets
3. rewording verified experience using accurate terminology from the target JD
4. emphasizing the most relevant verified impact
5. de-emphasizing low-relevance content
6. tightening wording for clarity and seniority
7. adding confirmed quick-win skills and confirmed personal projects (Steps 3 and 5 only, after explicit user approval)

Do not create new experience to close a qualification gap.

## WHO bullet method

Every experience bullet should follow WHO whenever the verified evidence allows it:

- **W — What:** what the candidate built, led, improved, analyzed, delivered, or implemented
- **H — How:** verified methods, technologies, data, stakeholders, or operating approach
- **O — Outcome:** verified quantitative or qualitative business/technical value

Preferred pattern:

**Action + method/context + verified impact**

Example:

> Built and deployed an LSTM customer-intent model using digital behavior data, increasing campaign conversion by 22%

Rules:

- use only verified outcomes
- preserve numerical metrics exactly
- if no quantified outcome is supported, use a truthful qualitative value
- if even qualitative impact is unsupported, omit the outcome rather than inventing one
- one primary achievement per bullet

## Current-role positioning (Bristol Myers Squibb, Senior Manager)

The BMS GenAI work is developed, deployed, and in production/user-facing use.
Never describe it as a prototype, POC, pilot-only, or exploratory work. "POC" may appear only when explicitly naming an earlier development stage.

Default the current BMS role to senior-level WHO bullets:

**What was led or delivered -> how -> business/product outcome**

The section should support the conclusion: leads and deploys AI products for pharmaceutical commercial/forecasting problems, strong technical depth, works across business, product, data, and engineering, operating at Associate Director/Director trajectory.

It should NOT read as: individual-contributor data scientist who builds models.

Practical rules:

- ~6 core bullets for the BMS role, plus one concise mentoring bullet if space allows
- lead with product delivery, deployed GenAI, and governance/reliability
- keep library-level detail (scikit-learn, Pandas, NumPy) in the skills table, not in bullets, unless the target role is explicitly deeply technical
- verbs: lead, deliver, deploy, establish, modernize, partner, mentor

## Role-family emphasis

For GenAI, AI Product, Applied AI, Senior Manager, Associate Director, Director, and other product-oriented roles, rank verified evidence in this order:

1. end-to-end AI product delivery (requirements -> solution design -> deployment -> adoption)
2. production-deployed GenAI (natural-language-to-chart, text-to-SQL, conversational analytics)
3. AI governance, evaluation, and reliability (LLM benchmarking, validation rules, guardrails, business-rule checks, controlled execution)
4. forecasting transformation (spreadsheet-heavy -> governed Python applications and pipelines)
5. cross-functional leadership across forecasting, commercialization, product, engineering, data science, and vendors
6. verified measurable outcomes
7. mentoring and technical review of consultants and junior data scientists

Avoid over-indexing on individual Python libraries unless the target role is explicitly deeply technical.

## Bullet length

- Prefer 1–2 rendered lines
- Never exceed 3 rendered lines
- Remove filler and unnecessary adjectives
- Avoid semicolon-heavy compound bullets
- Do not combine unrelated achievements
- Keep phrasing natural and senior, not keyword-stuffed

## Metrics

Preserve every verified number exactly.

Never:

- estimate
- round
- improve
- normalize
- reinterpret
- extrapolate
- create derived metrics unless explicitly supplied by the user

Examples of verified metrics are listed in `VERIFIED_FACTS.md`.

## Job-description mapping

Before editing, map the JD internally into:

- core responsibilities
- required qualifications
- preferred qualifications
- technical keywords
- business/domain keywords

## Requirement classification — five categories

Classify **every important JD requirement** into exactly one of these.

**DIRECT** — She has verified experience with it in `VERIFIED_FACTS.md` or in a `VERIFIED_PERSONAL_PROJECT`. Usable on the resume as experience.

**TRANSFERABLE** — Her existing experience strongly relates, but she must not claim direct experience. Usable only in wording that keeps the relationship honest.

**EASY_SKILL_BRIDGE** — No verified experience today, but the skill is extremely easy to learn because it sits directly adjacent to things she already knows. Requires approval; enters only the Technical Skills section.

**PROJECT_BRIDGE** — Not appropriate to simply list as a skill, but a small personal project could credibly bridge the gap. Routes to the Personal project fit analysis.

**UNSUPPORTED** — Cannot currently be claimed. Remains a gap and is reported as one.

### The no-promotion rule

**Never convert TRANSFERABLE, PROJECT_BRIDGE, or UNSUPPORTED into DIRECT.**

Not through rewording. Not through JD terminology. Not through an approved task. Not through APPROVE ALL. A classification can only change when new verified evidence arrives — Sri supplying a fact, or a project reaching `VERIFIED_PERSONAL_PROJECT`.

Use DIRECT and TRANSFERABLE matches to build the resume. Never insert an UNSUPPORTED requirement into the resume.

## Skill quick-win check

For JD requirements not already DIRECT, identify only genuinely easy, adjacent skills that could become baseline familiarity in about four hours or less. Never add them automatically. Ask Sri first, state why the skill is adjacent, what learning is needed, and the interview risk. Approval permits the skill only in Technical Skills and never creates experience bullets or production claims.

## Personal project fit analysis

Before finalizing, assess whether a role-relevant personal project would materially strengthen the application.

- propose the project to the user, do not write it into the resume
- state what it would demonstrate for the target role and roughly what it involves
- add it to the resume only after the user confirms she actually built it and completion evidence is verified
- proposed-but-unbuilt projects never appear in the resume, project bank, or VERIFIED_FACTS.md

## Projects

Propose **0–2 personal project ideas maximum**, and often zero. Recommend a project only when it materially bridges a real JD gap; prefer one strong project over several superficial ones. Proposed projects are never resume content until completed, verified, and explicitly approved for resume use.

Every proposed project should primarily reuse verified skills, be interview-friendly, be realistically buildable in roughly 4–12 hours (16 hours maximum for an unusually valuable gap), trace to a real JD requirement, and use domain advantage only when relevant.

### Resume project selection

When generating the resume itself, Projects are optional. Include **0–2 verified projects maximum** only when they materially improve fit and add evidence not already obvious from Experience.

- Use only projects explicitly supported in `VERIFIED_FACTS.md` or explicitly confirmed by Sri.
- Reword verified project descriptions for JD relevance only when the wording remains factual.
- Avoid duplicating the same achievement from Experience. If the same initiative appears in both places, Experience should emphasize ownership/business impact while Projects should add distinct technical/product evidence.
- Omit the Projects section entirely when it does not strengthen the application.
- Never include job-search tooling, resume-generation tooling, career-tracking tooling, or proposed/unbuilt projects on the resume.

## ATS optimization

Use JD terminology where it truthfully describes verified experience.

Do not keyword-stuff.

Do not imply direct experience with a platform simply because adjacent experience exists.

If the JD requests Salesforce, Veeva, Agentforce, or another platform and the verified resources do not establish usage, do not add the platform. Emphasize truthful adjacent product, commercial analytics, workflow, data, AI, stakeholder, or change-delivery experience instead.

## Seniority and ownership

Maintain credible scope.

Do not inflate organizational authority, formal product ownership, direct reports, team size, budget responsibility, executive decision authority, or enterprise deployment ownership.

Use "partnered," "led," "drove," "built," "developed," or "coordinated" only when supported by source evidence.

## Canonical LaTeX requirements

Start from `resources/MASTER_RESUME.tex`.

Preserve the canonical document class, packages, geometry, fonts, spacing commands, custom macros, and section structure unless the user explicitly requests a format change.

Target exactly one page.

Do NOT change margins, font size, geometry, or spacing merely to force a page limit.

If the tailored resume exceeds one page:

1. shorten wording
2. remove lower-priority bullets
3. reduce duplicated ideas
4. trim low-relevance skills/content

Make at most two content-only correction passes.

## Summary/headline

The master uses a compact headline rather than a long summary.

Tailor the headline only with verified descriptors.

Do not claim a target title as a current title.

Do not create aspirational expertise unsupported by the source.

## Output requirements

When file-generation/code execution is available, produce BOTH:

1. compiled downloadable PDF
2. complete `.tex` source

The `.tex` must be complete from `\documentclass` through `\end{document}`.

## Final validation

Before returning the resume, verify:

- every factual claim is supported
- every numerical metric is preserved exactly
- no unsupported JD skill/tool/platform was inserted
- no project was invented
- no leadership/product ownership scope was inflated
- no prototype/POC/exploratory wording is used for the deployed BMS GenAI work
- proposed personal projects and unconfirmed quick-win skills were excluded
- WHO structure is used where appropriate
- each bullet is ideally 1–2 rendered lines and never more than 3
- strongest JD alignments appear early
- duplicate ideas are removed
- LaTeX compiles
- final document is exactly one page
- contact details, titles, dates, education, and locations remain accurate

## Validation report

Along with the files, provide a short report containing:

- strongest JD alignments used
- unsupported JD gaps intentionally excluded
- verified metrics retained
- JD terminology added and the factual evidence supporting it
- compile status
- final page count

## Mission Control integration

Mission Control is a reporting and approval layer only. It must not carry an independent copy of candidate facts or resume strategy that can override this skill. Every proposed material change must be approval-gated. Generation must use only approved tasks plus canonical verified evidence. The machine-readable schemas for fit review, change tasks, generation runs, approval states, and notifications live in `resources/MISSION_CONTROL_CONTRACT.md`.
