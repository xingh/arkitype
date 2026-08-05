create a new skill from this document 

DueDilligence.md 

# Domain-to-Diligence: A Strategic Framework for AI-Driven Company Analysis
 
## TL;DR
 
- This framework lets an AI agent take a single domain name and produce an investment-grade company breakdown across 10 phases, scored on 8 weighted dimensions, ending in a PE-style verdict (Platform / Bolt-on / Growth Partnership / Services / Turnaround / Pass).# Domain-to-Diligence: A Strategic Framework for AI-Driven Company Analysis
 
## TL;DR
 
- This framework lets an AI agent take a single domain name and produce an investment-grade company breakdown across 10 phases, scored on 8 weighted dimensions, ending in a PE-style verdict (Platform / Bolt-on / Growth Partnership / Services / Turnaround / Pass).
- The core thesis for a technology-focused firm is the **“sweet spot”**: LOW Digital/Tech Maturity + HIGH Business Fundamentals = the highest-value target, because broken tech on top of a good business is the cheapest, fastest value to add.
- The framework is portable to any agent framework (LangGraph, CrewAI, OpenAI Agents, n8n, Claude) and converts directly into a Claude Skill (SKILL.md + scripts + templates), with every finding carrying a confidence label and only public data used.
 
## Key Findings (Design Principles Grounded in Research)
 
1. **Public-signal analysis is inherently probabilistic — so confidence scoring is mandatory.** Per Omniconvert’s 2026 study comparing SimilarWeb to Google Analytics across 1,787 eCommerce sites, “SimilarWeb overreported sessions by about 94 percent, almost double the tracked figure,” with “time on site emerging as the most reliable SimilarWeb metric.” Tech fingerprinting (Wappalyzer/BuiltWith) misses hidden backends, and WHOIS is largely redacted post-GDPR. Every finding must therefore be tagged **Verified / Corroborated / Inferred / Speculative**.
1. **The industry already proves the model works.** Grata “reads company websites like an analyst,” triangulates missing revenue/industry from public signals, and attaches confidence scores; per Harmonic.ai, the platform tracks “35M+ companies and 195M+ people… [sourcing] data from legal filings and dozens of public data sources,” and an Earlybird benchmark of 1,000 companies found Harmonic tracked 98% of relevant signals versus ~75% for legacy platforms. The agent replicates this multi-source triangulation loop.
1. **Job postings are the single strongest public growth signal.** Hiring precedes announcements: role clusters (e.g., 5 sales roles in 2 weeks), first-time role creation (first-ever RevOps or data engineer), and hiring-velocity spikes are the highest-predictive signals. A retailer suddenly posting data-scientist roles is investing in analytics/e-commerce months before revenue shows it.
1. **Technology maturity models converge on a stage ladder.** Per MIT CISR (Weill, Woerner & Sebastian, Dec 2024), based on an October 2022 survey of 721 companies, “enterprises in the first two stages of AI maturity had financial performance below industry average, while enterprises in stages 3 and 4 had financial performance well above industry average.” Deloitte/TM Forum’s Digital Maturity Model spans 5–6 dimensions (Customer, Strategy, Technology, Operations, Organization & Culture, Data) across 179 criteria. These anchor the Digital/Tech Maturity dimension.
1. **The PE playbook is real and repeatable.** Vista’s Vista Consulting Group — which per Umbrex’s profile “comprises 100+ professionals” (roughly on par with Vista’s deal team) codifying the “Vista Best Practices” playbook — and Thoma Bravo’s operating-partner model both center on rapid margin improvement plus technology standardization. Crosslake benchmarks targets with proprietary “TechIndicators, based on data from more than 6,000 prior technology M&A transactions… representing more than $30B in private equity transactions.” The agent’s scorecard mirrors this operational, benchmark-driven lens.
 
## Details: The Complete Pipeline
 
### Confidence Taxonomy (applied to EVERY finding)
 
- **Verified** — from an authoritative primary source (SEC filing, government registry, the company’s own site).
- **Corroborated** — consistent across 2+ independent public sources.
- **Inferred** — reasoned from indirect signals (e.g., job posts imply tech gaps).
- **Speculative** — single weak signal or model estimate (e.g., small-site traffic estimate).
 
-----
 
### PHASE 0 — Domain & Infrastructure Intelligence
 
**Goal:** Establish the digital foundation and age/scale of the company from the domain alone.
 
**Data to collect & sources (all free/keyless unless noted):**
 
- **RDAP** (modern WHOIS replacement, free/keyless): `https://rdap.org/domain/{domain}` (aggregator, auto-routes; ~10 req/10s Cloudflare limit) or direct, e.g. `https://rdap.verisign.com/com/v1/domain/{domain}`. Returns `events[]` (registration/expiration dates), registrar entity, EPP `status[]`, nameservers, DNSSEC. Note: gTLD WHOIS is no longer mandated since Jan 28, 2025 — use RDAP. Registrant PII usually redacted (GDPR).
- **DNS-over-HTTPS** (free/keyless): Google `https://dns.google/resolve?name={domain}&type={MX|TXT|A|NS}`; Cloudflare `https://cloudflare-dns.com/dns-query?name={domain}&type=MX` (requires header `Accept: application/dns-json`). Query A, MX, NS, and TXT for SPF (`{domain}`), DKIM (`default._domainkey.{domain}`), DMARC (`_dmarc.{domain}`).
- **Certificate Transparency / subdomain enumeration** (free/keyless): crt.sh `https://crt.sh/?q=%25.{domain}&output=json` — parse `name_value`, strip `*.`, dedupe. Flaky uptime + aggressive per-IP throttling: use backoff, check status codes, treat empty/non-200 as “source failed,” and fall back to Cert Spotter `https://api.certspotter.com/v1/issuances?domain={domain}&include_subdomains=true&expand=dns_names`.
- **Wayback Machine** (Internet Archive): historical snapshots to gauge domain age, redesign cadence, positioning shifts, and neglect.
 
**Signals & interpretation:**
 
- Domain age (RDAP registration event): old domain + modern site = established, reinvested; old domain + stale site = neglect/opportunity.
- MX records reveal the email stack (Google Workspace vs. Microsoft 365 vs. self-hosted → IT sophistication proxy).
- Missing SPF/DMARC = weak security hygiene = an easy quick-win to add.
- Subdomains reveal hidden infrastructure: `app.`, `api.`, `status.`, `careers.`, `shop.`, `staging.` → product surface, engineering maturity, e-commerce.
- CDN/hosting (from DNS/headers): Cloudflare/Fastly/AWS vs. bare shared hosting → scalability posture.
 
**Scoring (feeds Digital/Tech Maturity + Risk):** 1–10 on infrastructure modernity. 1–3 = shared hosting, no CDN, no email auth, expiring soon; 8–10 = modern CDN, DNSSEC, full email auth, clean subdomain architecture.
 
-----
 
### PHASE 1 — Website & Digital Presence Analysis
 
**Goal:** Understand what the company does, who it sells to, and how actively it maintains its presence.
 
