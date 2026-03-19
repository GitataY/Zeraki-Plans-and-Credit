# Product Requirements Document: Layer 1 - Zeraki Plans

## 1. Overview

### Product name
Zeraki Plans

### One-liner
Structured fee instalment plans managed through Zeraki Finance, replacing the informal verbal arrangements that schools and parents currently negotiate at the school gate.

### Problem statement
Kenyan schools already allow parents to pay fees in instalments. But the arrangement is verbal, inconsistent, and invisible. The bursar negotiates individually with dozens of parents, records nothing digitally, and has no way to track who's on track and who isn't. Children get sent home when the informal system breaks down, not because no arrangement exists, but because no one can see it or manage it at scale.

### Proposed solution
A structured instalment plan feature within Zeraki Finance that lets schools offer standard payment plans, lets parents request a plan (through the app, via SMS, or in person with the bursar), and gives the school an approval workflow and dashboard to manage adherence across all students. No new payment infrastructure. Parents still pay to the same school paybill using the same student registration number. The only change is that the arrangement is now visible, trackable, and dignified.

### Target users
- **Primary:** School bursars and administrators who manage fee collection in Zeraki Finance
- **Secondary:** Parents of students at Zeraki Finance schools

## 2. How It Works Today (The Baseline)

1. Term opens. Bursar has a list of who owes what.
2. Headteacher decides which students to send home for non-payment.
3. Parents come to school, negotiate verbally with the bursar or headteacher.
4. An informal agreement is made ("pay half by Friday, the rest by end of month").
5. The agreement is not recorded in any system. It lives in the bursar's memory or notebook.
6. If the parent pays on time, good. If not, the child may be sent home again.
7. The bursar has no aggregate view of how many arrangements exist, how many are on track, or how much money is expected and when.

## 3. How It Works With Zeraki Plans

**Setup (once per term):**
1. Before term starts, the school configures instalment plan templates in Zeraki Finance (e.g., "4 weekly payments" or "2 fortnightly payments").
2. The school decides whether plans require bursar approval or are auto-approved.

**Three paths to a plan:**

**Path A: Parent requests via the Zeraki app**
1. Parent opens the Zeraki app, sees their fee balance for the term.
2. Below the balance, available payment plan options are displayed (e.g., "Weekly Plan: 4 x KES 3,750" or "Fortnightly Plan: 2 x KES 7,500").
3. Parent selects a plan and submits the request.
4. The bursar receives a notification in Zeraki Finance: "Wanjiku Kamau has requested a Weekly Plan for James Otieno (4523). Approve / Adjust / Decline."
5. Bursar approves (or adjusts the terms based on context, or declines with a reason).
6. Parent receives a confirmation SMS and sees the approved plan in their app, with payment dates and amounts.

**Path B: Parent requests via SMS**
1. Parent receives the standard fee balance SMS at the start of term.
2. The SMS includes plan options: "Your Term 2 balance for James (4523) is KES 15,000. To request a payment plan, reply 1 for 4 weekly payments or reply 2 for 2 fortnightly payments."
3. Parent replies with their choice.
4. The bursar receives the same approval notification in Zeraki Finance.
5. Bursar approves, adjusts, or declines.
6. Parent receives a confirmation or adjustment SMS.

**Path C: Bursar creates the plan after an in-person conversation**
1. Parent comes to the school and negotiates with the bursar or headteacher, as they do today.
2. Instead of recording the agreement in a notebook, the bursar opens Zeraki Finance, selects the student, and assigns a plan.
3. The bursar can use a standard template or create custom terms for that specific parent.
4. Parent receives a confirmation SMS with the agreed plan details.

**All three paths converge:**
- A plan is recorded in Zeraki Finance against the student.
- Both the parent and the school can see the same plan, the same schedule, and the same status.
- Payment reminders are sent on scheduled dates.
- When the parent pays to the school paybill, the payment is matched to the plan automatically.
- The bursar's dashboard shows aggregate plan adherence across all students.
- Parents on a plan whose payments are on track are not sent home. This is the agreement, and it's visible to both sides.

## 4. Scope

### In scope (MVP)

