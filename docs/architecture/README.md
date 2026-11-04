# Architecture (area 07)

Human-readable overviews that the ADRs point to. Source of detail for the certification
lab and auditors.

| File | Content | Source today |
|------|---------|--------------|
| overview.md | two planes, services, data stores (mermaid) | sheet "Platforma", "Tinklo atsparumas" |
| rng-provably-fair.md | RNG dossier: rng-core, two reserved seeds, derivation, verifier, tests | sheet "RNG ir Provably Fair" + seed schema SVG |
| ledger.md | chart of accounts, posting rules, escrow, reconciliation | sheet "Ledger PostgreSQL" |
| network-resilience.md | session resume, grace windows, lag compensation, regions | sheet "Tinklo atsparumas" |
| wallet-custody.md | Fireblocks vault structure, TAP, sweep, coverage ratio | sheet "Wallet struktūra" |

Migration rule: when a sheet section becomes an engineering document here, the sheet row
gets a link and stops being edited – one home.