**Data & sources:** web_fetch the homepage, /about, /products, /pricing, /careers, /blog, /customers, plus `sitemap.xml` and `robots.txt`.
 
**Signals & interpretation:**
 
- **Positioning/messaging** → business model (B2B/B2C/SaaS/services/e-commerce), ICP, value prop.
- **Pricing page** present + transparent → mature GTM; “contact us only” → enterprise/high-touch sales.
- **Blog recency** → marketing investment (posts within 30 days = active; nothing for 12+ months = neglected).
- **Careers page** → growth intent and (critically) the tech-gap signal (see Phase 3).
- **Copyright year in footer** → a stale year (e.g., “© 2019”) is a classic neglected-web-presence tell.
- **Product/service catalog breadth** → revenue diversification and complexity.
 
**Scoring (feeds Business Model Quality + Digital Maturity):** clarity of positioning, GTM sophistication, content freshness.
 
-----
 
### PHASE 2 — Technology Stack Detection
 
**Goal:** Fingerprint the tech stack to assess sophistication and locate automation/AI gaps.
 
**Data & sources:** Wappalyzer/BuiltWith-style detection via HTTP headers, HTML, JS variables, and DNS. Agent approach: web_fetch the page and inspect response headers (Server, X-Powered-By, Set-Cookie), `<script>`/meta tags, and known fingerprints; or call a hosted detector API. Also check security headers, page speed (Core Web Vitals), mobile responsiveness, and accessibility.
 
**Signals & interpretation (the value-creation map):**
 
- **CMS:** WordPress — which per W3Techs (April 2025) runs “43.4% of the websites on the internet,” roughly nine times its nearest competitor Shopify (4.8%) — is common/low-cost; headless/custom = higher maturity.
- **E-commerce:** Shopify/BigCommerce vs. custom vs. none.
- **Analytics present?** No GA/analytics = flying blind = a data-infrastructure opportunity.
- **Marketing automation (HubSpot/Marketo/Klaviyo) absent?** = automation opportunity.
- **CRM signals** (forms, chat, tracking) → sales-ops maturity.
- **Security headers missing / old TLS** → risk + quick win.
- **No CDN, slow pages, poor mobile** → conversion drag + easy uplift.
- **Caveat:** passive fingerprinting misses hidden backends (stripped headers, Node behind Nginx, apps behind Cloudflare). Tag detections with confidence; carry a detector’s own confidence level through.
 
**Scoring (heavily feeds Digital/Tech Maturity + Technology Uplift Opportunity):** invert for opportunity — LOW maturity here + strong business = HIGH uplift.
 
-----
 
### PHASE 3 — Company & People Intelligence
 
**Goal:** Assess team, headcount trajectory, leadership, and read job posts as growth/tech-gap signals.
 
**Data & sources:** LinkedIn company page (public headcount, growth trend, leadership), founder/exec backgrounds (public bios, prior exits), Glassdoor (employee sentiment; ~3.3/5 is a common industry baseline), and job boards / the company’s own careers page. Public, no-login data only — no scraping behind auth.
 
**Signals & interpretation:**
 
- **Headcount growth on LinkedIn** = proxy for growth rate; department mix reveals strategy shifts (all-sales six months ago → all-engineers now = strategic pivot).
- **Job postings = the highest-value inferred signal:**
  - Hiring data engineers / ML engineers = investing in analytics/AI infrastructure.
  - First-ever RevOps / SDR / data role = building a function from zero (high intent).
  - Role clusters + velocity spikes = compressed urgency, real budget.
  - Job descriptions name the tech stack (Snowflake, Salesforce, Kubernetes) → technographic confirmation.
  - **Absence of tech/data roles despite growth = the technology gap a tech investor fills.**
- **Founder/leadership pedigree** → execution confidence (Thoma Bravo’s leadership test: open-mindedness, cares about numbers, strong followership).
- **Glassdoor** → culture/retention risk; watch for divergence from public messaging.
 
**Scoring (feeds Team Strength + Growth Trajectory):** headcount trend, leadership quality, hiring-signal strength.
 
-----
 
### PHASE 4 — Financial & Business Signals
 
**Goal:** Estimate scale, funding, revenue, and business-model economics from public proxies.
 
**Data & sources:**
 
- **SEC EDGAR** (free; REQUIRED User-Agent `"Name email"`, 10 req/s limit): Submissions `https://data.sec.gov/submissions/CIK##########.json` (10-digit zero-padded CIK); Company Facts `https://data.sec.gov/api/xbrl/companyfacts/CIK##########.json`; Full-text search `https://efts.sec.gov/LATEST/search-index?q=...`; ticker→CIK map `https://www.sec.gov/files/company_tickers.json`. (Public companies + anyone named in filings.)
- **Business registries:** OpenCorporates API (`https://api.opencorporates.com/v0.4/...`; free for open-data/journalism, commercial from ~£2,250/yr) for incorporation date, status, officers, jurisdiction; state Secretary of State business search (free but fragmented — access, fields, and bulk availability vary widely by state; Texas SOSDirect charges $1/search, others free).
- **Funding history:** Crunchbase / PitchBook-style sources (public profiles) for rounds, investors, totals.
- **Revenue estimates:** triangulate from headcount × revenue-per-employee benchmarks, pricing × customer-count signals, and third-party estimates (all Inferred/Speculative).
- **Case studies / logos / customer counts** on the site → customer concentration and segment.
 
**Signals & interpretation:**
 
- Funding stage + recency → runway and growth phase.
- Pricing model × customer signals → revenue quality (recurring vs. project; SaaS ARR is the PE gold standard, with 90%+ renewal rates).
- Registry status (active/good standing vs. delinquent) → basic health/risk.
- Enterprise logos → contract value; few large logos → customer-concentration risk.
 
**Scoring (feeds Financial Health Proxy):** be explicit that most values here are Inferred; never present modeled revenue as Verified.
 
-----
 
### PHASE 5 — Market & Competitive Analysis
 
**Goal:** Classify the industry, size the market, map competitors, and gauge share of voice.
 
**Data & sources:** industry classification (SIC/NAICS from filings or inference), TAM/SAM (public research, triangulated), competitor identification (search + “similar to” reasoning), SEO share of voice, and traffic estimates (SimilarWeb/Semrush/Ahrefs-style).
 
**Signals & interpretation:**
 
- **Traffic estimates are directional only.** Per Omniconvert’s 1,787-site study, SimilarWeb overreported sessions by ~94%; it is unreliable under ~100K monthly visits (error can exceed 70% on small sites) and is most reliable for large sites and on time-on-site rather than raw sessions. Use as a trend/relative signal and tag Speculative for SMBs.
- Competitor set + positioning → differentiation and pricing power.
- Fragmented market = roll-up/bolt-on opportunity (the Thoma Bravo/Vista buy-and-build thesis).
- SEO share of voice → demand-gen strength.
 
**Scoring (feeds Market Attractiveness):** market size, growth, fragmentation, competitive intensity, defensibility.
 
-----
 
