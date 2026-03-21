# User Stories

## Epics

| Epic | Layer | Description | Primary Persona |
|------|-------|-------------|-----------------|
| E1: Plan configuration | Layer 1 | School sets up instalment plan templates for the term | Mr. Kamau (Bursar) |
| E2: Plan request and approval | Layer 1 | Parents request plans, school approves | Otieno, Wanjiku, Mama Amani, Mr. Kamau |
| E3: Plan tracking and reminders | Layer 1 | Payments are matched to plans, reminders are sent, dashboard updates | Mr. Kamau, all parent personas |
| E4: Manual reconciliation | Layer 1 | Cash and bank payments are recorded against plans | Mr. Kamau |
| E5: Credit eligibility and offers | Layer 2 | System identifies eligible parents and delivers offers | Wanjiku, Mwende, Otieno |
| E6: Credit acceptance, disbursement, and repayment | Layer 2 | Parent accepts, lender pays school, repayment flows through waterfall | All parent personas, Mr. Kamau |
| E7: School controls and oversight | Both | School enables/disables credit, monitors settlement, views term reports | Mr. Kamau |

---

## Epic 1: Plan Configuration

### E1-S1: Create plan templates
**As a** bursar,
**I want to** create instalment plan templates for the term (e.g., "Weekly: 4 payments", "Fortnightly: 2 payments"),
**So that** parents have standardised options to choose from instead of each arrangement being a one-off negotiation.

**Acceptance criteria:**
- Bursar can create up to 3 templates per term
- Each template has: name, number of instalments, frequency (weekly/fortnightly/monthly), start date
- System calculates instalment amounts automatically based on each student's outstanding balance
- Templates can be edited before any parent has been assigned to them
- Templates cannot be deleted once a parent is on an active plan using that template

### E1-S2: Set approval mode
**As a** bursar,
**I want to** choose whether plan requests require my approval or are automatically approved,
**So that** I can review requests at schools where I want control, or save time at schools where auto-approval is appropriate.

**Acceptance criteria:**
- Setting is per-school, per-term
- Two options: "Require approval" (default) or "Auto-approve all requests"
- Can be changed mid-term (but does not retroactively affect already-approved plans)

---

## Epic 2: Plan Request and Approval

### E2-S1: Parent requests a plan via the app
**As a** parent using the Zeraki app,
**I want to** see available payment plans below my fee balance and request one,
**So that** I can set up a structured arrangement without calling the school or visiting in person.

**Acceptance criteria:**
- Available plans are shown on the fee balance screen with calculated amounts and due dates specific to my balance
- I can tap "Request Plan" on my preferred option
- I receive an in-app confirmation that my request is pending
- If auto-approve is enabled, the plan activates immediately and I see the schedule
- If approval is required, I see "Pending school approval" status

### E2-S2: Parent requests a plan via SMS
**As a** parent who doesn't use the app,
**I want to** request a payment plan by replying to the fee balance SMS,
**So that** I can access the same structured arrangements without needing a smartphone.

**Acceptance criteria:**
- Fee balance SMS includes plan options with reply codes (e.g., "Reply 1 for weekly, Reply 2 for fortnightly")
- My reply is recorded as a plan request
- I receive an SMS confirming my request is pending
- If auto-approve is enabled, I receive a confirmation SMS with the full schedule

### E2-S3: Bursar reviews and approves plan requests
**As a** bursar,
**I want to** see a queue of pending plan requests and approve, adjust, or decline each one,
**So that** I can apply my judgement to requests that need it while processing straightforward ones quickly.

**Acceptance criteria:**
- Plan request queue shows: student name, parent name, requested plan type, instalment amount, number of instalments
- I can approve individually or use "Approve All" for the full queue
- I can adjust the terms before approving (e.g., change from 4 to 6 instalments for a parent I know is on a tight budget)
- I can decline with no reason shown to the parent (parent is told to contact the school to discuss)
- Approved plans send a confirmation SMS to the parent immediately

