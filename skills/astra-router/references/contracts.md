# Handoff contracts

Omit unused fields. Pass facts once and subsequent changes as deltas.

Task: GOAL, WORKSPACE, REQUEST_MODE, AUTHORIZED_SCOPE, PROJECT_CONSTRAINTS, ACCEPTANCE, FACTS_WITH_SOURCES, UNKNOWNS. State a DECISION_QUESTION only if a brain is needed.

Evidence: observations with paths/lines or command/results and relevant snapshot; separate inference and unresolved assumptions. Send excerpts, not raw logs or repository dumps. Refresh affected evidence after changes.

Brain: STATUS=PROCEED|REVISE|NEEDS_EVIDENCE|NEEDS_INPUT|BLOCKED; EXECUTOR=TERRA|LUNA|NONE; DECISION, RATIONALE, bounded BRIEF, ACCEPTANCE_GATES.
Sol escalates only with a concrete strategic question. R4 Sol challenge supplies up to three options, counterevidence, material risks and the unresolved disagreement. Astra receives original constraints and cited evidence, not just Sol's recommendation.

Executor: complete the assigned investigation or authorized implementation and validation. Do not spawn agents; preserve others' edits. Return STATUS, ARTIFACTS, checks and outcomes, remaining issues. Ordinary implementation choices do not need brain approval.

Delta follow-up: previous decision identifier or short summary, changed fact/source, invalidated assumption, precise question. Preserve constraints without reposting unchanged transcripts.

Examples:
- Exact typo: R0; direct parent work can avoid a disproportionate handoff.
- Known failing test needing diagnosis: R1 Terra, not automatic Astra.
- User-supplied ordered implementation plan: R1 Terra; do not re-plan.
- Multi-stage dependencies with a clear goal but an unresolved sequencing decision: R2 Sol.
- Missing repository facts for competing architectures: Terra evidence, then R3 Astra.
- Migration with disputed rollback assumptions and material consequences: R4; no permission expansion.
- Strategic opinion with sufficient supplied evidence: R3, no executor.