### PHASE 6 — Customer & Reputation Signals
 
**Goal:** Gauge customer sentiment, satisfaction trend, and brand strength.
 
**Data & sources:** G2, Capterra, Trustpilot, Google, Yelp reviews; social presence/engagement; community (Reddit, forums); press coverage; awards.
 
- **News:** Google News RSS `https://news.google.com/rss/search?q={query}` and GDELT `https://api.gdeltproject.org/api/v2/doc/doc?query={query}&mode=ArtList&format=json` (free/keyless, includes tone/sentiment).
 
**Signals & interpretation:**
 
- **Review velocity** (rate + recency) matters more than raw count — a steady stream signals health; a burst then silence signals gaming; velocity decay erodes trust scores.
- **Cross-platform divergence** (G2 up, Trustpilot down) = different segments, different experiences — investigate.
- **Reddit/forums = most honest sentiment.** Curated review sites can be gamed: per Originality.ai’s Nov 2025 study of 187,000 G2 reviews across 15,231 companies, “more than 26% of reviews on G2 since the launch of ChatGPT are likely to be AI-generated… an increase of 92.8% compared to before ChatGPT launched,” peaking at 34.6% in June 2023. Use unfiltered sources to sanity-check.
- Rating level + trend → NPS proxy; press/awards → brand equity.
 
**Scoring (feeds Business Model Quality + Risk):** sentiment level, velocity trend, reputational red flags.
 
-----
 
### PHASE 7 — Risk & Compliance Signals
 
**Goal:** Surface litigation, regulatory, security, and concentration risks.
 
**Data & sources:**
 
- **Litigation:** CourtListener REST API v4 `https://www.courtlistener.com/api/rest/v4/search/?q={query}&type=o`. Note (2026): anonymous requests now return 401;  a free token is needed (`Authorization: Token {token}`), with free-tier limits of ~5 req/min, 50/hr, 125/day. Includes RECAP federal dockets (a free PACER mirror).
- **Regulatory/security:** breach-history checks, security headers (Phase 2), SEC litigation releases, and news (Phase 6).
- **Key-person & concentration:** inferred from Phases 3–4 (founder-dependence, few large logos).
 
**Signals & interpretation:** active litigation as defendant, regulatory actions, breach history, single-founder dependence, and customer concentration all raise risk. AKF Partners’ “too good to be true” heuristic (Benford’s-law-style anomalies, an over-dominant CEO answering every technical question) flags areas warranting deeper human diligence.
 
**Scoring (feeds Risk Profile — inverse):** more/severe risks → lower score.
 
-----
 
### PHASE 8 — Technology Gap & Opportunity Analysis (the differentiator)
 
**Goal:** Explicitly identify what tech/AI/automation the company LACKS that a technology-focused investor could add. This is the heart of the framework.
 
**Method:** synthesize Phases 0–3 into three scores:
 
1. **Digital Maturity Score** (Deloitte/TM Forum lens: Customer, Strategy, Technology, Operations, Organization & Culture, Data).
1. **AI-Readiness Score** — weight data maturity heavily (in common SMB AI-readiness frameworks, data maturity ≈ 30% of the score, infrastructure ~15%, budget alignment ~10%): Is data centralized (CRM + sales + ops integrated)? Clean, with 12+ months of history? Cloud/API-connected? MIT CISR’s ladder implies firms below stage 3 underperform peers.
1. **Automation Opportunity Map** — list detected gaps → concrete plays (no marketing automation → lifecycle automation; manual reporting → BI/dashboards; no chatbot → support deflection; no analytics → data infrastructure).
 
**Interpretation — the sweet spot:** plot Tech Maturity (low↔high) against Business Fundamentals (weak↔strong). **LOW tech maturity + HIGH fundamentals = the prime target** (broken tech, good business = cheap, fast value-add). HIGH tech + HIGH fundamentals = expensive, less headroom. LOW + LOW = pass/turnaround only.
 
**Scoring (this IS the Technology Uplift Opportunity dimension):** magnitude × feasibility × business quality of the gaps.
 
-----
 
### PHASE 9 — Synthesis, Scoring & Investment Memo Generation
 
Compute the composite score (below), assign a verdict, and generate the memo artifact. Use code execution for the scoring math and to render the memo; carry confidence labels into the output.
 
-----
 
## The Composite Scoring Model
 
Each dimension is scored 1–10 (with explicit rubric anchors), multiplied by weight, and summed to a 0–100 composite.
 
|#|Dimension                    |Weight (Platform preset)|What it measures                                          |Primary phases|
|-|-----------------------------|------------------------|----------------------------------------------------------|--------------|
|1|Market Attractiveness        |15%                     |Size, growth, fragmentation, defensibility                |5             |
|2|Business Model Quality       |15%                     |Revenue quality, recurring/ARR, pricing power, retention  |1,4,6         |
|3|Growth Trajectory            |12%                     |Headcount/hiring velocity, traffic trend, funding momentum|3,4,5         |
|4|Digital/Tech Maturity        |10%                     |Stack modernity, data/automation, security                |0,1,2         |
|5|Team Strength                |10%                     |Leadership pedigree, org depth, culture                   |3             |
|6|Financial Health Proxy       |13%                     |Scale, funding, runway, profitability signals             |4             |
|7|Risk Profile                 |10%                     |Litigation, compliance, concentration, key-person         |7             |
|8|Technology Uplift Opportunity|15%                     |Size & feasibility of tech/AI/automation value-add        |2,8           |
 
**Rubric anchors (example — Technology Uplift Opportunity):**
 
- 1–2: Already best-in-class tech; little to add.
- 3–4: Modern stack, marginal gains.
- 5–6: Some clear gaps (e.g., no marketing automation).
- 7–8: Multiple high-value gaps + strong business = strong thesis.
- 9–10: Pervasive tech neglect on top of an excellent, profitable business = ideal.
 
### Weighting Presets (rationale)
 
- **Acquisition / Platform target:** as above — balances fundamentals with uplift; Risk and Financial Health weighted higher because you’re buying control.
- **Growth Partnership:** raise Growth Trajectory (18%) and Technology Uplift (18%), lower Financial Health (8%) — you’re betting on trajectory, not buying the whole thing.
- **Services Client:** raise Technology Uplift (25%) and the Digital Maturity gap, lower Market/Financial — you just need a fixable problem and the ability to pay.
 
### The Key Insight (encoded in the verdict logic)
 
For a technology-focused firm, the highest-value quadrant is **low Digital/Tech Maturity (dim 4 low) + high Business Fundamentals (dims 1, 2, 6 high) + high Technology Uplift (dim 8 high)**. The scoring intentionally rewards this combination rather than penalizing low tech maturity outright.
 
### Verdict Taxonomy
 
