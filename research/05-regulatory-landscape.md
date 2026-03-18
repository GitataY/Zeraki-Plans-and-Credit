# Regulatory Landscape

## Overview

The product has two layers with different regulatory profiles. Layer 1 (instalment plans) is a school administration feature with minimal regulatory exposure. Layer 2 (credit top-ups) touches lending, data sharing, and consumer protection, which brings it into regulated territory.

This document maps the key regulatory questions and the likely answers based on publicly available Kenyan law and precedent.

## Layer 1: Zeraki Plans (Instalment Arrangements)

### Is a structured instalment plan between a school and a parent a regulated financial product?

**Likely no.** A school allowing a parent to pay fees in four weekly chunks is a commercial arrangement between a service provider (school) and a customer (parent). Schools have been doing this informally for decades. Formalising it through software doesn't change its legal character.

This is similar to a landlord allowing a tenant to pay rent in two instalments, or a hospital letting a patient pay a bill over several visits. These are standard business arrangements, not regulated credit products.

**Key distinction:** No interest is charged. No fees are added. The parent simply pays the same total amount over a longer period. If Zeraki or the school were to charge interest or a service fee on the instalment arrangement, it could be reclassified as a credit product, which would change the regulatory picture entirely.

**Recommendation:** Keep Layer 1 interest-free and fee-free. It's a school administration tool, not a financial product. This keeps it outside the scope of CBK and CMA oversight.

### Does Zeraki need any license to facilitate instalment plans?

**Likely no.** Zeraki is providing software that helps schools manage their existing fee collection process. It's not originating credit, holding funds, or processing payments (the school's M-Pesa paybill handles payments). Zeraki's role is tracking and communication.

**Analogy:** A restaurant using a reservation system that allows split billing doesn't make the software provider a payment processor. Zeraki is the system, not the financial counterparty.

### Data protection (DPA 2019)

The Data Protection Act 2019 applies to any processing of personal data. Zeraki already processes student and parent data for academic and fee purposes. Adding instalment plan tracking doesn't introduce a new category of data processing, but there are considerations:

- **Consent:** Parents should be informed that their fee payment patterns may be tracked and used to offer them payment plan options. This can be included in the school's existing Zeraki registration/consent process.
- **Purpose limitation:** Data collected for instalment tracking should only be used for that purpose (and for Layer 2 credit scoring, with separate consent).
- **Data minimisation:** Only collect and store what's needed. Payment dates, amounts, and plan adherence. Not unrelated personal information.

**Recommendation:** Update Zeraki's existing privacy policy and school-level consent forms to cover instalment plan tracking. This is a routine update, not a major compliance project.

## Layer 2: Zeraki Credit (Fee Top-Ups)

This is where regulatory complexity increases. The key questions depend on how the credit product is structured.

### Option A: School-funded deferral (school bears the risk)

The school agrees to let the parent start term with, say, 70% of fees paid and complete the balance over 4 weeks. Zeraki facilitates the arrangement and tracks repayment. No external lender is involved.

**Regulatory exposure: Low.**

This is still a commercial arrangement between the school and the parent. The school is not a lender. It's a service provider offering flexible payment terms for its own service. No interest is charged. No CBK license is required.

**Zeraki's role:** Software facilitator. Zeraki tracks the arrangement, sends reminders, and reports to the bursar. It does not originate credit, disburse funds, or bear risk.

**Risk:** If the arrangement is marketed as a "loan" or if Zeraki charges a fee for facilitating it, regulators could take a different view. Language matters.

**Recommendation:** Never call it a loan. Frame it as a "fee payment plan" or "flexible payment arrangement." Zeraki charges the school for the software feature (part of the Zeraki Finance subscription), not the parent for the credit.

### Option B: Third-party lender (Pezesha, SACCO, or MFI provides capital)

An external lender provides the top-up amount. The lender pays the school directly via the school's paybill. The parent repays the lender over time.

**Regulatory exposure: Medium to High (but for the lender, not for Zeraki).**

The lender needs to be properly licensed:
- **Digital Credit Provider (DCP):** CBK's Digital Credit Providers Regulations 2022 require any entity offering digital credit to be licensed. Pezesha has CMA regulatory approval (they exited the CMA regulatory sandbox as the first Kenyan company to do so). A SACCO would operate under SASRA. An MFI would operate under the Microfinance Act.
- **Interest rate disclosure:** CBK requires transparent disclosure of total cost of credit. Any fees, interest, or charges must be clearly communicated to the parent before they accept.
- **Responsible lending:** The lender must assess the borrower's ability to repay. Zeraki's fee payment data would support this assessment, but the lender makes the credit decision, not Zeraki.

**Zeraki's role under Option B:**

This is the critical regulatory question. Zeraki could be classified in several ways:

