# Codex runtime adapter

These are known identifiers in the environment where this skill was installed; verify availability in the current tool schema. They are defaults, not a guarantee for another host.

| Role | Model | Reasoning |
| --- | --- | --- |
| Astra | gpt-6-astra | medium |
| Sol | gpt-5.6-sol | medium |
| Terra | gpt-5.6-terra | medium |
| Luna | gpt-5.6-luna | low |

With collaboration.spawn_agent, use fork_turns="none" and an explicit model/reasoning_effort. Supply the compact task packet in the message. Do not use the unsupported fork_context parameter. Use agent_type="default" when selecting these models, unless an available specialized role is verified compatible with this workflow. In particular, the legacy sol_router_planner role may require the old fixed Sol → executor chain and must not be used for Astra escalation without checking its instructions.

Use collaboration.followup_task to resume an idle agent with a new assignment; send_message alone does not start an idle agent. Run brain and executor stages sequentially. An executor can remain idle while a brain reasons, then resume with the decision.

Use a real close/release operation only if the current environment exposes one. interrupt_agent interrupts work but does not promise to free a slot; never claim otherwise. Reuse idle agents with the same role and model rather than accumulating new agents. If slots prevent progress, report the actual limitation instead of retrying creation indefinitely.

If a required model or delegation tool is unavailable, state the limitation. Use an alternative only when already authorized; otherwise ask for the needed choice while preserving completed evidence. Never label a substitute as Astra, Sol, Terra, or Luna when it was not that model.

The skill guides behavior; it is not a technical permission sandbox. Do not use user-visible task creation tools for internal agents. Local project rules and higher-priority runtime instructions still apply.