|Composite + pattern                                         |Verdict                 |
|------------------------------------------------------------|------------------------|
|75+ with high uplift + strong fundamentals                  |**Platform Investment** |
|65–80, strong fit within a thesis, smaller                  |**Bolt-on / Add-on**    |
|60–75, high trajectory, minority/growth                     |**Growth Partnership**  |
|55–75, fixable tech gap + ability to pay, but not investable|**Services Opportunity**|
|45–65, weak now but salvageable                             |**Turnaround / Watch**  |
|<45 or fatal risk flags                                     |**Pass**                |
 
-----
 
## Output Artifacts: The Investment Memo Structure
 
1. **Executive Summary** — one paragraph + verdict + composite score + confidence caveat.
1. **Company Snapshot** — what they do, model, size estimate, founded, HQ, leadership (each field confidence-tagged).
1. **Scorecard Table** — 8 dimensions, score, weight, weighted contribution, composite, verdict.
1. **Dimension-by-Dimension Findings** — key evidence + confidence per dimension.
1. **Technology Uplift Roadmap** — Quick Wins (0–90 days: email auth, analytics, marketing automation, page speed) vs. Strategic Plays (data infrastructure, AI/automation, platform re-architecture).
1. **Deal Thesis** — why this fits; which quadrant; the value-creation angle.
1. **Risks & Red Flags** — with severity.
1. **Recommended Next Steps / Human Diligence Items** — what to verify with management/the data room (everything tagged Inferred/Speculative rises here).
 
-----
 
## Agent Implementation Guidance
 
### Workflow shape
 
- **Sequential with checkpoints, parallel within phases.** Phases 0–2 (infrastructure/site/stack) can run in parallel; Phases 3–7 as parallel research tracks; Phases 8–9 are synthesis gates that require prior outputs.
- **Confidence gating:** if a phase yields only Speculative data, flag it and continue; never block the whole run.
- **State object:** maintain a JSON company-analysis state that each phase appends to (findings + source + confidence), which Phase 9 consumes.
 
### Claude tool mapping
 
- **web_search** — company news, competitors, reviews, funding, leadership.
- **web_fetch** — homepage/subpages, sitemap, RDAP/DNS/crt.sh/SEC/CourtListener JSON endpoints, review pages.
- **code execution** — scoring math, revenue triangulation, DoH/crt.sh/SEC parsing, memo rendering, chart generation.
- **artifacts** — the final investment memo (and optionally an HTML scorecard).
 
### Portability to other frameworks
 
- **LangGraph:** each phase = a node; the state object = graph state; Phase 9 = a reducer.
- **CrewAI:** one agent per research track + a synthesis agent.
- **n8n:** HTTP Request nodes for the free APIs, a Function node for scoring, an LLM node for the memo.
- **OpenAI Agents:** tools = search/fetch/code; phases = handoffs.
 
### Data limitations & confidence (bake in)
 
- Traffic estimates are unreliable for SMBs; revenue is triangulated; WHOIS PII is redacted; tech fingerprinting misses hidden backends; review sites can be gamed. State these in every memo’s caveats.
 
### Ethical & legal guardrails
 
- **Public data only.** No scraping behind logins, no pretexting/fake accounts, no circumventing paywalls or auth. Respect robots.txt and platform ToS. Comply with fair use and honor API rate limits and required headers (e.g., the SEC User-Agent). GDPR: do not attempt to de-anonymize redacted registrant PII. Present all inferences as inferences.
 
### Mapping to a Claude Skill (SKILL.md)
 
A skill is a folder with a `SKILL.md` (YAML frontmatter: `name`, `description` — the description drives auto-invocation) plus optional `scripts/`, `references/`, `templates/`, `assets/`. Use progressive disclosure: keep SKILL.md lean (~1,500–2,000 words) and push detail to references, which load only when needed. Scripts run via bash without consuming context.
 
```
domain-to-diligence/
├── SKILL.md                      # workflow: the 10 phases + verdict logic (lean)
├── references/
│   ├── phase-playbooks.md        # detailed per-phase signal-interpretation guides
│   ├── data-sources.md           # exact API endpoints, headers, rate limits
│   └── scoring-rubrics.md        # 1-10 anchors per dimension + presets
├── scripts/
│   ├── domain_intel.py           # RDAP + DoH + crt.sh calls
│   ├── sec_lookup.py             # EDGAR submissions/facts (with UA header)
│   ├── score.py                  # composite scoring + verdict
│   └── render_memo.py            # memo/HTML generation
└── templates/
    └── investment_memo.md        # the 8-section memo template
```
 
SKILL.md frontmatter example: `description: Analyze a company from only its domain name and produce an investment-grade diligence memo with scores. Use when given a domain/website and asked to evaluate, screen, or diligence a company.`
 
-----
 
## The Quick-Run Version (15–30 min triage screen)
 
For fast PE sourcing triage before committing to the full deep-dive:
 
1. **RDAP + DNS + homepage fetch** (Phase 0–1 lite): age, stack sniff, positioning, copyright-year staleness.
1. **One tech-stack read** (Phase 2 lite): CMS, analytics present?, marketing automation present?, security headers.
1. **Careers page + LinkedIn headcount glance** (Phase 3 lite): growing? hiring tech roles?
1. **One reviews check + one news search** (Phase 6 lite): sentiment + any red flags.
1. **Rapid scorecard:** score just 4 dimensions — Business Model Quality, Growth Trajectory, Digital/Tech Maturity, Technology Uplift — and output a provisional verdict + a “worth a deep dive? Y/N.”
 
Output: a half-page triage card with provisional quadrant placement and the top 3 uplift hypotheses.
 
## Recommendations
 
1. **Build the quick-run screen first** and run it on 20–30 known companies to calibrate the rubric anchors before automating the full pipeline. Benchmark to advance: if the triage verdict agrees with a human analyst on ≥70% of a test set, proceed to the full build.
1. **Implement Phase 8 (tech gap) as the crown jewel** — it’s the differentiator versus generic tools like Grata/Harmonic, which score fit but not “what a tech investor could add.”
1. **Wrap every numeric output in a confidence band** and route all Inferred/Speculative items into the “human diligence” section — this protects credibility and defines the human handoff.
1. **Start with the free API tier** (SEC EDGAR, RDAP, DoH, crt.sh, CourtListener, Google News/GDELT, OpenCorporates open data) and only add paid data (Crunchbase, SimilarWeb, BuiltWith, PitchBook) once volume justifies it.
1. **Convert to a Claude Skill once the workflow is stable**, using the folder structure above, so it’s portable and reusable across the firm.
1. **Recalibrate quarterly** — API access changes fast (PatentsView went key-only in 2025 and is migrating to USPTO’s Open Data Portal; CourtListener tightened anonymous limits in 2026). Keep `references/data-sources.md` as the single source of truth.
 
## Caveats
 
- This is a public-signal screening tool, not a substitute for confirmatory diligence (data room, management calls, financial audit, legal/IP review). Its output is a prioritized hypothesis set, not a decision.
- Revenue/traffic/headcount figures are largely modeled or inferred and carry wide error bands, especially for SMBs and sub-100K-visit sites (where SimilarWeb error can exceed 70%).
- Review and social signals can be manipulated (over a quarter of recent G2 reviews are likely AI-generated); corroborate with unfiltered sources like Reddit.
- Free API access, keys, and rate limits shift frequently; the framework’s data-source layer must be actively maintained.
- The scoring weights are a starting template — calibrate them to the firm’s actual deal outcomes over time.
- One source correction to note for internal accuracy: Vista Consulting Group is documented at 100+ professionals (not 200+), per Umbrex; treat headcount figures for private operating groups as approximate.

