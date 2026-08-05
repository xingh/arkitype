create a new skill from this document 


ProposalWriter.md 

---

name: "rfp-proposal-responder"

description: "End-to-end RFP/solicitation response workflow: read every solicitation document and amendment, extract the scoring rubric, produce a one-page outline & compliance checklist, then generate a complete draft proposal in the government's mandated structure with firm-specific data flagged as REQUIRED placeholders, plus cost/timeline estimation. Covers three tracks: state & local law enforcement / public safety (CJIS, NIBRS, MBE/MFD goals, bonds), federal defense & intelligence (FAR/DFARS, Sections L & M, CMMC, clearances), and small business & nonprofit (grants, foundations, simplified procurements). Use whenever the user mentions an RFP, RFI, RFQ, solicitation, bid, proposal response, statement of work response, compliance matrix, evaluation criteria, amendment analysis, or asks 'can we bid this' / 'what would it take to win this' — even if they only upload solicitation PDFs without asking a question yet."

---

# RFP Proposal Responder

**Tier:** POWERFUL

**Category:** Business Growth

**Domain:** Government Procurement, Capture Management, Proposal Writing

---

## Overview

A repeatable pipeline that turns a pile of solicitation PDFs into three deliverables:

1. **One-page Outline & Checklist** — printable synthesis of the rubric, mandated proposal structure, deadlines, and disqualification traps

2. **Complete Draft Proposal** — full document in the government's exact mandated section order, with everything derivable from the solicitation written in final prose and firm-specific data flagged in red as `[REQUIRED]` placeholders

3. **Cost & Timeline Estimate** — bottoms-up range using solicitation signals (bond size, thresholds, user counts, term length) plus market comparables

**Not a substitute for capture strategy or legal review.** Drafts are strong starting points; price-to-win and teaming decisions stay human.

---

## Core Principles (apply to every track)

1. **The rubric is the outline.** Structure every response around the evaluators' scoresheet, in their order, using their labels and numbering. Never invent a structure.

2. **Amendments override everything.** Read every amendment before drafting. Amendments routinely reverse cover-page errors, change subcontracting goals, relocate attachments, and confirm/deny extensions. Build an "Amendment Corrections" list first.

3. **Placeholders, never fabrication.** Anything firm-specific (names, references, personnel, certifications, past performance, prices) becomes a visibly-flagged `[REQUIRED]` placeholder. Never invent references, credentials, or numbers.

4. **Compliance before eloquence.** A beautiful proposal that misses a mandatory form is rejected unread. Extract every pass/fail item into a checklist before writing a single narrative sentence.

5. **Answer the mandatory affirmations verbatim.** When a solicitation says "the Offeror must specifically state X," write a sentence that specifically states X, bolded, citing the section number.

6. **Price hours, protect rates.** Where labor rates get locked into the contract (task-order vehicles), competitiveness comes from reducing estimated *hours* per deliverable — never from cutting rates that will govern years of future work.

---

## Workflow (repeatable, all tracks)

### Phase 1 — Ingest & Inventory

1. List every provided file. Identify: base solicitation, amendments, attachments/exhibits, Q&A documents.

2. Read documents in this order: **amendments first** (they change everything downstream), then evaluation/award sections, then submission instructions, then scope/SOW, then attachments.

3. If PDFs are scanned images, note it and OCR or ask for text versions. If a referenced attachment is missing, flag it — sometimes it's embedded inside another document (check page footers like "L1", "K1").

4. Build the **Solicitation Fact Sheet** (template below).

### Phase 2 — Rubric & Compliance Extraction

1. Extract the full scoring table: criteria, points/weights, and which proposal section feeds each criterion.

2. Extract the **mandated proposal structure** (numbered submission items) — this becomes your table of contents verbatim.

3. Extract every pass/fail gate: registrations, forms, signatures, bonds, certifications, page limits, font/format rules, submission portal, deadline.

4. Produce **Deliverable 1: one-page Outline & Checklist** (print-optimized; two columns: rubric+structure on the left, flags+compliance on the right).

### Phase 3 — Draft Generation

1. Write the full proposal in the mandated structure. For each section:

   - Write final prose for everything derivable from the solicitation (affirmations, responsibility matrices, SOW methodology per deliverable, SLA tables, schedules, security plans, compliance summaries).

   - Insert `[REQUIRED — description of what's needed]` for firm data, styled red/bold.

   - Add a REQUIRED callout box wherever a government form must be downloaded, signed, and inserted (never recreate official forms — reference them).

2. Include: cover page, TOC, compliance affirmations in the cover letter, amendment acknowledgment table, and a pre-award readiness appendix.

3. Output as Markdown. Offer docx conversion (see Tooling).

### Phase 4 — Cost & Timeline

1. Mine the solicitation for price signals: bond amounts, "high dollar" thresholds, user counts, term length, labor category tables, mandatory SLAs.

