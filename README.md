# ACC Runner

ACC Runner is the controlled execution-runtime module for the canonical ACC™ platform at `https://acc.onegodian.com`.

## Canonical role

ACC Runner processes approved Work Orders, tasks, and workflow steps after authority and policy checks have been satisfied.

ACC V2 adds a provider-independent work hierarchy above execution:

```text
Project
→ Responsibility
→ Work Order
→ Authorization / Approval
→ ACC Runner or approved external provider
→ Verification
→ Audit
```

Runner output must preserve `project_id`, `responsibility_id` when present, `work_order_id`, provider identity, executor identity, approval state, execution state, verification evidence, and resulting artifacts.

## Provider boundary

ACC Runner is the canonical internal executable provider: `acc-runner`.

External provider identifiers may be attached to planned Work Orders, but Runner must not dispatch a provider unless its ACC adapter is explicitly executable and authorized. Unknown identifiers fail closed.

Current compatibility identifiers include `openai-agents`, `openai-codex`, `chatgpt-work`, `external-mcp`, `omos`, `human`, and reserved `openai-dot`.

`openai-dot` is non-executable until a supported developer integration is implemented, verified, repeatable, and deployed.

## Execution boundary

```text
Authorized Human Judgment
→ Oru’Valen / OMOS decision support
→ ACC Work Order
→ OCP authorization
→ OEG governed execution
→ ACC Runner / approved adapters / agents
→ verification + audit evidence
```

ACC Runner does not self-authorize privileged work. Retries, failures, provider changes, and state transitions must not bypass policy or approval controls.

## Source of truth

The canonical ACC platform repository is `ohi-stack/acc`. Shared work-order and execution-provider contracts are synchronized through `ohi-stack/acc-core`.

**Synchronization target:** ACC `2.0.0-alpha.1` delegation foundation. Production state remains tied to separately verified deployment evidence.
