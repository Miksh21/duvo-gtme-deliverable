# Duvo GTM Company OS — proposed structure sketch

> **This file is an idea, not a delivered artifact.** It outlines what the full Duvo GTM Company OS could look like — modelled on gtm-master's 4-layer operating model (Input → Rules → Skills → Memory) and Workflows.io's published [`company-os-starter-kit`](https://github.com/Workflowsio/company-os-starter-kit) pattern, tailored to Duvo's actual GTM surfaces (Clarity-as-wedge motion, signals A–F, multi-voice cast, customer roster).
>
> **What I commit to in week 3–4 of the transition:** seed the structure + start the memory-writes-back loop on one slice. **Everything else builds over months and years, in production, with the team.**

---

## Proposed directory tree

```
duvo-gtm-os/                          # Git repo, vector-indexed for semantic query
│
├── README.md                          # entry point + querying guide
├── CLAUDE.md                          # rules layer · the OS constitution
│
├── 1-positioning/                     # how we talk about Duvo
│   ├── clarity-value-prop.md          # process mapping in days, not months
│   ├── automation-value-prop.md       # agents that close manual ops work
│   ├── reliable-execution.md          # brand line · queue · audit · human-in-loop
│   ├── lego-not-playdoh.md            # competitive framing vs generic AI
│   ├── tomas-rohlik-origin.md         # founder narrative · "human API"
│   └── customer-roster.md             # public + private outcomes
│
├── 2-icp/                             # who we sell to
│   ├── tier-1-enterprise-retail.md    # €500M+ SAP multi-market
│   ├── tier-2-midmarket-retail.md
│   ├── adjacent-fmcg-cpg.md
│   ├── geo-cee.md                     # CZ / SK / HU / RO / DE / AT
│   ├── geo-uk-dach.md
│   └── _scoring-rubric.md             # 0–100 scale · ICP-40 + Signal-40 + Persona-20
│
├── 3-personas/                        # 5-role committee × per vertical
│   ├── economic-buyer-coo-cfo.md
│   ├── champion-supply-chain-procurement.md
│   ├── technical-sap-it-rpa.md
│   ├── finance-fpa.md
│   ├── end-user-ops-analyst.md
│   ├── transformation-process-excellence.md   # Clarity's direct buyer
│   └── _committee-multithread.md      # Tier-1 fan-out logic
│
├── 4-customers/                       # cases + one-liners per buyer role
│   ├── rohlik.md                      # €2.1M / €1.4M · CZ → DE → HU → AT → RO
│   ├── notino.md                      # 468 hrs/yr · 10+ processes · review-reply
│   ├── pilulka.md                     # +15% stock in 2 weeks
│   ├── topfer.md                      # process mapping + transformation · DACH
│   ├── travel-retailer-anon.md        # €1M leakage surfaced in 1–2 days
│   └── _index.md                      # cross-cut by vertical · use case · outcome
│
├── 5-signals/                         # what fires what · scoring · routing
│   ├── a-leadership-change.md
│   ├── b-post-rpa.md
│   ├── c-s4hana-migration.md
│   ├── d-margin-mandate.md
│   ├── e-expansion-mna.md
│   ├── f-events-engagement.md
│   ├── _scoring-and-slas.md           # 0–100 · T1 <1h / T2 <24h / T3 weekly
│   ├── _composite-stacking.md         # multi-signal heat rules
│   └── _add-a-signal-template.md      # recipe for the 7th, 8th, 9th
│
├── 6-copy/                            # proven + evolving
│   ├── _modular-templates.md          # T1 / T2 / T3 templates
│   ├── opener-matrix-signal-x-tier.md # the 18-cell matrix (grows w/ new signals)
│   ├── committee-per-role.md          # 5 voice samples
│   ├── winning-variants-log.md        # ← memory writes here from copy-intelligence
│   └── losing-variants-log.md         # ← what stopped working · when · hypothesis
│
├── 7-objections/                      # what they push back + how we respond
│   ├── budget.md
│   ├── timing.md
│   ├── competitor-uipath.md
│   ├── competitor-sap-build.md
│   ├── security-audit-compliance.md   # MEDDPICC + reliable execution
│   └── _index.md
│
├── 8-process/                         # operational rules
│   ├── meddpicc-fields.md
│   ├── qualification-gates.md         # 7-gate pipeline (per gtm-master)
│   ├── tier-routing.md
│   ├── crm-state-gates.md             # don't collide with in-flight deals
│   ├── scale-gates.md                 # 3 gates before ramping volume
│   └── slas.md
│
├── 9-skills/                          # Claude Code skills · playbooks-as-code
│   ├── icp-modeller/                  # vague description → tiered model
│   ├── outbound-copywriter/           # drafts in voice via opener matrix
│   ├── discovery-prep/                # pre-call brief per account
│   ├── reply-classifier/              # 7-cat MEDDPICC auto-fill
│   ├── signal-router/                 # signal × persona → tier · SLA · voice · draft
│   └── _index.md
│
├── 10-clients/                        # per-account context (auto-synced from CRM)
│   ├── _template-account.md           # firmographic · signal-history · MEDDPICC · outreach-log
│   └── [account-slug]/                # one folder per Tier-1 account
│       ├── account-card.md
│       ├── signals-log.md
│       └── outreach-log.md
│
├── 11-metrics/
│   ├── kpis.md
│   ├── weekly-snapshots/              # rolling state · feeds compounding
│   ├── benchmarks-internal.md
│   ├── benchmarks-external.md         # gtm-master + Workflows.io
│   └── outcomes-vs-predictions.md     # the learning corpus
│
└── raw/                               # unstructured dumping ground (Trigify pattern)
    ├── transcripts/                   # webinars, calls, podcasts (e.g. 21 May)
    ├── ideas/
    └── slack-clips/                   # paste-ins for later structuring
```

---

## How it's queryable — simply

- **Git-tracked markdown** = grep-able, diff-able, version-controlled. Every change has a commit; every claim has a source.
- **Vector layer** (LanceDB or similar, cron-indexed against the markdown) = semantic lookup. AEs ask in natural language; the system surfaces the relevant file(s).
- **Claude / Cowork as the query layer**, sitting on top of Git + vector. AE on a call: *"What's our line on S/4HANA migration objections?"* → answer in seconds, with source links into `/5-signals/c-s4hana-migration.md` and `/7-objections/timing.md`.
- **Per-account context** (`/10-clients/[account-slug]/`) auto-syncs from HubSpot via n8n. The discovery-prep skill reads from there before any call.

---

## The self-improvement loop · memory writes back to itself

This is what separates a Company OS from a wiki:

1. Outbound runs (the system overview's `Detect → Qualify → Engage → Convert → Learn` engine).
2. Reply classifier tags each reply with MEDDPICC fields.
3. **Winning variants** (by reply rate, by tier) auto-append to `/6-copy/winning-variants-log.md`.
4. **Losing patterns** auto-append to `/6-copy/losing-variants-log.md` with the date they stopped working + hypothesis.
5. **Signal calibration** adjusts based on outcomes — `/5-signals/_composite-stacking.md` gets re-weighted as deals close.
6. **Per-account memory** grows in `/10-clients/[account-slug]/` — every signal, every reply, every meeting note.

The vault becomes a *living model of the business*, not a passive log (the Trigify-Obsidian pattern that gtm-master cites).

---

## Scope: week 3–4 vs months vs years

### Week 3–4 (the actual commitment)

- Scaffold the directory tree above
- Port what already exists in this addendum:
  - `1-positioning/` ← from "What Duvo sells today"
  - `2-icp/` ← from v1 + the addendum scoring rubric
  - `4-customers/` ← from the customer roster (Rohlik / Notino / Pilulka / Töpfer)
  - `5-signals/` ← from Signals A–F (v1 + addendum)
  - `6-copy/` ← from modular templates + opener matrix
- Wire one query interface (Claude / Cowork on Git + a vector layer)
- Start the **memory-writes-back loop** on `/6-copy/winning-variants-log.md` — the cheapest, highest-frequency feedback signal

### Months 2–3

- `CLAUDE.md` — the OS constitution (writing voice · what to always check · what to never do)
- `3-personas/` and `7-objections/` content (populated from real sales-call data)
- `9-skills/` — first 2–3 skills built (signal-router, reply-classifier, discovery-prep)
- `10-clients/_template-account.md` defined; first ~10 accounts seeded

### Months 6+

- `10-clients/` auto-sync running per Tier-1 account
- `11-metrics/weekly-snapshots/` compounding into a real learning corpus
- AEs actively querying on live calls (the test of usefulness)

### Year 1+

- Full self-improvement loop running across signals, copy, objections, qualification
- Marketing briefs read from + write back to it
- New-hire onboarding = read the OS, watch one week of live operation

---

## Honest framing

This sketch is a **target, not a promise.** The full OS is a months-of-work project for a v1 and years to compound real value. **What I commit to in week 3–4 is seeding the structure and proving the query pattern works on one slice** — so the compounding can start day one. Everything else builds with the team, in production, over quarters.

- The gtm-master 4-layer reference (`Company OS → client repos → skill library → MCP / CLI execution`) is the model.
- Workflows.io's [`company-os-starter-kit`](https://github.com/Workflowsio/company-os-starter-kit) is the working pattern to learn from.
- The Trigify-Obsidian pattern (memory vault that writes back to itself) is the loop discipline.

The result has to be **Duvo's** — not a copy of any of them.
