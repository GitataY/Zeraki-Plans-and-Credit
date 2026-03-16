# Zeraki Savings: Embedded School Fee Savings for Kenya

> A product case study exploring how Zeraki - Kenya's largest school management platform - could embed a micro-savings and fee financing product for parents, using existing payment infrastructure and behavioural nudging to turn the school fees crisis from a termly emergency into a manageable daily habit.

## Why This Exists

School fees are the single biggest financial stressor for low-income Kenyan families. Every January, May, and September, millions of parents scramble to pay - borrowing from shylocks at 20%+ monthly interest, pulling children out of school, or going into debt spirals. Meanwhile, Zeraki already sits inside 4,000+ schools with fee tracking, parent communication, and payment data. The infrastructure exists. The data exists. The product doesn't - yet.

This repo is a full product case study: research, PRD, user stories, technical architecture, and go-to-market strategy for an embedded savings and fee financing product built on top of Zeraki's existing platform.

## Repo Structure

```
├── research/                    # Market research, competitive analysis, data
│   ├── 01-problem-sizing.md         # The school fees crisis in numbers
│   ├── 02-competitive-landscape.md  # Who else is trying to solve this
│   ├── 03-zeraki-platform-audit.md  # What Zeraki has today and what's missing
│   ├── 04-parent-payment-behaviour.md # How parents actually pay fees
│   └── 05-regulatory-landscape.md   # Lending licenses, CBK sandbox, consumer protection
│
├── product/                     # Core product documents
│   ├── 01-prd.md                    # Full product requirements document
│   ├── 02-user-personas.md          # Parent personas based on payment behaviour
│   ├── 03-user-stories.md           # Epics and user stories
│   ├── 04-metrics-framework.md      # KPIs, success metrics, tracking plan
│   └── 05-risks-and-mitigations.md  # What could go wrong
│
├── design/                      # UX flows, wireframes, interaction design
│   ├── 01-sms-nudge-flows.md        # SMS message sequences and logic
│   ├── 02-parent-app-flows.md       # App-based progress tracking UX
│   └── 03-school-admin-dashboard.md # Bursar/admin view in Zeraki Finance
│
├── technical/                   # Architecture, integrations, data models
│   ├── 01-system-architecture.md    # How this sits on Zeraki + M-Pesa paybill
│   ├── 02-data-model.md             # Core entities and relationships
│   ├── 03-integrations.md           # M-Pesa API, Zeraki Finance, SMS gateway
│   └── 04-underwriting-model.md     # Credit scoring from fee payment behaviour
│
├── go-to-market/                # Launch strategy
│   ├── 01-pilot-plan.md             # 50-school pilot design
│   ├── 02-school-pitch.md           # How to sell this to school administrators
│   └── 03-partnership-strategy.md   # MFI/SACCO/Pezesha integration approach
│
└── .claude/                     # Claude Code project context
    └── CLAUDE.md                    # Project brief for Claude Code sessions
```

## Key Product Decisions

| Decision | Choice | Rationale |
| --- | --- | --- |
| Payment mechanism | Existing school paybill + student reg number | Zero behaviour change for parents; school already reconciles via Zeraki Finance |
| Primary channel | SMS (not app-first) | Majority of target parents don't use the Zeraki app; SMS reaches everyone |
| Savings model | Pre-payment to school account, not separate wallet | Avoids pooled fund regulation; money goes directly to school; builds trust |
| Credit model | Fee deferral (school-funded) first, MFI top-up second | Deferral requires no lending license; MFI partnership adds complexity |
| Targeting | Parents with 2+ terms of Zeraki Finance payment history | Need behavioural baseline to segment and nudge effectively |

## Context

This is one project in a broader portfolio exploring embedded finance opportunities for underserved populations in East Africa. Other case studies in progress:

- **Fuliza for electricity** —> prepaid utility credit for Kenya Power customers
- **Kwendo financial identity** —> work-data-to-credit pipeline for casual workers

## How to Use This Repo

If you're a **product manager**: Start with `research/01-problem-sizing.md` for context, then read `product/01-prd.md` for the full product spec.

If you're a **founder or investor**: Start with `README.md` (you're here), then `go-to-market/01-pilot-plan.md` for the launch strategy.

If you're an **engineer**: Start with `technical/01-system-architecture.md` for the integration approach.

If you're **Zeraki**: I'd love to talk. This product builds on what you've already created and aligns with the payment products roadmap your CEO described publicly.

---

*Built with research, not assumptions. All market data is sourced and cited in the research documents.*