### E2-S4: Bursar creates a plan after an in-person conversation
**As a** bursar,
**I want to** record a payment arrangement in Zeraki Finance after agreeing terms with a parent face-to-face or by phone,
**So that** the arrangement is tracked in the system instead of in my notebook.

**Acceptance criteria:**
- I can open any student's fee record and select "Create Plan"
- I can use a template or set custom terms (custom number of instalments, custom amounts, custom start date)
- The plan is created as active immediately (no approval step needed since I am the approver)
- Parent receives a confirmation SMS with the agreed schedule
- The plan appears on the dashboard alongside app-requested and SMS-requested plans

### E2-S5: Parent views approved plan in the app
**As a** parent whose plan has been approved,
**I want to** see my plan schedule in the app with payment dates and amounts,
**So that** I know exactly what I owe and when.

**Acceptance criteria:**
- Plan screen shows: total fee, amount covered by plan, number of instalments, amount per instalment, due dates
- Each instalment shows status: upcoming, paid, partially paid, overdue
- A progress indicator shows how many payments I've completed (e.g., "2 of 4")
- I can see any payments already matched to the plan

---

## Epic 3: Plan Tracking and Reminders

### E3-S1: Automatic payment matching (M-Pesa)
**As the** system,
**When** a payment arrives at the school's M-Pesa paybill for a student with an active plan,
**I should** automatically match the payment to the current scheduled instalment and update the plan status.

**Acceptance criteria:**
- Payment matched by student registration number in the paybill account field
- If payment >= instalment amount: mark instalment as paid, advance to next
- If payment < instalment amount: record partial payment, update remaining for that instalment
- If payment > instalment amount: apply excess to next instalment(s)
- Dashboard and app update in real time (or near-real-time)
- Parent receives a payment confirmation SMS

### E3-S2: Payment reminders
**As a** parent on an active plan,
**I want to** receive a reminder before each scheduled payment,
**So that** I don't miss a due date unintentionally.

**Acceptance criteria:**
- SMS sent on the day the payment is due (morning)
- Includes: amount due, student name, paybill number, account number, progress (e.g., "Payment 3 of 4")
- One reminder per instalment. No repeated messages for the same due date.
- Not sent if the instalment has already been paid before the due date

### E3-S3: Overdue notification
**As a** bursar,
**I want to** be notified when a parent misses a scheduled payment by more than 3 days,
**So that** I can follow up personally with the ones who need attention.

**Acceptance criteria:**
- Parent receives one overdue SMS 3 days after the missed due date
- Bursar sees the student flagged as "behind schedule" on the dashboard
- No further automated messages to the parent for that instalment (bursar handles escalation)

### E3-S4: Plan completion
**As a** parent who has made all scheduled payments,
**I want to** receive a confirmation that my plan is complete and fees are fully paid,
**So that** I have peace of mind and a record.

**Acceptance criteria:**
- SMS sent when the final instalment is paid: "All Term [N] fees for [CHILD] are now fully paid. Thank you."
- Plan status changes to "Complete" on the dashboard and in the parent app
- Student is removed from any outstanding-fees lists in Zeraki Finance

---

## Epic 4: Manual Reconciliation

### E4-S1: Record a cash payment against a plan
**As a** bursar,
**I want to** record a cash payment from a parent and have it matched to their active plan,
**So that** parents who pay cash get the same plan tracking experience as those who pay via M-Pesa.

**Acceptance criteria:**
- From the student's fee record, I select "Record Payment"
- I enter: amount, date, payment method (cash), receipt number (optional)
- The system applies the payment to the plan using the same matching logic as M-Pesa payments
- Plan status and dashboard update immediately
- Parent receives a confirmation SMS
- A receipt can be printed via the Zeraki Finance thermal printer app

### E4-S2: Record a bank deposit against a plan
**As a** bursar,
**I want to** record a bank deposit from a parent and have it matched to their active plan,
**So that** bank-paying parents are not shown as overdue when they've already paid.

**Acceptance criteria:**
- Same flow as cash, but payment method is "bank deposit" with a reference number field
- Bursar verifies the deposit slip before recording
- Same plan matching logic applies

