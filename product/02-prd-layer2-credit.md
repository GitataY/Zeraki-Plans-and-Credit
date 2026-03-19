# Product Requirements Document: Layer 2 - Zeraki Credit

## 1. Overview

### Product name
Zeraki Credit

### One-liner
Affordable, purpose-locked fee top-up financing for parents who have demonstrated commitment through their payment history, delivered through Zeraki Finance and paid directly to the school.

### Problem statement
Even parents who consistently pay fees can hit a rough term. A hospital bill, a job loss, a funeral contribution, a slow work season. When this happens, their options are: borrow from a digital lender at 15%+ monthly interest, borrow from a shylock at worse rates, or let their child be sent home. None of these options are proportionate to the problem. A parent who's paid in full for 6 straight terms and is KES 4,000 short this term doesn't need a predatory loan. They need a small, cheap, purpose-locked top-up that goes directly to the school.

### Proposed solution
An embedded credit product within Zeraki Finance that offers fee top-ups to eligible parents. Eligibility is determined by the parent's actual fee payment history (from Zeraki Finance data), not by phone metadata or a traditional credit score. The top-up is disbursed directly to the school's paybill, never to the parent's M-Pesa. Repayment happens through the same paybill over the following weeks.

### Target users
- **Primary:** Parents who qualify based on payment history (two groups, described below)
- **Secondary:** School bursars who manage and monitor credit arrangements in Zeraki Finance

## 2. Who Qualifies: Two Entry Paths

Not every parent qualifies. The product serves two specific groups, both defined by Zeraki Finance data.

### Path 1: Historically strong payers having a tough term

These are parents whose records show consistent, timely fee payment across multiple terms. They don't need to go through a Layer 1 instalment plan to prove themselves. Their track record is the proof.

**Profile:** Paid 90%+ of fees within the first 4 weeks of term for at least the last 4 terms. This term, something went wrong. They've paid some of the fees but can't cover the full amount.

**Why they deserve credit:** The data shows years of reliable behaviour. One difficult term doesn't erase that history. Offering affordable credit to this parent prevents them from turning to expensive alternatives for a temporary shortfall.

### Path 2: Plan-adherent parents from Layer 1

These are parents who selected an instalment plan (Layer 1) and stuck to it, but fell short in the final stretch due to a disruption.

**Profile:** On an active Zeraki Plan, made 3+ of their scheduled payments on time, reached 70%+ of their total fee. The remaining balance is a gap, not a pattern of non-payment.

**Why they deserve credit:** They demonstrated commitment through structured behaviour. They signed up for a plan and followed through on most of it. The shortfall is situational, not habitual.

### Who does NOT qualify

- Parents with no payment history in Zeraki Finance (new students with no data)
- Parents who have consistently paid late or incompletely across multiple terms without improvement
- Parents who selected a Layer 1 plan but made fewer than 3 scheduled payments
- Parents who already have an outstanding credit balance from a previous term

The product is deliberately selective. It rewards demonstrated behaviour, not need alone. This keeps default rates low and makes the product sustainable.

## 3. How It Works

### Step 1: System identifies eligible parents

At a configurable point during the term (e.g., Week 4, or when a Layer 1 plan enters its final instalment), Zeraki Credit runs an eligibility check against Zeraki Finance data.

For Path 1 parents: the system checks historical payment records across the last 4+ terms.
For Path 2 parents: the system checks current plan adherence against the criteria above.

Eligible parents are flagged in the bursar's dashboard.

### Step 2: School decides whether to enable credit offers

The school must opt in. The bursar (or headteacher) reviews the list of eligible parents and decides:
- Enable credit offers for all eligible parents
- Enable for specific parents only (manual selection)
- Disable credit offers this term (school chooses not to participate)

The school controls whether the feature is active. Zeraki does not offer credit to parents without the school's approval.

### Step 3: Parent receives the offer

**App path:** Parent opens the Zeraki app, sees their fee balance, and below it: "You qualify for a fee top-up of up to KES [AMOUNT]. Funds go directly to the school. Repay over [N] weeks. [View Details]."

**SMS path:** Parent receives an SMS: "[SCHOOL]: Based on your payment history, you may qualify for a fee top-up of up to KES [AMOUNT] for [CHILD] ([REG]). Funds paid directly to school. Reply INFO for details."

Parent replies INFO and receives: "[SCHOOL]: Fee top-up for [CHILD]: up to KES [AMOUNT]. Repay KES [WEEKLY] per week for [N] weeks. Total cost: KES [TOTAL_WITH_FEE]. Funds go to school, not your M-Pesa. Reply YES to apply."

### Step 4: Parent applies

**App:** Parent taps "Apply", confirms the amount and terms, and submits.
**SMS:** Parent replies YES.

