---
name: opportunity-finder
description: "Systematically find, verify, score, and package grant, fellowship, award, prize, sponsorship, accelerator, and research-funding opportunities, ending in ranked shortlists and proposal handoff briefs. Designed for AI education, AI governance/alignment/sovereignty, open-source, workforce-development, civic-tech, and public-interest technology initiatives, but works for any nonprofit, researcher, or founder. Use when the user asks to find grants, fellowships, funders, or funding for a project ('find me grants for X', 'what fellowships could fund this', 'quick grants we can apply to this week'), wants a funding landscape map, or needs a proposal handoff brief for a known opportunity. Markdown-only: no scripts, no OS assumptions, no paid software required."
---

# Opportunity Finder — Grants, Fellowships, Awards & Research Funding

Help a researcher or grant strategist find relevant funding fast, filter it against an ideal grant profile and beneficiary profile, prioritize by fit, urgency, effort, and probability, and hand the top opportunities to a proposal-writing workflow as structured briefs. Optimize for speed and usefulness, not exhaustive research.

## When to use / not use

**Use for:** fast grant searches, strategic funding landscapes, rapid-application pipelines, fellowship searches, profile-based filtering, and proposal handoffs.

**Do not use when:** the user already has one grant and only needs proposal writing (hand off instead); needs legal, tax, or audited-financial advice; wants guaranteed eligibility; or asks for fabricated funding sources.

## Non-negotiable behavior rules

- Prefer **primary sources**; link every opportunity.
- **Never fabricate deadlines** and never hardcode stale ones — verify every deadline from the funder's own page and record the check date.
- Never assume eligibility if unclear; mark unknowns rather than guessing.
- Separate verified facts from strategic interpretation, using this ladder: *Verified from primary source / Verified from secondary source / Unverified / Stale — needs checking / Not enough information*.
- Translate the user's project into funder language; avoid overfitting to buzzwords.
- Always end with the next best action.

## Inputs to collect (or infer, stating assumptions)

Applicant name and type · tax status · fiscal sponsor status · geography · project name, description, and stage · funding need and minimum useful grant size · maximum application effort · deadline window · topic areas · target beneficiaries · existing partners and past funders · budget/proposal materials on hand · exclusions · whether government grants, individual fellowships, prizes, sponsorships, and international opportunities are acceptable.

**Defaults when information is missing:** prioritize easier applications, recurring opportunities, primary-source application pages, and funders explicitly supporting education/research/public-interest/AI-safety/workforce/open-source work; prefer LOIs, rolling windows, and short forms; deprioritize complex registrations and audited-financial requirements unless the user says they're ready.

## Workflow

1. **Clarify the funding thesis** — define the project in funder language (e.g., AI literacy and workforce development, public-interest AI education, AI governance training, AI sovereignty and local capacity, responsible AI implementation, open-source AI tooling, community-based AI learning).
2. **Build the Ideal Grant Profile** (template below).
3. **Build the Ideal Beneficiary Profile** (template below).
4. **Generate search themes** from the thesis — combine topic × beneficiary × geography × applicant type × funding type. Query patterns: `"[topic]" grant "[geography]"` · `"[topic]" fellowship application` · `"[topic]" request for proposals` · `"[beneficiary]" workforce development grant` · `"[topic]" AI governance funding`.
5. **Search across source categories** (below).
6. **Verify each opportunity from primary sources:** status, deadline, eligibility, geography, amount, topic fit, process, required documents, reporting burden, whether recurring.
7. **Create an opportunity card per finalist** (template below).
8. **Score and rank** with the fit rubric (below).
9. **Produce the requested report:** quick-apply shortlist, full landscape, fellowship shortlist, funder map, proposal pipeline, 30-day plan, or 90-day strategy — always including an Apply First / Monitor / Reject split and a rejection log with reasons.
10. **Produce proposal handoff briefs** for top-ranked opportunities (template below).

## Source categories to search

- **Government:** Grants.gov, SAM.gov, NSF, NIH, Dept. of Education, Dept. of Labor, Commerce/NIST/NTIA, IMLS, NEH, NEA, SBA, state workforce/humanities/arts agencies, digital equity offices.
- **Foundations & philanthropy:** Candid/Foundation Directory, Instrumentl, GrantForward, GrantStation, Philanthropy News Digest, Inside Philanthropy, community foundations, donor-advised funds, corporate foundations.
- **Fellowships:** ProFellow, Opportunity Desk, university fellowship offices, public-interest tech fellowship lists, AI safety/governance fellowship lists, policy fellowship directories.
- **AI safety / governance / public-interest tech:** AI safety funders, AI governance centers, responsible-tech funders, digital democracy funders, university AI centers, think tanks.
- **Open source:** Open Collective, GitHub Sponsors, Sovereign Tech Fund, NLnet, Mozilla and Linux Foundation programs, research software funds.
- **Corporate & ecosystem:** cloud credits, startup programs, developer grants, AI platform credits, social-impact sponsorships.
- **Prizes & challenges:** Challenge.gov, XPRIZE, MIT Solve, HeroX, Devpost, civic innovation portals.

Never claim any specific opportunity is currently open unless verified from a current primary source during this session.

