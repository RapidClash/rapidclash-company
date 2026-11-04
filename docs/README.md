# RapidClash docs (docs-as-code)

This folder is the single home for engineering and process documentation
(framework areas **02 Processes**, **03 Interfaces**, **07 Engineering**).
Governance, legal, policies and evidence live in Google Drive (see `_README RapidClash Workspace`).
Registers (roadmap, MVP, task tracking, decision log, document register) live in the
Google Sheet "RapidClash Launch Roadmap 2027".

## Rules

1. **One home.** A document lives here *or* in Drive, never both. Everywhere else: a link.
2. **Every document has front matter** (`id`, `title`, `status`, `version`, `owner`, `updated`).
   `id` comes from the document register (`RC-<area>-<nnn>`). Status: `draft → in-review → approved → superseded`.
3. **Changes go through pull requests.** `CODEOWNERS` routes reviews. Anything touching
   money, RNG, AML or player data needs a human approver **and** a Reviewer-assistant pass
   (a separate agent with fresh context) before merge.
4. **Approved is frozen.** To change an approved document, open a PR that bumps `version`
   and sets the old one to `superseded` in history – never edit in place silently.
5. **Language.** English in this repo (future hires, the certification lab and auditors read it).
   Lithuanian is fine in PR discussion and in Drive governance documents.
6. **Diagrams as code.** Mermaid blocks in Markdown; no binary diagrams except exported PNG/SVG
   next to the source.
7. **No secrets, no player data.** Nothing personal, no keys, no KYC material – ever.

## Layout

```
docs/
  README.md                  this file
  adr/                       Architecture Decision Records (MADR format, numbered)
  architecture/              system overviews, RNG dossier, network resilience, ledger design
  processes/
    process-map.md           L0 value chain + L1 end-to-end flows
    l2/                      L2 process descriptions (one file per process)
    runbooks/                step-by-step instructions for manual and hybrid processes
  interfaces/
    internal/                service contracts: ports, events, message envelope
    vendors/                 adapter contracts: custody, KYC, KYT, geo, travel rule
    partner-api/             B2B API (design only until funded)
    player/                  player-facing states, messages, fairness card
    regulator/               SAR / CTR / AOFA report and lab submission formats
  assistants/                AI assistant instructions per tandem + shared skills
  templates/                 copy these to start a new document
```

## How to add a document

1. Get an `id` from the document register (Sheet → "Dokumentų registras").
2. Copy the matching template from `docs/templates/`.
3. Fill front matter; write; open a PR; request the CODEOWNER.
4. When approved, set `status: approved`, add the date, and update the register.
