---
id: RC-03-0xx
title: <Interface name, e.g. LedgerPort>
status: draft
version: 0.1
owner: A3 Ramūnas
updated: YYYY-MM-DD
kind: internal-port | event | vendor-adapter | partner-api | player | regulator-format
package: packages/shared/src/<path>
---

# <Interface name>

## Purpose and boundary
What crosses this boundary and what does not. Who calls, who implements.

## Contract
```ts
// Type definitions live in packages/shared – copy the public signature here for readers.
export interface LedgerPort {
  openEscrow(cmd: OpenEscrow): Promise<EscrowOpened>;
  settle(cmd: SettleMatch): Promise<MatchSettled>;
}
```

## Events emitted / consumed
| Event | Direction | Envelope fields | Idempotency key |
|-------|-----------|-----------------|-----------------|

## Invariants and errors
- Idempotent on `idempotency_key`; replay returns the same result.
- Error codes and what the caller must do.

## Implementations
| Name | Where | Used in |
|------|-------|---------|
| InMemory… (fake) | packages/<x>/src/fakes | unit tests, walking skeleton |
| Postgres… / <Vendor>Adapter | packages/<x> | staging, prod |

## Contract tests
`packages/<x>/test/contract/*.test.ts` – the same suite runs against the fake and the real
implementation. A PR that changes this file must keep both green.

## Change control
Changing a published event or port is a **breaking change**: new ADR + version bump + migration note.
