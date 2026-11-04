---
id: ADR-0001
title: Platform baseline – GCP, GKE Autopilot, PostgreSQL ledger, two planes
status: accepted
date: 2026-10-26
deciders: [Ramūnas]
consulted: [Povilas, Giedrius]
rc_id: RC-07-001
---

# ADR-0001: Platform baseline

## Context and problem statement
The demo runs on Cloud Run with a loosely structured code base. The licensed, real-money
platform needs a baseline that survives investment without a rewrite and that a
certification lab and an auditor can read.

## Decision drivers
- No rewrite when funding arrives: sizes and vendors change, architecture does not.
- Money correctness (double-entry ledger, escrow per match) is non-negotiable.
- Players in Africa and LATAM on weak networks; money must stay in one place.
- Certification freezes rng-core and game mappings – isolate them.

## Decision outcome
- Google Cloud stays; compute moves from Cloud Run to **GKE Autopilot** (one cluster now).
- **Cloud SQL PostgreSQL** holds profiles, matches and the **ledger** with our own
  append-only double-entry logic (no external ledger product).
- **Memorystore Redis** for matchmaking queues and session state; **Cloudflare** at the edge.
- **Two planes**: a regional *game plane* (ws-gateway, matchmaking execution, game-engine,
  regional Redis) chosen per match by max RTT, and one central *money plane*
  (ledger, wallet, KYC) in europe-west4.
- TypeScript monorepo; every external vendor behind an adapter interface with a fake.
- All sizes, regions and vendor modes are Terraform variables / configuration, not code.

### Consequences
- Good: investment = larger numbers and real API keys, same code.
- Good: lab certifies one small package (rng-core + mappings).
- Bad: GKE has more operational surface than Cloud Run – mitigated by Autopilot and IaC.
- Follow-ups: ADR-0002 monorepo layout, ADR-0003 RNG protocol, ADR-0004 ledger, ADR-0005 network.

## Links
- Roadmap D1, D2, D9; sheets "Platforma", "Ledger PostgreSQL", "Tinklo atsparumas", "RNG ir Provably Fair"
