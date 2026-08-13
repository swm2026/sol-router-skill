---
name: sol-router
description: On-demand token-conscious task routing. Use only when the user explicitly invokes $sol-router and wants GPT-5.6 Sol to plan without executing, then have exactly one GPT-5.6 Terra or GPT-5.6 Luna agent perform the project work.
---

# Sol Router

Use this workflow only after explicit `$sol-router` invocation. Never activate it implicitly.

## Workflow

1. Preserve the user's complete task, workspace, constraints, allowed files, and acceptance criteria.
2. Spawn exactly one planning agent with model `gpt-5.6-sol`, reasoning effort `medium`, and `fork_context: false`.
3. Give Sol only the task and compact, already-known project facts. Do not ask it to scan the repository or execute tools. Require exactly:

```text
EXECUTOR=TERRA|LUNA
REASON=<one sentence>
EXECUTION_BRIEF=<bounded implementation instruction>
```

4. Sol must choose:
   - `LUNA` for clear, repeatable, low-risk work with a narrow scope: documentation, deterministic validation, metadata, simple assets, or typically no more than two straightforward files.
   - `TERRA` for code or scene changes, debugging, behavior tests, cross-file integration, ambiguous failures, architecture, security, or medium/high-risk work.
5. Wait for Sol, record its decision, then close it before spawning the executor.
6. Spawn exactly one executor with `fork_context: false`:
   - `TERRA`: model `gpt-5.6-terra`, reasoning effort `medium`.
   - `LUNA`: model `gpt-5.6-luna`, reasoning effort `low`.
7. Send the executor the original task, Sol's execution brief, workspace path, constraints, acceptance criteria, and this instruction: complete implementation and validation end to end; do not spawn subagents; return only changed files, validation results, and known issues.
8. The parent must not duplicate implementation. It may only relay essential updates, review the executor result, and summarize it.
9. If the executor reports a genuine blocker, stop and report it. Do not automatically start another model.
10. Close the executor after collecting its final result.

## Cost Controls

- Never run Sol, Terra, and Luna concurrently.
- Never spawn both Terra and Luna for one invocation.
- Never fork the full conversation context.
- Never ask Sol for implementation details beyond the bounded execution brief.
- Do not repeat repository scans, tests, or file reads already completed by the executor.
- Keep all inter-agent responses concise.

## Sol Boundary

Sol is a planner and router only. It must not edit files, run commands, browse, test, generate assets, or perform project execution. If no execution is required, Sol may choose the cheaper executor to produce the requested artifact; the parent still does not execute it locally.

## Completion Report

```text
SOL_ROUTER_USED=true
EXECUTOR=TERRA|LUNA
SOL_EXECUTED_PROJECT_WORK=false
PARALLEL_AGENTS_USED=false
```
