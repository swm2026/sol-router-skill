---
name: astra-router
description: Explicit-only economical GPT-6 routing. Use Luna for mechanical low-cost work, Sol for demanding execution and scoped planning, and Astra only for consequential decisions where higher judgment materially changes the outcome.
---

# Astra Router v2

Use only for an explicitly requested routed task.

Discussing, reviewing, editing, or improving this skill does not itself trigger its agent workflow.

The public name remains `astra-router`.

GPT-6 Astra, Sol, and Luna are distinct models with different economic and capability roles.

The goal is not to use the strongest model available. The goal is to use the minimum sufficient route that preserves correctness, authorization, and acceptance quality.

# Core routing principle

Route based on:

1. task ambiguity,
2. engineering uncertainty,
3. consequence of a wrong decision,
4. existence of genuine competing directions,
5. whether independent judgment is materially useful.

Do not route upward merely because of repository size, file count, number of edits, token count, long runtime, one failed test, missing evidence, unfamiliar code, or implementation difficulty that the executor can investigate directly.

Missing evidence triggers investigation before stronger routing.

A strong executor may plan its own implementation.

# Choose the minimum sufficient route

| Level | Trigger | Default path |
| --- | --- | --- |
| R0 | Mechanical, narrow, deterministic, low-impact work | Luna |
| R1 | Clear goal and acceptance; ordinary or demanding coding, debugging, investigation, integration, testing, migration, or repair | Sol |
| R2 | Goal is known, but a genuinely separate decomposition or sequencing decision would materially improve execution | Sol planning → Sol or Luna execution |
| R3 | Competing architecture, authority, product, safety, cost, or irreversible directions require consequential judgment | Astra decision → Sol execution if implementation is needed |
| R4 | High consequences AND a concrete unresolved dispute justify independent challenge before final judgment | Sol challenge → Astra decision → Sol execution if needed |

R0 and R1 normally require zero separate brain calls.

R2 normally requires one planning call only when the executor cannot reasonably settle sequencing itself.

R3 normally requires one Astra judgment.

R4 normally requires one independent Sol challenge followed by one Astra judgment.

These are routing defaults, not token budgets or billing guarantees.

# Model roles

## Luna

Use Luna for work that is mechanical, repetitive, narrow, deterministic, easy to verify, and low consequence.

Examples include formatting, small deterministic transforms, narrow file edits, simple extraction, repetitive migrations, known command execution, and straightforward validation.

Luna should not be promoted merely because the task is long. If substantial engineering uncertainty emerges, replace Luna with Sol and transfer the evidence gathered so far.

## Sol

Sol is the default engineering and investigation model.

Use Sol for repository investigation, ordinary and difficult coding, debugging, integration, test repair, root-cause analysis, migrations, system tracing, evidence gathering, scoped planning, implementation sequencing, and technical challenge before Astra when required.

Sol may investigate, plan, implement, test, and validate end to end.

Do not create a separate planning stage when Sol can reasonably plan while executing. A Sol planning stage exists only when separating planning from execution materially improves reliability or coordination.

## Astra

Astra is reserved for consequential judgment.

Use Astra when evidence supports a real decision between materially different directions, such as canonical authority choice, architecture tradeoff, irreversible migration direction, major safety boundary, material production risk, conflicting system contracts, high-cost strategic choice, or competing approaches where choosing incorrectly would create substantial rework or risk.

Do not call Astra merely to approve Sol's work, inspect repositories, rerun tests, review routine patches, summarize evidence, resolve ordinary implementation failures, or provide prestige confirmation.

Astra may be capable of end-to-end implementation, but this router intentionally reserves Astra primarily for consequential judgment to reduce cost and unnecessary orchestration.

If an Astra decision already resolves the question and no project modification is required, `EXECUTOR=NONE` is valid.

# Execute and recover

1. Preserve the user goal, exact workspace, applicable instructions, authorization scope, protected state, and acceptance criteria.
2. Reuse current valid evidence. Do not repeat repository scans, benchmarks, tests, provider research, or architectural reviews unless relevant files changed, evidence is stale, a failure contradicts prior evidence, the requested scope changed, or the previous result was incomplete.
3. For R0/R1, let Luna or Sol investigate and execute end to end. The executor owns inspection, implementation, validation, and focused recovery.
4. For R2, first ask whether Sol can reasonably plan during execution. If yes, downgrade to R1. If no, Sol produces a compact execution plan, then Sol or Luna executes it.
5. For R3, first gather missing project evidence with Sol. Send Astra only the compact consequential decision packet. Resume Sol with that decision and the original authorization.
6. For R4, use only when consequences are genuinely high, a concrete dispute exists, evidence supports more than one serious direction, and independent challenge may change the decision. Sol challenges assumptions and identifies failure modes; Astra makes the final routing judgment; Sol executes if needed.

