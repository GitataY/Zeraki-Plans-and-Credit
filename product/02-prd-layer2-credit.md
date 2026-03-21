# Product Requirements Document: Layer 2 - Zeraki Credit

## 1. Overview

### Product name
Zeraki Credit

### One-liner
Affordable, purpose-locked fee top-up financing for parents who have earned it through their payment history - funded by a lending partner, invisible to the parent, and settled through the school's existing paybill.

### Problem statement
Even parents who consistently pay fees can hit a rough term. A hospital bill, a job loss, a funeral contribution, a slow work season. When this happens, their options are: borrow from a digital lender at 15%+ monthly interest, borrow from a shylock at worse rates, or let their child be sent home. None of these options are proportionate to the problem. A parent who's paid in full for 6 straight terms and is KES 4,000 short this term doesn't need a predatory loan. They need a small, cheap, purpose-locked top-up that goes directly to the school.

### Proposed solution
An embedded credit product within Zeraki Finance that connects eligible parents to affordable fee financing from a licensed lending partner (e.g., Pezesha, a SACCO, or an MFI). The parent never interacts with the lender. From the parent's perspective, the entire experience happens inside the school relationship: the offer comes from the school, the payment goes to the school's paybill, and the reminders come from the school.

Behind the scenes, Zeraki handles the waterfall. When a parent with an active credit arrangement pays to the school paybill, Zeraki's system splits the incoming payment: the lender's share is forwarded to the lending partner, and any remainder stays with the school. The lender is invisible infrastructure, not a customer-facing entity.

This mirrors the Twiga-Pezesha embedded lending model, where vendors pay Twiga (not Pezesha) and the platform handles repayment allocation silently. The same principle applies here: the parent pays the school. The system handles the rest.

### Who benefits

**The parent** gets affordable credit at the exact moment they need it, pre-qualified by data the school already has. No application forms, no phone metadata harvesting, no 15% monthly interest. They don't need to learn a new paybill number, interact with a lender, or manage a separate repayment relationship. They pay the school, same as always.

**The school** gets paid in full. The lender pays the fee balance directly to the school's paybill. From the school's perspective, the fees are settled. No cash flow exposure, no deferred payments to manage, no risk to absorb.

**The lender** gets a pre-qualified borrower with verified payment behaviour data that doesn't exist anywhere else. Plan adherence data from Layer 1 is a stronger credit signal than anything Tala, Branch, or Fuliza can access. The loan is purpose-locked (can't be diverted), small (KES 2,000-10,000), and repayment flows through a channel the parent already uses - school fees. As long as the child is in school, the parent keeps paying to the paybill, and the lender gets repaid through the waterfall.

**Zeraki** earns a data and distribution fee per credit arrangement. This is the business model for the platform.

### Target users
- **Primary:** Parents who qualify based on payment history (two groups, described below)
- **Secondary:** School bursars who monitor credit arrangements in Zeraki Finance

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

The product is deliberately selective. It rewards demonstrated behaviour, not need alone. This keeps default rates low and makes the product sustainable for the lending partner.

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

**Why the school still has a say, even though they bear no financial risk:** The parent experiences the credit offer as coming from the school. If the credit product creates problems - over-indebtedness, aggressive follow-up, CRB listings - the school's reputation suffers. The opt-in protects that relationship.

### Step 3: Parent receives the offer

**App path:** Parent opens the Zeraki app, sees their fee balance, and below it: "You qualify for a fee top-up of up to KES [AMOUNT]. Funds go directly to the school. Repay over [N] weeks. [View Details]."

**SMS path:** Parent receives an SMS: "[SCHOOL]: Based on your payment history, you may qualify for a fee top-up of up to KES [AMOUNT] for [CHILD] ([REG]). Funds paid directly to school. Reply INFO for details."

Parent replies INFO and receives: "[SCHOOL]: Fee top-up for [CHILD]: KES [AMOUNT]. Repay KES [WEEKLY]/week for [N] weeks. Total cost: KES [TOTAL] (includes KES [FEE] service fee). Same paybill, same account. Reply YES to apply."