**School admin side (Zeraki Finance):**
- Plan template configuration: school sets instalment options (number of payments, frequency, amounts)
- Plan approval workflow: bursar reviews, approves, adjusts, or declines parent plan requests
- Bursar-initiated plan creation: assign a plan directly after an in-person conversation
- Plan adherence dashboard: aggregate view showing paid-in-full, on-plan-on-track, on-plan-behind, no-plan
- Per-student plan status: visible in the existing fee register alongside fee balance
- Automated payment matching: when a paybill payment comes in, it's matched to the student's plan schedule
- Manual payment recording: bursar records cash and bank deposit payments against a student's plan, with the same matching logic as M-Pesa
- Overdue alerts: bursar is notified when a parent misses a scheduled payment

**Parent side (app):**
- View fee balance with available plan options below it
- Request a plan (submit for school approval)
- View approved plan: schedule, amounts, due dates, progress
- Receive confirmation when plan is approved or adjusted

**Parent side (SMS, for parents without the app):**
- Receive fee balance SMS with plan options
- Request a plan by replying to the SMS
- Receive confirmation when plan is approved
- Receive payment reminders on scheduled dates
- Receive confirmation when a payment is matched to the plan
- Check balance and plan status by texting a keyword

### Out of scope (MVP)

- Predictive collection forecasting (V2, requires historical plan data)
- Credit top-up offers (Layer 2, separate product)
- Inter-term pre-payment tracking (future enhancement)
- Multi-child plan management in a single view (V2)
- WhatsApp as a communication channel (V2)
- USSD-based plan selection (V2)
- Automatic plan suggestions based on parent's historical payment pattern (V2)

## 5. Detailed Requirements

### 5.1 Plan Template Configuration (School Admin)

**What the bursar does:** In Zeraki Finance settings, the school creates one or more instalment plan templates for the term.

**Required fields per template:**
- Plan name (e.g., "Weekly Plan", "Fortnightly Plan")
- Number of instalments (e.g., 4, 8)
- Frequency (weekly, fortnightly, monthly)
- Start date (defaults to first day of term, adjustable)
- Approval mode: auto-approve all requests, or require bursar approval for each

**System calculates:**
- Individual instalment amounts (total outstanding balance divided by number of instalments)
- Payment due dates based on frequency and start date

**Constraints:**
- All plans must complete within the term. No plan should extend beyond the term end date.
- Maximum of 3 plan templates per school per term (keeps SMS selection simple and avoids decision paralysis in the app).
- Plans are interest-free and fee-free. No charges for using a plan.

### 5.2 Plan Request and Approval

**Three paths, one approval workflow:**

