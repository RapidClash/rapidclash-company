# Issue registry

A lightweight, append-only log of open operational issues — access problems,
tooling gaps, decisions blocking someone — things that need tracking but
aren't a roadmap item (Sheet) or a formal process/spec (`docs/`). Separate
from GitHub Issues: this stays readable and writable by anyone with repo
access, human or AI assistant, without needing GitHub's Issues UI or API.

**How to use this file**

- **New issue:** append a new `###` entry at the top, right below this
  block. Give it the next `ISSUE-NNN` number (IDs are never reused, even
  once an issue closes and moves to history — check both this file and
  `ISSUES_HISTORY.md` for the highest existing number).
- **Close an issue:** set `status: CLOSED`, add a `closed:` timestamp and a
  one-line resolution, then move the whole entry to the top of
  `ISSUES_HISTORY.md` in the same PR. Don't edit it in place and leave it
  here — closed issues don't stay in this file.
- **Review:** every change here still goes through a PR with one approval
  (CODEOWNERS routes this file to all four current people, so any one of
  you — not only Ramūnas — can approve). An AI assistant may draft and open
  the PR; a human merges it. Same rule as everywhere else in this repo.

---

### ISSUE-004 — Issue file access confirmation

- **status:** NEW
- **timestamp:** 2026-11-06T00:00:00Z
- **reporter:** Ramūnas (A3)

**Description**

Every person and AI assistant actually operating in this repo should
confirm, in writing, right here, that they can read this file and open a
PR updating it. Not a formality — it's the cheapest possible smoke test for
ISSUE-003 (not everyone has a working path to update GitHub yet). Append a
line under **Confirmations** below with your name/assistant, the date, and
how you read/wrote it (WSL + Claude Code, GitHub web editor, a Claude.ai
connector, etc.) — that detail is useful data for closing ISSUE-003.

**Confirmations**

- Claude (Sonnet 5), running as Ramūnas's assistant via Claude Code/WSL —
  2026-11-06 — drafted and opened the PR creating this file; confirms the
  write path works from this session. Ramūnas's own confirmation as the
  human on this seat is still needed separately, alongside everyone else's.
 - Ramunas - 2026-11-06 confirmed access
 - Povilas - 2026-11-06 confirmed access
- Claude (Opus 5.5), running as Povilas's assistant in the Claude app
  (claude.ai, cloud session with the GitHub repo attached, no WSL/CLI on
  his PC) — 2026-11-06 — read this file and opened the PR adding this
  line; confirms the read and write path works from the Claude app.
  Data point for ISSUE-003: the in-app path worked once the GitHub
  connection was granted push access to this repo — it was refused at
  first, before that access was in place.
  - Giedrius - 2026-11-06 confirmed access
---

### ISSUE-003 — GitHub update access for non-WSL tandems

- **status:** NEW
- **timestamp:** 2026-11-06T00:00:00Z
- **reporter:** Ramūnas (A3)

**Description**

Right now only Ramūnas has a working setup for updating GitHub directly
(Claude Code in WSL, with a personal token scoped to the org). Giedrius,
Povilas and Aleksandra use the Claude app on their own PCs, not Claude
Code — they don't have a git/CLI-based path to read or write this repo
yet. Needs a solution for each of them, individually, since what's
available depends on what their own Claude app setup supports:

- **Browser editing, no setup needed, works today.** All three already
  have repo access (member/owner). GitHub's own web file editor (the
  pencil icon on any file, or github.com/RapidClash/rapidclash-company)
  lets anyone with Write access edit a file and open a PR straight from
  the browser — no token, no CLI. Covers occasional edits like this
  registry; doesn't cover anything needing local tooling (running tests,
  CI, etc.).
- **A GitHub connector inside the Claude app**, if their account has one
  available to enable (Settings → Connectors, or similar) — would let
  their AI assistant read/write the repo directly from the chat app,
  closer to what this WSL session does. Unconfirmed whether this is
  available to them; each person needs to check their own app.
- **Installing Claude Code themselves** — the full setup this session
  uses. Works for anyone, but a bigger ask for non-engineers; not the
  default recommendation here.

**Open question:** which of these (or a mix) each of the three actually
wants/needs — not something to decide for them from this session.

---

### ISSUE-002 — Roadmap tracker: accessible to humans and AI assistants

- **status:** NEW
- **timestamp:** 2026-11-06T00:00:00Z
- **reporter:** Ramūnas (A3)

**Description**

The live roadmap/task tracker is a Google Sheet, access-restricted to 4
human email accounts — AI assistants can't read or write it, and this
session confirmed it can't even open it. Proposed direction (not yet
decided): migrate the two actively-updated tracker tabs ("Darbų sekimas ir
tvirtinimas" and "MVP") to GitHub Projects (v2) — free on any plan, API/CLI
accessible, same access model already set up for this repo. The other
~16 Sheet tabs (Roadmap gantt, Biudžetas, Licencijos checklist, Dokumentų
registras, Sprendimų žurnalas, technical spec tabs) stay in the Sheet —
they're reference/governance material, not something bots need to write to
routinely.

**Options**

1. Migrate the two tracker tabs to GitHub Projects (recommended — matches
   the framework document's own named exit plan: "until volume justifies
   GitHub Projects or Linear").
2. Grant the AI-assistant-connected Google account(s) read/write access to
   the Sheet instead of migrating. Simpler short-term, keeps the
   spreadsheet-editing UX everyone already knows; doesn't solve the
   "two copies, two owners" risk if some people keep editing one while
   others edit via API.
3. Do nothing yet; keep today's split (humans in the Sheet, bots blind to
   it) until it causes a real problem.

**Needs:** an owners' decision, then (if option 1) a one-time CSV export
of the two tabs for the actual migration, plus adding the `project` scope/
permission to each person's GitHub token.

---

### ISSUE-001 — GitHub plan: paid tier needed for branch protection

- **status:** NEW
- **timestamp:** 2026-11-06T00:00:00Z
- **reporter:** Ramūnas (A3)

**Description**

Confirmed directly: GitHub blocks branch protection and CODEOWNERS
enforcement on a **private** repo unless the org is on a paid plan — Free
only gets those on public repos. The repo is public right now specifically
to work around this while the plan decision is pending; the intent is to
go private again once a plan is chosen.

**Options**

1. **GitHub Team** (~$4/user/month — confirm the current number on
   github.com/pricing before budgeting; it bills per org *member*, and
   outside collaborators don't count as billable seats, so keeping
   membership lean could matter here). Unlocks branch protection, CODEOWNERS
   enforcement, required reviewers, more Actions minutes.
2. Stay on Free, keep the repo public indefinitely. No cost, but the
   platform code and AI-assistant instructions this repo is meant to hold
   (per ADR-0001) become visible to anyone, pre-launch.
3. GitHub Enterprise — not sized for a 4-5 person team; not recommended now.

**Needs:** a decision from the owners (now three: Ramūnas, Giedrius,
Povilas) and someone to set up billing. Billing/plan changes are
explicitly left to the owners, not this session.

---