2. Build a component table (one-time vs. recurring) with low/high ranges from market comparables for the system class.

3. State the evaluated-price sweet spot and what fixed costs (bonds, insurance, escrow) must be absorbed into pricing.

4. If AI-assisted delivery (e.g., Claude Code) is assumed: apply savings only to code-heavy services (interfaces, ETL, test automation, documentation), never to COTS subscriptions; note that calendar compression is limited by government-paced activities (workshops, UAT, training).

### Phase 5 — Review Gates (adapt color-team language to audience)

- **Compliance pass:** every checklist item mapped to a page number.

- **Rubric pass:** score the draft against the extracted rubric as an evaluator would.

- **Red-flag pass:** unsupported claims, invented facts, missed affirmations, stale amendment status ("check for Amendment N+1 before submitting").

---

## Templates

### T1 — Solicitation Fact Sheet

```markdown

| Field | Value |

|---|---|

| Solicitation # / Title | |

| Issuing agency / office | |

| Submission portal & format | |

| Due date/time (+ questions deadline, pre-proposal conf.) | |

| Contract type & term (base + options) | |

| Evaluation method (LPTA / best value / tradeoff) | |

| Set-asides / preferences / subcontracting goals | |

| Bonds / insurance / registrations required | |

| Amendments issued & key corrections | |

| Estimated value signals | |

| Government POCs | |

```

### T2 — Compliance Matrix

```markdown

| # | Requirement (verbatim cite) | Source § | Proposal Section | Status | Notes |

|---|---|---|---|---|---|

| 1 | | | | ☐ | |

```

One row per "shall/must/will" statement and per required form. Status: Compliant / Partial / Exception / Placeholder.

### T3 — Proposal Section Skeleton

```markdown

# Section [N] — [Government's exact label] (§[cite])

[Final prose for all solicitation-derivable content]

**[REQUIRED — firm-specific item, what to insert, where it comes from]**

> ⚑ REQUIRED FORM: download, complete, sign [FORM ID] and insert behind this page.

```

### T4 — Cost Model Shell

```markdown

| Component | Basis | Low | High | Notes |

|---|---|---|---|---|

| One-time implementation | hours × loaded rate | | | |

| Recurring subscription/O&M | per user/yr × users × yrs | | | |

| Interfaces / integrations | per interface | | | |

| Data conversion | per source system | | | |

| Bonds, insurance, escrow | absorbed into price | | | |

| **Total (full term incl. options)** | | | | |

```

### T5 — Executive Summary / Win Themes

```markdown

- Understanding: restate the buyer's mission problem in their vocabulary (from Background section)

- Solution fit: map 3–5 discriminators to the highest-point rubric criteria

- Risk reduction: comparable deployments, certifications, key personnel

- Value: pricing philosophy tied to the evaluation method

```

---

## Track A — State & Local Law Enforcement / Public Safety

**Typical vehicles:** county/city RFPs on BidNet Direct, Periscope/mdBUY, state eProcurement portals; cooperative riders (rider clauses extending pricing to other jurisdictions).

**Recurring requirements to hunt for:**

- **CJIS Security Policy** (cite current version + date), FBI/state audits, fingerprinting, security awareness training, NDAs

- **NIBRS/state UCR** reporting with error-rate ceilings; state-specific report types (DV, hate/bias)

- SaaS responsibility affirmations; data ownership, e-discovery notification, destruction-on-exit; **source code escrow**

- **Performance bonds** (often $1M–$5M), state SDAT/Secretary-of-State good standing, vendor registration systems

- **MBE/MFD/DBE subcontracting goals** — note whether points require *meeting* or *exceeding* the goal; plans often due WITH the proposal

- **Local business preference** — check amendments; cover pages are often wrong

- Prevailing/living wage laws; labor-category tables with locked rates governing future task orders

- Interfaces to the regional ecosystem: CAD, JMS, courts, prosecutors, AFIS, evidence, BWC platforms, state message switches (NCIC/state equivalents)

**Scoring pattern:** written phase (~1000 pts) + shortlist interview/demo phase (~1000 pts) with scripted scenarios; cost typically 15–25% of total.

**Resources:** FBI CJIS Security Policy (le.fbi.gov file repository) · FBI UCR/NIBRS technical specs · state procurement portal + vendor registration · IJIS Institute standards (NIEM) · agency annual reports (sizing data for the cover letter).

---

## Track B — Federal Defense & Intelligence

**Typical vehicles:** SAM.gov solicitations, GSA/GWACs, IDIQs, OTAs; classified annexes distributed separately.

**Recurring requirements to hunt for:**

- **Section L** (instructions) and **Section M** (evaluation factors) — L is your structure, M is your rubric; volumes (Technical / Management / Past Performance / Cost) with hard **page limits, font, and margin rules** (violations = pages discarded)

