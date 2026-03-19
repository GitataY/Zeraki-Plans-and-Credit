# User Personas

## Parent Personas

These personas represent distinct payment behaviour patterns that would exist in Zeraki Finance data. In a real implementation, the segmentation would be validated against actual data from pilot schools.

---

### Persona 1: Wanjiku, the Consistent Payer

**Profile:** Runs a small food kiosk in Kasarani. Two children at a local private primary school. Earns KES 800-1,200 per day. Has a basic smartphone (Tecno Pop 5) and uses the Zeraki parent app to check her children's grades.

**Fee payment behaviour:**
- Pays in 2-3 chunks within the first 3 weeks of term
- Has never had her children sent home for fees
- Has used Zeraki's parent app to check fee balances
- Total termly fees: KES 24,000 (KES 12,000 per child)

**How she interacts with the product:**

**Layer 1 (Plans):** Wanjiku probably doesn't need a formal plan most terms. She pays relatively quickly. But she might request a plan during a tough term (e.g., January when December spending has drained her savings). She'd request via the app, selecting a 4-week plan. The bursar would auto-approve given her strong history.

**Layer 2 (Credit):** Wanjiku qualifies through Path 1 (historically strong payer). If she has a bad term, she'd see a credit offer in the app. She'd likely accept a small top-up (KES 3,000-4,000) and repay within 2-3 weeks. Low risk. This is the parent who "always pays but sometimes needs a bridge."

**Channel preference:** App primary, SMS secondary. She checks the app for grades anyway, so fee plans and credit offers in the app feel natural.

**What matters to her:** Speed and privacy. She doesn't want to negotiate at the school gate. She wants to handle it on her phone quietly and keep her dignity intact.

---

### Persona 2: Otieno, the Instalment Payer

**Profile:** Casual construction worker in Ruiru. One child in a public secondary day school. Earns KES 700-1,500 per day but works irregularly (15-22 days per month). Wife sells vegetables at the local market. Has a smartphone but mostly uses it for M-Pesa and WhatsApp.

**Fee payment behaviour:**
- Pays in 4-6 chunks spread across the full term
- His child has been sent home twice in the past year
- Has made pledges to the school and honoured about 70% of them
- Total termly fees: KES 13,500

**How he interacts with the product:**

**Layer 1 (Plans):** Otieno is the core user for Zeraki Plans. He already pays in instalments informally. A formal plan gives him structure and protects his child from being sent home. He'd likely select a plan via SMS (he doesn't regularly use the Zeraki app). A weekly plan of 4 x KES 3,375 matches his income pattern on good weeks.

**Layer 2 (Credit):** Otieno qualifies through Path 2 (plan-adherent) if he makes 3+ of his 4 scheduled payments. If he hits Week 4 and is KES 3,000 short because work dried up, a top-up offer via SMS could cover the gap. He'd accept. Repayment would happen over the next 3-4 weeks as work picks back up.

**Channel preference:** SMS only. He won't download the app or check it regularly. Everything needs to work through text messages.

**What matters to him:** That his child stays in school. The shame of his son being sent home in front of classmates is what keeps him up at night. A plan that prevents that, even if the payments are tight, is worth it.

---

### Persona 3: Mama Amani, the Struggling Payer

**Profile:** Single mother, domestic worker in Lavington. One child in a low-cost private school. Earns KES 18,000 per month as a house help. Has a feature phone (no smartphone).

**Fee payment behaviour:**
- Pays in 5-6 small chunks across the entire term
- Always has a balance at end of term that rolls over
- Has negotiated directly with the headteacher multiple times
- Total termly fees: KES 8,000

**How she interacts with the product:**

**Layer 1 (Plans):** Mama Amani is the parent the informal system fails most. She negotiates every term, feels ashamed every time, and her arrangements are forgotten or overridden when the school is under financial pressure. A formal plan gives her something she's never had: a written agreement that both sides can see. She'd select a plan via SMS (feature phone). Even a 6-week plan of roughly KES 1,350 per week is a stretch, but it's structured and visible.

**Layer 2 (Credit):** Mama Amani might not qualify initially. Her payment history is inconsistent, and she often carries balances across terms. But after one or two terms on a Layer 1 plan where she demonstrates adherence (making most scheduled payments), she'd build the data needed to qualify through Path 2. The product creates a path from "struggling payer with no options" to "structured payer who qualifies for affordable support."

**Channel preference:** SMS only, feature phone. USSD if available in V2.

