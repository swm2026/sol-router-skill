---
name: astra-router
description: Explicit-only economical routing with Sol for necessary planning, Astra for consequential decisions, and direct Terra/Luna execution for ordinary work.
---

# Astra Router

Use only for an explicitly requested routed task. Discussing or editing this skill does not itself require its agent workflow. The public name stays astra-router; Sol and Astra are distinct internal models.

## Choose the minimum sufficient route

| Level | Trigger | Default path |
| --- | --- | --- |
| R0 | Mechanical, narrow, low-impact work | Luna |
| R1 | Clear goal and acceptance; ordinary coding, debugging, investigation or integration | Terra |
| R2 | A known goal needs a separate decomposition or sequencing decision that the executor cannot reasonably settle | Sol → Terra/Luna |
| R3 | Competing directions, architecture or material risk require a consequential decision | Astra → executor if needed |
| R4 | High consequences AND a concrete dispute justify independent challenge before judgment | Sol challenge → Astra → Terra if needed |

File count, code changes, or a failed test alone do not trigger a brain. Executors may plan their own work. Missing evidence triggers investigation, not a stronger model. R0/R1 have zero separate brain calls; R2/R3 normally one; R4 normally two. These are decision defaults, not measured token savings.

Sol plans a known goal; Astra decides material tradeoffs. Neither brain scans repositories, runs project commands, edits, tests, or generates assets. For an already-supported advisory decision, allow EXECUTOR=NONE. Brain judgment never expands user authorization.

## Execute and recover

1. Preserve the goal, exact workspace, applicable instructions, authorized scope and acceptance. Use existing valid evidence.
2. For R0/R1, let the executor investigate, implement and validate end to end. For R2–R4, gather missing evidence with that same executor before asking a precise decision question. Read [contracts](references/contracts.md) only when constructing a handoff.
3. Send the selected brain a compact evidence packet. Sol may return a concrete strategic question for Astra; do not automatically add Astra to approve Sol's plan.
4. Resume the executor with the supported decision and existing authorization. Ordinary failures stay with the executor. Reopen a brain decision only when new evidence invalidates a material assumption; send the delta and reason, not the whole history.
5. Verify proportionately. Do not repeat reads or tests unless changes, stale evidence, failure or contradictions justify it. Preserve other contributors' work. Executors do not spawn agents.

Run child stages sequentially; idle agents may remain available while another stage runs. Keep at most one executor active. Reuse the same executor through investigation and implementation. Replace Luna with Terra if new engineering uncertainty warrants it, transferring evidence and disclosing the replacement.

Two attempts with the same unresolved condition require root-cause analysis or a changed approach. Pause dependent work for missing necessary input/authority or external prerequisites; continue independent authorized work. Preserve project account, broker-write and runtime-guard restrictions. Never demand fresh authorization for work already authorized.

## Avoid orchestration overhead

Before delegation, read [runtime](references/runtime.md). If the parent already runs the required model, use it in that role instead of spawning a duplicate. A parent acting as a brain retains the no-project-execution boundary, including project typo edits. A trivial non-project answer or formatting task on supplied text may be completed directly by the parent when a handoff would add more work; disclose direct execution. Project execution belongs to Terra/Luna.

Use short, source-backed packets and delta-only follow-ups. Soft targets: brain input 800–1,200 tokens, Sol output 150–250, Astra output 200–350. Expand only for material evidence, constraints or acceptance. These targets do not cap internal reasoning or enforce billing limits. Do not reload unchanged skill references or narrate internal handoffs at length.

Do not call a second brain for routine approval or start a fresh agent for every stage. Reuse an existing valid decision until its assumptions change. For long unrelated work, prefer a fresh user-started task with a compact handoff; do not create tasks unasked. This skill cannot switch the parent model or make its context free.

## Report and improve

Give outcome, validation and limitations, then one short trace: route, actual parent/model roles, brain calls, executor starts/resumes, and status. If actual model or usage information is unavailable, say unknown. Never claim a child was used when only the parent ran tools.

Read [efficiency](references/efficiency.md) when the user requests a cost audit or observed overhead/recurring rework warrants analysis. Propose optimizations from evidence; do not silently rewrite this skill, launch benchmarks, or remove acceptance gates.