| Classification | What it means | License needed? |
|---------------|--------------|-----------------|
| **Software provider** | Zeraki provides the platform, the lender does everything else | No |
| **Credit information provider** | Zeraki shares parent payment data with the lender for credit decisions | Possibly (CRB regulations may apply) |
| **Loan origination agent** | Zeraki presents the credit offer to the parent on behalf of the lender | Depends on arrangement with lender |
| **Payment facilitator** | Zeraki processes the disbursement or repayment | Possibly (depends on money movement) |

**Recommendation for Option B:**
- Zeraki positions itself as a **data and distribution partner**, not a lender or credit provider.
- The lender (Pezesha, SACCO, MFI) holds the license, makes the credit decision, bears the risk, and handles regulatory compliance.
- Zeraki provides: (1) the behavioural data that supports underwriting, (2) the communication channel to present offers to parents, and (3) the dashboard for schools to track arrangements.
- Money flows from the lender to the school's paybill directly. Zeraki does not touch funds.
- A formal data sharing agreement governs what data Zeraki shares with the lender, under what consent, and for what purpose.

### Data sharing and consent (DPA 2019)

Sharing parent fee payment data with an external lender requires explicit, informed consent from the parent. This is non-negotiable under the Data Protection Act.

**What consent must cover:**
- What data is being shared (fee payment history, amounts, dates, plan adherence)
- Who it's being shared with (named lender)
- Why (to assess eligibility for a fee top-up)
- How long the data will be retained
- The parent's right to withdraw consent

**How to capture consent:**
- For app users: consent screen within the Zeraki parent app before any credit offer is shown
- For SMS users: a clear SMS explaining the data sharing and requiring a reply (e.g., "Reply YES to allow [Lender] to view your fee payment history for a payment plan offer")

**Recommendation:** Design consent capture as part of the credit offer flow, not as a separate step. The parent sees the offer and the consent request together. If they decline consent, no data is shared, and they simply don't get the credit offer. No penalty, no reduced access to other Zeraki features.

### CBK Digital Credit Providers Regulations 2022

Key provisions relevant to Layer 2:

- **Licensing:** Any entity offering digital credit must be licensed by CBK. This applies to the lender, not to Zeraki (if structured correctly).
- **Cost of credit disclosure:** Total cost must be disclosed before the borrower accepts. Includes interest, fees, and any other charges.
- **Cooling-off period:** Borrowers must have a period to reconsider after accepting a digital loan.
- **Debt collection practices:** Restrictions on aggressive collection. No harassment, no contacting the borrower's employer (though in this case the school already knows about the arrangement).
- **CRB reporting:** Digital credit providers must report to Credit Reference Bureaus. This means a fee top-up loan would appear on the parent's credit record, which could be positive (builds credit history) or negative (if they default).

### Consumer protection considerations

- Fee top-up offers must never be coercive. A parent who declines must face no consequences from Zeraki or the school.
- Interest rates and total cost must be clearly stated in simple language, in the parent's preferred language (English or Kiswahili).
- The product must not create a debt trap. Maximum loan amounts and eligibility criteria should prevent parents from taking on more than they can repay.
- Children must never be penalised based on their parent's engagement with the credit product. A parent who declines a loan offer or defaults on a top-up must not have their child treated differently from other students.

## Regulatory Strategy Summary

| Layer | Regulatory risk | Key requirement | Recommended approach |
|-------|----------------|-----------------|---------------------|
| Layer 1 (Plans) | Low | DPA 2019 consent for data processing | Update existing privacy policy; keep instalment plans interest-free |
| Layer 2, Option A (School deferral) | Low | Avoid "loan" language; no interest or fees | Frame as flexible payment arrangement; Zeraki is the software tool |
| Layer 2, Option B (Third-party lender) | Medium | Lender holds DCP/MFI/SACCO license; DPA consent for data sharing | Zeraki is data and distribution partner; lender handles compliance |

## Recommended Sequencing

1. **Launch Layer 1 first.** Minimal regulatory overhead. Establishes the instalment plan infrastructure and generates behavioural data.
2. **Pilot Layer 2, Option A (school-funded deferrals) next.** Still low regulatory risk. Tests the credit concept without involving external lenders or licenses.
3. **Introduce Layer 2, Option B (third-party lender) last.** Requires partnership agreements, data sharing consent flows, and regulatory alignment with the chosen lender. Start conversations with Pezesha early, but don't launch until Layers 1 and 2A are proven.

## Open Questions

- [ ] Consult a Kenyan fintech lawyer on whether Zeraki's role in Layer 2 could be classified as "credit information provision" under CRB regulations
- [ ] Review CBK's DCP regulations in detail for any provisions that could apply to the platform (Zeraki) rather than the lender
- [ ] Confirm whether Pezesha's CMA approval covers the education sector or if additional authorisation would be needed
- [ ] Check SASRA requirements if the lending partner is a SACCO rather than an MFI or DCP
- [ ] Research whether the Basic Education Act has any provisions on sending children home for fees that could be relevant to how Layer 1 is positioned

---

*Note: This is a preliminary regulatory analysis based on publicly available Kenyan law and regulations. It is not legal advice. A qualified Kenyan fintech lawyer should review the product structure before launch, particularly for Layer 2.*