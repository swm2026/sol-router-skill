# Codex runtime adapter

Verify availability in the current tool schema; these defaults are not a guarantee for another host.

| Role | Model | Reasoning |
| --- | --- | --- |
| Astra | gpt-6-astra | medium |
| Terra | gpt-5.6-terra | medium |
| Luna | gpt-5.6-luna | low |

With `collaboration.spawn_agent`, use `fork_turns="none"` and an explicit model/reasoning effort. Supply the compact task packet in the message. Use `agent_type="default"` unless a compatible specialized role is verified. Run brain and executor stages sequentially; an executor can remain idle during Astra's decision and then resume.

Use a real close/release operation only if the environment exposes one. Interrupting an agent does not promise to free a slot. Reuse idle agents rather than accumulating new agents. If a required model or delegation tool is unavailable, state the limitation and never label a substitute as Astra, Terra, or Luna.

The skill guides behavior; it is not a permission sandbox. Local project rules and higher-priority runtime instructions still apply.
