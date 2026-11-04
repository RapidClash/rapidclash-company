# Architecture Decision Records

Format: [MADR](https://adr.github.io/madr/) – one file per decision, numbered, never deleted.
File name: `NNNN-short-title.md`. A superseded ADR stays and points to its successor.

| ADR | Title | Status |
|-----|-------|--------|
| 0001 | Platform baseline: GCP, GKE Autopilot, PostgreSQL ledger, two planes | accepted (roadmap D1) |
| 0002 | Monorepo layout and package boundaries | proposed |
| 0003 | RNG and provably-fair protocol (two reserved server seeds) | proposed (see sheet "RNG ir Provably Fair") |
| 0004 | Ledger: append-only double entry in PostgreSQL | proposed |
| 0005 | Network resilience: regional game plane, central money plane | proposed |

Rule: a change to rng-core, ledger posting rules or the wire protocol needs a new ADR
before code – these are the three things that are expensive to change later.
