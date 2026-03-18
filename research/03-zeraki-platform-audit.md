# Zeraki Platform Audit: What Exists and What's Missing

## Company Overview

Zeraki is a Kenyan edtech company founded in 2014 by Isaac Nyangolo and Erick Oude. It started as a digital learning platform for high school students, pivoted to school data analytics during COVID-19, and has since expanded into school finance management.

- **Scale**: 4,000+ schools in Kenya, covering nearly half of high schools
- **Geography**: Kenya (primary), Uganda, Guinea, with plans for 10 new markets
- **Funding**: $1.8M seed (Dec 2022) led by Acumen Fund, with Save the Children Impact Investment Fund, Verdant Frontiers Fintech, and Logos Ventures
- **Team size**: Not publicly disclosed, but actively hiring (product designers, engineers)
- **Revenue model**: Subscription per school (pricing tiers not publicly available)

## Product Suite

### Zeraki Analytics (Core Product)

The most widely adopted product. A mobile-first school management system for academic data.

**What it does:**
- Teachers upload student grades from their phones
- Generates performance breakdowns per student, subject, and stream
- Produces PDF report cards and transcripts
- Tracks student attendance
- Stores student biographical and contact information
- Bulk SMS to parents (grades, announcements)
- Parent portal. Parents log in via app to view academic records and fee balances

**Why it matters for this case study:** It's the reason Zeraki is inside 4,000+ schools. Analytics is the distribution channel. Any new product (Plans, Credit) rides on the existing Analytics relationship with schools and parents.

### Zeraki Finance (Critical for This Case Study)

School accounting software integrated with Analytics.

**What it does:**
- **Cashflow summaries**: Shows how much fee has been collected versus what the school expected to collect each term
- **Receipting**: Records fee payments per student, issues receipts (has a companion thermal printer app for physical receipts)
- **Pledge tracking**: Records parent promises to pay (amount pledged, date promised, whether fulfilled)
- **Expense tracking**: Payment vouchers, LPOs, LSOs
- **Reporting**: Auto-generated fee statements, fee registers, cashbooks, trial balances
- **SMS fee reminders**: Bursar sends bulk SMS to parents about outstanding balances

**What it holds (the data that matters):**

| Data | Exists? | Notes |
|------|---------|-------|
| Fee structure per school per term | ✅ | Broken down by vote heads (tuition, lunch, exam, etc.) |
| Per-student fee balance | ✅ | Amount owed, amount paid, outstanding |
| Payment history per student | ✅ | Dates and amounts across multiple terms |
| Pledge records | ✅ | Promised amount, promised date, fulfilment status |
| Parent phone numbers | ✅ | Registered through school, used for SMS |
| Student registration numbers | ✅ | Used as M-Pesa paybill account number |
| School paybill number | ✅ | Configured in the system |
| School expense data | ✅ | What the school spends and when |
| Parent payment behaviour score | ❌ | Data exists to calculate this, but no scoring model |
| Structured instalment plans | ❌ | Pledges exist but not formal payment plans |
| Predictive collection forecasting | ❌ | Shows collected-vs-expected but doesn't predict future pace |
| Credit products | ❌ | No lending, no partner integration |
| Plan adherence tracking | ❌ | Pledges are tracked as yes/no, not as ongoing compliance |

### Zeraki Learning

E-learning platform with video lessons and quizzes for high school students. 500,000+ PlayStore downloads. KICD-approved content for 15 subjects. Has student, teacher, and parent login portals.

**Relevance to this case study:** Low. Learning is a separate product. However, the parent login system (phone number + password) is shared infrastructure that a Plans/Credit product could build on.

### Zeraki Timetables

Class scheduling tool for teachers. Integrates with Analytics.

**Relevance to this case study:** None.

## How Parents Interact with Zeraki Today

