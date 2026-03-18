# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

This is a **product strategy case study** — not a software project. There is no code, no build system, and no tests. All content is Markdown documentation authored by Yvonne Gitata (Product Manager).

The repository documents a product proposal: **Zeraki Plans & Credit** — embedded fee management and parent credit products built on Zeraki Finance, a school accounting SaaS used by 4,000+ Kenyan schools.

## Product Overview

**The problem**: Kenyan schools need cash on Day 1 of term; parents earn irregularly and can't accumulate lump-sum fees by deadline. The informal verbal arrangement system is undignified and unreliable. When parents borrow elsewhere, they pay 15–20%+ monthly interest.

**Two-layer product:**

- **Layer 1 — Zeraki Plans**: Structured fee instalment plans replacing informal verbal negotiations. Parents select a payment schedule; schools get a dashboard replacing 150+ individual arrangements.
- **Layer 2 — Zeraki Credit**: Affordable top-up financing for parents with strong Zeraki payment history or demonstrated plan adherence. Loans disburse directly to the school's M-Pesa paybill (never to the parent's wallet). Underwritten by actual fee payment behaviour from Zeraki Finance — not phone metadata.

**Why Layer 1 enables Layer 2**: Plans generate new behavioural data ("did they stick to a weekly commitment?") that, combined with Zeraki's existing multi-term payment history, powers credit underwriting.

## Repository Structure

```
research/    ← Completed foundational research (5 files)
product/     ← PRDs, personas, stories, metrics, risks (6 files — mostly stubs)
design/      ← User experience flows and dashboard specs (2 files — stubs)
```

The README also describes planned directories (`technical/`, `go-to-market/`) that don't exist yet.

### Research (completed)
| File | Contents |
|------|----------|
| `01-problem-sizing.md` | Market size, fee cost structure, cash-flow mismatch evidence |
| `02-how-fees-actually-work.md` | End-to-end mechanics of how schools collect fees (M-Pesa, receipts, pledges, SMS reminders) |
| `03-zeraki-platform-audit.md` | What Zeraki Finance currently does and its gaps relevant to this product |
| `04-competitive-landscape.md` | Tala, Fuliza, SMS lenders — why existing credit products fail this use case |
| `05-regulatory-landscape.md` | CBK licensing requirements, CRB reporting, data protection (PDPA), consumer protection |

### Product & Design (stubs awaiting content)
The `product/` and `design/` files were created but are largely empty — these are the next documents to write.

## Key Context for Writing

- **Tone**: Direct, evidence-based, unsentimental. The README sets the voice: "Built with research, not assumptions."
- **The first assumption killed**: Parents don't forget fees. It's an income timing problem, not a behaviour problem. Avoid framing parents as irresponsible.
- **Credit design constraint**: Money must flow to the school paybill, not the parent's M-Pesa — this prevents misuse and is a regulatory/trust consideration.
- **Distribution advantage**: Zeraki already has school relationships. Both products ride existing distribution; no new school acquisition needed.
- **Regulatory context**: Kenya — CBK oversight for credit (Digital Credit Provider license), CRB reporting obligations, PDPA data protection. See `research/05-regulatory-landscape.md` for detail.
- **Target lending partner**: Pezesha mentioned as a potential fintech infrastructure provider for Layer 2.