The phrase "same paybill, same account" is deliberate. The parent needs to know nothing changes about how they pay. They don't need to learn a new paybill number or interact with a lender.

### Step 4: Parent applies and consents

**App:** Parent taps "Apply", reviews the terms (amount, weekly repayment, total cost including fees), and confirms. A consent screen explains: "By applying, you allow [SCHOOL] to share your fee payment history with a credit partner to assess your application. Repayment may be reported to a credit reference bureau."

**SMS:** Parent replies YES. A follow-up SMS confirms: "By applying, you allow [SCHOOL] to share your fee payment history with a credit partner. Repayment may be reported to a credit bureau. Reply CONFIRM to proceed or CANCEL to stop."

Two-step consent for SMS (YES then CONFIRM) is deliberate. This is a credit product with CRB implications. The parent must understand that data is being shared with a third party, even though that third party is invisible in the day-to-day experience. DPA 2019 requires this transparency.

**Note on lender naming:** The consent flow refers to "a credit partner" rather than naming Pezesha specifically. The parent doesn't need to know or care who the lender is. If they want to know, the app consent screen includes a "Learn more" link with the partner's name, license, and contact. But it's not front and centre.

### Step 5: Credit decision

Zeraki shares the parent's payment history with the lending partner via API. The data package includes:

- Number of terms with fee data
- Payment amounts and dates per term
- Average weeks to full payment
- Current term: amount paid, balance, plan status (if applicable)
- Plan adherence data (if on a Layer 1 plan): scheduled vs actual payments
- Zeraki's eligibility score (described in Section 6)

The lender makes the credit decision. For most eligible parents, this should be near-instant (automated decisioning based on the data package). The lender may decline a parent that Zeraki flagged as eligible - the lender has the final say.

If approved, the parent receives a confirmation SMS from the school. If declined, the parent receives a neutral SMS: "[SCHOOL]: Your fee top-up application could not be approved at this time. This does not affect your child's enrolment."

### Step 6: Disbursement

The lender sends the top-up amount to the school's M-Pesa paybill, referencing the student's registration number. Zeraki Finance reconciles this as a payment against the student's fee balance.

From the school's perspective: the fees are now paid. The student's balance in the fee register shows zero (or reduced by the credit amount). A paid balance is a paid balance - the school doesn't need to track who paid from their own pocket and who had a credit arrangement.

From the parent's perspective: the school fees are covered. They now have a repayment schedule to clear the top-up, paying to the same paybill they always use.

### Step 7: Repayment (the waterfall)

The parent pays to the school's paybill using the student's registration number as the account reference. Nothing changes about how or where they pay. This is the key design decision.

When the payment comes in, Zeraki's system checks whether the student has an active credit arrangement. If yes, the system runs the waterfall:

