# Metrics Framework

## North Star Metric

**Percentage of students who remain in school for the full term without fee-related disruption, across all Zeraki Plans and Credit schools.**

This is the outcome that matters. Everything else (plan adoption, repayment rates, bursar efficiency) is a leading indicator. If children are still being sent home at the same rate after we launch, the product has failed regardless of how many plans are created.

---

## Layer 1: Zeraki Plans

### Adoption Metrics (Are parents and schools using it?)

| Metric | Definition | Target (Pilot) | How to measure |
|--------|-----------|-----------------|----------------|
| School activation rate | % of pilot schools that configure at least 1 plan template | 90% | Zeraki Finance settings |
| Plan request rate | % of parents with outstanding fees who request a plan (app or SMS) | 25% | Plan requests / total parents with balances |
| Plan approval rate | % of plan requests approved by the bursar | 85% | Approved / total requests |
| Bursar-initiated plans | % of all active plans created directly by the bursar (Path C) | 40% | Path C plans / total active plans |
| Channel split | % of parent-initiated requests via app vs SMS | Track, no target | Request source field |

The channel split is tracked but not targeted. It tells us how parents prefer to engage, which informs V2 investment decisions.

### Adherence Metrics (Are parents sticking to their plans?)

| Metric | Definition | Target (Pilot) | How to measure |
|--------|-----------|-----------------|----------------|
| Plan adherence rate | % of parents on plans who make all scheduled payments on time | 65% | Completed plans / total active plans |
| Instalment completion rate | % of individual instalments paid on or before the due date | 75% | On-time instalments / total scheduled instalments |
| Partial payment rate | % of instalments where parent paid something but less than the scheduled amount | Track | Partial payments / total instalments |
| Plan dropout rate | % of parents who make 0 payments after selecting a plan | Below 10% | Zero-payment plans / total active plans |
| Average days overdue | For overdue instalments, average number of days past due before payment | Below 7 days | Date paid minus due date, for overdue payments |

### School Impact Metrics (Is the school better off?)