**What matters to her:** Not being judged. The current system makes her feel like a bad parent every term. A formal plan that she can follow, with clear expectations, gives her a sense of control she's never had over this process.

---

### Persona 4: Mwende, the Full Payer Who Hits a Crisis

**Profile:** Teacher at a neighbouring school. Two children at a mid-range private primary. Earns KES 45,000 per month. Uses the Zeraki parent app regularly. Always pays fees in full during the first week of term.

**Fee payment behaviour:**
- Pays 100% within the first 5 days, every term, for the past 3 years
- Has never needed any arrangement or negotiation
- Total termly fees: KES 60,000 (KES 30,000 per child)

**How she interacts with the product:**

**Layer 1 (Plans):** Mwende doesn't use Layer 1 under normal circumstances. She pays in full.

**Layer 2 (Credit):** This is the term her husband lost his job. Or she had a medical emergency. Or a family member passed away and the funeral costs were significant. Suddenly, KES 60,000 in Week 1 is impossible. She has KES 40,000 and is KES 20,000 short.

Mwende qualifies immediately through Path 1 (historically strong payer). Her 3 years of perfect payment history means the system doesn't hesitate. She sees a credit offer in the app for up to KES 15,000 (capped at 30% of fees or KES 5,000 per child). She accepts, the school is paid, and she repays over 4 weeks as her salary comes in.

Without this product, Mwende would have taken a bank loan or Fuliza to cover the shortfall. With it, she handles it through the school at zero interest.

**Channel preference:** App. She's digitally comfortable and would prefer to manage everything through the interface.

**What matters to her:** Speed and discretion. She doesn't want anyone at the school to know she's struggling this term. The app-based flow means no phone calls, no visits to the bursar, no visible change from the school's perspective. The fees just get paid.

---

## School Persona

### Mr. Kamau, the Bursar

**Profile:** School bursar at a 400-student private primary school in Githurai. Uses Zeraki Finance daily for receipting, tracking fee balances, and sending SMS reminders. Has been the bursar for 5 years and knows most parents by name.

**Current reality:**
- Spends the first 2-3 weeks of every term chasing fees
- Manages 50-80 individual verbal arrangements per term, tracked in a notebook
- Sends children home on the headteacher's instruction, which he personally dislikes
- His phone rings constantly in Week 1 with parents calling to negotiate
- Ends each term with 5-15% of fees uncollected

**How he interacts with the product:**

**Layer 1 (Plans):**
- Configures 2-3 plan templates at the start of term (weekly, fortnightly)
- Reviews and approves plan requests from the app and SMS queue
- Uses Path C to record arrangements made in person (replacing his notebook)
- Checks the adherence dashboard daily during the first month, weekly after that
- Follows up only with parents who are behind on their plans or have no plan at all

**Layer 2 (Credit):**
- Reviews the list of eligible parents and enables credit offers
- Sets school-level limits (e.g., maximum 30 active credit arrangements, KES 3,000 cap)
- Monitors repayment progress on the dashboard
- Escalates overdue cases to the headteacher only when automated reminders haven't worked

**What changes for him:**
- Week 1 phone calls drop because parents can request plans through the app or SMS instead of calling him
- His notebook is replaced by a dashboard he can check on his phone
- He can tell the headteacher exactly how much money is expected and when, instead of guessing
- He spends his time on the 20% of parents who need attention, not on the 80% who are on track

**What matters to him:** Reducing his workload and having data to back his decisions. When the headteacher asks "how much will we collect this month?" he wants to pull up a dashboard, not flip through a notebook.

---

## Persona Priority

| Persona | Layer 1 priority | Layer 2 priority | Notes |
|---------|:---:|:---:|-------|
| Otieno (Instalment Payer) | **P1** | P2 | Core Layer 1 user. The product is designed for his situation. |
| Mr. Kamau (Bursar) | **P1** | **P1** | Must see value in both layers or the school won't adopt. |
| Mama Amani (Struggling Payer) | **P1** | P3 | Needs Layer 1 most, but may not qualify for Layer 2 initially. Layer 1 builds her path to Layer 2. |
| Wanjiku (Consistent Payer) | P2 | **P1** | Uses Layer 1 occasionally. Primary Layer 2 user (Path 1). |
| Mwende (Full Payer in Crisis) | P3 | **P1** | Rarely needs Layer 1. Layer 2 Path 1 is designed for her exact situation. |