- The core thesis for a technology-focused firm is the **“sweet spot”**: LOW Digital/Tech Maturity + HIGH Business Fundamentals = the highest-value target, because broken tech on top of a good business is the cheapest, fastest value to add.
- The framework is portable to any agent framework (LangGraph, CrewAI, OpenAI Agents, n8n, Claude) and converts directly into a Claude Skill (SKILL.md + scripts + templates), with every finding carrying a confidence label and only public data used.
 
## Key Findings (Design Principles Grounded in Research)
 
1. **Public-signal analysis is inherently probabilistic — so confidence scoring is mandatory.** Per Omniconvert’s 2026 study comparing SimilarWeb to Google Analytics across 1,787 eCommerce sites, “SimilarWeb overreported sessions by about 94 percent, almost double the tracked figure,” with “time on site emerging as the most reliable SimilarWeb metric.” Tech fingerprinting (Wappalyzer/BuiltWith) misses hidden backends, and WHOIS is largely redacted post-GDPR. Every finding must therefore be tagged **Verified / Corroborated / Inferred / Speculative**.
1. **The industry already proves the model works.** Grata “reads company websites like an analyst,” triangulates missing revenue/industry from public signals, and attaches confidence scores; per Harmonic.ai, the platform tracks “35M+ companies and 195M+ people… [sourcing] data from legal filings and dozens of public data sources,” and an Earlybird benchmark of 1,000 companies found Harmonic tracked 98% of relevant signals versus ~75% for legacy platforms. The agent replicates this multi-source triangulation loop.
1. **Job postings are the single strongest public growth signal.** Hiring precedes announcements: role clusters (e.g., 5 sales roles in 2 weeks), first-time role creation (first-ever RevOps or data engineer), and hiring-velocity spikes are the highest-predictive signals. A retailer suddenly posting data-scientist roles is investing in analytics/e-commerce months before revenue shows it.
1. **Technology maturity models converge on a stage ladder.** Per MIT CISR (Weill, Woerner & Sebastian, Dec 2024), based on an October 2022 survey of 721 companies, “enterprises in the first two stages of AI maturity had financial performance below industry average, while enterprises in stages 3 and 4 had financial performance well above industry average.” Deloitte/TM Forum’s Digital Maturity Model spans 5–6 dimensions (Customer, Strategy, Technology, Operations, Organization & Culture, Data) across 179 criteria. These anchor the Digital/Tech Maturity dimension.
1. **The PE playbook is real and repeatable.** Vista’s Vista Consulting Group — which per Umbrex’s profile “comprises 100+ professionals” (roughly on par with Vista’s deal team) codifying the “Vista Best Practices” playbook — and Thoma Bravo’s operating-partner model both center on rapid margin improvement plus technology standardization. Crosslake benchmarks targets with proprietary “TechIndicators, based on data from more than 6,000 prior technology M&A transactions… representing more than $30B in private equity transactions.” The agent’s scorecard mirrors this operational, benchmark-driven lens.
 
## Details: The Complete Pipeline
 
### Confidence Taxonomy (applied to EVERY finding)
 
- **Verified** — from an authoritative primary source (SEC filing, government registry, the company’s own site).
- **Corroborated** — consistent across 2+ independent public sources.
- **Inferred** — reasoned from indirect signals (e.g., job posts imply tech gaps).
- **Speculative** — single weak signal or model estimate (e.g., small-site traffic estimate).
 
-----
 
### PHASE 0 — Domain & Infrastructure Intelligence
 
**Goal:** Establish the digital foundation and age/scale of the company from the domain alone.
 
**Data to collect & sources (all free/keyless unless noted):**
 
- **RDAP** (modern WHOIS replacement, free/keyless): `https://rdap.org/domain/{domain}` (aggregator, auto-routes; ~10 req/10s Cloudflare limit) or direct, e.g. `https://rdap.verisign.com/com/v1/domain/{domain}`. Returns `events[]` (registration/expiration dates), registrar entity, EPP `status[]`, nameservers, DNSSEC. Note: gTLD WHOIS is no longer mandated since Jan 28, 2025 — use RDAP. Registrant PII usually redacted (GDPR).
- **DNS-over-HTTPS** (free/keyless): Google `https://dns.google/resolve?name={domain}&type={MX|TXT|A|NS}`; Cloudflare `https://cloudflare-dns.com/dns-query?name={domain}&type=MX` (requires header `Accept: application/dns-json`). Query A, MX, NS, and TXT for SPF (`{domain}`), DKIM (`default._domainkey.{domain}`), DMARC (`_dmarc.{domain}`).
- **Certificate Transparency / subdomain enumeration** (free/keyless): crt.sh `https://crt.sh/?q=%25.{domain}&output=json` — parse `name_value`, strip `*.`, dedupe. Flaky uptime + aggressive per-IP throttling: use backoff, check status codes, treat empty/non-200 as “source failed,” and fall back to Cert Spotter `https://api.certspotter.com/v1/issuances?domain={domain}&include_subdomains=true&expand=dns_names`.
- **Wayback Machine** (Internet Archive): historical snapshots to gauge domain age, redesign cadence, positioning shifts, and neglect.
 
**Signals & interpretation:**
 
- Domain age (RDAP registration event): old domain + modern site = established, reinvested; old domain + stale site = neglect/opportunity.
- MX records reveal the email stack (Google Workspace vs. Microsoft 365 vs. self-hosted → IT sophistication proxy).
- Missing SPF/DMARC = weak security hygiene = an easy quick-win to add.
- Subdomains reveal hidden infrastructure: `app.`, `api.`, `status.`, `careers.`, `shop.`, `staging.` → product surface, engineering maturity, e-commerce.
- CDN/hosting (from DNS/headers): Cloudflare/Fastly/AWS vs. bare shared hosting → scalability posture.
 
**Scoring (feeds Digital/Tech Maturity + Risk):** 1–10 on infrastructure modernity. 1–3 = shared hosting, no CDN, no email auth, expiring soon; 8–10 = modern CDN, DNSSEC, full email auth, clean subdomain architecture.
 
-----
 
### PHASE 1 — Website & Digital Presence Analysis
 
**Goal:** Understand what the company does, who it sells to, and how actively it maintains its presence.
 
**Data & sources:** web_fetch the homepage, /about, /products, /pricing, /careers, /blog, /customers, plus `sitemap.xml` and `robots.txt`.
 
**Signals & interpretation:**
 
