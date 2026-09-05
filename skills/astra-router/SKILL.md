---
name: astra-router
description: Explicit-only, token-conscious task orchestration. Use when the user invokes $astra-router; bypass Astra for mechanical or routine work and use Astra only for engineering or strategic judgment.
---

# Astra Router

Activate only when the user invokes `$astra-router`. Preserve the user's goal, workspace, authorization, project rules, scope, and acceptance criteria.

## Responsibilities

- Parent classifies the task, relays compact evidence, manages agents, reviews results, and communicates. It does not duplicate delegated work.
- Astra is the only planning and decision brain when planning is needed. It chooses what should be done, whether it should be done, and which executor is suitable.
- Terra/Luna gather evidence, implement authorized changes, and validate results.
- Astra must not inspect repositories, run commands, edit files, test, or generate assets. Astra's judgment never expands user authorization or overrides project constraints.
- Executors must not spawn agents. Run at most one executor at a time and tell it that other work may exist and must not be reverted.

## Routing

Classify by uncertainty, behavioral impact, reversibility, and consequence—not file count alone.

| Level | Conditions | Route |
| --- | --- | --- |
| R0 | Method and acceptance are explicit; work is mechanical, low impact, and recoverable | Luna directly |
| R1 | Goal, method, and acceptance are clear; execution is routine and low risk | Luna directly (no Astra) |
| R2 | Debugging, behavior, implementation, or integration needs engineering judgment | Astra → Terra |
| R3 | Direction or a material tradeoff must be decided | Astra → executor if needed |
| R4 | Material consequences and disputed assumptions warrant an adversarial evidence review | Terra investigation → Astra → executor if needed |

R0 and R1 are the token-saving path: do not call Astra. R2–R4 use Astra only when its judgment can change the implementation or risk outcome. R4 is exceptional. Astra must distinguish observation, inference, uncertainty, and decision. Missing facts call for bounded investigation, not automatic escalation. Advice-only work may return `EXECUTOR=NONE`; a decision does not authorize implementation.

## Evidence and execution loop

1. Build a compact task packet containing goal, scope, constraints, acceptance, known facts with sources, and unknowns.
2. If the task is R0/R1, route directly to Luna and do not create a planning-agent call. If material evidence is missing for R2–R4, use one executor for a bounded read-only investigation first. Use Terra for uncertain repository or runtime behavior.
3. For R2–R4, give Astra only the task packet and evidence. If Astra needs more facts, request a targeted investigation from the same executor and resume Astra; never force a decision from an inadequate summary.
4. After a supported decision and explicit implementation authorization, resume that executor with the decision, scope, evidence, and acceptance gates. Otherwise create the selected executor.
5. Executors solve ordinary failures within scope. If a key assumption is disproven, return evidence and the smallest proposed adjustment. Resume Astra only for a material decision change, then resume the executor.
6. Run proportionate validation and report evidence against the acceptance criteria.

If Luna reveals genuine engineering uncertainty, park it, transfer its evidence, and replace it with Terra transparently. Never silently substitute an unavailable model.

## Stop conditions

Pause only for missing necessary authorization or user information, unavailable external prerequisites, or an unresolved blocker after focused recovery. Two attempts with the same condition require root-cause analysis or a changed approach. Stop cycling when progress requires user input or an external change. Report `BLOCKED`, `NEEDS_INPUT`, `PARTIAL`, or `COMPLETE` honestly.

Project rules govern sensitive actions, Git operations, and external writes. Astra approval is never user approval. Preserve investment-project restrictions such as `broker_orders_enabled=false` and `runtime_guard`.

## Runtime and cost

Before spawning, read [references/runtime.md](references/runtime.md) and verify the current tool schema and model availability. Use `fork_turns="none"`; run stages sequentially and reuse an idle executor when practical. Do not claim token savings without comparable observed usage.

Keep evidence compact without omitting sources, uncertainty, authorization, or acceptance gates. Do not send repository dumps. R0/R1 should normally use one executor call and zero Astra calls; R2/R3 one Astra call and one executor; R4 adds a justified investigation pass. These are routing targets, not guarantees. The skill does not switch the parent model.

## Completion

Report outcome, changed artifacts, validation evidence, limitations, route level, Astra usage, executor usage, and status. Disclose fallbacks or deviations. Never report work or checks that did not occur.