### E4-S3: Duplicate payment detection
**As a** bursar,
**I want to** be alerted if a payment might be a duplicate (e.g., same student, same amount, same day recorded twice),
**So that** I don't accidentally credit a student's plan twice for a single payment.

**Acceptance criteria:**
- System flags potential duplicates: same student, same amount, within 24 hours, different recording methods (e.g., one M-Pesa auto-match and one manual cash entry)
- Flag is a warning, not a block. Bursar reviews and confirms or dismisses.
- Dismissed duplicates are not flagged again

---

## Epic 5: Credit Eligibility and Offers

### E5-S1: System identifies eligible parents
**As the** system,
**I should** automatically identify parents who qualify for a fee top-up based on their payment history,
**So that** the bursar has a ready list of eligible parents without manual analysis.

**Acceptance criteria:**
- Runs at a configurable point during the term (default: Week 4)
- Checks Path 1 criteria (4+ terms history, 90%+ payment within 4 weeks) against Zeraki Finance historical data
- Checks Path 2 criteria (active plan, 3+ payments made, 70%+ coverage) against current term plan data
- Produces a list of eligible parents with their calculated credit limit
- List is visible to the bursar in Zeraki Finance, not to parents (until the school enables offers)

### E5-S2: School enables credit offers
**As a** bursar,
**I want to** review the eligible parent list and decide whether to enable credit offers this term,
**So that** the school controls who receives offers and protects the school-parent relationship.

**Acceptance criteria:**
- Bursar can enable offers for all eligible parents, for specific parents only, or disable for the term
- Bursar can choose auto-offer (all eligible parents receive offers automatically) or manual (bursar approves each individually)
- The school bears no financial risk. Enabling offers does not create any school exposure. A lending partner provides the capital.

### E5-S3: Parent receives credit offer via the app
**As a** parent who qualifies for a fee top-up,
**I want to** see the offer in my app with clear terms,
**So that** I can make an informed decision about whether to accept.

**Acceptance criteria:**
- Offer appears below the fee balance on the app home screen
- Shows: maximum amount available, repayment schedule, total cost (including service fee), what happens if I accept (money goes to school, I repay to same paybill)
- Consent screen explains data sharing with credit partner and CRB reporting before I can accept
- Clear "Accept" and "No thanks" buttons
- If I decline, the offer disappears and does not return this term

### E5-S4: Parent receives credit offer via SMS
**As a** parent who qualifies but doesn't use the app,
**I want to** receive the offer via SMS with a way to get details and accept,
**So that** I have the same access as app-using parents.

**Acceptance criteria:**
- Initial SMS: brief offer with a "Reply INFO for details" prompt
- Details SMS: amount, repayment schedule, total cost (including service fee), "Same paybill, same account. Reply YES to apply."
- Consent SMS (when parent replies YES): explains data sharing with credit partner and CRB reporting. "Reply CONFIRM to proceed or CANCEL to stop."
- Two-step consent (YES then CONFIRM) is required for SMS. This is a credit product with CRB implications.
- If parent replies CANCEL or doesn't reply within 7 days, offer expires. No follow-up sent.

---

## Epic 6: Credit Acceptance and Repayment

### E6-S1: Parent accepts credit and school is paid
**As a** parent who accepts a fee top-up offer,
**I want to** have the school paid directly by the lending partner so my child's fee balance is settled,
**So that** the school sees me as covered and my child stays in school.

**Acceptance criteria:**
- Upon acceptance, Zeraki shares the parent's payment history with the lending partner via API (consent already captured)
- Lending partner makes a credit decision (approve/decline/adjusted amount). Target: near-instant automated decisioning.
- If approved: lender disburses the top-up amount to the school's M-Pesa paybill, referencing the student's registration number
- Zeraki Finance reconciles the disbursement as a payment against the student's fee balance
- A repayment schedule is created with weekly amounts and due dates
- Parent receives confirmation SMS from the school sender ID with the full schedule, including total cost and "Pay to [SCHOOL_PAYBILL], Acc [REG]"
- If declined: parent receives a neutral SMS from the school sender ID. No reason given. "This does not affect your child's enrolment."
- The app shows the credit arrangement alongside any existing plan

