---
id: RC-03-001
title: Event envelope and ID conventions
status: draft
version: 0.1
owner: A3 Ramūnas
updated: 2026-11-01
kind: event
package: packages/shared/src/events/envelope.ts
---

# Event envelope and ID conventions

Every block writes and reads events with the same envelope. Integration = agreeing on event types.

```ts
export interface EventEnvelope<T = unknown> {
  event_id: string;        // ULID, globally unique
  type: string;            // e.g. "match.settled", "seed.reserved"
  match_id?: string;       // ULID when match-scoped
  player_id?: string;
  seq: number;             // per-match sequence, gapless
  ts_server: string;       // ISO 8601, the only clock
  idempotency_key?: string;// present on every state-changing command
  payload: T;
}
```

Conventions: ULID for all ids; server time is the only clock; every state-changing command
carries an idempotency key and replay returns the original result; money truth = ledger,
match truth = game-engine, never a second copy of state another block owns.
