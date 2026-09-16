# ACC Runner

ACC Runner is the controlled execution-runtime module for the canonical ACC™ platform at `https://acc.onegodian.com`.

## Canonical role

ACC Runner processes approved tasks and workflow steps after authority and policy checks have been satisfied.

It may execute work delegated through:

- ACC workflows
- approved agent tasks
- adapters and tools
- governed OMOS execution requests
- Oru’Valen-prepared actions after required authorization

ACC Runner does not self-authorize privileged work.

## Execution boundary

```text
Authorized Human Judgment
→ Oru’Valen / OMOS decision support
→ ACC
→ OCP authorization
→ OEG governed execution
→ ACC Runner / adapters / agents
→ verification + audit evidence
```

Runner output must remain attributable, reviewable, and auditable. Retries, failures, and state transitions must not bypass policy or approval controls.

## Source of truth

The canonical ACC platform repository is `ohi-stack/acc`. This repository is an execution module and must remain compatible with the contracts and authority model defined there.

Synchronized to ACC platform `v1.3.0` architecture on September 16, 2026.