### E6-S2: Waterfall payment allocation
**As the** system,
**When** a payment arrives at the school's M-Pesa paybill for a student with an active credit arrangement,
**I should** allocate the lender's share and forward it to the lending partner, with the remainder going to the school.

**Acceptance criteria:**
- System checks incoming payment against active credit arrangements by student registration number
- If active credit: allocate the weekly repayment amount to the lender. Forward via B2B transfer.
- Any amount above the weekly repayment goes to the school
- If payment is less than the weekly repayment: full payment goes to the lender. Parent is behind on schedule.
- If no active credit: full amount goes to the school as normal
- Manual payments (cash/bank deposit) recorded by the bursar follow the same waterfall logic
- Settlement with the lending partner happens daily (batch)
- All allocations are logged and visible to the bursar on the Credit page

### E6-S3: Credit repayment tracking
**As a** bursar,
**I want to** see credit repayment progress for all students with active arrangements,
**So that** I have visibility into the credit activity at my school, even though the school bears no financial risk.

**Acceptance criteria:**
- Credit page shows: total active arrangements, total disbursed to school, total repaid, total outstanding, number on track, number overdue
- Per-student view: credit amount, repaid, remaining, payments made vs scheduled, status, funded-by column
- Overdue flag after 3 days. CRB warning flag after 21 days.
- This is informational only. No "chase payment" buttons. Reminders are automated by the system. Repayment is between the parent and the waterfall.

### E6-S4: Credit repayment reminders
**As a** parent with an active credit arrangement,
**I want to** receive weekly reminders from my school with the amount due and paybill details,
**So that** I stay on track with my repayments.

**Acceptance criteria:**
- All reminders come from the school sender ID. The lending partner never contacts the parent directly.
- Includes: amount due, remaining balance, school paybill number and account number, progress (e.g., "Payment 2 of 4")
- Overdue notice sent once, 3 days after a missed payment, from school sender ID
- CRB warning sent at 21 days overdue, from school sender ID, before 30-day CRB listing

### E6-S5: Credit fully repaid
**As a** parent who has completed all credit repayments,
**I want to** receive confirmation that the arrangement is closed,
**So that** I know I have no remaining obligations.

**Acceptance criteria:**
- SMS: "[SCHOOL]: Fee top-up for [CHILD] ([REG]) is fully repaid. Thank you."
- Credit status changes to "Complete" on the dashboard and in the parent app
- Parent's eligibility for future credit is maintained (successful repayment strengthens their profile)

---

## Epic 7: School Controls and Oversight

### E7-S1: Enable or disable credit offers
**As a** bursar or headteacher,
**I want to** control whether credit offers are sent to parents at our school,
**So that** the school can decide whether to participate in the credit programme each term.

**Acceptance criteria:**
- Toggle in Zeraki Finance Settings: "Enable credit offers this term: On/Off"
- Off by default. School must actively opt in each term.
- When disabled: no new offers are sent. Existing arrangements continue as normal (school was already paid, repayment continues through the waterfall).
- Choice between auto-offer (all eligible parents) or manual (bursar approves each individually)

### E7-S2: View waterfall settlement detail
**As a** bursar,
**I want to** see how incoming payments are being split between the school and the lending partner,
**So that** I can trust the system and verify the correct amounts are being forwarded.

**Acceptance criteria:**
- Credit page shows a settlement log: each payment received, how it was allocated (school share vs lender share), date forwarded
- Totals match the lending partner's records (reconciliation)
- Bursar can export the settlement log as CSV

### E7-S3: Term-end summary report
**As a** bursar,
**I want to** see a summary of all plans and credit activity for the term,
**So that** I can report to the headteacher and school board on how the feature performed.

**Acceptance criteria:**
- Report includes: total plans created, adherence rate, total credit offered, total repaid, total outstanding, default rate
- Comparison to previous term (if data exists)
- Exportable as PDF or CSV
- Available in the Zeraki Finance reports section