| Channel | What parents can do | Who uses it |
|---------|-------------------|-------------|
| **Zeraki parent app** | Log in to view academic records and fee balance | Smartphone parents who've been onboarded by the school |
| **SMS from school** | Receive fee balance reminders, grade notifications, announcements | All parents (school-initiated, via Zeraki's bulk SMS) |
| **School paybill (M-Pesa)** | Pay fees using student reg number as account number | All paying parents. This is the standard payment method |

**Key insight:** The SMS channel reaches everyone. The app reaches a subset. Any product designed for broad adoption must work via SMS first, with the app as an enhancement.

**Second key insight:** The parent doesn't interact with "Zeraki." They interact with their child's school. Messages come from the school. The app shows the school's name. Zeraki is invisible infrastructure. This is important for trust. The school is the brand, not the fintech.

## What's Missing: The Gaps That Create the Product Opportunity

### Gap 1: No structured instalment plans

Zeraki Finance has pledge tracking. The bursar records that a parent promised to pay KES 5,000 by March 15th. But a pledge is not a plan. There's no:
- Standard plan templates the school can offer (e.g., "4 weekly instalments")
- Parent self-selection of a plan (currently the bursar records pledges manually after a verbal conversation)
- Automated tracking of whether the parent is on schedule
- Distinction between "parent on a plan and paying" vs "parent with no plan and not paying"

The informal arrangements that happen at the school gate have no digital representation in Zeraki Finance. They exist in the bursar's memory or notebook.

### Gap 2: No payment behaviour analysis

Zeraki Finance stores payment history but doesn't analyse it. The system can tell you "Parent X paid KES 5,000 on February 12th." It cannot tell you:
- Parent X typically takes 4 weeks to clear fees, paying in 3 instalments
- Parent X has cleared fees in full for the last 6 terms
- Parent X's payment speed is slowing term over term
- Parent X honoured 80% of their pledges historically
- Parents in Form 2 pay faster on average than parents in Form 1

This analysis would be valuable for both the school (forecasting, identifying at-risk parents early) and for credit decisions (Layer 2).

### Gap 3: No predictive collection forecasting

The cashflow summary shows "collected vs expected", a backward-looking snapshot. It doesn't project forward. A bursar can see "we've collected 40% by Week 2" but can't see "based on historical patterns, we'll likely reach 75% by Week 4 and 92% by end of term."

Predictive forecasting would help schools plan expenses, manage teacher salary timing, and make informed decisions about enforcement, instead of panicking in Week 2 and sending everyone home.

### Gap 4: No credit or lending infrastructure

Zeraki's CEO has publicly stated the intention to build "payment products on the parents' side" and to support parents with "fee loans." As of the most recent public information, this hasn't shipped.

There is no:
- Credit scoring model based on fee payment data
- Integration with a lending partner (Pezesha, SACCO, MFI)
- Mechanism to disburse a loan directly to the school's paybill
- Parent-facing credit offer within the app or via SMS

### Gap 5: No inter-term engagement

Zeraki Finance is active during term. Bursars receipt payments, send reminders, track expenses. During school holidays, the system goes quiet. There's no communication with parents between terms about upcoming fees, no mechanism for early payment, and no way to track whether parents are preparing.

This gap is relevant but secondary to our focus. Layer 1 (Plans) operates during term. Layer 2 (Credit) operates during term. Inter-term engagement could be a future enhancement but isn't core to the product.

## Strategic Signals

### What the CEO has said publicly

From TechCrunch (December 2022):
> "We plan on building more administrative tools for schools, and payment products on the parents' side."

> "We've built an extensive distribution channel covering almost half of the high schools in Kenya, and that means we have an opportunity to solve other tech needs that schools have."

From Safaricom Newsroom:
> Schools asked Zeraki for "library and stock management systems, finance and accounting software" after adopting Analytics. This demand-led expansion pattern suggests schools would also adopt instalment plan management if offered.

### What the investors signal

Verdant Frontiers **Fintech** participated in the seed round. The inclusion of a fintech-focused investor suggests the fintech direction is part of the investment thesis, not just a founder aspiration.

## Technical Assumptions (To Be Validated)

- [ ] Zeraki Finance can expose per-student fee balances and payment history via an internal API or database query
- [ ] The school's M-Pesa paybill has real-time or near-real-time payment confirmations that Zeraki Finance can reconcile (via Safaricom C2B API)
- [ ] Zeraki's SMS gateway supports automated, scheduled sends, not just manual bulk sends triggered by the bursar
- [ ] Parent consent for fee-related communications can be managed through the existing school enrolment process
- [ ] Schools can configure instalment plan templates without needing Zeraki support for each setup

## Summary: What We're Building On

| Zeraki asset | How Layer 1 uses it | How Layer 2 uses it |
|-------------|--------------------|--------------------|
| Fee balance per student | Basis for instalment plan calculation | Determines top-up amount needed |
| Payment history | Validates plan adherence in real-time | Historical data feeds credit scoring |
| Pledge tracking | Evolves into formal plan tracking | Pledge fulfilment rate is a credit input |
| SMS channel | Sends plan confirmations and reminders | Delivers credit offers and repayment reminders |
| Parent app | Displays plan progress and schedule | Shows credit offer, terms, and repayment status |
| School paybill | Where instalment payments go (unchanged) | Where credit disbursement goes (directly to school) |
| Bursar dashboard | Shows plan adherence across all students | Shows credit arrangements and repayment status |

---

*Note: This audit is based entirely on publicly available information, including Zeraki's website, app store listings, press coverage (TechCrunch, Safaricom Newsroom), investor disclosures, and LinkedIn. I do not work at Zeraki and have not had access to internal documentation, product roadmaps, or proprietary data. Assumptions about internal capabilities are flagged as such and would need validation with the Zeraki team.*