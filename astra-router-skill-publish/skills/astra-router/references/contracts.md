# Compact handoff contracts

Use only applicable fields. Preserve critical details even when they exceed a soft length target.

## Task packet

GOAL; WORKSPACE; REQUEST_MODE=ADVICE|INVESTIGATE|IMPLEMENT;
AUTHORIZED_SCOPE; PROJECT_CONSTRAINTS; ACCEPTANCE;
KNOWN_FACTS_WITH_SOURCES; UNKNOWNS; DECISION_QUESTION.

## Executor investigation

FACTS: source paths/lines or command and result; identify snapshot/revision where relevant.
UNVERIFIED_ASSUMPTIONS; MATERIAL_UNKNOWNS; OPTIONS_IF_KNOWN;
DECISION_NEEDED; RECOMMENDED_NEXT_CHECK.

Separate observations from inference. Inspect applicable project instructions before project work. Evidence may become stale after edits or runtime changes; refresh only the affected evidence.

## Brain decision

STATUS=PROCEED|REVISE|NEEDS_EVIDENCE|NEEDS_INPUT|BLOCKED
EXECUTOR=TERRA|LUNA|NONE
RATIONALE; DECISION_OR_ANSWER; EXECUTION_BRIEF; ACCEPTANCE_GATES.

For NEEDS_EVIDENCE: include a precise evidence request and why it changes the decision.
For R4 challenge review: provide up to three options, material risks, counterevidence, key disagreement, and a recommendation. Astra receives original constraints and source-backed evidence as well as this analysis.

## Executor instructions and result

Complete the assigned investigation or authorized implementation and proportionate validation. Do not spawn agents. You are not alone in the workspace; preserve others' edits. Do not expand scope or silently alter key decisions. Correct routine implementation problems yourself; surface disproven assumptions with evidence.

Return STATUS; CHANGED_FILES_OR_ARTIFACTS; VALIDATION_RESULTS (commands/checks, outcomes, and relevant failures); KNOWN_ISSUES; DECISION_NEEDED if any. For advice or investigation, return findings and source evidence rather than fabricated changed files.

## Routing examples

- Exact typo replacement with known acceptance: R0, Luna.
- Change a test assertion to bypass an unexplained failure: investigate with Terra; R2, not automatic R0.
- Compare architectures with missing repository facts: Terra investigation, Astra decision, no edits unless authorized.
- Ambiguous runtime bug: R2; Terra can return evidence and resume after a revised plan.
- High-impact migration with disputed rollback assumptions: R4; brain judgment does not authorize deployment.
- Supplied evidence sufficient for a strategic opinion: R3, Astra, EXECUTOR=NONE.