If the credit is provided by an external lender (Option B), the parent also consents to data sharing at this step. The SMS or app screen explains: "By applying, you allow [SCHOOL] to share your fee payment history with [LENDER] to assess your application."

### Step 5: Credit decision

**Option A (School-funded deferral):** The school has already approved the eligible list. The "loan" is simply the school agreeing to let the parent complete payment over additional weeks. No external decision needed. Plan is activated immediately.

**Option B (Third-party lender):** Zeraki shares the parent's payment history with the lending partner (Pezesha, SACCO, or MFI) via API. The lender makes the credit decision. If approved, the lender disburses directly to the school's paybill.

In both cases, the parent receives a confirmation SMS with the exact terms.

### Step 6: Disbursement

The money never goes to the parent's M-Pesa.

**Option A:** No disbursement needed. The school simply extends the payment deadline. The parent's fee balance in Zeraki Finance is updated to show the new repayment schedule.

**Option B:** The lender sends the top-up amount to the school's M-Pesa paybill, referencing the student's registration number. Zeraki Finance reconciles this as a payment against the student's fee balance. From the school's perspective, the fees are now paid. From the parent's perspective, they now owe the lender, not the school.

### Step 7: Repayment

The parent repays via the same M-Pesa paybill (Option A) or via the lender's collection mechanism (Option B).

**Option A repayment:** Parent pays to the school paybill as usual. Zeraki Finance matches the payment to the credit repayment schedule (similar to Layer 1 plan matching). Weekly reminders are sent.

