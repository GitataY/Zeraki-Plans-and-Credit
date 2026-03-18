# Competitive Landscape

## Who Else Is Trying to Solve School Fee Payments in Kenya?

The short answer: almost nobody is solving it the way we're proposing. There are products that touch school fees, but none that combine structured instalment plans with embedded credit inside a school management platform. Here's what exists and where the gaps are.

## Direct Competitors (School Fee Financing)

### Digital Lenders Used for Fees (Tala, Branch, Fuliza)

**What they do:** General-purpose personal loans disbursed to the borrower's M-Pesa. Parents use them for fees, but the products aren't designed for that purpose.

**How parents use them:** Parent takes a KES 5,000 loan from Tala to cover a fee shortfall. Money goes to their M-Pesa. They then pay the school via paybill. They repay Tala over 30 days at 15%+ effective monthly interest.

**Why this isn't what we're building:**
- Money goes to the parent, not the school. It can be diverted to other needs.
- Underwriting is based on phone metadata (app usage, SMS patterns, device data), not school fee payment behaviour.
- No integration with the school. The school doesn't know the parent borrowed, and the lender doesn't know whether the money went to fees.
- Interest rates are high because the lender has no purpose-specific risk data.
- No instalment plan structure. It's a lump-sum loan with a fixed repayment date.

**Relevance:** These are what parents currently use as a last resort. Layer 2 directly competes with this by offering cheaper, purpose-locked credit through the school channel.

### Fuliza (Safaricom/NCBA)

**What it does:** M-Pesa overdraft facility. When a parent's M-Pesa balance is insufficient for a paybill payment, Fuliza can automatically cover the shortfall.

**How parents use it for fees:** Parent tries to pay KES 10,000 to the school paybill but only has KES 7,000 in M-Pesa. Fuliza covers the KES 3,000 gap. The parent is charged a one-time 1% access fee (KES 30) plus a daily maintenance fee on the outstanding balance, ranging from KES 0 to KES 30 per day depending on the amount. The first 3 days are free for balances under KES 1,000, but higher amounts incur daily charges immediately.

**Why this isn't what we're building:**
- Fuliza is automatic and undiscriminating. It doesn't assess whether the parent can sustainably repay.
- Daily maintenance fees add up. A KES 3,000 Fuliza balance at KES 10/day for 30 days costs KES 300 plus the KES 30 access fee, totalling KES 330. Higher balances cost more, up to KES 30/day.
- No relationship to the school or to fee payment history. It's a general M-Pesa feature.
- No instalment structure. The full amount is due and accrues fees daily until cleared.

**Relevance:** Fuliza is the closest thing to "embedded fee credit" that exists today, because it activates at the moment of the paybill payment. But it's expensive, unsupervised, and disconnected from the school's data.

### School Fee Insurance (Britam Elimu Plan, similar products)

**What it does:** Insurance product that pays school fees if the parent dies or becomes permanently disabled. Some variants cover temporary inability to work.

**Why this isn't what we're building:**
- It's an insurance product, not a credit or instalment product.
- Covers catastrophic events (death, disability), not ordinary cash flow gaps.
- Low uptake among low-income families due to premium costs and distrust of insurance.
- Doesn't help a parent who's alive and working but short on cash this term.

**Relevance:** Minimal. Different problem, different product category.

### HELB (Higher Education Loans Board)

**What it does:** Government student loans for university and TVET institutions.

**Why this isn't relevant:** Only covers higher education. Does not apply to primary or secondary school fees, which is our focus.

### County Bursaries and CDF Funds

**What they do:** Government and Constituency Development Fund bursaries that subsidise fees for needy students. Distributed through local government offices.

**Why this isn't what we're building:**
- Heavily oversubscribed. Far more applicants than available funds.
- Bureaucratic and slow. Applications often take weeks, with disbursement delayed beyond when the money is needed.
- One-time or occasional. Not a reliable, recurring solution.
- No connection to school management systems.

**Relevance:** These are a safety net for the most vulnerable families, but they don't solve the cash flow timing problem for the broader parent population.

## Adjacent Competitors (School Management Platforms)

