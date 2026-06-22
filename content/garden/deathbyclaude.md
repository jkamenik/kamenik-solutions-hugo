---
title: "DeathByClaude"
date: 2026-06-17
lastmod: 2026-06-22
draft: false

keywords:
  - DeathByClaude
  - Death by Clawd

params:
  aliases:
    - Death by Clawd
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
    subcategories:
      - ai-techniques
---

[DeathByClaude](https://deathbyclawd.com/) (branded **Death by Clawd**) is a satirical SaaS replaceability scanner. It scores whether a product's core value could be replicated by a Claude Skill (a `.md` instructions file). We **trial** it as a quick AI-disruption vibe check during company research. Treat scores as provocative heuristics, not diligence evidence.

## Blurb

> Find out if your SaaS can be replaced by a Claude Skill. The SaaSpocalypse Survival Scanner.

## Summary

**What it is:** A public web app where you enter a company domain and get a **death score** (0-100), a rating band, a one-liner roast, and a mock `SKILL.md` replacement. The site frames the **SaaSpocalypse**: AI agents lowering the bar to replicate UI-wrapper SaaS.

**When to use:** early **[[gbrain]]** company profiles when you want a memorable disruption snapshot; brainstorming moat strength before deeper research; sharing a concrete "could this be a skill?" prompt with stakeholders.

**When to skip:** investment, acquisition, or compliance decisions that need audited evidence; companies where the scanner lacks context (hardware, regulated infra, frontier labs); replacing product teardown or financial analysis.

**Not the same as:** rigorous competitive intelligence; **[[Agent Skills Framework]]** itself (the portable skill format); **[[Netlify]]** (only the host). The scanner is commentary with an API, not a neutral data vendor.


## Details

| Topic | Notes |
|-------|--------|
| **URL** | https://deathbyclawd.com/ (`?url=<domain>` pre-fills the scanner) |
| **Hosting** | Runs on **[[Netlify]]**; serverless analyze endpoint at `/.netlify/functions/analyze` |
| **Score scale** | 0 = most AI-resistant, 100 = most at risk; bands include SAFE, SWEATING, CRITICAL, Flatlining, ALREADY DEAD |
| **Outputs** | `deathScore`, `deathRating`, `oneLiner`, `causeOfDeath`, optional `skillMdFile`, `metrics`, `eulogy` |

**API (programmatic scan):**

```bash
curl -sL -X POST "https://deathbyclawd.com/.netlify/functions/analyze" \
  -H "Content-Type: application/json" \
  -d '{"url":"<domain>"}'
```

Pass the bare domain (e.g. `sola.security`), not a full URL. The company-research skill uses this endpoint when building `resources/companies/` profiles.

**How to read results:** Low scores often reflect physical goods, deep enterprise lock-in, or infra Claude cannot trivially replicate. High scores target form builders, dashboards, and thin AI wrappers. The humor is the point, but the underlying question (is the moat more than UI?) is worth asking in every SaaS eval.

**References**

- [Death by Clawd](https://deathbyclawd.com/)
- [Agent Skills Framework](https://agentskills.io/) (the `.md` skill model the site riffs on)