- **Positioning/messaging** → business model (B2B/B2C/SaaS/services/e-commerce), ICP, value prop.
- **Pricing page** present + transparent → mature GTM; “contact us only” → enterprise/high-touch sales.
- **Blog recency** → marketing investment (posts within 30 days = active; nothing for 12+ months = neglected).
- **Careers page** → growth intent and (critically) the tech-gap signal (see Phase 3).
- **Copyright year in footer** → a stale year (e.g., “© 2019”) is a classic neglected-web-presence tell.
- **Product/service catalog breadth** → revenue diversification and complexity.
 
**Scoring (feeds Business Model Quality + Digital Maturity):** clarity of positioning, GTM sophistication, content freshness.
 
-----
 
### PHASE 2 — Technology Stack Detection
 
**Goal:** Fingerprint the tech stack to assess sophistication and locate automation/AI gaps.
 
**Data & sources:** Wappalyzer/BuiltWith-style detection via HTTP headers, HTML, JS variables, and DNS. Agent approach: web_fetch the page and inspect response headers (Server, X-Powered-By, Set-Cookie), `<script>`/meta tags, and known fingerprints; or call a hosted detector API. Also check security headers, page speed (Core Web Vitals), mobile responsiveness, and accessibility.
 
**Signals & interpretation (the value-creation map):**
 
- **CMS:** WordPress — which per W3Techs (April 2025) runs “43.4% of the websites on the internet,” roughly nine times its nearest competitor Shopify (4.8%) — is common/low-cost; headless/custom = higher maturity.
- **E-commerce:** Shopify/BigCommerce vs. custom vs. none.
- **Analytics present?** No GA/analytics = flying blind = a data-infrastructure opportunity.
- **Marketing automation (HubSpot/Marketo/Klaviyo) absent?** = automation opportunity.
- **CRM signals** (forms, chat, tracking) → sales-ops maturity.
- **Security headers missing / old TLS** → risk + quick win.
- **No CDN, slow pages, poor mobile** → conversion drag + easy uplift.
- **Caveat:** passive fingerprinting misses hidden backends (stripped headers, Node behind Nginx, apps behind Cloudflare). Tag detections with confidence; carry a detector’s own confidence level through.
 
**Scoring (heavily feeds Digital/Tech Maturity + Technology Uplift Opportunity):** invert for opportunity — LOW maturity here + strong business = HIGH uplift.
 
-----
 
### PHASE 3 — Company & People Intelligence
 
**Goal:** Assess team, headcount trajectory, leadership, and read job posts as growth/tech-gap signals.
 
**Data & sources:** LinkedIn company page (public headcount, growth trend, leadership), founder/exec backgrounds (public bios, prior exits), Glassdoor (employee sentiment; ~3.3/5 is a common industry baseline), and job boards / the company’s own careers page. Public, no-login data only — no scraping behind auth.
 
**Signals & interpretation:**
 
- **Headcount growth on LinkedIn** = proxy for growth rate; department mix reveals strategy shifts (all-sales six months ago → all-engineers now = strategic pivot).
- **Job postings = the highest-value inferred signal:**
  - Hiring data engineers / ML engineers = investing in analytics/AI infrastructure.
  - First-ever RevOps / SDR / data role = building a function from zero (high intent).
  - Role clusters + velocity spikes = compressed urgency, real budget.
  - Job descriptions name the tech stack (Snowflake, Salesforce, Kubernetes) → technographic confirmation.
  - **Absence of tech/data roles despite growth = the technology gap a tech investor fills.**
- **Founder/leadership pedigree** → execution confidence (Thoma Bravo’s leadership test: open-mindedness, cares about numbers, strong followership).
- **Glassdoor** → culture/retention risk; watch for divergence from public messaging.
 
**Scoring (feeds Team Strength + Growth Trajectory):** headcount trend, leadership quality, hiring-signal strength.
 
-----
 
### PHASE 4 — Financial & Business Signals
 
**Goal:** Estimate scale, funding, revenue, and business-model economics from public proxies.
 
**Data & sources:**
 
- **SEC EDGAR** (free; REQUIRED User-Agent `"Name email"`, 10 req/s limit): Submissions `https://data.sec.gov/submissions/CIK##########.json` (10-digit zero-padded CIK); Company Facts `https://data.sec.gov/api/xbrl/companyfacts/CIK##########.json`; Full-text search `https://efts.sec.gov/LATEST/search-index?q=...`; ticker→CIK map `https://www.sec.gov/files/company_tickers.json`. (Public companies + anyone named in filings.)
- **Business registries:** OpenCorporates API (`https://api.opencorporates.com/v0.4/...`; free for open-data/journalism, commercial from ~£2,250/yr) for incorporation date, status, officers, jurisdiction; state Secretary of State business search (free but fragmented — access, fields, and bulk availability vary widely by state; Texas SOSDirect charges $1/search, others free).
- **Funding history:** Crunchbase / PitchBook-style sources (public profiles) for rounds, investors, totals.
- **Revenue estimates:** triangulate from headcount × revenue-per-employee benchmarks, pricing × customer-count signals, and third-party estimates (all Inferred/Speculative).
- **Case studies / logos / customer counts** on the site → customer concentration and segment.
 
**Signals & interpretation:**
 
- Funding stage + recency → runway and growth phase.
- Pricing model × customer signals → revenue quality (recurring vs. project; SaaS ARR is the PE gold standard, with 90%+ renewal rates).
- Registry status (active/good standing vs. delinquent) → basic health/risk.
- Enterprise logos → contract value; few large logos → customer-concentration risk.
 
**Scoring (feeds Financial Health Proxy):** be explicit that most values here are Inferred; never present modeled revenue as Verified.
 
-----
 
### PHASE 5 — Market & Competitive Analysis
 
**Goal:** Classify the industry, size the market, map competitors, and gauge share of voice.
 
**Data & sources:** industry classification (SIC/NAICS from filings or inference), TAM/SAM (public research, triangulated), competitor identification (search + “similar to” reasoning), SEO share of voice, and traffic estimates (SimilarWeb/Semrush/Ahrefs-style).
 
**Signals & interpretation:**
 
- **Traffic estimates are directional only.** Per Omniconvert’s 1,787-site study, SimilarWeb overreported sessions by ~94%; it is unreliable under ~100K monthly visits (error can exceed 70% on small sites) and is most reliable for large sites and on time-on-site rather than raw sessions. Use as a trend/relative signal and tag Speculative for SMBs.
- Competitor set + positioning → differentiation and pricing power.
- Fragmented market = roll-up/bolt-on opportunity (the Thoma Bravo/Vista buy-and-build thesis).
- SEO share of voice → demand-gen strength.
 
**Scoring (feeds Market Attractiveness):** market size, growth, fragmentation, competitive intensity, defensibility.
 
-----
 
### PHASE 6 — Customer & Reputation Signals
 
**Goal:** Gauge customer sentiment, satisfaction trend, and brand strength.
 
**Data & sources:** G2, Capterra, Trustpilot, Google, Yelp reviews; social presence/engagement; community (Reddit, forums); press coverage; awards.
 