**Waterfall logic:**
1. Incoming payment is received via the school's paybill
2. System checks: does this student have an active credit arrangement?
3. If yes: allocate the lender's weekly repayment amount to the lender. Forward this amount to the lending partner via B2B transfer.
4. Any amount above the weekly repayment: allocate to the school (e.g., next term's fees, or any remaining non-credit balance)
5. If no active arrangement: full amount goes to the school as normal

**Example:**
- James Otieno (4523) has a credit arrangement: KES 4,500 top-up, repay KES 1,181/week for 4 weeks (includes 5% fee)
- His parent pays KES 1,181 to the school paybill, account 4523
- Zeraki allocates: KES 1,181 forwarded to Pezesha. KES 0 to school (no remaining balance this week)
- If the parent pays KES 2,000 instead: KES 1,181 forwarded to Pezesha, KES 819 allocated to school

**What if the parent pays less than the weekly repayment amount?**
- The full payment is forwarded to the lender. The parent is behind on their repayment schedule by the shortfall amount.
- No payment is split where the school gets some and the lender gets some. If there's an active credit arrangement, the lender is first in the waterfall until the arrangement is complete.

**What if the parent pays cash or bank deposit instead of M-Pesa?**
- The bursar records the payment manually in Zeraki Finance (same as Layer 1)
- The waterfall logic is the same: system allocates the lender's share and the school's share
- For the lender's share: Zeraki initiates a B2B transfer from the school's account to the lender. This requires the settlement arrangement described in Section 8.

**What about the existing fee balance?**
- The credit arrangement covers a specific amount of the fee balance. Once disbursed, that portion of the balance is settled from the school's perspective.
- Any remaining fee balance (not covered by the credit) is owed directly to the school, with no waterfall involved.
- If the parent has both a remaining fee balance and a credit repayment due, the credit repayment takes priority in the waterfall. This protects the lender and is a condition of the partnership.

### Step 8: Reminders and status updates

All parent-facing communication comes from the school sender ID.

**Weekly repayment reminder:**
"[SCHOOL]: Repayment of KES [WEEKLY] for [CHILD] ([REG]) fee top-up is due [DATE]. Pay to [SCHOOL_PAYBILL], Acc [REG]. Payments made: [X] of [N]."

**Repayment received:**
"[SCHOOL]: KES [AMOUNT] received toward fee top-up for [CHILD] ([REG]). Remaining: KES [BALANCE]. [X] of [N] payments complete."

**Overdue (3 days after missed payment):**
"[SCHOOL]: Repayment of KES [WEEKLY] for [CHILD] ([REG]) was due [DATE]. Please pay as soon as possible. [SCHOOL_PAYBILL], Acc [REG]."

**Credit fully repaid:**
"[SCHOOL]: Fee top-up for [CHILD] ([REG]) is fully repaid. Thank you."

The lender never contacts the parent directly. Zeraki handles all communication on behalf of the school. If the lender needs to escalate (e.g., persistent default leading to CRB listing), they do so through Zeraki, who sends the appropriate notification from the school sender ID. The parent's relationship stays inside the school.

## 4. Credit Terms

Terms are set by the lending partner, not by Zeraki. However, Zeraki should negotiate baseline terms as part of the partnership agreement to protect the parent experience.

| Parameter | Target range | Rationale |
|-----------|-------------|-----------|
| Maximum amount | 30% of term fees or KES 10,000 (whichever is lower) | Small, proportionate to the shortfall |
| Repayment period | 4-8 weeks | Short enough to clear before next term. Long enough to be manageable. |
| Repayment frequency | Weekly | Matches income cycles for most families |
| Fee/interest | Target: 5% flat fee or lower | Must be transparently disclosed. Must be significantly cheaper than Tala (15%+), Fuliza (access fee + daily maintenance), or informal lenders. |
| Late payment handling | SMS reminder from school sender ID at due date + 3 days. No direct lender contact with parent. | Lender communicates through Zeraki, not around it. |
| CRB reporting | Yes, by the lender | Positive reporting builds the parent's credit history. Default reporting is a risk the parent must understand before accepting. |
| Rollover/refinancing | Not permitted | Credit cannot roll into the next term. No compounding. No new debt cycle through Zeraki. |

### What Zeraki should negotiate with the lending partner

These aren't product requirements - they're partnership terms. But they directly affect the parent experience:

- **Rate cap:** Maximum 5% flat fee per arrangement. If the lender needs more to make the economics work, the data quality isn't good enough yet. Fix the data, don't raise the price.
- **No direct parent contact:** The lender never contacts the parent. All communication goes through Zeraki via the school sender ID. This is the core of the invisible lender model and must be contractual.
- **CRB reporting threshold:** Positive reporting for all arrangements. Negative reporting only after 30+ days overdue, with at least 2 SMS warnings (from the school sender ID) before listing. A parent who misses one week shouldn't get a CRB black mark.
- **Decline rate transparency:** The lender shares their approval/decline rates and reasons with Zeraki monthly. If they're declining 50%+ of Zeraki-eligible parents, either the eligibility criteria need tightening or the lender's risk appetite doesn't fit.
- **Collection escalation protocol:** If a parent is 30+ days overdue, the lender must go through Zeraki to initiate CRB listing. Zeraki sends a final warning SMS from the school sender ID before the listing happens. The parent is never surprised by a CRB entry.

## 5. Scope

### In scope (MVP)

**School admin side (Zeraki Finance - Credit page):**
- Eligibility dashboard: list of parents who qualify, with their payment history summary and eligibility path (Path 1 or Path 2)
- Enable/disable credit offers per school, per term
- Individual approval or bulk approval of eligible parents to receive offers
- Credit arrangement tracking: who has active credit, repayment progress, overdue alerts
- Funded By column showing the lending partner name (bursar visibility only)
- Filter: "All" / "On Track" / "Overdue" / "Complete"
- Total disbursed to school this term (the value prop for schools)

**School admin side (Zeraki Finance - Settings):**
- Toggle: "Enable credit offers this term: On/Off"
- Credit partner display: shows connected partner name and status
- Auto-offer vs manual: school can choose to automatically send offers to all eligible parents, or review and approve each individually

**Parent side (app):**
- View credit offer with clear terms (amount, repayment schedule, total cost including fees)
- Consent screen explaining data sharing with credit partner and CRB reporting
- Accept or decline the offer
- View active credit arrangement: repayment schedule, payments made, remaining balance
- Pay to same school paybill as always

**Parent side (SMS):**
- Receive credit offer via SMS from school sender ID
- Reply to request details and to accept (two-step consent: YES then CONFIRM)
- Receive weekly repayment reminders from school sender ID
- Check credit balance via keyword

**Payment waterfall:**
- Intercept incoming paybill payments for students with active credit arrangements
- Allocate lender's share and school's share per the waterfall logic
- Forward lender's share via B2B transfer
- Handle manual payment recording (cash/bank deposit) with same waterfall logic
- Settlement reconciliation with lending partner (daily or weekly batch)

**Integration:**
- API to share parent payment data with lending partner (with consent)
- API to receive credit decision from lender (approve/decline/amount)
- API to confirm disbursement to school paybill
- API to report repayment status to lender (amount, date, running balance)
- B2B payment integration for forwarding lender's share from school paybill

### Out of scope (MVP)

- Multiple lending partners (V2 - start with one partner, likely Pezesha)
- Automatic credit limit increases based on repayment history (V2)
- Credit offers during inter-term holidays (future consideration)
- Parent-initiated credit requests (MVP is system-initiated offers only)
- Credit for non-fee school costs like uniforms, books, or transport (future consideration)

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

For parents who pass the hard rules, a simple score determines how much credit to offer. This is not a complex model. It uses data Zeraki Finance already has. The score is shared with the lending partner as part of the data package - the lender can use it as an input to their own decisioning or ignore it.

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
| 80-100 | 30% of term fee or KES 10,000 (lower of the two) |
| 60-79 | 20% of term fee or KES 6,000 (lower of the two) |
| 40-59 | 15% of term fee or KES 3,000 (lower of the two) |
| Below 40 | Not eligible |

The lender may approve a lower amount than Zeraki's recommendation based on their own risk assessment. The parent sees only the final approved amount.

## 7. SMS Notifications

All SMS comes from the school sender ID. The lender is never named in parent-facing communications unless the parent explicitly requests more information.

**Credit offer (sent to eligible parents):**
"[SCHOOL]: Based on your payment history, you may qualify for a fee top-up of up to KES [AMOUNT] for [CHILD] ([REG]). Funds go directly to school. Reply INFO for details."

**Credit details (sent when parent replies INFO):**
"[SCHOOL]: Fee top-up for [CHILD]: KES [AMOUNT]. Repay KES [WEEKLY]/week for [N] weeks. Total cost: KES [TOTAL] (includes KES [FEE] service fee). Same paybill, same account. Reply YES to apply."

**Data sharing consent (sent when parent replies YES):**
"By applying, you allow [SCHOOL] to share your fee payment history with a credit partner. Repayment may be reported to a credit bureau. Reply CONFIRM to proceed or CANCEL to stop."

**Credit approved:**
"[SCHOOL]: Fee top-up of KES [AMOUNT] approved for [CHILD] ([REG]). KES [AMOUNT] paid to school. Repay KES [WEEKLY]/week for [N] weeks starting [DATE]. Total cost: KES [TOTAL]. Pay to [SCHOOL_PAYBILL], Acc [REG]."

**Credit declined:**
"[SCHOOL]: Your fee top-up application could not be approved at this time. This does not affect your child's enrolment."

**Weekly repayment reminder:**
"[SCHOOL]: Repayment of KES [WEEKLY] for [CHILD] ([REG]) fee top-up is due [DATE]. Pay to [SCHOOL_PAYBILL], Acc [REG]. Payments made: [X] of [N]."

**Repayment received:**
"[SCHOOL]: KES [AMOUNT] received toward fee top-up for [CHILD] ([REG]). Remaining: KES [BALANCE]. [X] of [N] payments complete."

**Overdue (3 days after missed payment):**
"[SCHOOL]: Repayment of KES [WEEKLY] for [CHILD] ([REG]) was due [DATE]. Please pay as soon as possible. [SCHOOL_PAYBILL], Acc [REG]."

**CRB warning (sent 21 days after first missed payment, before 30-day CRB listing):**
"[SCHOOL]: Your fee top-up repayment for [CHILD] ([REG]) is [DAYS] days overdue. Outstanding: KES [BALANCE]. Unpaid amounts may be reported to a credit reference bureau. Please pay to [SCHOOL_PAYBILL], Acc [REG] or contact the school."

**Credit fully repaid:**
"[SCHOOL]: Fee top-up for [CHILD] ([REG]) is fully repaid. Thank you."

**Design principles:**
- Every SMS comes from the school sender ID. The parent's relationship stays inside the school.
- The credit offer is sent once. If the parent doesn't respond, no follow-up is sent. This is not a sales funnel.
- The word "loan" is never used in any SMS. It's a "fee top-up."
- Total cost is always disclosed upfront, including the service fee.
- The decline SMS explicitly states it doesn't affect enrolment.
- The CRB warning is sent through Zeraki, not by the lender directly. The parent is never surprised by a CRB entry.
- "Same paybill, same account" reinforces that nothing changes about how the parent pays.

## 8. The Settlement Layer

The waterfall model requires Zeraki to handle money movement between the school and the lending partner. This is the most technically complex part of the product and the part that needs the most careful design.

### How settlement works

1. Parent pays to school's M-Pesa paybill
2. Zeraki Finance receives the payment notification (via C2B callback)
3. Zeraki's system checks: does this student have an active credit arrangement?
4. If yes: calculate the lender's share (weekly repayment amount or remaining balance, whichever is lower)
5. Queue a B2B transfer from the school's paybill to the lender's settlement account
6. Record the allocation in Zeraki Finance (school's share vs lender's share)
7. Update the credit arrangement status (payment count, remaining balance)

### Settlement frequency

Two options, to be determined based on the paybill integration model:

**Real-time forwarding:** Each payment triggers an immediate B2B transfer of the lender's share. Simpler accounting, but higher transaction costs and requires real-time B2B capability on the school's paybill.

**Batch settlement:** Zeraki accumulates the lender's share across all payments during the day (or week) and sends a single batch transfer. Lower transaction costs, but requires Zeraki to track the unsettled balance and the school to accept that some funds in their paybill are earmarked for the lender.

The batch model is more practical for MVP. Daily settlement (end of day, all lender shares forwarded in one transfer) balances cost and complexity.

### Trust and reconciliation

The school needs to trust that Zeraki is forwarding the correct amounts. The lender needs to trust that they're receiving their full share. This requires:

- **Transparent ledger:** The Credit page in Zeraki Finance shows every payment received, how it was split, and when the lender's share was forwarded. The bursar can see this at any time.
- **Lender reconciliation API:** The lender receives a daily settlement report showing: payments received, amounts forwarded, per-student breakdown, running balances.
- **Dispute resolution:** A process for handling discrepancies (e.g., a payment was recorded but the B2B transfer failed). Zeraki owns this process.

### Cash and bank deposit payments

When the bursar records a manual payment (cash or bank deposit), the same waterfall logic applies. The system calculates the lender's share and includes it in the next batch settlement. The school must have sufficient funds in their paybill to cover the B2B transfer, since the cash/bank deposit went into a different account.

This is a potential friction point. If a parent pays KES 1,181 in cash and the waterfall says KES 1,181 goes to the lender, the school needs to forward that amount from their paybill even though the cash is sitting in their safe or bank account, not in M-Pesa. For MVP, this may need to be a manual process the bursar initiates, rather than an automatic B2B transfer.

## 9. School Admin Dashboard (Zeraki Finance)

### Credit page

This is a standalone page in the sidebar navigation. It shows the school's credit picture at a glance.

**Top row - summary cards:**
- Active arrangements: 18
- On Track: 15 (83%)
- Overdue: 3 (17%)
- Fully repaid this term: 8
- Total disbursed to school this term: KES 141,000

The "Total disbursed to school" number matters. It shows the bursar how much money the school received through credit that it would otherwise still be waiting for. This is the value proposition for the school.

**Second row - arrangements table:**

| Student | Reg No. | Credit | Repaid | Outstanding | Funded By | Status | Payments |
|---------|---------|--------|--------|-------------|-----------|--------|----------|
| James Otieno | 4523 | KES 4,500 | KES 2,250 | KES 2,250 | Pezesha | On Track | 2 of 4 |
| Mary Achieng | 4601 | KES 3,000 | KES 3,000 | KES 0 | Pezesha | Complete | 4 of 4 |
| Peter Mwangi | 4412 | KES 2,000 | KES 0 | KES 2,000 | Pezesha | Overdue 7d | 0 of 4 |
| Grace Wanjiru | 4530 | KES 3,500 | KES 875 | KES 2,625 | Pezesha | On Track | 1 of 4 |
| Mwende Kilonzo | 4545 | KES 5,000 | KES 3,750 | KES 1,250 | Pezesha | On Track | 3 of 4 |

Filter tabs above the table: "All (18)" | "On Track (15)" | "Overdue (3)" | "Complete (8)"

**Important UX note:** The bursar can see repayment status but cannot take action on collections. There are no "chase payment" or "send reminder" buttons for the credit repayment. Reminders are automated by the system. The bursar's fees are already paid. This table is informational, not operational.

The bursar can, however, click into a student's record to see the waterfall detail: which payments came in, how they were split, what was forwarded to the lender. This transparency builds trust in the system.

**Bottom row:**
- "Export Report" button
- "Credit Settings" link (goes to Settings page)

### What the bursar does NOT see

- The interest rate or fee the parent is paying. This is between the parent and the credit product.
- The lender's internal risk score or decision rationale.
- Whether a specific parent was declined by the lender (the bursar sees "Offer sent" and "Arrangement active" but not the gap between those).

This is deliberate. The bursar shouldn't know the financial details of a parent's credit arrangement. It could create bias in how they treat the parent or child.

### School controls (in Settings)

- **Enable/disable credit offers:** Toggle for the current term. Off by default - school must actively opt in.
- **Auto-offer vs manual:** School can choose to automatically send offers to all eligible parents, or review and approve each individually.
- **Credit partner:** Shows connected partner name and status (e.g., "Pezesha - Connected"). Not editable by the bursar - configured by Zeraki during onboarding.

There are no school exposure limits or maximum concurrent arrangement caps. The school bears no financial risk. The lender manages their own risk appetite through their approval/decline decisions.

## 10. Key Product Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| Invisible lender | Parent never interacts with the lender. All communication from school sender ID. Payment to school paybill. | Preserves the school-parent trust relationship. Simpler parent experience. No new paybill to learn. |
| Payment waterfall | Zeraki splits incoming payments between school and lender | Same model as Twiga-Pezesha. Parent pays the platform, platform handles allocation. Lender gets repaid through the existing payment channel. |
| Partner-funded only | Licensed lender provides capital, not the school | School gets paid in full with no exposure. Lender bears the risk. Zeraki stays in the platform role. No lending license needed. |
| Two eligibility paths | Historical strong payers AND plan-adherent parents | Strong payers shouldn't need a plan to prove themselves. Plan-adherent parents have demonstrated recent commitment. Both deserve access. |
| School opt-in | School must enable credit offers each term | Protects the school-parent trust relationship. School reputation is on the line even though the money isn't. |
| Language | "Fee top-up" in all school communications | Non-threatening. Signals purpose (fees) not product type (loan). |
| Offer frequency | One offer per parent per term, no follow-up if ignored | This is not a sales product. Parents who don't want it shouldn't be pressured. |
| CRB reporting | Required, with pre-acceptance disclosure and 30-day grace | Positive reporting builds credit history. Parent is warned before any negative listing. |
| Credit-first waterfall | Lender's share takes priority over school's share in payment allocation | Protects the lender's repayment, which is what makes the partnership viable. The school's fees are already paid (by the disbursement). |

## 11. What This Does NOT Do

- **Does not lend Zeraki's money.** The lending partner provides capital. Zeraki is the data, distribution, and settlement layer, not a financier.
- **Does not put the school's cash flow at risk.** The lender pays the school directly. If the parent defaults on repayment, that's between the system and the lender. The school's fees are settled.
- **Does not expose parents to a lender relationship.** The parent pays the school. The school handles communication. The lender is invisible. A parent who takes a fee top-up should feel no different from a parent who paid in full, except that they have a repayment schedule.
- **Does not trap parents in debt.** Maximum amounts are small (KES 3,000-10,000). Repayment periods are short (4-8 weeks). No compounding interest. No rollover to next term.
- **Does not penalise parents who decline.** A parent who ignores or declines a credit offer faces no consequences from Zeraki, the school, or the lender.
- **Does not share data without consent.** Explicit two-step consent is required before any payment history goes to the lender. DPA 2019 compliant.
- **Does not affect enrolment.** Whether a parent is approved, declined, defaults, or never applies - none of it affects their child's place in school. The school was already paid.

## 12. The Economics

### Who earns what

| Party | Revenue | How |
|-------|---------|-----|
| Lending partner | Interest/fee income from the parent (e.g., 5% flat fee on KES 5,000 = KES 250) | Lender bears the credit risk and earns the spread |
| Zeraki | Data and distribution fee per arrangement (e.g., 1-2% of disbursed amount, or a flat fee per arrangement) | Zeraki provided the data, the eligible parent, the distribution channel, and the settlement infrastructure |
| School | Nothing directly, but gets paid faster | School's fees are settled in Week 4 instead of trickling in through Week 10 |

### Why this works financially

A KES 5,000 fee top-up with a 5% flat fee generates KES 250 for the lender. If Zeraki takes 1.5% (KES 75), the lender retains KES 175 per arrangement.

At scale: a school with 500 students, 50 credit arrangements per term at an average of KES 4,000 = KES 200,000 disbursed. Zeraki earns ~KES 3,000 per school per term. Across 1,000 schools, that's KES 3M per term or KES 9M per year.

These are illustrative numbers. The real economics depend on uptake rate, average top-up amount, default rate, and Zeraki's negotiated share. The point is that even at modest scale, this generates meaningful recurring revenue for Zeraki without requiring Zeraki to take on any credit risk.

### The lender's economics are better because of the invisible model

The lender doesn't need to build distribution (Zeraki has 4,000+ schools). The lender doesn't need to acquire customers (the school relationship does that). The lender doesn't need a collection infrastructure for these borrowers (the waterfall handles repayment through an existing payment channel). The lender's cost per loan is dramatically lower than a standalone digital lending product, which means they can offer dramatically lower rates and still make money.

## 13. Risks

| Risk | Severity | Mitigation |
|------|----------|------------|
| Parents default on repayment | Medium | Strict eligibility criteria. Purpose-locked disbursement. Repayment flows through existing school payment channel. Expected default rate: 5-10%. |
| CRB listing harms parents who default | Medium | Two-step consent ensures parents understand CRB implications. Negotiate 30-day grace period. CRB warning SMS sent before listing. |
| Lender has no direct collection lever if parent stops paying entirely | Medium | Built into lender's risk model. CRB listing is the enforcement mechanism. Purpose-locked small amounts keep per-borrower exposure low. Natural incentive: parent keeps paying school fees as long as child is enrolled. |
| Parents feel pressured to accept credit | Medium | Offer sent once, no follow-up. Decline has no consequences. Language is invitational, not urgent. |
| School reputation damaged by CRB listings tied to credit product | Medium | School opt-in gives them control. CRB warning goes through school sender ID so school is aware. Negotiate 30-day grace to minimize listings. |
| Paybill integration doesn't support the waterfall model | Medium | Flagged as open question. May require Zeraki-managed paybill or integration with existing paybill provider. Critical to validate before build. |
| Cash/bank deposit payments create settlement friction | Medium | MVP: manual bursar process for forwarding lender's share from cash payments. V2: automate via reconciliation. |
| Lending partner pulls out or changes terms | Medium | Design integration to be partner-agnostic. API abstraction layer means swapping partners doesn't require a product rebuild. |
| Regulatory change affecting DCP lending or data sharing | Low-Medium | Lender holds the license and bears the regulatory burden. Zeraki's DPA 2019 consent flow is robust. |
| Credit becomes expected (entitlement) | Low | Eligibility resets each term. Past credit doesn't guarantee future credit. The product rewards behaviour, not tenure. |

## 14. Success Criteria (Pilot)

| Metric | Target |
|--------|--------|
| Eligible parents identified (per school) | 10-15% of parents with outstanding fees |
| Offer acceptance rate | 50%+ of those who receive the offer |
| Lender approval rate | 70%+ of parents who apply |
| Disbursement speed (application to school paybill) | Under 24 hours |
| Repayment completion rate (within agreed timeframe) | 85%+ |
| Default rate (30+ days overdue) | Below 10% |
| Waterfall settlement accuracy | 99%+ of lender shares forwarded correctly |
| Parent satisfaction (survey) | 80%+ would use it again |
| Reduction in "sent home" incidents for credit-receiving families | Measurable decrease vs previous term |
| School satisfaction | 80%+ of pilot schools would continue |
| Zeraki revenue per school per term | Validate unit economics are positive |

## 15. Open Questions

- [ ] **Paybill integration model:** Schools have their own M-Pesa paybills. For the waterfall to work, Zeraki needs to intercept incoming payments and forward the lender's share. This requires either (a) schools moving to a Zeraki-managed paybill, (b) Zeraki integrating with the school's existing paybill provider to intercept and allocate, or (c) a different settlement model. This is the highest-priority technical question and must be validated before build.
- [ ] What minimum data does the lending partner need to make an automated credit decision? Can they work with Zeraki's payment history format, or do they need additional signals (e.g., national ID verification, phone number validation)?
- [ ] Should credit eligibility be visible to the parent before they need it? e.g., "You currently qualify for up to KES 4,000 in fee support if needed." Or is it better to only surface the offer when there's an actual shortfall?
- [ ] How does the product handle a parent who qualifies under both paths (strong historical payer who also has a Layer 1 plan this term)? Use the higher eligibility, or keep them separate?
- [ ] What happens if a parent accepts credit and then makes additional payments that would have covered the balance anyway? Can the credit arrangement be closed early with reduced fees?
- [ ] What is the minimum school size (student count) for credit to make economic sense for the lending partner? A school with 50 students might generate 5 credit arrangements per term - is that enough volume?
- [ ] How should the product handle parents whose children attend multiple Zeraki-enabled schools (e.g., siblings at different schools)?
- [ ] Should Zeraki's data-sharing consent be per-term or persistent? Per-term is safer (DPA 2019 compliance) but adds friction each term.
- [ ] For cash/bank deposit payments: is a manual forwarding process acceptable for MVP, or does it create too much friction for the bursar?
- [ ] How does the settlement work if the school's paybill has insufficient funds to cover a B2B transfer to the lender (e.g., school withdrew funds before the batch settlement ran)?

---

*Note: All references to Zeraki's existing platform capabilities, data, and CEO statements are based on publicly available information (website, app stores, press, social media). This case study does not claim insider knowledge of Zeraki's internal systems or roadmap.*