**Path A: Parent requests via the Zeraki app**
1. Parent opens the app, navigates to fee balance for the current term.
2. Below the balance, the system displays available plan templates with calculated amounts and dates.
3. Parent taps "Request Plan" on their preferred option.
4. System creates a plan request with status PENDING.
5. Bursar receives a notification in Zeraki Finance: "[Parent Name] has requested [Plan Name] for [Student Name] ([Reg]). [N] payments of KES [Amount]. Approve / Adjust / Decline."
6. If approved: plan status changes to ACTIVE. Parent receives a confirmation SMS and sees the plan in their app.
7. If adjusted: bursar modifies the terms (e.g., changes from 4 to 6 instalments based on knowledge of the parent's situation). Parent sees the adjusted offer in the app and confirms.
8. If declined: parent receives a message suggesting they contact the school to discuss alternatives. No reason is shown to avoid embarrassment.

**Path B: Parent requests via SMS**
1. Parent receives fee balance SMS with plan options.
2. Parent replies with a number to request a plan.
3. System creates a plan request with status PENDING.
4. Same approval flow as Path A (bursar approves, adjusts, or declines in Zeraki Finance).
5. Parent receives confirmation or adjustment via SMS.

**Path C: Bursar creates the plan directly**
1. Parent and bursar have a conversation (in person or by phone), as they do today.
2. Bursar opens the student's record in Zeraki Finance.
3. Bursar selects a template or creates custom terms (custom number of instalments, custom amounts, custom dates).
4. Plan is created with status ACTIVE immediately (no approval needed since the bursar is the approver).
5. Parent receives a confirmation SMS summarising the agreed plan.

**Why the approval step matters:**
- It gives the school control. A parent with a history of broken pledges might get adjusted terms or a shorter plan.
- It preserves the bursar's judgement for cases that need it, without requiring the bursar to initiate every plan manually.
- It makes the process dignified for the parent. They're submitting a request through a system, not pleading at the gate. Even if the plan is adjusted, the interaction is structured and private.
- It prevents gaming. A parent can't just select the longest plan with the smallest payments without the school's agreement.

**Approval queue for the bursar:**

In Zeraki Finance, the bursar sees a "Plan Requests" queue:

| Student | Parent | Requested Plan | Amount/Instalment | Status | Action |
|---------|--------|---------------|-------------------|--------|--------|
| James Otieno (4523) | Wanjiku Kamau | Weekly (4x) | KES 3,750 | Pending | Approve / Adjust / Decline |
| Mary Achieng (4601) | Otieno Odhiambo | Fortnightly (2x) | KES 7,500 | Pending | Approve / Adjust / Decline |
| Peter Mwangi (4412) | Grace Mwangi | Weekly (4x) | KES 2,250 | Pending | Approve / Adjust / Decline |

The bursar can approve all with one click ("Approve All") for efficiency, or review individually. Schools that set approval mode to "auto-approve" skip this step entirely and all requests are activated immediately.

### 5.3 Plan Adherence Dashboard (School Admin)

**Aggregate view (new widget on Zeraki Finance home):**

Shows for the current term:
- Total students: X
- Paid in full: Y (Z%)
- On a plan, on track: Y (Z%)
- On a plan, behind schedule: Y (Z%)
- On a plan, not started (selected plan but made no payment): Y (Z%)
- No plan, partial payment: Y (Z%)
- No plan, no payment: Y (Z%)

**Per-student view (enhanced fee register):**

New columns in the existing fee register:
- Plan status: None / On Track / Behind / Overdue / Complete
- Next payment due: date and amount
- Payments made vs scheduled: e.g., "3 of 4"

Sortable and filterable by plan status.

### 5.4 Payment Matching and Manual Reconciliation

Payments come in through multiple channels. The system must handle all of them.

**Channel 1: M-Pesa paybill (automatic matching)**

When a payment arrives at the school's M-Pesa paybill:
1. Zeraki Finance matches it to the student account (using the registration number in the account field)
2. If the student has an active plan, the system checks: does this payment satisfy the current scheduled instalment?
3. If yes (payment >= scheduled amount): mark instalment as paid, advance to next scheduled payment
4. If partial (payment < scheduled amount): record the payment, update remaining balance for that instalment, do not advance schedule
5. If overpayment (payment > scheduled amount): apply excess to next instalment(s)
6. Update the dashboard and plan status in real time (or near-real-time, depending on C2B callback timing)

**Channel 2: Cash payment at the school office (manual recording)**

Some parents pay cash directly to the bursar. This is common, especially in rural schools and for smaller amounts. The bursar must be able to record this against the student's plan:

1. Parent pays cash at the office. Bursar issues a physical receipt (or prints one from Zeraki Finance's thermal printer app).
2. Bursar opens the student's record in Zeraki Finance.
3. Bursar selects "Record Payment" and enters: amount, date, payment method (cash), and optionally a receipt number.
4. The system applies the payment to the student's plan using the same logic as M-Pesa (satisfies instalment, partial, or overpayment).
5. Plan status and dashboard update immediately.
6. Parent receives a confirmation SMS (if they have a phone number on file).

This is essentially what bursars already do today with Zeraki Finance receipting. The only addition is that the payment is now also matched against an active plan, not just recorded against the fee balance.

**Channel 3: Bank deposit (manual recording)**

Some parents deposit fees directly into the school's bank account, especially for larger amounts. The flow is similar to cash:

1. Parent makes a bank deposit and brings the deposit slip to school (or sends a photo via WhatsApp).
2. Bursar verifies the deposit and records it in Zeraki Finance: amount, date, payment method (bank deposit), reference number from the slip.
3. System applies the payment to the plan.
4. Parent receives a confirmation SMS.

**Why manual reconciliation matters:**

If the system only works for M-Pesa payments, it creates a two-tier experience. Parents who pay via M-Pesa see their plan update automatically. Parents who pay cash or bank deposit see nothing until the bursar manually records it. If the bursar is busy (which they always are in Week 1), the cash-paying parent's plan shows "overdue" even though they've already paid. This erodes trust in the system.

The manual recording flow must be quick (under 30 seconds per payment) and available on the bursar's phone, not just desktop. Bursars already receipt payments on their phones through Zeraki Finance. This builds on that existing behaviour.

**Edge cases to handle:**
- Parent pays a lump sum that covers the entire remaining plan balance: mark plan as complete
- Parent pays outside the schedule (e.g., on a Wednesday when instalment was due Monday): still match to the current instalment, don't penalise timing within the week
- Parent pays without a plan: record as a normal payment (no plan tracking applies)
- Two payments in one day (e.g., M-Pesa and cash): both count toward the plan
- Duplicate recording: if a bursar accidentally records a cash payment that was already matched via M-Pesa, the system should flag potential duplicates (same student, same amount, same day) for review

### 5.5 SMS Notifications

**Plan request received (sent when parent requests a plan via SMS or app):**
"[SCHOOL]: Your request for a payment plan for [CHILD] ([REG]) has been received. We'll confirm your plan shortly."

**Plan approved (sent when bursar approves the request):**
"[SCHOOL]: Payment plan approved for [CHILD] ([REG]). [N] payments of KES [AMOUNT] every [FREQUENCY]. First payment due [DATE]. Paybill [PAYBILL], Acc [REG]."

**Plan adjusted (sent when bursar modifies the requested terms):**
"[SCHOOL]: A payment plan for [CHILD] ([REG]) has been set up. [N] payments of KES [AMOUNT] every [FREQUENCY]. First payment due [DATE]. Paybill [PAYBILL], Acc [REG]. Contact school with any questions."

**Plan declined (sent when bursar declines the request):**
"[SCHOOL]: We were unable to set up the requested plan for [CHILD] ([REG]). Please contact the school to discuss payment options."

**Plan created by bursar (sent after in-person conversation, Path C):**
"[SCHOOL]: Payment plan confirmed for [CHILD] ([REG]). [N] payments of KES [AMOUNT] every [FREQUENCY]. First payment due [DATE]. Paybill [PAYBILL], Acc [REG]."

**Payment reminder (sent on or before each due date):**
"[SCHOOL]: Payment of KES [AMOUNT] for [CHILD] ([REG]) is due [DATE]. Paybill [PAYBILL], Acc [REG]. Payments made: [X] of [TOTAL]."

**Payment received confirmation:**
"[SCHOOL]: KES [AMOUNT] received for [CHILD] ([REG]). Plan progress: [X] of [N] payments complete. Remaining balance: KES [BALANCE]."

**Overdue notice (sent 3 days after a missed payment):**
"[SCHOOL]: Payment of KES [AMOUNT] for [CHILD] ([REG]) was due [DATE]. Please pay as soon as possible. Paybill [PAYBILL], Acc [REG]."

**Plan completion:**
"[SCHOOL]: All Term [N] fees for [CHILD] ([REG]) are now fully paid. Thank you."

**Design principles for all SMS:**
- Messages come from the school's sender ID, not "Zeraki"
- Maximum 1 reminder per scheduled payment (no repeated nagging for the same instalment)
- Overdue notice sent once, 3 days after the due date. No further automated follow-up (the bursar handles escalation from here)
- Encouraging, factual tone. No threatening language.
- Decline messages do not state a reason. The parent contacts the school directly to discuss.
- Under 160 characters where possible (single SMS to reduce carrier costs)

### 5.6 Balance Check (Parent-Initiated)

Parent sends keyword "BAL" to the school's SMS short code (or replies "BAL" to any Zeraki message).

System replies:
"[CHILD] ([REG]) at [SCHOOL]. Term [N] fees: KES [TOTAL]. Paid: KES [PAID]. Remaining: KES [REMAINING]. Plan: [X] of [N] payments made. Next due: KES [AMOUNT] by [DATE]."

If no plan: "Plan: None. Contact school to set up a payment plan."

Works on any phone. No app or data required.

## 6. Key Product Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| Payment mechanism | Existing school paybill + student reg number | Zero behaviour change for parents |
| Plan terms | Set by the school, not by Zeraki | Schools know their context; a Nairobi private school and a rural public school need different options |
| Plan request channels | App + SMS + bursar-initiated | App for parents who use it, SMS for those who don't, bursar-initiated for in-person conversations. All three paths end in the same system. |
| School approval | Required by default, with auto-approve option | Gives the school control over who gets a plan and on what terms. Auto-approve available for schools that prefer a hands-off approach. |
| Interest/fees on plans | Zero | Keeps it out of lending regulation; maintains it as a school admin feature |
| Overdue handling | One automated notice, then bursar discretion | The system informs; the human decides what to do |
| Plan visibility | Both parent and school see the same plan status | Transparency prevents disputes |

## 7. Dependencies

- **Zeraki Finance internal API/database:** Read fee balances, write plan records and payment matches, serve plan request queue to bursars
- **Zeraki Finance receipting flow:** Manual payment recording for cash and bank deposits must integrate with plan matching. This builds on the existing receipting feature, not a new system.
- **Zeraki parent app:** Display fee balance with plan options, handle plan request submission, show approved plan with progress. Requires updates to the existing parent-facing app.
- **M-Pesa C2B callback:** Real-time or near-real-time payment confirmation for automatic plan matching on paybill payments
- **SMS gateway:** Programmatic, scheduled sends with school sender ID. Also handles inbound SMS replies for plan requests.
- **School buy-in:** Headteacher and bursar agree to offer formal plans, use the approval workflow, and honour the "on plan = stays in school" commitment

## 8. What This Does NOT Do

To be explicit about boundaries:

- **Does not guarantee the child stays in school.** The school retains full authority. The product provides visibility and structure, but the headteacher still makes enforcement decisions.
- **Does not replace the bursar's judgement.** Hardship cases, exceptional circumstances, and edge cases still require human discretion. The product handles the routine; the bursar handles the exceptions.
- **Does not offer credit.** No money is lent, no interest is charged, no financial risk is taken by Zeraki. This is a tracking and communication tool for arrangements the school and parent agree to.
- **Does not change how much parents owe.** The total fee is the same. The plan just spreads the payment over time.

## 9. Success Criteria (Pilot)

| Metric | Baseline (estimated) | Target |
|--------|---------------------|--------|
| Parents on a formal plan | 0% (all arrangements are informal) | 30% of parents with outstanding fees |
| Plan adherence rate | Unknown (no tracking exists) | 70% of parents on plans make all scheduled payments |
| Bursar time on fee collection (first 2 weeks) | Estimated 15-20 hours | 40% reduction |
| "Sent home" incidents (first 2 weeks) | Baseline TBD per school | 30% reduction |
| Parent opt-out from SMS | N/A | Below 3% |
| Bursar satisfaction (survey) | N/A | 80%+ rate the feature as useful |

## 10. Open Questions

- [ ] Will schools actually honour the "on a plan = stays in school" commitment? This is the product's core promise, and it depends on school behaviour, not technology.
- [ ] What percentage of parents at Zeraki schools actively use the parent app vs only receiving SMS? This determines how much to invest in the app experience vs the SMS flow for launch.
- [ ] What happens when a parent has children at multiple schools on Zeraki? Each school has its own plans. The parent manages them separately via app or SMS. Is this confusing?
- [ ] Should the plan automatically roll over unpaid balance to the next term, or should each term start fresh?
- [ ] How does this interact with existing pledge tracking in Zeraki Finance? Does it replace pledges, or do both systems coexist?
- [ ] What is the expected bursar workload for plan approvals in Week 1? A school with 200 plan requests on opening day needs to process them quickly, or the approval step becomes a bottleneck. Is "Approve All" sufficient, or do we need batch approval with filters?
- [ ] Should declined plan requests show a reason to the parent, or just redirect them to contact the school? Showing a reason adds transparency but could feel harsh via SMS.