## Templates

### Ideal Grant Profile

```markdown
## Applicant
- Name / type / tax status / fiscal sponsor available / geography / years operating / existing funders & partners
## Project
- Name / one-sentence description / stage / amount needed / minimum useful size / use of funds / timeline / existing materials
## Topic fit (rate 1–5 each)
- AI education · AI literacy · curriculum development · workforce development · AI governance · AI alignment · AI safety · AI sovereignty · open-source AI · civic tech · public-sector innovation · digital equity · research · community building
## Eligibility preferences
- Nonprofit-only OK? · individual fellowships OK? · for-profit OK? · fiscal sponsor required? · government OK? · international OK? · sponsorships OK? · prizes OK?
## Application preferences
- Max time to apply · deadline window · rolling/LOI/short-form preferred · budget & letters available · audited financials available
## Exclusions
- Funders / geographies / topics / application types / ethical restrictions
```

### Ideal Beneficiary Profile

```markdown
- Primary & secondary beneficiaries · sector · geography · community type · skill level · technology maturity
- Pain points: what problem, why now, what fails without it, what's missing
- Desired outcomes: learning / workforce / research / governance / community / economic / public benefit
- Equity & access: underserved groups, access barriers, affordability, digital access
- Funder-relevant framing: why a funder cares, public good created, evidence of need, scalability, urgency
```

### Opportunity Card

```markdown
# [Opportunity] — [Funder]
- Type/category · link · status · deadline (verified [date]) · recurring? · amount · duration
- Eligibility: applicant types · geography · tax status · individuals allowed? · fiscal sponsor allowed? · restrictions
- Funder priorities: what they say they fund · target demographic · language to mirror
- Fit: curriculum ☐ · AI education ☐ · governance/alignment/sovereignty ☐ · workforce ☐ · public-interest tech ☐ · open source ☐
- Application: format · required documents · estimated time to apply · complexity · registrations · reporting burden · match required?
- Scores: mission fit · eligibility · beneficiary · topic · size · speed · probability · strategic value → overall
- Recommendation: apply now / monitor / relationship-build / reject · positioning · risks · missing info · next action
```

### Ranked opportunity table

```markdown
| Rank | Opportunity | Funder | Type | Status | Deadline | Amount | Eligible | Fit Score | Speed | Strategic | Next Step | Link |
|---|---|---|---|---|---|---|---|---:|---:|---:|---|---|
```

### Proposal Handoff Brief

```markdown
# Proposal Handoff Brief
## Opportunity summary — opportunity, funder, program, deadline, link, amount, applicant, apply/no-apply decision
## Strategic recommendation — recommended title, framing, best-fit thesis, why this funder, why this applicant, why now
## Funder priorities — stated priorities, target demographic, review criteria, keywords to mirror, phrases to avoid, evidence expected
## Project alignment — relevant work, components, beneficiaries, outcomes, partners, prior proof
## Narrative direction — problem, solution, activities, outputs, outcomes, evaluation, sustainability, equity framing, AI-responsibility framing
## Budget direction — recommended request, eligible costs, costs to avoid, match requirement, indirect notes
## Required materials — narrative, budget, work plan, letters, org documents, registrations
## Risks and gaps — eligibility concerns, missing documents, weaknesses, deadline risk
## Drafting instructions — mirror the funder's language; emphasize strongest fit; do not invent facts, partners, outcomes, or financials; mark assumptions and placeholders clearly
```

## Scoring rubrics

**Fit score (100 points):** mission fit 20 · eligibility fit 15 · topic fit 15 · beneficiary fit 10 · funding size fit 10 · speed to apply 10 · probability of success 10 · strategic value 10.
Interpretation: 90–100 apply immediately · 75–89 apply if capacity · 60–74 needs tailoring or a partner · 40–59 monitor/relationship-build · <40 reject for now.

**Speed-to-apply levels:** L1 same day (simple form, rolling) · L2 1–3 days (short proposal + basic budget) · L3 1 week (full narrative, budget, work plan) · L4 2–4 weeks (partner letters, evaluation plan, registrations) · L5 1–3 months (major federal/institutional, complex compliance).

**AI sovereignty/alignment fit (0–5 each, max 50):** explicit AI governance language · explicit safety/alignment language · public-interest tech · democratic tech governance · community control of technology · digital sovereignty/DPI · responsible innovation · open-source infrastructure · research/evaluation/policy · AI education/capacity building. 40–50 direct fit · 30–39 strong adjacent · 20–29 narrative fit · below 20 weak.

**Curriculum fit (0–5 each, max 50):** explicitly funds curriculum · education programs · workforce development · adult learning · professional training · facilitator training · digital learning · OER · community learning · learning-outcome evaluation. Same interpretation bands.

## Operational checklist (tell the user)

1. Fill out the Ideal Grant Profile → 2. Fill out the Beneficiary Profile → 3. Run the search → 4. Verify primary sources → 5. Score and rank → 6. Build the quick-apply shortlist → 7. Create handoff briefs for the top opportunities → 8. Pass briefs to the proposal-writing workflow (pairs with the `rfp-proposal-responder` skill).
