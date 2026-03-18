# Zeraki Plans & Credit: Embedded Fee Management for Kenyan Schools

> Kenyan schools already let parents pay fees in instalments. The headteacher negotiates at the gate, the bursar scribbles in a notebook, and children get sent home when the informal system breaks down. This case study explores how Zeraki - already inside 4,000+ schools - could formalise what's already happening and layer affordable credit on top for parents who need it.

## The Problem (It's Not What You Think)

Parents don't forget school fees exist. Every parent in Kenya knows the dates: January, May, September. The problem is:

- **Schools need cash on Day 1** to pay teachers, buy supplies, and operate - but fees trickle in over 8-12 weeks
- **Parents earn in small, irregular amounts** and can't accumulate a lump sum by the deadline
- **The informal arrangement system is invisible and undignified** - parents negotiate verbally, agreements live in someone's memory, and children are sent home when the system fails
- **When parents borrow to cover the gap**, they pay 15-20%+ monthly interest to digital lenders or shylocks

The child who gets pulled out of class and sent home isn't experiencing a financial event. They're experiencing a humiliation that affects their learning, their confidence, and their relationship with school.

## What Zeraki Already Has

Zeraki Finance is an accounting tool used by 4,000+ Kenyan schools. It tracks fee balances, processes receipts, monitors expenses, tracks pledges, and sends SMS fee reminders to parents. Parents can view balances through the Zeraki app.

**What it doesn't do:** structured instalment plans, payment behaviour analysis, predictive collection forecasting, or credit products. The data to power all of this already exists in the system. It's just not being used.

Zeraki's CEO has publicly stated they plan to build "payment products on the parents' side." This case study is a blueprint for what those products could look like.

## The Product: Two Layers

### Layer 1 - Zeraki Plans: Formalised Fee Instalment Arrangements

Replace the informal, verbal, gate-negotiation system with structured payment plans managed through Zeraki Finance.

**For parents**: Select a payment plan at the start of term (e.g., 4 weekly instalments). No begging, no negotiating, no performing poverty at the school gate. If you're on a plan and making payments, your child stays in school.

**For schools**: A dashboard showing which parents are on plans, who's on track, who's behind - replacing 150 individual verbal negotiations with a system. The bursar stops being a debt collector and starts being an administrator.

**For children**: They stay in school. That's the point.

### Layer 2 - Zeraki Credit: Top-Up Financing for Parents Who Need It

Life happens. A parent who's paid on time for 6 straight terms suddenly can't this term - a hospital bill, a funeral, a job loss. Another parent has been on an instalment plan, made 3 of 4 payments, and then hit a wall in the final week. Both deserve affordable credit. Neither should have to borrow from a shylock at 20% interest.

Layer 2 serves **two groups**:
- **Historically strong payers** whose Zeraki Finance records show consistent, timely payment across multiple terms - but who need help this particular term. The data already exists. No instalment plan required.
- **Plan-adherent parents** from Layer 1 who've demonstrated commitment (3+ scheduled payments made) but fell short due to a disruption.

**Key design decisions:**
- Money goes directly to the school's paybill - never touches the parent's M-Pesa
- Underwritten by actual fee payment behaviour from Zeraki Finance - not phone metadata
- Interest dramatically lower than digital lenders
- Not just for struggling families - any parent can have a bad term, and the data should reflect their full history, not just this moment

## Why This Works

Layer 1 creates **new behavioural data** that doesn't exist today - not just "did they pay eventually" but "did they stick to a weekly commitment?" That data, combined with the **historical payment records** Zeraki Finance already holds, powers Layer 2.

Layer 2 uses both signals - years of payment history AND recent plan adherence - to offer credit at the **exact moment it's needed**, to people who've **earned it through their track record**, for a **specific purpose**, through a channel they **already use**. A parent with 6 terms of perfect payment history doesn't need to go through an instalment plan to prove they're creditworthy. The data is already there.

Neither layer assumes parents are forgetful or irresponsible. Layer 1 adds structure to what already happens informally. Layer 2 adds a safety net for when income doesn't match obligations - which is the actual problem.

## Repo Structure

```
├── research/
│   ├── 01-problem-sizing.md
│   ├── 02-how-fees-actually-work.md
│   ├── 03-zeraki-platform-audit.md
│   ├── 04-competitive-landscape.md
│   └── 05-regulatory-landscape.md
│
├── product/
│   ├── 01-prd-layer1-plans.md
│   ├── 02-prd-layer2-credit.md
│   ├── 03-user-personas.md
│   ├── 04-user-stories.md
│   ├── 05-metrics-framework.md
│   └── 06-risks-and-mitigations.md
│
├── design/
│   ├── 01-parent-experience-flows.md
│   ├── 02-school-admin-dashboard.md
│   └── 03-sms-notifications.md
│
├── technical/
│   ├── 01-system-architecture.md
│   ├── 02-data-model.md
│   ├── 03-integrations.md
│   └── 04-underwriting-model.md
│
├── go-to-market/
│   ├── 01-pilot-plan.md
│   ├── 02-school-pitch.md
│   └── 03-partnership-strategy.md
│
└── .claude/
    └── CLAUDE.md
```

## Author

Yvonne Gitata - Product Manager
[Portfolio](https://www.notion.so/Hey-I-m-Yvonne-2ff02075289d80e49bf2eafe9b44a319) | [LinkedIn](https://www.linkedin.com/in/yvonne-gitata-3b7151237/) | [Medium](https://wamuyugitata.medium.com/) | [GitHub](https://github.com/GitataY)

---

## How to Use This Repo

If you're a **product manager**: Start with `research/01-problem-sizing.md` for context, then read `product/01-prd.md` for the full product spec.

If you're a **founder or investor**: Start with `README.md` (you're here), then `go-to-market/01-pilot-plan.md` for the launch strategy.

If you're an **engineer**: Start with `technical/01-system-architecture.md` for the integration approach.

If you're **Zeraki**: I'd love to talk. This product builds on what you've already created and aligns with the payment products roadmap your CEO described publicly.

---

*Built with research, not assumptions. The first assumption we killed was that parents forget to pay school fees - they don't. It's an income problem, not a memory problem.*