### Other School Management Systems (JibuSMS, ShulepPro, SchoolTool)

**What they do:** Similar to Zeraki. School administration software covering fee management, academic records, timetabling, and communication.

**Do any of them offer instalment plans or credit?** Based on publicly available information, no. They offer fee tracking, receipting, and SMS reminders, similar to Zeraki Finance. None appear to have formalised instalment plan management or embedded lending.

**Why Zeraki has the advantage:** Scale. 4,000+ schools and nearly half of Kenya's high schools gives Zeraki a distribution moat that smaller competitors can't match. Any financial product built on Zeraki reaches more parents on day one than a competitor could reach in years.

### Pezesha

**What they do:** B2B embedded lending infrastructure. Pezesha provides APIs that let platforms offer working capital loans to their merchant ecosystems. Currently integrated with Twiga Foods, Jumia, Marketforce, iPay, and 20+ other partners.

**Do they work with schools?** Not currently, based on public information. Their focus is merchant and MSME lending through supply chain and e-commerce platforms.

**Why they matter:** Pezesha is the most likely credit partner for Layer 2. Their API infrastructure is designed for exactly this use case: a platform (Zeraki) provides behavioural data, Pezesha provides lending infrastructure and capital, and credit is offered within the platform's existing user experience. Zeraki wouldn't need to build lending from scratch or obtain a lending license. Pezesha has CMA regulatory approval and operates in Kenya, Uganda, Ghana, and Nigeria.

**Relevance:** Not a competitor. A potential partner. This is covered in detail in `go-to-market/03-partnership-strategy.md`.

## International Analogues

### School Fee Plan (UK)

A UK company that pays school fees upfront to the school and lets parents repay in monthly instalments. The school gets full payment on Day 1, the parent spreads the cost over the term. Regulated by the Financial Conduct Authority.

**Relevance:** This is conceptually close to our Layer 2, but designed for a completely different market (UK private schools, GBP 5,000+ per term fees). The model of "pay the school upfront, parent repays over time" is sound. The challenge is adapting it for Kenya's low-income context, mobile money infrastructure, and regulatory environment.

### EasyPay Education (India)

Indian company offering school fee financing through EMI (equated monthly instalments). Partners with schools to offer parents structured payment plans.

**Relevance:** Closest international analogue. Operates in a market with similar dynamics: low-income parents, lump-sum fee demands, and a large private school sector. Worth studying their model for lessons on school partnership, default management, and regulatory approach.

## Competitive Summary

| Solution | Instalment plans? | Credit for gap? | School-integrated? | Uses fee payment data? | Affordable? |
|----------|:-:|:-:|:-:|:-:|:-:|
| **Zeraki Plans + Credit (proposed)** | ✅ | ✅ | ✅ | ✅ | ✅ |
| Tala / Branch | ❌ | ✅ (general loan) | ❌ | ❌ | ❌ (15%+/month) |
| Fuliza | ❌ | ✅ (overdraft) | ❌ | ❌ | ❌ (1% fee + daily charges) |
| Britam Elimu | ❌ | ❌ (insurance only) | ❌ | ❌ | N/A |
| County bursaries | ❌ | ✅ (grant) | ❌ | ❌ | ✅ (free) |
| JibuSMS / ShulepPro | ❌ | ❌ | ✅ | ❌ | N/A |
| Pezesha (as partner) | ❌ | ✅ (infrastructure) | Via partner | Via partner | ✅ |

The gap is clear: no one currently offers structured, school-integrated instalment plans backed by fee payment behaviour data, with affordable embedded credit for the shortfall.

## Research Gaps

- [ ] Confirm that JibuSMS, ShulepPro, and other Kenyan school management systems do not offer instalment plan features
- [ ] Research EasyPay Education (India) model in depth for transferable lessons
- [ ] Check whether any Kenyan banks offer school-specific fee financing products (beyond general personal loans)
- [ ] Investigate whether Pezesha has explored the education sector or has any school-related integrations
---

*Note: Competitive analysis is based on publicly available information as of early 2026. Product features and partnerships may have changed since the sources were last reviewed.*