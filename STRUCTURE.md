# Document Structure Map

A high-level navigation guide for AI agents or human readers approaching this repo.

## Parts

| Part | Status | Topic | Repo? |
|---|---|---|---|
| Part 1 · UK BESS developer signal engine | Shipped | Battery storage developer surfacing for a Norwegian GTM/ABM agency on behalf of their BESS-vendor client | Public · github.com/Miksh21/bess-signal-pipeline |
| Part 2 · Dateio CEE retailer terminal-growth engine | In progress | Multi-market retail terminal growth pipeline at Dateio (B2B fintech ad-tech) | Internal to Dateio |
| Part 3 · LinkedIn hiring-post outreach pipeline | Operating | Fractional GTME engagement at a B2B HR-tech client — outbound forensics + operations | Client IP |
| Part 4 · The Duvo proposal | The JD answer | What Jan would wire first at Duvo across all four JD pillars | This repo |

## Part 4 sections

1. **Signals + Campaigns** — Signal A (retail leadership change) + Signal B (post-RPA disillusionment), with six worked campaign instances across both signals × three tiers
2. **Tier routing** — Tier 1 Hot (Tomáš manual) / Tier 2 Warm (Smartlead CEO sequence) / Tier 3 Cool (Smartlead daily batch) + AI reply classifier + ghost-recovery agent
3. **Internal tooling** — 10 vibecoded micro-builds, classifier + copy agent as the flagship pair
4. **Rollout plan** — Four-week sequencing (Week 1 access + warmup → Week 4 both signals live)
5. **Stack cost** — ~$780–1,480/mo at pilot scale, ~500–1,000 accounts monitored

## Key architectural decisions

- **Tomáš's email from-name on all 3 tiers** via Maildoso secondary domains (`tomas.cupr@duvo-team.com`), protecting `@duvo.ai` inbox reputation regardless of volume
- **Tomáš's personal LinkedIn = manual forever.** No HeyReach, no automation, ever
- **AE's LinkedIn = HeyReach for Tier 1** once first AE is hired (high-touch tier, where LinkedIn automation belongs)
- **Tier 2 + 3 = email-only at every phase.** Never any LinkedIn
- **AI classifier** = single n8n + Anthropic API workflow, 7-category JSON output, calendar-aware, tier-aware Slack routing, never replies as the rep
- **Ghost-recovery agent** = pre-meeting Supabase state object + Gong/Granola held-check + recovery sequence from the same email thread on a 2–3 week cadence
- **Booked + held meeting** = canonical terminal that all Signal A/B diagrams end on

## Diagrams

All six mermaid diagrams are in `/diagrams/` as standalone `.mmd` files. They also appear inline in `README.md` as fenced mermaid blocks. The canonical version is the standalone `.mmd` file — the README is a mirror.