**Option B repayment:** The lender collects directly from the parent via M-Pesa (STK push, standing order, or manual payment to the lender's paybill). Zeraki tracks the repayment status for the school's visibility but is not involved in the money flow.

## 4. Credit Terms

### Option A: School-funded deferral

| Parameter | Value | Rationale |
|-----------|-------|-----------|
| Maximum amount | 30% of term fees or KES 5,000 (whichever is lower) | Keep exposure small per parent |
| Repayment period | 4-6 weeks from approval | Must complete within the term |
| Repayment frequency | Weekly | Matches income cycles for most families |
| Interest or fees | Zero | Not a loan. A flexible payment arrangement. Keeps it unregulated. |
| Late payment handling | SMS reminder at due date + 3 days grace. Bursar notified after 7 days. | School retains enforcement discretion |
| Default definition | More than 14 days past due on any weekly instalment | Triggers manual school follow-up |

### Option B: Third-party lender

| Parameter | Value (indicative, negotiated with lender) | Rationale |
|-----------|------------------------------------------|-----------|
| Maximum amount | 30% of term fees or KES 10,000 (whichever is lower) | Lender may accept higher exposure due to better risk data |
| Repayment period | 4-8 weeks | Lender sets terms based on risk assessment |
| Repayment frequency | Weekly | Consistency with Option A experience |
| Interest or fees | Target: 5% flat fee or lower | Must be transparently disclosed. Significantly cheaper than Tala (15%+) or shylocks (20%+) |
| Late payment handling | Per lender's policy, subject to CBK DCP regulations | Zeraki monitors but does not enforce |
| CRB reporting | Yes, by the lender | Positive reporting builds parent's credit history. Default reporting is a risk the parent should understand. |

### Recommended sequencing

Start with Option A (school-funded deferrals). It's simpler, requires no lending license, and tests the core product mechanics. Move to Option B (third-party lender) once:
- Option A has run for at least 2 terms with measurable results
- Default rates are validated
- A lending partner (Pezesha or similar) is engaged and integrated
- Data sharing consent flows are built and tested

## 5. Scope

### In scope (MVP, Option A only)

**School admin side (Zeraki Finance):**
- Eligibility dashboard: list of parents who qualify, with their payment history summary
- Enable/disable credit offers per school, per term
- Individual approval or bulk approval of eligible parents
- Credit arrangement tracking: who has active credit, repayment progress, overdue alerts
- School-level controls: maximum number of concurrent credit arrangements, maximum amount per student

**Parent side (app):**
- View credit offer with clear terms (amount, repayment schedule, total cost)
- Accept or decline the offer
- View active credit arrangement: repayment schedule, payments made, remaining balance

**Parent side (SMS):**
- Receive credit offer via SMS
- Reply to request details and to accept
- Receive weekly repayment reminders
- Check credit balance via keyword

**Repayment:**
- Automatic matching of paybill payments to the credit repayment schedule (same logic as Layer 1 plan matching)
- Manual reconciliation for cash and bank deposit repayments (same flow as Layer 1)

### Out of scope (MVP)

- Third-party lender integration, Option B (V2)
- Pezesha API or SACCO integration (V2)
- DPA 2019 data sharing consent flow for external lenders (V2, not needed for Option A)
- CRB reporting (V2, only relevant for Option B)
- Credit offers during inter-term holidays (future consideration)
- Automatic credit limit increases based on repayment history (V2)

## 6. Eligibility and Scoring

### Hard eligibility rules (all must be met)

**Path 1 (Historically strong payers):**

| Rule | Threshold |
|------|-----------|
| Terms of fee payment data in Zeraki Finance | 4 or more |
| Percentage of fees paid within 4 weeks of term start (average across last 4 terms) | 90% or higher |
| Current term payment | At least some payment made (not zero) |
| Outstanding credit from a previous term | None |

**Path 2 (Plan-adherent parents from Layer 1):**

| Rule | Threshold |
|------|-----------|
| Active Zeraki Plan for current term | Yes |
| Scheduled payments made on time | 3 or more |
| Fee coverage from plan payments | 70% or higher of total fee |
| Outstanding credit from a previous term | None |

### Scoring (determines the amount offered)

For parents who pass the hard rules, a simple score determines how much credit to offer. This is not a complex model. It uses data Zeraki Finance already has.

| Input | Weight | Logic |
|-------|--------|-------|
| Historical payment speed | 30% | Average weeks to full payment across last 4 terms. Faster = higher score. |
| Payment consistency | 25% | How regular are payments? Steady weekly payments score higher than erratic lump sums. |
| Pledge fulfilment rate | 20% | Percentage of past pledges honoured on time. |
| Tenure at school | 15% | More terms of data = more confidence in the pattern. |
| Current term effort | 10% | Percentage of current term fee already paid. Higher = lower top-up needed = lower risk. |

### Score to amount mapping

| Score range | Maximum credit offered |
|-------------|----------------------|
| 80-100 | 30% of term fee or KES 5,000 (lower of the two) |
| 60-79 | 20% of term fee or KES 3,000 (lower of the two) |
| 40-59 | 15% of term fee or KES 2,000 (lower of the two) |
| Below 40 | Not eligible |

The school can override these defaults by setting lower maximums in their Zeraki Finance settings.

## 7. SMS Notifications

**Credit offer (sent to eligible parents):**
"[SCHOOL]: Based on your payment history, you may qualify for a fee top-up of up to KES [AMOUNT] for [CHILD] ([REG]). Funds go directly to school. Reply INFO for details."

**Credit details (sent when parent replies INFO):**
"[SCHOOL]: Fee top-up for [CHILD]: KES [AMOUNT]. Repay KES [WEEKLY]/week for [N] weeks. No interest. Funds go to school. Reply YES to accept or NO to decline."

**Credit confirmed:**
"[SCHOOL]: Fee top-up of KES [AMOUNT] confirmed for [CHILD] ([REG]). First repayment of KES [WEEKLY] due [DATE]. Paybill [PAYBILL], Acc [REG]."

**Weekly repayment reminder:**
"[SCHOOL]: Repayment of KES [WEEKLY] for [CHILD] ([REG]) fee top-up is due [DATE]. Paybill [PAYBILL], Acc [REG]. Payments made: [X] of [N]."

**Repayment received:**
"[SCHOOL]: KES [AMOUNT] received toward fee top-up for [CHILD] ([REG]). Remaining: KES [BALANCE]. [X] of [N] payments complete."

**Overdue (3 days after missed payment):**
"[SCHOOL]: Repayment of KES [WEEKLY] for [CHILD] ([REG]) was due [DATE]. Please pay as soon as possible. Paybill [PAYBILL], Acc [REG]."

**Credit fully repaid:**
"[SCHOOL]: Fee top-up for [CHILD] ([REG]) is fully repaid. Thank you."

**Design principles:**
- Same principles as Layer 1: school sender ID, factual tone, no threatening language
- Credit offer is sent once. If the parent doesn't respond, no follow-up offer is sent. This is not a sales funnel.
- The word "loan" is never used in any SMS. It's a "fee top-up" or "payment arrangement."
- Total cost is always disclosed upfront (for Option A this is zero; for Option B it includes the fee/interest)

## 8. School Admin Dashboard (Zeraki Finance)

### Credit overview widget

Shows for the current term:
- Eligible parents: X
- Offers sent: Y
- Offers accepted: Z
- Active credit arrangements: Z
- On track (repaying on schedule): A
- Behind schedule: B
- Fully repaid: C
- Total amount outstanding: KES X
- School's maximum exposure: KES Y (set in settings)
- Remaining capacity: KES Z

### Per-student credit view

Added to the existing fee register:

| Student | Fee | Paid | Credit | Repaid | Credit Status |
|---------|-----|------|--------|--------|---------------|
| James Otieno (4523) | 15,000 | 10,500 | 4,500 | 2,250 | On Track (2 of 4) |
| Mary Achieng (4601) | 15,000 | 12,000 | 3,000 | 3,000 | Complete |
| Peter Mwangi (4412) | 15,000 | 11,000 | 2,000 | 0 | Overdue (7 days) |

### School controls

- **Maximum concurrent arrangements:** e.g., "No more than 40 students on credit at any time"
- **Maximum amount per student:** e.g., "KES 3,000 maximum"
- **Auto-offer vs manual:** School can choose to automatically send offers to all eligible parents, or review and approve each individually
- **Pause credit:** Emergency switch to stop all new offers if the school's cash flow is too tight (relevant for Option A where the school bears the cost)

## 9. Key Product Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| Disbursement | Directly to school paybill, never to parent's M-Pesa | Purpose-locked. Eliminates diversion risk. |
| Two eligibility paths | Historical strong payers AND plan-adherent parents | Strong payers shouldn't need a plan to prove themselves. Plan-adherent parents have demonstrated recent commitment. Both deserve access. |
| Option A first | School-funded deferral before third-party lender | No licensing required. Simpler. Tests mechanics. School already absorbs late payments informally. |
| Language | "Fee top-up" and "payment arrangement", never "loan" | Keeps Option A outside lending regulation. Reduces parent anxiety about borrowing. |
| Offer frequency | One offer per parent per term, no follow-up if ignored | This is not a sales product. Parents who don't want it shouldn't be pressured. |
| School control | School must opt in and can set limits | The school bears the risk (Option A). They must control the exposure. |

## 10. What This Does NOT Do

- **Does not lend Zeraki's own money.** In Option A, the school absorbs the deferred payment. In Option B, the lender provides capital. Zeraki is the platform, not the financier.
- **Does not replace the school's authority.** The school decides whether to enable credit, which parents to offer it to, and what limits to set.
- **Does not trap parents in debt.** Maximum amounts are small (KES 2,000-5,000). Repayment periods are short (4-6 weeks). No compounding interest. No rollover to next term.
- **Does not penalise parents who decline.** A parent who ignores or declines a credit offer faces no consequences from Zeraki or the school.
- **Does not share data without consent.** For Option A, no external data sharing occurs. For Option B, explicit parent consent is required before any data goes to a lender.

## 11. Risks

| Risk | Severity | Mitigation |
|------|----------|------------|
| School can't absorb deferrals (Option A) | High | School sets its own limits. Small maximum amounts. Pilot with financially stable schools first. |
| Parents default on repayment | Medium | Strict eligibility criteria. Only parents with proven track records qualify. Expected default rate: 5-10%. |
| Parents feel pressured to accept credit | Medium | Offer sent once, no follow-up. Decline has no consequences. Language is invitational, not urgent. |
| Regulatory reclassification | Low (Option A), Medium (Option B) | Option A: no interest, no fees, no external lender. Option B: lender holds the license. Zeraki stays in the platform role. |
| Credit becomes expected (entitlement) | Low | Eligibility resets each term. Past credit doesn't guarantee future credit. The product rewards behaviour, not tenure. |
| Feature used by schools to avoid addressing root cash flow issues | Low | Layer 2 is a parent-side product. School cash flow is a separate problem (potential Layer 3). |

## 12. Success Criteria (Pilot, Option A)

| Metric | Target |
|--------|--------|
| Eligible parents identified (per school) | 10-15% of parents with outstanding fees |
| Offer acceptance rate | 50%+ of those who receive the offer |
| Repayment completion rate (within agreed timeframe) | 85%+ |
| Default rate (more than 14 days overdue) | Below 10% |
| Parent satisfaction (survey) | 80%+ would use it again |
| Reduction in "sent home" incidents for credit-receiving families | Measurable decrease vs previous term |
| School satisfaction | 80%+ of pilot schools would continue offering it |

## 13. Open Questions

- [ ] What is the realistic financial exposure a school can absorb for Option A? A school with 500 students and 50 credit arrangements at KES 3,000 each is carrying KES 150,000 in deferred fees. Is this manageable for a typical Zeraki Finance school?
- [ ] How quickly do schools need the money? If a school offers deferrals in Week 2 but needs the cash by Week 4 for teacher salaries, the 4-6 week repayment window may not work. This is the core tension of Option A.
- [ ] For Option B, what minimum data does Pezesha need to make a credit decision? Can they work with Zeraki's payment history format, or do they need additional signals?
- [ ] Should credit eligibility be visible to the parent before they need it? e.g., "You currently qualify for up to KES 4,000 in fee support if needed." Or is it better to only surface the offer when there's an actual shortfall?
- [ ] How does the product handle a parent who qualifies under both paths (strong historical payer who also has a Layer 1 plan this term)? Use the higher eligibility, or keep them separate?
- [ ] What happens if a parent accepts credit and then makes additional payments that would have covered the balance anyway? Can the credit be cancelled or reduced mid-arrangement?