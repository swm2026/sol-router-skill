---
name: astra-router
description: Explicit-only, evidence-first task orchestration. Use when the user invokes $astra-router to route planning to Sol or strategic judgment to Astra, with at most one active Terra or Luna executor and resumable investigation and validation.
---

# Astra Router

Activate only when the user invokes this skill to perform a task. Merely discussing or editing the skill does not activate its agent workflow. Preserve the user's goal, workspace, existing authorization, project rules, scope, and acceptance criteria.

## Responsibilities and authority

- Parent: classify the task, relay compact evidence, manage agent lifecycle, review results, and communicate. Do not duplicate delegated implementation or repeat checks without a concrete reason.
- Sol: plan a known goal and identify questions that need strategic judgment.
- Astra: assess competing directions, material tradeoffs, and disputed evidence.
- Terra/Luna: gather project evidence, implement authorized changes, and validate results.
- Brains do not inspect repositories, run project commands, edit files, test, or generate assets. They may request specific evidence from the executor. Their judgments never expand user authorization or override project constraints.
- Executors must not spawn agents. Use one executor identity per task when practical and never run two executors concurrently. Tell every executor that other work may exist and must not be reverted.

## Routing

Classify by uncertainty, behavioral impact, reversibility, and consequence—not file count or domain keywords alone.

| Level | Conditions | Route |
| --- | --- | --- |
| R0 | Method and acceptance are explicit; work is mechanical, low impact, and recoverable | Luna directly |
| R1 | Goal is clear; a small plan resolves the remaining uncertainty | Sol → Luna |
| R2 | Debugging, behavior, implementation, or integration needs engineering judgment | Sol → Terra |
| R3 | Direction or a material tradeoff must be decided | Astra → executor if needed |
| R4 | Material consequences AND a concrete disputed assumption or competing option warrant a separate challenge pass | Sol challenge → Astra → executor if needed |

R4 is exceptional. Sol should expose counterevidence and alternatives, not simply endorse a preferred option. Two model calls do not prove correctness. Do not add Sol after Astra unless a specific unresolved planning need justifies it.

Missing facts call for investigation, not automatically a stronger brain or a higher route. For advice-only work, allow EXECUTOR=NONE and return the brain's answer when sufficient evidence is already supplied. A decision request does not authorize implementation.

## Evidence and execution loop

1. Build a compact task packet with goal, scope, constraints, acceptance, known facts and their sources, and unknowns. Pass relevant project instructions explicitly because full history is not inherited.
2. If material evidence is missing, use the single executor for a bounded read-only investigation first; choose Terra for uncertain repository/runtime behavior. Return the evidence packet in [references/contracts.md](references/contracts.md).
3. Invoke only the required brain, with the task and evidence packet. If it needs more facts, request a targeted investigation from the same executor and resume the brain. Do not force a decision from an inadequate summary.
4. Once the decision is supported and implementation is authorized, resume that executor with the decision, allowed scope, acceptance gates, and relevant evidence. If none exists, create the selected executor.
5. Executors solve ordinary implementation failures within scope. If evidence invalidates a key assumption, return the smallest proposed adjustment and evidence to the parent. Resume the appropriate brain only for a material decision change; then resume the executor.
6. Complete proportionate validation. Review evidence against acceptance criteria. Repeat a check only after relevant changes, an unresolved failure, missing evidence, or a concrete contradiction.

If initial Luna work reveals genuine engineering uncertainty, park Luna before making a justified replacement with Terra, transfer its evidence, and disclose the change. Prefer this explicit exception over pretending Luna completed unsuitable work. Never silently substitute unavailable models.

## Stop and escalation conditions

Pause dependent work only for missing necessary authorization/user information, an unavailable external prerequisite, or an unresolved blocker after focused recovery. Continue independent authorized work where useful. Do not require the user to invoke the skill again for ordinary recovery.

Two attempts with the same unresolved condition trigger root-cause analysis or a changed approach, not another identical retry. Stop automated cycling when further progress requires user input or external change. Distinguish BLOCKED, NEEDS_INPUT, PARTIAL, and COMPLETE honestly.

Project rules govern sensitive actions, Git operations, and external writes. Brain approval is never user approval. For investment projects, preserve their explicit account, broker-write, runtime-guard, and promotion restrictions; do not invent permissions from task classification.

## Runtime and cost

Before spawning, read [references/runtime.md](references/runtime.md) and use the actual tool schema and available model identifiers. At most one child agent runs at a time; idle agents may be retained for resumption. Do not spawn agents just to test whether the skill loads.

Keep packets concise, with sources and uncertainty intact. Aim for brain inputs around 1,200 tokens and outputs around 180–350 tokens when practical; these are soft targets. Do not omit acceptance gates, relevant evidence, or authorization boundaries to meet them. Send focused excerpts instead of repository dumps and reuse evidence while it remains valid.

Optimize measured end-to-end quality, cost, latency, and rework. A parent running Astra still incurs its own inference cost; this skill does not switch the parent model. Do not claim token savings without comparable observed usage.

## Completion

Report the outcome, changed artifacts if any, validation evidence, and remaining limitations. Add a compact routing trace: route level, actual brain(s), actual executor(s) or NONE, and status. Disclose fallbacks, replacements, or deviations. Never report model execution or checks that did not occur.
