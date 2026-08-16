# Mission Control Contract

`SKILL.md` is authoritative on behavior and truth rules. This file defines the reporting shapes used by Mission Control.

Universal rule: **nothing defaults to approved.** Every generated recommendation uses `approval_required: true`, `default_approved: false`, and `approval_state: "PENDING"`.

## Requirement classification

```json
{
  "requirement": "...",
  "classification": "DIRECT | TRANSFERABLE | EASY_SKILL_BRIDGE | PROJECT_BRIDGE | UNSUPPORTED",
  "evidence": "...",
  "notes": "..."
}
```

A classification may never be promoted to DIRECT by approval alone. Only new verified evidence changes it.

## Fit review

```json
{
  "fit_review_id": "fr_...",
  "job_id": "...",
  "target_company": "...",
  "target_title": "...",
  "scores": {
    "current_resume_fit": 0,
    "verified_candidate_fit": 0,
    "potential_fit": 0
  },
  "verdict": "Strong | Good | Moderate | Weak",
  "strongest_alignments": [],
  "transferable_strengths": [],
  "unsupported_gaps": [],
  "requirement_classifications": [],
  "tasks": [],
  "state": "DECISION_READY_FOR_REVIEW"
}
```

## Change task

```json
{
  "task_id": "t1",
  "task_type": "RESUME_EDIT | EASY_SKILL_PROPOSAL | PERSONAL_PROJECT | POSITIONING_CHANGE | CONTENT_REMOVAL | OTHER",
  "title": "...",
  "affected_section": "...",
  "impact": "High | Medium | Low",
  "proposed_action": {
    "before": "...",
    "after": "..."
  },
  "rationale": "...",
  "verified_evidence": "...",
  "overclaim_risk": "None | Low | Medium | High",
  "approval_required": true,
  "default_approved": false,
  "approval_state": "PENDING | APPROVED | REJECTED"
}
```

## Easy skill proposal

Approval authorizes baseline familiarity in Technical Skills only. It never authorizes experience bullets, production usage, ownership, outcomes, metrics, or proficiency claims.

## Personal project

```json
{
  "project_id": "p1",
  "name": "...",
  "state": "PROPOSED_PROJECT | APPROVED_TO_BUILD | IN_PROGRESS | COMPLETED_UNVERIFIED | VERIFIED_PERSONAL_PROJECT",
  "gap_addressed": "...",
  "estimated_hours": 8,
  "resume_eligible": false
}
```

`resume_eligible` may be true only when `state == "VERIFIED_PERSONAL_PROJECT"` and Sri explicitly authorizes resume use.

## Approval actions

```json
{
  "action": "APPROVE_INDIVIDUAL | APPROVE_SELECTED | APPROVE_ALL | REJECT | ADD_CUSTOM_CHANGE | REGENERATE_RECOMMENDATIONS | GENERATE_WITHOUT_CHANGES",
  "task_ids": [],
  "custom_instruction": null
}
```

APPROVE ALL never disables truth rules.

## Generation run

```json
{
  "generation_run_id": "gr_...",
  "job_id": "...",
  "target_company": "...",
  "target_title": "...",
  "fit_review_id": "fr_...",
  "approved_task_ids": [],
  "source_skill_repository": "sriupanya/resume-tailoring-verified-latex",
  "source_skill_commit": "...",
  "generated_resume_version": "v1",
  "validation_report": "...",
  "pdf_reference": "...",
  "latex_reference": "...",
  "state": "RESUME_READY_FOR_REVIEW | APPROVED_FOR_APPLICATION"
}
```

Versions are immutable. Regeneration creates a new version.

## Final approval

Final application use requires explicit confirmation that Sri reviewed the exact resume and wants to use that exact version.

## Notifications

Notify only on genuine state changes such as `DECISION_READY_FOR_REVIEW` or `RESUME_READY_FOR_REVIEW`.

## Approval audit

The final validation report should identify approved tasks implemented, approved tasks skipped and why, rejected/pending tasks excluded, easy skills added or kept out, verified projects used, unverified projects excluded, and custom changes implemented.