| Metric | Definition | Target (Pilot) | How to measure |
|--------|-----------|-----------------|----------------|
| Week 1 collection rate | % of expected term fees collected by end of Week 1 | No change expected (plans spread payments, don't accelerate them) | Zeraki Finance cashflow |
| Week 4 collection rate | % of expected term fees collected by end of Week 4 | 75% (up from estimated 55-70%) | Zeraki Finance cashflow |
| End-of-term collection rate | % of total fees collected by last day of term | 95% (up from estimated 85-93%) | Zeraki Finance cashflow |
| "Sent home" incidents | Number of students sent home for fees in first 3 weeks | 30% reduction vs previous term | School-reported (manual tracking) |
| Bursar time on collections | Self-reported hours spent chasing fees in first 3 weeks | 40% reduction | Bursar survey |
| Plan request queue processing time | Average time from parent request to bursar approval/decline | Under 24 hours | Timestamp difference in system |

**Note on Week 1 collection:** Plans don't make parents pay faster. They structure payments over time. So Week 1 collection might not improve. The improvement shows up in Week 4 and end-of-term numbers, because structured plans convert "might never pay" into "will pay over 4 weeks."

### Child Welfare Metrics (Is the real problem being addressed?)

| Metric | Definition | Target (Pilot) | How to measure |
|--------|-----------|-----------------|----------------|
| Fee-related absence days | Total student-days lost to fee-related exclusion | 50% reduction | School attendance records, filtered by reason |
| Students completing full term | % of enrolled students present on last day of term | Track, compare to baseline | Zeraki Analytics attendance data |

These are the hardest to measure and the most important. They require schools to record the reason for absence (fee-related vs other), which many don't do today. The pilot should establish this tracking practice.

---

## Layer 2: Zeraki Credit

### Eligibility Metrics (Is the scoring working?)

| Metric | Definition | Target (Pilot) | How to measure |
|--------|-----------|-----------------|----------------|
| Eligible parents (Path 1) | % of all parents who qualify through historical payment records | 10-15% | Eligibility engine output |
| Eligible parents (Path 2) | % of parents on Layer 1 plans who qualify through plan adherence | 15-20% of plan users | Eligibility engine output |
| Total eligible | Combined unique parents eligible through either path | 12-18% of all parents with outstanding fees | Deduplicated eligibility list |

If eligibility is too high (e.g., 40%+), the criteria are too loose and default risk will be unacceptable. If too low (e.g., 3%), the product won't have enough impact to justify building.

### Credit Uptake Metrics (Are eligible parents using it?)

| Metric | Definition | Target (Pilot) | How to measure |
|--------|-----------|-----------------|----------------|
| Offer delivery rate | % of eligible parents who successfully receive the credit offer (SMS delivered or app screen viewed) | 90% | SMS delivery reports + app analytics |
| Offer acceptance rate | % of parents who receive an offer and accept | 50% | Acceptances / offers delivered |
| Average credit amount | Mean top-up amount accepted | KES 3,000-4,000 | Sum of credit / number of arrangements |
| Decline rate | % who explicitly decline (vs simply not responding) | Track | Declines / offers delivered |
| No-response rate | % who don't respond within 7 days | Track | Expired offers / offers delivered |

The gap between decline rate and no-response rate is informative. High explicit declines might mean the terms aren't attractive. High no-response might mean the offer didn't reach them or wasn't understood.

### Repayment Metrics (Is the credit sustainable?)

| Metric | Definition | Target (Pilot) | How to measure |
|--------|-----------|-----------------|----------------|
| Repayment completion rate | % of credit arrangements fully repaid within the agreed timeframe | 85% | Completed / total active |
| On-time repayment rate | % of weekly repayments made on or before the due date | 75% | On-time payments / total scheduled |
| Default rate | % of arrangements where any instalment is 14+ days overdue | Below 10% | Overdue arrangements / total active |
| Total loss rate | % of credit amount not recovered by end of term | Below 5% | Unrecovered amount / total credit disbursed |
| Average days to full repayment | Mean calendar days from credit activation to final payment | Within agreed period (28-42 days) | Date of final payment minus activation date |

### Financial Metrics (Does the model work economically?)

| Metric | Definition | Target (Pilot) | How to measure |
|--------|-----------|-----------------|----------------|
| Total credit outstanding | Sum of all active, unrepaid credit | Below school-set limits | Zeraki Finance dashboard |
| School exposure as % of term fees | Total credit outstanding / total expected term fees | Below 3% | Calculation |
| Revenue per credit arrangement (Option B only) | Origination fee or revenue share earned per arrangement | Track for V2 modelling | Partner agreement terms |
| Cost of credit to parent (Option A) | Zero | Zero (validation that no hidden charges exist) | Audit |

---

## System Health Metrics

| Metric | Definition | Target | How to measure |
|--------|-----------|--------|----------------|
| Payment matching accuracy | % of M-Pesa payments correctly matched to the right student and plan | 99.5% | Manual audit of sample transactions |
| Manual reconciliation rate | % of total payments recorded manually (cash + bank) vs automatically (M-Pesa) | Track | Payment method field |
| SMS delivery rate | % of messages successfully delivered to parent phones | 95% | SMS gateway delivery reports |
| App engagement (plan users) | % of parents on plans who check the app at least once during the term | Track | App analytics |
| Approval queue latency | Time from plan request to bursar action | Under 24 hours (working days) | System timestamps |
| Duplicate payment flags | Number of potential duplicate flags raised per term | Track (should decrease over time) | Duplicate detection logs |

---

## Measurement Approach

### Baseline (Before Launch)

Before launching at pilot schools, capture for each school:
- Term N-1 fee collection timeline (what % collected by Week 1, Week 2, Week 4, end of term)
- Number of "sent home" incidents in the first 3 weeks (school-reported estimate if no formal records)
- Bursar's self-reported hours spent on fee collection in first 3 weeks
- Number of informal arrangements the bursar made (estimated from memory)
- Average number of fee payment transactions per parent per term

### Pilot Comparison

**Within-school comparison:** Compare Term N (with product) vs Term N-1 (without) at the same schools. Controls for school-specific factors.

**Cross-school comparison:** Compare pilot schools vs matched non-pilot Zeraki Finance schools in the same term. Controls for seasonal or economic factors (e.g., a bad economy affects all schools, but pilot schools should still perform better than non-pilot).

### Cohort Tracking

Track parents across multiple terms:
- Term 1: Baseline (no product)
- Term 2: First exposure to Zeraki Plans
- Term 3: Second term with Plans. Do adherence rates improve with familiarity?
- Term 4+: Introduce Layer 2 Credit. Track uptake and repayment.

Track whether parents who start on plans graduate to paying in full without plans over time. If the product is working, some parents will internalise the structure and no longer need it. That's success, even though it reduces plan adoption numbers.

---

## Reporting Cadence

| Audience | Report | Frequency |
|----------|--------|-----------|
| Zeraki product team | Full metrics dashboard (all metrics above) | Weekly during pilot |
| School bursar | Plan adherence summary + credit status | Weekly (automated in Zeraki Finance) |
| School headteacher/board | Term performance report (collection rates, sent-home incidents, plan/credit summary) | Per term |
| Zeraki leadership | Pilot performance summary with go/no-go recommendation | Per term |
| Lending partner (Option B, V2) | Portfolio performance (disbursed, repaid, default rate) | Monthly |

---

## What Good Looks Like After 2 Terms

If the pilot is working, after 2 full terms we should see:

- 25-30% of parents with outstanding fees are on formal plans
- 65%+ of those parents are completing their plans on time
- End-of-term collection rate has improved by 3-5 percentage points
- "Sent home" incidents have dropped measurably
- Bursars report spending significantly less time chasing fees
- 10-15% of parents with outstanding fees qualify for Layer 2 credit
- Credit repayment rate is 85%+, default rate is below 10%
- Parents who used a plan in Term 1 show improved payment behaviour in Term 2 (some no longer need a plan)
- Schools that piloted want to continue. Schools that didn't are asking to join.

If we don't see these patterns, something in the product design, the school implementation, or the underlying assumptions needs to be revisited.