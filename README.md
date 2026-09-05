# ACC Runner

ACC Runner is the execution/runtime component for the Algonquian Real Estate Agent Command Console.

## Canonical deployment

**Production node:** `https://acc.algonquianrealestate.com`

ACC is intentionally deployed separately from the unified ARE API gateway:

- `https://api.algonquianrealestate.com` — canonical API/backend gateway
- `https://acc.algonquianrealestate.com` — dedicated Agent Command Console node

## Role

ACC may coordinate and display:

- agent execution and workflow runs;
- approval queues and human gates;
- next actions and transaction exceptions;
- agent/system health;
- command dispatch;
- activity and audit visibility.

ACC consumes the canonical ARE API:

`https://api.algonquianrealestate.com/v1/`

It must not directly become a second system of record for Deals, underwriting, offers, documents, funding, buyers, signatures, or closing records.

## Architecture

```text
acc.algonquianrealestate.com
          │
          ▼
api.algonquianrealestate.com/v1/
          │
          ▼
ARE API Bridge
          │
          ▼
ARE_Platform_Service_Interface
          │
          └── authoritative ARE operational plugins
```

Pipeline CRM remains authoritative for the canonical `deal_id`.

## Security boundary

ACC should use service authentication, scoped permissions, correlation IDs, idempotency controls for commands, audit events, and explicit human approval for consequential actions.

Production credentials belong in protected deployment secrets and must not be committed to the repository.
