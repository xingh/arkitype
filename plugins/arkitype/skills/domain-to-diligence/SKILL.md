---
name: domain-to-diligence
description: "Analyze a company from only its domain name and produce an investment-grade diligence memo with scores. Runs 10 phases of public-signal research (infrastructure, website, tech stack, people, financials, market, reputation, risk, tech-gap, synthesis), scores 8 weighted dimensions, and ends in a PE-style verdict (Platform / Bolt-on / Growth Partnership / Services / Turnaround / Pass). Use when given a domain or website and asked to evaluate, screen, research, or diligence a company, or to find its technology gaps and uplift opportunities."
---

# Domain-to-Diligence

Take a single domain name and produce an investment-grade company breakdown: 10 research phases → 8 weighted dimensions → a composite 0–100 score → a PE-style verdict. The core thesis for a technology-focused firm is the **sweet spot**: LOW digital/tech maturity + HIGH business fundamentals = the highest-value target, because broken tech on top of a good business is the cheapest, fastest value to add.

## Confidence taxonomy (tag EVERY finding)

- **Verified** — authoritative primary source (SEC filing, government registry, the company's own site)
- **Corroborated** — consistent across 2+ independent public sources
- **Inferred** — reasoned from indirect signals (e.g., job posts imply tech gaps)
- **Speculative** — single weak signal or model estimate (e.g., small-site traffic estimate)

Public-signal analysis is probabilistic: traffic estimators overreport (SimilarWeb sessions ~94% high vs. GA in one 1,787-site study; unreliable under ~100K visits/month), tech fingerprinting misses hidden backends, and WHOIS PII is redacted post-GDPR. Never present modeled figures as Verified.

## Ethical guardrails

**Public data only.** No scraping behind logins, no pretexting or fake accounts, no circumventing paywalls or auth. Respect robots.txt, platform ToS, API rate limits, and required headers (e.g., SEC's User-Agent). Do not attempt to de-anonymize redacted registrant PII. Present all inferences as inferences.

## The 10 phases

Run Phases 0–2 in parallel, 3–7 as parallel research tracks, 8–9 as synthesis gates. Maintain a running state of findings, each with source and confidence. If a phase yields only Speculative data, flag it and continue — never block the run.

**Phase 0 — Domain & infrastructure.** RDAP (`https://rdap.org/domain/{domain}`) for age/registrar/DNSSEC; DNS-over-HTTPS (`https://dns.google/resolve?name={domain}&type=MX|TXT|NS`) for mail stack and SPF/DKIM/DMARC; crt.sh (`https://crt.sh/?q=%25.{domain}&output=json`, fall back to Cert Spotter) for subdomain enumeration; Wayback Machine for redesign cadence. Old domain + stale site = neglect/opportunity; missing email auth = hygiene quick-win; `app.`/`api.`/`status.` subdomains = hidden product surface.

**Phase 1 — Website & digital presence.** Fetch homepage, /about, /products, /pricing, /careers, /blog, sitemap.xml. Read positioning → business model and ICP; transparent pricing → mature GTM; blog recency → marketing investment; stale footer copyright year → classic neglect tell.

**Phase 2 — Tech stack detection.** Fingerprint from headers, HTML, script tags: CMS, e-commerce platform, analytics present?, marketing automation present?, CRM signals, security headers, page speed. Caveat: passive fingerprinting misses hidden backends — carry confidence through. LOW maturity here + strong business = HIGH uplift.

**Phase 3 — Company & people.** LinkedIn headcount trend and department mix; founder/exec pedigree; Glassdoor sentiment; job postings — **the strongest public growth signal**: role clusters and velocity spikes = real budget; first-ever data/RevOps role = building from zero; job descriptions confirm the stack; absence of tech roles despite growth = the gap a tech investor fills. Public, no-login data only.

**Phase 4 — Financial & business signals.** SEC EDGAR (`https://data.sec.gov/submissions/CIK##########.json`, User-Agent `"Name email"` required, 10 req/s); OpenCorporates / state registries for status and officers; funding history from public profiles; revenue triangulated from headcount × benchmarks and pricing × customer signals (always Inferred/Speculative); customer logos → concentration risk.

**Phase 5 — Market & competitive.** Industry classification, TAM/SAM triangulation, competitor set, SEO share of voice. Traffic estimates are directional only — tag Speculative for SMBs. Fragmented market = roll-up/bolt-on opportunity.

**Phase 6 — Customer & reputation.** G2/Capterra/Trustpilot/Google reviews (velocity and recency over raw count; cross-platform divergence = investigate), Reddit/forums for unfiltered sentiment (curated review sites can be gamed — a large share of recent G2 reviews are likely AI-generated), Google News RSS (`https://news.google.com/rss/search?q={query}`) and GDELT for press and tone.

**Phase 7 — Risk & compliance.** CourtListener v4 search (free token required; includes RECAP federal dockets) for litigation; breach history; security posture from Phase 2; key-person and customer concentration from Phases 3–4. More/severe risks → lower score.

**Phase 8 — Technology gap & opportunity (the differentiator).** Synthesize Phases 0–3 into: a Digital Maturity Score (customer, strategy, technology, operations, culture, data), an AI-Readiness Score (weight data maturity heavily: centralized? clean? 12+ months history? API-connected?), and an Automation Opportunity Map (no marketing automation → lifecycle automation; manual reporting → BI; no analytics → data infrastructure). Plot tech maturity × business fundamentals: **LOW tech + HIGH fundamentals = prime target**; HIGH + HIGH = expensive, less headroom; LOW + LOW = pass/turnaround only.

**Phase 9 — Synthesis & memo.** Compute the composite (use code execution for the math), assign the verdict, render the memo. Carry confidence labels into the output.

## Composite scoring model

Score each dimension 1–10, multiply by weight, sum to 0–100:

| # | Dimension | Weight | Feeds from phases |
|---|---|---|---|
| 1 | Market Attractiveness | 15% | 5 |
| 2 | Business Model Quality | 15% | 1, 4, 6 |
| 3 | Growth Trajectory | 12% | 3, 4, 5 |
| 4 | Digital/Tech Maturity | 10% | 0, 1, 2 |
| 5 | Team Strength | 10% | 3 |
| 6 | Financial Health Proxy | 13% | 4 |
| 7 | Risk Profile (inverse) | 10% | 7 |
| 8 | Technology Uplift Opportunity | 15% | 2, 8 |

Presets: **Growth Partnership** — raise Growth Trajectory and Tech Uplift to 18%, cut Financial Health to 8%. **Services Client** — raise Tech Uplift to 25%, lower Market/Financial. The scoring deliberately rewards low tech maturity *combined with* strong fundamentals rather than penalizing low maturity outright.

### Verdict taxonomy

| Composite + pattern | Verdict |
|---|---|
| 75+ with high uplift + strong fundamentals | **Platform Investment** |
| 65–80, strong thesis fit, smaller | **Bolt-on / Add-on** |
| 60–75, high trajectory, minority/growth | **Growth Partnership** |
| 55–75, fixable tech gap + ability to pay, not investable | **Services Opportunity** |
| 45–65, weak now but salvageable | **Turnaround / Watch** |
| <45 or fatal risk flags | **Pass** |

## Output: the investment memo

1. **Executive Summary** — one paragraph + verdict + composite + confidence caveat
2. **Company Snapshot** — what they do, model, size estimate, founded, HQ, leadership (each field confidence-tagged)
3. **Scorecard Table** — 8 dimensions, score, weight, weighted contribution, composite, verdict
4. **Dimension-by-Dimension Findings** — key evidence + confidence
5. **Technology Uplift Roadmap** — Quick Wins (0–90 days: email auth, analytics, marketing automation, page speed) vs. Strategic Plays (data infrastructure, AI/automation, re-architecture)
6. **Deal Thesis** — which quadrant, the value-creation angle
7. **Risks & Red Flags** — with severity
8. **Recommended Next Steps / Human Diligence Items** — everything Inferred/Speculative rises here

## Quick-run triage (15–30 min screen)

When the user wants fast sourcing triage, not the full deep-dive:

1. RDAP + DNS + homepage fetch — age, stack sniff, positioning, copyright staleness
2. One tech-stack read — CMS, analytics?, marketing automation?, security headers
3. Careers page + LinkedIn headcount glance — growing? hiring tech roles?
4. One reviews check + one news search — sentiment + red flags
5. Rapid scorecard on 4 dimensions only (Business Model Quality, Growth Trajectory, Digital/Tech Maturity, Technology Uplift) → provisional verdict + "worth a deep dive? Y/N"

Output: a half-page triage card with quadrant placement and top 3 uplift hypotheses.

## Caveats to state in every memo

This is a public-signal screening tool, not confirmatory diligence — output is a prioritized hypothesis set, not a decision. Revenue/traffic/headcount are largely modeled with wide error bands. Review and social signals can be manipulated. Free API access and rate limits shift frequently.
