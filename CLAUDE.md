# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Zeraki Savings** is a product case study — not a software application. It explores how Zeraki (Kenya's largest school management platform, operating in 4,000+ schools) could embed a micro-savings and fee financing product for parents, using existing M-Pesa paybill infrastructure and behavioural nudging via SMS.

The core problem: school fees are the single biggest financial stressor for low-income Kenyan families, who currently borrow from shylocks at 20%+ monthly interest each term. Zeraki already has fee tracking, parent communication, and payment data — the infrastructure exists; the product doesn't yet.

## Repo Structure

All content is Markdown documentation organized into five sections:

```
research/       # Problem sizing, competitive landscape, platform audit, regulatory
product/        # PRD, personas, user stories, metrics framework, risks
design/         # SMS nudge flows, parent app UX, school admin dashboard
technical/      # System architecture, data model, M-Pesa/SMS integrations, underwriting model
go-to-market/   # Pilot plan (50-school), school pitch, MFI/SACCO partnership strategy
```

None of these directories or their files exist yet — the repo currently contains only this CLAUDE.md and the README.

## Key Product Decisions (Do Not Contradict Without Good Reason)

| Decision | Choice | Rationale |
| --- | --- | --- |
| Payment mechanism | Existing school paybill + student reg number | Zero behaviour change for parents |
| Primary channel | SMS (not app-first) | Most target parents don't use the Zeraki app |
| Savings model | Pre-payment to school account (not a wallet) | Avoids pooled fund regulation; builds trust |
| Credit model | Fee deferral first (school-funded), MFI top-up second | Deferral needs no lending license |
| Targeting | Parents with 2+ terms of Zeraki Finance payment history | Provides behavioural baseline for segmentation |

## Writing Guidelines

- All documents are research-backed; cite sources and data when making claims about market size, behaviour, or regulatory requirements
- Kenyan context: M-Pesa is the dominant payment rail; CBK regulates lending (deposit-taking requires a licence; fee deferral does not); Kenya's school calendar runs three terms (Jan, May, Sep)
- Target audience is low-income urban and peri-urban Kenyan parents - write personas and UX flows with this in mind
- The SMS channel must work on feature phones (no rich media, short messages, Swahili/English mix)
- When writing technical documents, ground architecture decisions in Zeraki's existing stack (school management + Zeraki Finance) and standard M-Pesa Daraja API patterns