- **News:** Google News RSS `https://news.google.com/rss/search?q={query}` and GDELT `https://api.gdeltproject.org/api/v2/doc/doc?query={query}&mode=ArtList&format=json` (free/keyless, includes tone/sentiment).
 
**Signals & interpretation:**
 
- **Review velocity** (rate + recency) matters more than raw count — a steady stream signals health; a burst then silence signals gaming; velocity decay erodes trust scores.
- **Cross-platform divergence** (G2 up, Trustpilot down) = different segments, different experiences — investigate.
- **Reddit/forums = most honest sentiment.** Curated review sites can be gamed: per Originality.ai’s Nov 2025 study of 187,000 G2 reviews across 15,231 companies, “more than 26% of reviews on G2 since the launch of ChatGPT are likely to be AI-generated… an increase of 92.8% compared to before ChatGPT launched,” peaking at 34.6% in June 2023. Use unfiltered sources to sanity-check.
- Rating level + trend → NPS proxy; press/awards → brand equity.
 
**Scoring (feeds Business Model Quality + Risk):** sentiment level, velocity trend, reputational red flags.
 
-----
 
### PHASE 7 — Risk & Compliance Signals
 
**Goal:** Surface litigation, regulatory, security, and concentration risks.
 
**Data & sources:**
 
- **Litigation:** CourtListener REST API v4 `https://www.courtlistener.com/api/rest/v4/search/?q={query}&type=o`. Note (2026): anonymous requests now return 401;  a free token is needed (`Authorization: Token {token}`), with free-tier limits of ~5 req/min, 50/hr, 125/day. Includes RECAP federal dockets (a free PACER mirror).
- **Regulatory/security:** breach-history checks, security headers (Phase 2), SEC litigation releases, and news (Phase 6).
- **Key-person & concentration:** inferred from Phases 3–4 (founder-dependence, few large logos).
 
**Signals & interpretation:** active litigation as defendant, regulatory actions, breach history, single-founder dependence, and customer concentration all raise risk. AKF Partners’ “too good to be true” heuristic (Benford’s-law-style anomalies, an over-dominant CEO answering every technical question) flags areas warranting deeper human diligence.
 
**Scoring (feeds Risk Profile — inverse):** more/severe risks → lower score.
 
-----
 
### PHASE 8 — Technology Gap & Opportunity Analysis (the differentiator)
 
**Goal:** Explicitly identify what tech/AI/automation the company LACKS that a technology-focused investor could add. This is the heart of the framework.
 
**Method:** synthesize Phases 0–3 into three scores:
 
1. **Digital Maturity Score** (Deloitte/TM Forum lens: Customer, Strategy, Technology, Operations, Organization & Culture, Data).
1. **AI-Readiness Score** — weight data maturity heavily (in common SMB AI-readiness frameworks, data maturity ≈ 30% of the score, infrastructure ~15%, budget alignment ~10%): Is data centralized (CRM + sales + ops integrated)? Clean, with 12+ months of history? Cloud/API-connected? MIT CISR’s ladder implies firms below stage 3 underperform peers.
1. **Automation Opportunity Map** — list detected gaps → concrete plays (no marketing automation → lifecycle automation; manual reporting → BI/dashboards; no chatbot → support deflection; no analytics → data infrastructure).
 
**Interpretation — the sweet spot:** plot Tech Maturity (low↔high) against Business Fundamentals (weak↔strong). **LOW tech maturity + HIGH fundamentals = the prime target** (broken tech, good business = cheap, fast value-add). HIGH tech + HIGH fundamentals = expensive, less headroom. LOW + LOW = pass/turnaround only.
 
**Scoring (this IS the Technology Uplift Opportunity dimension):** magnitude × feasibility × business quality of the gaps.
 
-----
 
### PHASE 9 — Synthesis, Scoring & Investment Memo Generation
 
Compute the composite score (below), assign a verdict, and generate the memo artifact. Use code execution for the scoring math and to render the memo; carry confidence labels into the output.
 
-----
 
## The Composite Scoring Model
 
Each dimension is scored 1–10 (with explicit rubric anchors), multiplied by weight, and summed to a 0–100 composite.
 
|#|Dimension                    |Weight (Platform preset)|What it measures                                          |Primary phases|
|-|-----------------------------|------------------------|----------------------------------------------------------|--------------|
|1|Market Attractiveness        |15%                     |Size, growth, fragmentation, defensibility                |5             |
|2|Business Model Quality       |15%                     |Revenue quality, recurring/ARR, pricing power, retention  |1,4,6         |
|3|Growth Trajectory            |12%                     |Headcount/hiring velocity, traffic trend, funding momentum|3,4,5         |
|4|Digital/Tech Maturity        |10%                     |Stack modernity, data/automation, security                |0,1,2         |
|5|Team Strength                |10%                     |Leadership pedigree, org depth, culture                   |3             |
|6|Financial Health Proxy       |13%                     |Scale, funding, runway, profitability signals             |4             |
|7|Risk Profile                 |10%                     |Litigation, compliance, concentration, key-person         |7             |
|8|Technology Uplift Opportunity|15%                     |Size & feasibility of tech/AI/automation value-add        |2,8           |
 
**Rubric anchors (example — Technology Uplift Opportunity):**
 
- 1–2: Already best-in-class tech; little to add.
- 3–4: Modern stack, marginal gains.
- 5–6: Some clear gaps (e.g., no marketing automation).
- 7–8: Multiple high-value gaps + strong business = strong thesis.
- 9–10: Pervasive tech neglect on top of an excellent, profitable business = ideal.
 
### Weighting Presets (rationale)
 
- **Acquisition / Platform target:** as above — balances fundamentals with uplift; Risk and Financial Health weighted higher because you’re buying control.
- **Growth Partnership:** raise Growth Trajectory (18%) and Technology Uplift (18%), lower Financial Health (8%) — you’re betting on trajectory, not buying the whole thing.
- **Services Client:** raise Technology Uplift (25%) and the Digital Maturity gap, lower Market/Financial — you just need a fixable problem and the ability to pay.
 
### The Key Insight (encoded in the verdict logic)
 
For a technology-focused firm, the highest-value quadrant is **low Digital/Tech Maturity (dim 4 low) + high Business Fundamentals (dims 1, 2, 6 high) + high Technology Uplift (dim 8 high)**. The scoring intentionally rewards this combination rather than penalizing low tech maturity outright.
 
### Verdict Taxonomy
 
|Composite + pattern                                         |Verdict                 |
|------------------------------------------------------------|------------------------|
|75+ with high uplift + strong fundamentals                  |**Platform Investment** |
|65–80, strong fit within a thesis, smaller                  |**Bolt-on / Add-on**    |
|60–75, high trajectory, minority/growth                     |**Growth Partnership**  |
|55–75, fixable tech gap + ability to pay, but not investable|**Services Opportunity**|
|45–65, weak now but salvageable                             |**Turnaround / Watch**  |
|<45 or fatal risk flags                                     |**Pass**                |
 
-----
 
## Output Artifacts: The Investment Memo Structure
 