- **FAR/DFARS clauses** incorporated by reference — flag flow-downs affecting price: DFARS 252.204-7012 (safeguarding CUI), **CMMC level**, NIST SP 800-171 self-assessment score in SPRS

- **SAM.gov registration** (active, with correct NAICS/size), UEI, reps & certs; **facility clearance (FCL)** and personnel clearances; ITAR/EAR registration where applicable

- **Organizational Conflict of Interest (OCI)** representations; TAA/Buy American; Section 508 accessibility

- **Past performance:** CPARS references with contract numbers, values, POCs — relevancy defined in M

- Cost volume realism/reasonableness; certified cost or pricing data thresholds; DCAA-adequate accounting for cost-type work

- Small-business subcontracting plan (if large business) per FAR 19.7

**Scoring pattern:** adjectival ratings (Outstanding→Unacceptable) with tradeoff language; strengths/weaknesses/deficiencies vocabulary — write so an evaluator can quote "strengths" verbatim.

**Resources:** SAM.gov · acquisition.gov (FAR/DFARS full text) · SPRS (sprs.csd.disa.mil) · CMMC (dodcio.defense.gov/cmmc) · CPARS · agency forecast sites & SBIR/STIR portals · FPDS/USASpending for incumbent pricing intel.

---

## Track C — Small Business & Nonprofits

**Typical vehicles:** foundation RFPs, grants.gov federal grants, state/local mini-bids and simplified procurements, fiscal-sponsor pass-throughs.

**Recurring requirements to hunt for:**

- **Eligibility gates first:** 501(c)(3) determination letter, years of audited financials, geographic/mission fit, budget-size bands — disqualify yourself early or don't bid

- **Budget + budget narrative** as a scored volume: personnel with FTE %, fringe, **indirect rate** (negotiated NICRA vs. 10% de minimis), match/cost-share requirements

- **Logic model / theory of change**, SMART outcomes, evaluation plan with named metrics

- Letters of support/commitment (start collecting day one — longest lead item)

- Grants.gov mechanics: SAM/UEI registration (takes weeks — verify immediately), Workspace forms (SF-424 family), attachment naming rules

- Reporting burden and allowable-cost rules (2 CFR 200 for federal)

**Scoring pattern:** rubrics are shorter and mission-weighted; reviewers are often non-specialists — write plainly, front-load outcomes, avoid jargon.

**Resources:** grants.gov + Grants Learning Center · 2 CFR 200 (eCFR) · Candid/Foundation Directory · funder's prior awardee lists (990s show grant sizes) · state single points of contact for grant review.

---

## Tooling (optional — suggest, never require)

This skill is fully functional with Markdown output alone. When the user wants polished deliverables, suggest installing:

| Need | Tool | Install |

|---|---|---|

| Markdown → Word | pandoc | `brew install pandoc` / `apt install pandoc` → `pandoc proposal.md -o proposal.docx --reference-doc=firm-template.docx` |

| Native .docx generation (styled tables, TOC, red placeholders) | docx (npm) | `npm install docx` |

| One-page printable checklist | plain HTML + `@page` CSS | none — any browser prints it |

| Scanned-PDF text extraction | pdfplumber / tesseract | `pip install pdfplumber` · `apt install tesseract-ocr` |

| Render/verify docx | LibreOffice + poppler | `apt install libreoffice poppler-utils` |

If none are available, deliver Markdown with an instruction block showing the pandoc command for later conversion.

---

## Common Pitfalls

1. **Trusting the cover page over amendments** — preference programs, goals, and attachment locations get corrected in Q&A amendments; the corrected value governs.

2. **Recreating official forms** — governments require *their* form with *their* signature block; always insert the real form, never a lookalike.

3. **Missing the "submit WITH proposal" trap** — some plans/certifications (subcontracting plans, security plans) are due at submission, not award; late = rejected.

4. **Inventing past performance or references** — placeholders only; fabrication is disqualifying and sometimes actionable.

5. **Page-limit violations (federal)** — excess pages are removed before evaluation; the rubric response you buried on page 31 of 30 never gets read.

6. **Rate-cutting on task-order vehicles** — locked rates govern all future work; cut hours, not rates.

7. **Ignoring absorbed costs** — bonds, insurance, escrow, and prevailing-wage deltas must live inside the evaluated price.

8. **Submitting without re-checking the portal** — always verify no new amendment posted between draft and submission; acknowledge every amendment by number and date.

---

## Definition of Done (per engagement)

- ☐ Fact Sheet complete; all documents inventoried and read (amendments first)

- ☐ One-page Outline & Checklist delivered (printable)

- ☐ Compliance Matrix rows all mapped to proposal sections

- ☐ Full draft in mandated structure; every placeholder flagged `[REQUIRED]`

- ☐ Cost & timeline range with stated assumptions

- ☐ Rubric self-score + red-flag list delivered with the draft

