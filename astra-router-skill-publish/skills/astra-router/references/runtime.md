# Runtime adapter

Verify available tools and model identifiers; defaults are environment-dependent.

| Role | Model | Default reasoning |
| --- | --- | --- |
| Sol planner | gpt-5.6-sol | low for bounded planning; medium for disputed dependencies |
| Astra decision | gpt-6-astra | medium; increase only for a stated decision need |
| Terra executor | gpt-5.6-terra | medium |
| Luna executor | gpt-5.6-luna | low |

Use collaboration.spawn_agent with fork_turns="none", explicit model/reasoning_effort, and agent_type="default" unless a specialized role's instructions are compatible. Avoid legacy fixed-chain planner roles. A compact packet must include applicable project constraints because history is not inherited. Tool definitions and environment instructions may still be supplied; an empty history is not zero input cost.

Use followup_task to resume an idle agent; send_message alone does not start an idle turn. Reuse role-compatible agents. Interrupt is not close/release; do not claim it frees a slot. Use a real close operation only if exposed. If capacity or required models are unavailable, disclose the limitation; use a substitute only when authorized and report the actual model.

If the parent is a known Terra/Luna executor, direct execution avoids a redundant child. If it is a known Sol/Astra brain for the selected route, reason once locally and delegate project work. Do not call the same brain again simply to formalize its answer. Do not infer the parent's model from the skill name.

Normal project work is often better hosted in a Terra parent with on-demand brain delegation; this is a workflow option, not an automatic model switch. A parent running Astra still processes task context and tool returns. Lower visible output, fewer tokens, lower account usage and lower monetary cost are different metrics. Reasoning settings and prompt length targets are not hard token budgets.