1. **Executive Summary** — one paragraph + verdict + composite score + confidence caveat.
1. **Company Snapshot** — what they do, model, size estimate, founded, HQ, leadership (each field confidence-tagged).
1. **Scorecard Table** — 8 dimensions, score, weight, weighted contribution, composite, verdict.
1. **Dimension-by-Dimension Findings** — key evidence + confidence per dimension.
1. **Technology Uplift Roadmap** — Quick Wins (0–90 days: email auth, analytics, marketing automation, page speed) vs. Strategic Plays (data infrastructure, AI/automation, platform re-architecture).
1. **Deal Thesis** — why this fits; which quadrant; the value-creation angle.
1. **Risks & Red Flags** — with severity.
1. **Recommended Next Steps / Human Diligence Items** — what to verify with management/the data room (everything tagged Inferred/Speculative rises here).
 
-----
 
## Agent Implementation Guidance
 
### Workflow shape
 
- **Sequential with checkpoints, parallel within phases.** Phases 0–2 (infrastructure/site/stack) can run in parallel; Phases 3–7 as parallel research tracks; Phases 8–9 are synthesis gates that require prior outputs.
- **Confidence gating:** if a phase yields only Speculative data, flag it and continue; never block the whole run.
- **State object:** maintain a JSON company-analysis state that each phase appends to (findings + source + confidence), which Phase 9 consumes.
 
### Claude tool mapping
 
- **web_search** — company news, competitors, reviews, funding, leadership.
- **web_fetch** — homepage/subpages, sitemap, RDAP/DNS/crt.sh/SEC/CourtListener JSON endpoints, review pages.
- **code execution** — scoring math, revenue triangulation, DoH/crt.sh/SEC parsing, memo rendering, chart generation.
- **artifacts** — the final investment memo (and optionally an HTML scorecard).
 
### Portability to other frameworks
 
- **LangGraph:** each phase = a node; the state object = graph state; Phase 9 = a reducer.
- **CrewAI:** one agent per research track + a synthesis agent.
- **n8n:** HTTP Request nodes for the free APIs, a Function node for scoring, an LLM node for the memo.
- **OpenAI Agents:** tools = search/fetch/code; phases = handoffs.
 
### Data limitations & confidence (bake in)
 
- Traffic estimates are unreliable for SMBs; revenue is triangulated; WHOIS PII is redacted; tech fingerprinting misses hidden backends; review sites can be gamed. State these in every memo’s caveats.
 
### Ethical & legal guardrails
 
- **Public data only.** No scraping behind logins, no pretexting/fake accounts, no circumventing paywalls or auth. Respect robots.txt and platform ToS. Comply with fair use and honor API rate limits and required headers (e.g., the SEC User-Agent). GDPR: do not attempt to de-anonymize redacted registrant PII. Present all inferences as inferences.
 
### Mapping to a Claude Skill (SKILL.md)
 
A skill is a folder with a `SKILL.md` (YAML frontmatter: `name`, `description` — the description drives auto-invocation) plus optional `scripts/`, `references/`, `templates/`, `assets/`. Use progressive disclosure: keep SKILL.md lean (~1,500–2,000 words) and push detail to references, which load only when needed. Scripts run via bash without consuming context.
 
```
domain-to-diligence/
├── SKILL.md                      # workflow: the 10 phases + verdict logic (lean)
├── references/
│   ├── phase-playbooks.md        # detailed per-phase signal-interpretation guides
│   ├── data-sources.md           # exact API endpoints, headers, rate limits
│   └── scoring-rubrics.md        # 1-10 anchors per dimension + presets
├── scripts/
│   ├── domain_intel.py           # RDAP + DoH + crt.sh calls
│   ├── sec_lookup.py             # EDGAR submissions/facts (with UA header)
│   ├── score.py                  # composite scoring + verdict
│   └── render_memo.py            # memo/HTML generation
└── templates/
    └── investment_memo.md        # the 8-section memo template
```
 
SKILL.md frontmatter example: `description: Analyze a company from only its domain name and produce an investment-grade diligence memo with scores. Use when given a domain/website and asked to evaluate, screen, or diligence a company.`
 
-----
 
## The Quick-Run Version (15–30 min triage screen)
 
For fast PE sourcing triage before committing to the full deep-dive:
 
1. **RDAP + DNS + homepage fetch** (Phase 0–1 lite): age, stack sniff, positioning, copyright-year staleness.
1. **One tech-stack read** (Phase 2 lite): CMS, analytics present?, marketing automation present?, security headers.
1. **Careers page + LinkedIn headcount glance** (Phase 3 lite): growing? hiring tech roles?
1. **One reviews check + one news search** (Phase 6 lite): sentiment + any red flags.
1. **Rapid scorecard:** score just 4 dimensions — Business Model Quality, Growth Trajectory, Digital/Tech Maturity, Technology Uplift — and output a provisional verdict + a “worth a deep dive? Y/N.”
 
Output: a half-page triage card with provisional quadrant placement and the top 3 uplift hypotheses.
 
## Recommendations
 
1. **Build the quick-run screen first** and run it on 20–30 known companies to calibrate the rubric anchors before automating the full pipeline. Benchmark to advance: if the triage verdict agrees with a human analyst on ≥70% of a test set, proceed to the full build.
1. **Implement Phase 8 (tech gap) as the crown jewel** — it’s the differentiator versus generic tools like Grata/Harmonic, which score fit but not “what a tech investor could add.”
1. **Wrap every numeric output in a confidence band** and route all Inferred/Speculative items into the “human diligence” section — this protects credibility and defines the human handoff.
1. **Start with the free API tier** (SEC EDGAR, RDAP, DoH, crt.sh, CourtListener, Google News/GDELT, OpenCorporates open data) and only add paid data (Crunchbase, SimilarWeb, BuiltWith, PitchBook) once volume justifies it.
1. **Convert to a Claude Skill once the workflow is stable**, using the folder structure above, so it’s portable and reusable across the firm.
1. **Recalibrate quarterly** — API access changes fast (PatentsView went key-only in 2025 and is migrating to USPTO’s Open Data Portal; CourtListener tightened anonymous limits in 2026). Keep `references/data-sources.md` as the single source of truth.
 
## Caveats
 
- This is a public-signal screening tool, not a substitute for confirmatory diligence (data room, management calls, financial audit, legal/IP review). Its output is a prioritized hypothesis set, not a decision.
- Revenue/traffic/headcount figures are largely modeled or inferred and carry wide error bands, especially for SMBs and sub-100K-visit sites (where SimilarWeb error can exceed 70%).
- Review and social signals can be manipulated (over a quarter of recent G2 reviews are likely AI-generated); corroborate with unfiltered sources like Reddit.
- Free API access, keys, and rate limits shift frequently; the framework’s data-source layer must be actively maintained.
- The scoring weights are a starting template — calibrate them to the firm’s actual deal outcomes over time.
- One source correction to note for internal accuracy: Vista Consulting Group is documented at 100+ professionals (not 200+), per Umbrex; treat headcount figures for private operating groups as approximate.