Do not reopen a brain decision because implementation is inconvenient. Reopen only when new evidence invalidates or materially changes constraints, authority, risk, cost, system behavior, or acceptance feasibility. Follow-up packets contain only the delta and why the prior decision may no longer hold.

Keep at most one executor active. Reuse the same Sol executor through investigation, implementation, testing, repair, and validation unless replacement is materially justified. Executors must not recursively spawn new agents unless explicitly supported and authorized.

# Repeated failure rule

One failure: the executor investigates.

After two attempts with the same unresolved condition, do not continue equivalent retries. Before a third material attempt, classify the blocker and require either `ROOT_CAUSE_IDENTIFIED` or `APPROACH_CHANGED`.

Use these blocker classes:

* `CODE_DEFECT`
* `CONTRACT_MISMATCH`
* `DATA_INPUT`
* `CREDENTIAL`
* `ENTITLEMENT`
* `EXTERNAL_DEPENDENCY`
* `RUNTIME`
* `AUTHORITY_CONFLICT`
* `USER_AUTHORIZATION`
* `UNKNOWN`

A repeated failure alone does not justify Astra. Use Astra only if the root cause exposes a consequential decision or genuine competing direction.

# External prerequisites

Pause only dependent work when required input or authority is unavailable. Continue independent authorized work where useful.

Never bypass credentials, entitlements, missing legal input, user authorization, account restrictions, broker safeguards, or runtime safety guards. Do not manufacture evidence to keep execution moving. `BLOCKED_EXTERNAL_ACCESS` is a valid completed outcome.

# Preserve authority boundaries

Brain judgment never expands user authorization.

A route decision cannot authorize broker writes, financial orders, account changes, production mutation, protected-state modification, secret retrieval, or destructive repository actions unless those actions are already explicitly authorized.

Respect all project-specific protected-state restrictions.

# Avoid orchestration overhead

Before delegation, inspect the active runtime/model state when available. If the parent already runs the model needed for the requested role, use the parent in that role rather than spawning a duplicate.

Do not create one agent per file, one brain per phase, approval agents, redundant reviewers, or repeated planning stages. Keep at most one executor active. Executors must not recursively spawn agents unless explicitly supported and authorized.

# Parallelism

Default to sequential execution when stages depend on each other.

Parallelize only independent read-only investigation when evidence cannot conflict, it materially reduces elapsed time, and merge/reconciliation cost is low.

Never allow two executors to mutate the same project authority concurrently.

# Evidence packets

Brain packets must be compact and decision-focused:

`QUESTION`

`CURRENT_FACTS`

`CONSTRAINTS`

`OPTIONS`

`MATERIAL_RISKS`

`UNRESOLVED_POINT`

`DECISION_REQUIRED`

Prefer evidence references over large repository dumps.

Default soft targets:

Sol planning/challenge input: 800–1,500 tokens

Sol planning/challenge output: 150–350 tokens

Astra input: 800–1,500 tokens

Astra output: 200–500 tokens

Expand only when material evidence requires it. These are efficiency targets, not hard limits.

# Cost discipline

Route upward only when the expected value of stronger reasoning exceeds added model cost, orchestration latency, duplicated context, and additional failure surfaces.

Prefer Luna over Sol when work is deterministic, Sol over Astra when the problem is engineering rather than judgment, and Astra over Sol only when consequential decision quality is the actual bottleneck.

Do not use Astra as routine insurance.

# Long-running work

For a long authorized mission, reuse the same executor and existing decisions.

Do not restart routing after every phase. Only reroute when mission scope materially changes, evidence invalidates a routing assumption, or a consequential decision appears.

For unrelated future work, prefer a new user-started task with a compact handoff.

This skill cannot switch the parent model itself or make context free.

# Reporting

At completion, report:

1. outcome,
2. validation,
3. limitations or blockers,
4. one short routing trace.

Routing trace format:

`ROUTE=R?`

`PARENT_MODEL=<known or unknown>`

`SOL_CALLS=<n>`

`ASTRA_CALLS=<n>`

`LUNA_EXECUTOR_STARTS=<n>`

`SOL_EXECUTOR_STARTS=<n>`

`EXECUTOR_RESUMES=<n>`

`FINAL_STATUS=<status>`

Never claim a child model ran when only the parent executed tools.

If actual model identity, token usage, or cost is unavailable, report `UNKNOWN`.

# Efficiency review

Read `references/efficiency.md` only when the user explicitly requests a cost audit, repeated orchestration overhead is observed, unnecessary brain calls recur, or repeated rework suggests routing failure.

Do not silently rewrite this router. Do not launch benchmarks solely to justify a routing preference. Do not remove acceptance or safety gates merely to reduce model usage.

# Guiding principle

The best route is:

`minimum sufficient intelligence`

+ `minimum necessary orchestration`

+ `preserved authorization`

+ `verifiable execution`

Use Luna when the answer is already clear. Use Sol when the work is hard. Use Astra when the decision is consequential.
