---
name: teardown-playbook
description: Run a deterministic AI-visibility teardown on any local business website — 11 live checks, 0-100 score, findings, and 30-day fixes. Use when evaluating a business's web presence or generating a sales asset.
---

# Teardown Playbook — AI-Visibility Teardown

Run a structured, deterministic teardown of any business website. No LLM inference required — every check is a live probe. Output is a scored report usable as a sales asset (the "free audit" that opens a $499/mo conversation).

## The 11 checks

| # | Check | Pass | Warn | Fail |
|---|---|---|---|---|
| 1 | DNS resolves | A record found | Slow resolution (>3s) | No A record |
| 2 | Reachability | HTTP 200 < 5s | Redirects / slow | Timeout / 4xx / 5xx |
| 3 | HTTPS | Valid cert, no warnings | Mixed content | No HTTPS / expired cert |
| 4 | Title tag | Present, < 70 chars, business-relevant | Present but generic | Missing |
| 5 | Meta description | Present, 120–160 chars | Present but short/long | Missing |
| 6 | Mobile viewport | `viewport` meta + responsive | Viewport only | Neither |
| 7 | Tap-to-call | `tel:` link visible on mobile | Phone as plain text | No phone found |
| 8 | Facebook link | Links to a live FB page | FB link present but dead | No social link |
| 9 | Contact form | Form with name/message fields | Email link only | No contact path |
| 10 | Visible phone | Phone in header/hero | Phone in footer only | No phone anywhere |
| 11 | Google Business Profile signal | NAP consistent + maps embed/reviews link | Partial | None detected |

## Scoring

- Pass = 10, Warn = 5, Fail = 0. Total / 110, scaled to 0–100.
- 80+: healthy. 50–79: fixable gaps — lead with the top 3. <50: rebuild conversation.

## Report format

1. **Score + one-line verdict** ("62/100 — visible but leaking calls").
2. **Top 3 fixes** ordered by revenue impact (missed calls > SEO polish, always).
3. **Full check table** with per-check status and one-line detail.
4. **30-day fix list** — concrete actions, no jargon.

## Rules

- Every claim verified same-day against the live site. Never invent a check result.
- Re-run before sending — sites change; a stale teardown is a lie.
- The teardown is the opener, not the product. End every report with the next step (the paid offer), not with the audit itself.

## Live reference implementation

A working $0-cost implementation of this playbook runs at:
- Web (free, 3/day): https://citrus-coast-ai-teardown.onrender.com
- API (x402, $0.50 USDC on Base): POST https://citrus-coast-ai-teardown.onrender.com/api/teardown
- Agent card: https://citrus-coast-ai-teardown.onrender.com/.well-known/agent.json
