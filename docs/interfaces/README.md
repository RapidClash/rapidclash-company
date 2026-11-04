# Interfaces (area 03)

Contracts are the integration backbone when we build in blocks: every boundary is defined
here **before** the code behind it exists, has a fake implementation and contract tests.

| Folder | What | First files |
|--------|------|-------------|
| internal/ | ports and events between ledger, wallet, matchmaking, game-engine, rng-core | `envelope.md`, `rng-port.md`, `ledger-port.md`, `match-events.md` |
| vendors/ | adapter contracts: Fireblocks, Sumsub, KYT (Chainalysis/Elliptic), Seon, MaxMind/Cloudflare, Notabene | one file per vendor |
| partner-api/ | B2B API – design document only until funded | `design.md` |
| player/ | states, messages, error texts, fairness card | `states-and-messages.md` |
| regulator/ | SAR, CTR, AOFA periodic report, incident notice, lab submission package | one file per format |

Rules: types live in `packages/shared`; this folder documents them for humans and reviewers.
A published event or port is versioned; breaking changes need an ADR.
