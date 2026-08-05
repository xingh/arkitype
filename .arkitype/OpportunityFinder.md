You are Arkitype, an expert skill architect for research, grants, fellowships, and proposal development workflows.
Create a complete, reusable skill called:
Opportunity Finder: Grants, Fellowships, Awards, and Research Funding
The purpose of this skill is to help a user systematically find, evaluate, filter, prioritize, and package grant, fellowship, award, sponsorship, accelerator, prize, and research-funding opportunities so that a later workflow can generate strong proposals, letters of intent, concept notes, or full applications.
This skill should be designed for use by organizations like Intelcraft, Arkitekt, Anant, Tekt, or similar AI education, AI curriculum, AI governance, AI sovereignty, AI alignment, open-source, workforce-development, and public-interest technology initiatives.
The skill must be comprehensive, but it must not include executable scripts, shell commands, Python code, JavaScript, automation files, browser extensions, or platform-specific instructions. It must work equally well for Windows, macOS, Linux, web-only users, and non-technical users.
The final skill should contain only:
Markdown instructions
Research workflows
Source/reference lists
Templates
Rubrics
Scoring matrices
Prompt templates
Report formats
Decision checklists
Proposal handoff artifacts
Do not create scripts.
Do not assume any operating system.
Do not require local installation.
Do not require paid software, although you may list optional research databases as references.
Do not hardcode stale grant deadlines. Instead, instruct the user to verify all deadlines from primary sources.

Skill Objective
Build a skill that can help a researcher or grant strategist:
Find relevant funding opportunities quickly
Identify recurring and currently open opportunities
Compare grants, fellowships, awards, prizes, sponsorships, and contracts
Filter opportunities against an ideal grant profile
Filter opportunities against an ideal customer profile or beneficiary profile
Determine whether the opportunity supports curriculum development
Determine whether the opportunity supports AI alignment, AI safety, AI sovereignty, AI governance, AI literacy, or public-interest technology research
Prioritize opportunities based on fit, urgency, effort, and probability of success
Create an opportunity report that is useful to a proposal-writing workflow
Produce a proposal handoff brief with funder priorities, language, constraints, and recommended framing
The skill should work for both small quick-apply grants and larger strategic fellowships.
The skill should be optimized for speed and usefulness, not just exhaustive research.

Primary Use Cases
Design the skill around these use cases:
1. Fast Grant Search
The user wants to quickly find a list of relevant grants, fellowships, or awards that could fund a project.
Example:
“Find me grants that could support an AI education curriculum for professionals.”
2. Strategic Funding Landscape
The user wants a broad map of the funding landscape around a theme.
Example:
“Find the best funders for AI governance, AI sovereignty, and AI alignment research.”
3. Rapid Application Pipeline
The user wants opportunities that can be applied to quickly, regardless of size.
Example:
“Find quick grants under $25k that we can apply to this week.”
4. Fellowship Search
The user wants fellowships for individuals, researchers, educators, founders, technologists, or public-interest builders.
Example:
“Find fellowships that would support me building Intelcraft curriculum.”
5. Proposal Handoff
The user already has an opportunity and needs the next workflow to write a proposal.
Example:
“Create a proposal handoff brief for this grant.”
6. Ideal Grant Profile Filtering
The user wants only opportunities matching a specific profile.
Example:
“Only show grants that fund nonprofits, curriculum, AI literacy, and applied public-interest technology.”
7. Ideal Customer / Beneficiary Profile Filtering
The user wants to match grants based on who the project helps.
Example:
“Prioritize funders that care about workforce development for educators, small businesses, public-sector teams, or underserved communities.”

Skill Audience
The skill should support users such as:
AI education founders
Nonprofit leaders
Research program directors
Curriculum developers
Public-interest technologists
AI governance researchers
AI alignment researchers
Civic technology builders
Workforce development organizations
Open-source infrastructure teams
Universities and research labs
Independent researchers
Fellowship applicants
Grant writers
Proposal strategists
Community organizers
Professional service firms building public-good AI programs

Core Concepts the Skill Must Define
Include clear definitions for the following:
Opportunity
Any external source of support, including:
Grant
Fellowship
Award
Prize
Challenge
Sponsorship
Accelerator
Residency
Research program
Public-sector funding program
Philanthropic funding
University center funding
Foundation RFP
Government contract or cooperative agreement
Corporate social impact funding
Donor-advised funding pathway
Ideal Grant Profile
The profile of the best-fit funding opportunity.
It should include:
Eligible applicant type
Geography
Funding size
Project type
Topic area
Application effort
Deadline urgency
Reporting burden
Match requirement
Fiscal sponsor acceptability
Nonprofit requirement
Individual applicant acceptability
Indirect cost limitations
Allowed expenses
Disallowed expenses
Probability of success
Strategic relationship value
Proposal readiness
Ideal Customer Profile / Ideal Beneficiary Profile
The population, organization, or stakeholder the funded work is meant to serve.
It should include:
Target audience
Sector
Community type
Skill level
Geography
Institution type
Pain points
Outcomes desired
Equity or access considerations
Public benefit
Economic benefit
Educational benefit
Research benefit
Policy benefit
Funding Fit
A measure of whether the funder’s stated priorities align with the applicant’s project.
Application Readiness
A measure of whether the applicant can submit a strong application quickly.
Proposal Handoff
A structured brief that gives the next workflow enough context to write a tailored application.

Required Skill File Structure
Generate a clean markdown-only skill package with this structure:
opportunity-finder/
  SKILL.md
  references/
    funding-source-map.md
    grant-databases.md
    government-sources.md
    foundation-sources.md
    fellowship-sources.md
    ai-alignment-ai-governance-sources.md
    education-workforce-sources.md
    open-source-public-interest-tech-sources.md
    university-and-research-center-sources.md
    corporate-philanthropy-sources.md
    international-sources.md
  templates/
    opportunity-intake-template.md
    ideal-grant-profile-template.md
    ideal-customer-profile-template.md
    search-query-template.md
    opportunity-card-template.md
    opportunity-table-template.md
    grant-scorecard-template.md
    funding-landscape-report-template.md
    quick-apply-shortlist-template.md
    proposal-handoff-brief-template.md
    funder-language-extraction-template.md
    eligibility-checklist-template.md
    application-readiness-checklist-template.md
    source-verification-log-template.md
    no-fit-rejection-log-template.md
  rubrics/
    fit-scoring-rubric.md
    speed-to-apply-rubric.md
    strategic-value-rubric.md
    proposal-readiness-rubric.md
    funder-alignment-rubric.md
    ai-sovereignty-alignment-rubric.md
    curriculum-development-fit-rubric.md
  examples/
    example-intelcraft-ideal-grant-profile.md
    example-intelcraft-opportunity-report.md
    example-proposal-handoff-brief.md
The files should be written as plain markdown references and templates. No executable code.

SKILL.md Requirements
The SKILL.md file should include:
1. Skill Summary
Explain what the skill does in 3–5 sentences.
2. When to Use This Skill
List situations where the assistant should use this skill.
3. When Not to Use This Skill
Include cases such as:
User already has a specific grant and only needs proposal writing
User needs legal advice
User needs tax advice
User needs audited financial preparation
User needs guaranteed eligibility
User asks for fabricated funding sources
4. Inputs to Collect
The skill should ask for or infer:
Applicant name
Applicant type
Tax status
Fiscal sponsor status
Geography
Project name
Project description
Project stage
Funding need
Minimum useful grant size
Maximum application effort
Target deadline window
Topic areas
Target beneficiaries
Existing partners
Past funders
Budget readiness
Proposal materials already available
Restrictions or exclusions
Preferred funding sources
Whether government grants are acceptable
Whether individual fellowships are acceptable
Whether prizes/challenges are acceptable
Whether sponsorships are acceptable
Whether international opportunities are acceptable
5. Default Assumptions
If the user does not provide enough information, the skill should use sensible defaults:
Prioritize opportunities that are easier to apply to
Prioritize recurring opportunities with clear fit
Prioritize primary-source application pages
Prioritize funders that explicitly support education, research, public interest, civic technology, AI safety, AI governance, workforce development, or open-source infrastructure
Prefer opportunities with concept notes, letters of inquiry, rolling applications, short forms, nominations, or lightweight initial screens
Deprioritize grants with complex registrations unless strategically important
Deprioritize grants requiring years of audited financials unless the user says they are ready
Mark unknowns clearly rather than guessing
6. Research Workflow
Include a step-by-step workflow:
Step 1: Clarify Funding Thesis
Define the project in funder language.
For Intelcraft-like work, possible funding theses include:
AI literacy and workforce development
Public-interest AI education
AI curriculum for professionals
AI governance training
AI sovereignty and local AI capacity
AI alignment education
Responsible AI implementation
Civic AI infrastructure
Open-source AI tooling
Knowledge management for AI systems
Human-centered AI adoption
Community-based AI learning
AI for nonprofits and public-sector teams
AI safety and evaluation education
AI-enabled economic mobility
Step 2: Build the Ideal Grant Profile
Use the ideal grant profile template.
Step 3: Build the Ideal Customer / Beneficiary Profile
Use the ICP / beneficiary template.
Step 4: Generate Search Themes
Create search themes based on the funding thesis.
Examples:
AI education grants
AI literacy grants
Responsible AI fellowships
AI governance funding
AI alignment fellowships
AI safety grants
Public interest technology fellowships
Civic technology grants
Workforce development grants
Digital equity grants
Adult education innovation grants
Open-source sustainability grants
Research infrastructure grants
Democracy and technology grants
Technology and society fellowships
Future of work grants
STEM education grants
Nonprofit technology capacity grants
Community innovation funds
Government innovation grants
Step 5: Search Funding Sources
Search across:
Government grant portals
Foundation grant pages
Fellowship directories
University centers
Think tanks
Philanthropic programs
Public-interest technology networks
AI safety and governance organizations
Open-source funding programs
Corporate philanthropy programs
Challenge/prize platforms
Local and state funding sources
International funding sources where relevant
Step 6: Verify Each Opportunity
For each opportunity, verify from primary sources:
Current status
Deadline
Eligibility
Applicant type
Geography
Funding amount
Topic fit
Application process
Required documents
Reporting requirements
Contact information
Restrictions
Whether recurring
Step 7: Create Opportunity Cards
Each opportunity should have a card with:
Opportunity name
Funder
Category
Link
Status
Deadline
Funding amount
Eligible applicants
Target demographic
What the funder is looking for
Relevant project themes
Curriculum development fit
AI sovereignty / AI alignment / AI governance fit
Application complexity
Time-to-apply estimate
Strategic value
Risks or blockers
Recommended positioning
Next action
Step 8: Score and Rank
Score each opportunity using:
Mission fit
Eligibility fit
Topic fit
Beneficiary fit
Funding size
Speed to apply
Application complexity
Probability of success
Strategic value
Proposal readiness
Relationship value
Deadline urgency
Step 9: Produce Reports
The skill should support different report formats:
Quick-apply shortlist
Full opportunity landscape
Fellowship shortlist
Government grant shortlist
Foundation funder map
AI alignment / AI governance funder map
Curriculum development funder map
Proposal pipeline
30-day application plan
90-day funding strategy
Step 10: Produce Proposal Handoff Briefs
For each top opportunity, create a proposal handoff brief that includes:
Recommended project title
Funder priorities
Relevant language from funder
Applicant eligibility summary
Recommended project framing
Target beneficiaries
Outcomes to emphasize
Evidence needed
Budget framing
Partnerships to mention
Risks to address
Attachments required
Review criteria
Suggested proposal outline
Suggested next-step prompt for proposal drafting

Opportunity Categories
The skill should classify opportunities into categories:
Government
Examples:
Federal grants
State grants
Local grants
Cooperative agreements
Research agency grants
Workforce development grants
Education grants
Digital equity grants
Innovation grants
Philanthropic Foundations
Examples:
Private foundations
Family foundations
Community foundations
Donor-advised funds
Corporate foundations
Issue-specific grantmakers
Fellowships
Examples:
Individual fellowships
Founder fellowships
Research fellowships
Policy fellowships
Technology fellowships
Education fellowships
Civic innovation fellowships
AI Alignment / AI Safety / AI Governance
Examples:
AI safety research grants
Responsible AI programs
AI governance fellowships
Model evaluation funding
Public-interest AI programs
AI policy institutes
Technical alignment fellowships
AI security and sovereignty programs
Curriculum / Education / Workforce
Examples:
Curriculum development grants
STEM education grants
Adult learning grants
Workforce development funding
Digital literacy funding
Teacher training grants
Professional upskilling grants
Public Interest Technology
Examples:
Civic technology grants
Democracy and technology grants
Public-sector innovation
Nonprofit technology capacity
Open data
Digital public infrastructure
Human rights and technology
Open Source
Examples:
Open-source sustainability grants
Developer ecosystem grants
Public infrastructure funding
Research software funding
Community tooling grants
Corporate and Ecosystem Funding
Examples:
Cloud credits
Startup programs
Developer grants
Ecosystem funds
AI platform credits
Social impact sponsorships
Prizes and Challenges
Examples:
Innovation challenges
AI competitions
Civic innovation prizes
Education technology competitions
Public benefit technology prizes

Reference Source Requirements
Create reference files listing places to search. Each reference should include:
Name
Type
What it is useful for
Typical opportunity types
Best-fit themes
Notes on application complexity
Link placeholder
Verification reminder
Do not claim that any specific opportunity is currently open unless the user or research workflow verifies it from a current primary source.
Include references for:
Government Sources
Examples to include:
Grants.gov
SAM.gov
NSF
NIH
Department of Education
Department of Labor
Department of Commerce
NIST
NTIA
IMLS
NEH
NEA
SBA
State workforce agencies
State humanities councils
State arts councils
Local economic development agencies
Digital equity offices
National labs and research agencies
Foundation and Philanthropy Sources
Examples to include:
Candid
Foundation Directory
GrantStation
Instrumentl
GrantForward
Philanthropy News Digest
Inside Philanthropy
Community foundation directories
Issue-specific funder networks
Fellowship Sources
Examples to include:
ProFellow
Opportunity Desk
Fellowship search portals
University fellowship offices
Public-interest technology fellowship lists
AI safety and governance fellowship lists
Policy fellowship directories
Founder fellowship directories
AI / Technology / Public Interest Sources
Examples to include:
AI safety funding organizations
AI governance centers
Public-interest technology networks
Responsible technology funders
Digital democracy funders
Open-source foundations
Civic technology funders
University AI centers
Think tanks
Technology policy programs
Open Source Sources
Examples to include:
Open Collective
GitHub Sponsors
Sovereign Tech Fund
NLnet
Mozilla-related funding programs
Linux Foundation-related programs
Open-source ecosystem grants
Research software funding programs
Prize and Challenge Sources
Examples to include:
Challenge.gov
XPRIZE
MIT Solve
HeroX
Devpost
Kaggle competitions where relevant
Civic innovation challenge portals

Ideal Grant Profile Template
Create a template with these fields:
# Ideal Grant Profile

## Applicant

- Applicant name:
- Applicant type:
- Tax status:
- Fiscal sponsor available:
- Geography:
- Years operating:
- Existing funders:
- Existing partners:

## Project

- Project name:
- One-sentence description:
- Full description:
- Stage:
- Amount needed:
- Minimum useful grant size:
- Ideal grant size:
- Use of funds:
- Timeline:
- Existing materials:

## Topic Fit

Rate each 1–5:

- AI education:
- AI literacy:
- Curriculum development:
- Workforce development:
- AI governance:
- AI alignment:
- AI safety:
- AI sovereignty:
- Open-source AI:
- Civic technology:
- Public-sector innovation:
- Nonprofit capacity:
- Digital equity:
- Research:
- Community building:

## Applicant Eligibility Preferences

- Nonprofit-only acceptable?
- Individual fellowships acceptable?
- For-profit grants acceptable?
- Fiscal sponsor required?
- University partner required?
- Government grants acceptable?
- International grants acceptable?
- State/local grants acceptable?
- Corporate sponsorship acceptable?
- Prizes/challenges acceptable?

## Application Preferences

- Maximum time to apply:
- Deadline window:
- Rolling preferred:
- LOI preferred:
- Short form preferred:
- Full proposal acceptable:
- Budget required:
- Letters of support available:
- Audited financials available:
- Evaluation plan available:
- Prior results available:

## Exclusions

- Excluded funders:
- Excluded geographies:
- Excluded topics:
- Excluded application types:
- Ethical restrictions:

Ideal Customer / Beneficiary Profile Template
Create a template with these fields:
# Ideal Customer / Beneficiary Profile

## Beneficiary Overview

- Primary beneficiary:
- Secondary beneficiaries:
- Sector:
- Geography:
- Community type:
- Organization type:
- Skill level:
- Technology maturity:

## Pain Points

- What problem do they have?
- Why does it matter now?
- What happens if it is not solved?
- What systems are failing them?
- What knowledge or tools are missing?

## Desired Outcomes

- Learning outcomes:
- Workforce outcomes:
- Research outcomes:
- Governance outcomes:
- Community outcomes:
- Economic outcomes:
- Public benefit outcomes:

## Equity and Access

- Underserved groups:
- Access barriers:
- Affordability issues:
- Language or cultural barriers:
- Digital access barriers:
- Institutional barriers:

## Funder-Relevant Framing

- Why would a funder care?
- What public good is created?
- What evidence supports the need?
- What makes this scalable?
- What makes this replicable?
- What makes this urgent?

Opportunity Table Template
Create a reusable table with these columns:
| Rank | Opportunity | Funder | Type | Category | Status | Deadline | Amount | Eligible Applicants | Target Demographic | What They Fund | Curriculum Fit | AI Governance / Alignment / Sovereignty Fit | Application Effort | Time to Apply | Fit Score | Speed Score | Strategic Score | Recommended Next Step | Link |
|---|---|---|---|---|---|---|---|---|---|---|---:|---:|---|---|---:|---:|---:|---|---|

Opportunity Card Template
Create a detailed opportunity card:
# Opportunity Card

## Basic Information

- Opportunity:
- Funder:
- Program:
- Type:
- Category:
- Link:
- Status:
- Deadline:
- Recurring:
- Funding amount:
- Award duration:

## Eligibility

- Eligible applicant types:
- Geography:
- Tax status:
- Individual applicants allowed:
- Organizations allowed:
- Fiscal sponsor allowed:
- University partner required:
- Restrictions:

## Funder Priorities

- What the funder says they are looking for:
- Target demographic:
- Target outcomes:
- Preferred project types:
- Language to mirror:

## Fit Analysis

- Curriculum development fit:
- AI education fit:
- AI governance fit:
- AI alignment fit:
- AI sovereignty fit:
- Workforce development fit:
- Public-interest technology fit:
- Open-source fit:

## Application Analysis

- Application format:
- Required documents:
- Estimated time to apply:
- Complexity:
- Registration requirements:
- Budget required:
- Letters required:
- Reporting burden:
- Match required:

## Scoring

- Mission fit:
- Eligibility fit:
- Beneficiary fit:
- Topic fit:
- Funding size fit:
- Speed score:
- Probability score:
- Strategic value:
- Overall score:

## Recommendation

- Apply now / monitor / relationship-build / reject:
- Recommended positioning:
- Best project angle:
- Risks:
- Missing information:
- Next action:

Fit Scoring Rubric
Create a 100-point scoring rubric.
Suggested weights:
Mission fit: 20
Eligibility fit: 15
Topic fit: 15
Beneficiary fit: 10
Funding size fit: 10
Speed to apply: 10
Probability of success: 10
Strategic value: 10
Include scoring guidance:
90–100
Excellent fit. Apply immediately.
75–89
Strong fit. Apply if capacity exists.
60–74
Possible fit. Requires tailoring or partner.
40–59
Weak fit. Monitor or relationship-build.
Below 40
Reject for now.

Speed-to-Apply Rubric
Create a rubric with five levels:
Level 1: Same Day
Simple form
No budget or attachments
Short narrative
Rolling or immediate submission
Level 2: 1–3 Days
Short proposal
Basic budget
Organization information
Minimal attachments
Level 3: 1 Week
Full narrative
Budget
Work plan
Some supporting documents
Level 4: 2–4 Weeks
Complex application
Partner letters
Detailed budget
Evaluation plan
Registration requirements
Level 5: 1–3 Months
Major federal or institutional grant
Complex compliance
Multiple partners
Extensive documentation

AI Sovereignty / Alignment Fit Rubric
Create a rubric that evaluates whether a funder is likely to support AI sovereignty, AI alignment, AI safety, or AI governance work.
Score each 0–5:
Explicit AI governance language
Explicit AI safety or alignment language
Supports public-interest technology
Supports democratic technology governance
Supports local or community control of technology
Supports digital sovereignty or digital public infrastructure
Supports responsible innovation
Supports open-source infrastructure
Supports research, evaluation, or policy
Supports education or capacity-building around AI
Define interpretation:
40–50: Direct fit
30–39: Strong adjacent fit
20–29: Possible narrative fit
10–19: Weak fit
0–9: Not relevant

Curriculum Development Fit Rubric
Create a rubric that evaluates whether a funder is likely to support curriculum development.
Score each 0–5:
Explicitly funds curriculum
Funds education programs
Funds workforce development
Funds adult learning
Funds professional training
Funds teacher/facilitator training
Funds digital learning
Funds open educational resources
Funds community learning
Funds evaluation of learning outcomes
Define interpretation:
40–50: Direct curriculum funder
30–39: Strong education fit
20–29: Possible training fit
10–19: Weak fit
0–9: Not relevant

Proposal Handoff Brief Template
Create a template that the opportunity finder produces for the proposal-writing workflow.
# Proposal Handoff Brief

## Opportunity Summary

- Opportunity:
- Funder:
- Program:
- Deadline:
- Link:
- Funding amount:
- Applicant:
- Recommended apply / no-apply decision:

## Strategic Recommendation

- Recommended project title:
- Recommended project framing:
- Best-fit funding thesis:
- Why this funder is a fit:
- Why this applicant is credible:
- Why now:

## Funder Priorities

- Stated priorities:
- Target demographic:
- Review criteria:
- Keywords to mirror:
- Phrases to avoid:
- Evidence the funder expects:

## Project Alignment

- Relevant applicant work:
- Relevant project components:
- Relevant beneficiaries:
- Relevant outcomes:
- Relevant partners:
- Relevant prior proof:

## Proposal Narrative Direction

- Core problem:
- Proposed solution:
- Main activities:
- Expected outputs:
- Expected outcomes:
- Evaluation approach:
- Sustainability:
- Scalability:
- Equity / access framing:
- AI responsibility / governance framing:

## Budget Direction

- Recommended request amount:
- Eligible costs:
- Costs to avoid:
- Budget categories:
- Match requirement:
- Indirect cost notes:

## Required Materials

- Narrative:
- Budget:
- Work plan:
- Timeline:
- Letters of support:
- Organizational documents:
- Financial documents:
- Attachments:
- Registration requirements:

## Risks and Gaps

- Eligibility concerns:
- Missing documents:
- Weaknesses:
- Questions to resolve:
- Compliance issues:
- Deadline risk:

## Drafting Instructions for Proposal Workflow

Use this opportunity brief to draft a tailored proposal. Mirror the funder’s language. Emphasize the applicant’s strongest fit with the stated priorities. Do not invent facts, partners, outcomes, or financial details. Clearly mark assumptions and placeholders.

Quick-Apply Shortlist Template
Create a template for opportunities that can be applied to quickly.
# Quick-Apply Grant and Fellowship Shortlist

## Search Parameters

- Applicant:
- Project:
- Target themes:
- Geography:
- Minimum funding:
- Maximum application effort:
- Deadline window:
- Search date:

## Top Opportunities

| Rank | Opportunity | Funder | Amount | Deadline | Why It Fits | Time to Apply | Required Materials | Recommended Action |
|---|---|---:|---|---|---|---|---|

## Apply First

1. 
2. 
3. 

## Monitor

1. 
2. 
3. 

## Reject

1. 
2. 
3. 

## Notes

- Best immediate opportunity:
- Best strategic opportunity:
- Best fellowship:
- Best curriculum opportunity:
- Best AI governance / sovereignty opportunity:
- Biggest missing document:
- Recommended next action:

Funding Landscape Report Template
Create a long-form report template:
# Funding Landscape Report

## Executive Summary

## Applicant and Project Context

## Ideal Grant Profile

## Ideal Beneficiary Profile

## Search Method

## Funding Themes

## Top 25 Opportunities

## Quick-Apply Opportunities

## Strategic Opportunities

## Fellowship Opportunities

## Government Opportunities

## Foundation Opportunities

## AI Governance / Alignment / Sovereignty Opportunities

## Curriculum Development Opportunities

## Open-Source / Public-Interest Technology Opportunities

## Rejected or Low-Fit Opportunities

## Recommended 30-Day Action Plan

## Recommended 90-Day Funding Strategy

## Proposal Pipeline

## Source Verification Log

## Open Questions

Search Query Template
Create a template that helps the user generate better search queries.
Include query patterns such as:
"[topic]" "grant" "[geography]"
"[topic]" "fellowship" "application"
"[topic]" "request for proposals"
"[topic]" "funding opportunity"
"[topic]" "foundation" "grant"
"[beneficiary]" "workforce development grant"
"[topic]" "curriculum development" "grant"
"[topic]" "public interest technology" "fellowship"
"[topic]" "AI governance" "funding"
"[topic]" "AI safety" "grant"
"[topic]" "open source" "funding"
"[topic]" "digital equity" "grant"
"[topic]" "responsible AI" "fellowship"
Include guidance to search combinations of:
Topic
Beneficiary
Geography
Applicant type
Funding type
Deadline terms
Funder language
Policy language
Education language
Research language

Source Verification Log Template
Create a source verification log:
# Source Verification Log

| Opportunity | Primary Source Link | Date Checked | Deadline Verified | Eligibility Verified | Amount Verified | Notes | Confidence |
|---|---|---|---|---|---|---|---|
The skill should require the assistant to distinguish:
Verified from primary source
Verified from secondary source
Unverified
Stale / needs checking
Not enough information

No-Fit Rejection Log
Create a template for rejected opportunities:
# No-Fit Rejection Log

| Opportunity | Funder | Reason Rejected | Could Become Relevant If | Monitor? | Notes |
|---|---|---|---|---|---|
Common rejection reasons:
Applicant ineligible
Geography mismatch
Topic mismatch
Deadline passed
Too complex
Funding too small for effort
Requires university partner
Requires 501(c)(3)
Requires audited financials
Does not fund curriculum
Does not fund research
Does not fund AI or technology
Invitation only
Relationship required
Ethical mismatch

Assistant Behavior Guidelines
The skill should instruct the assistant to:
Prefer primary sources
Cite or link every opportunity
Never fabricate deadlines
Never assume eligibility if unclear
Mark uncertainty clearly
Separate verified facts from strategic interpretation
Avoid overfitting to buzzwords
Translate the user’s project into funder language
Prioritize speed when the user asks for quick-apply opportunities
Prioritize strategic fit when the user asks for a funding landscape
Include rejected opportunities when useful
Create proposal handoff briefs for top-ranked opportunities
Always preserve the user’s strategic constraints
Always identify the next best action

Intelcraft Example Profile
Create an example ideal grant profile for Intelcraft.
Use this project context:
Intelcraft is an AI education and enablement initiative focused on helping professionals, organizations, nonprofits, public-sector teams, and communities understand and use AI responsibly. It develops curriculum, workshops, study halls, office hours, knowledge bases, and practical AI workflows. It may also support research and public-interest work around AI sovereignty, AI alignment, AI governance, local AI capacity, knowledge management, open-source AI tools, and human-centered AI adoption.
Potential funder framings:
AI literacy for professionals
Responsible AI workforce development
Public-interest AI education
Community AI capacity building
AI governance education
AI sovereignty and local control of AI systems
Applied AI alignment education
Human-centered AI implementation
Open-source AI knowledge infrastructure
Digital public infrastructure for AI learning
AI upskilling for nonprofits and public-sector teams
Potential beneficiaries:
Nonprofit staff
Public-sector teams
Small business operators
Professional service providers
Educators
Workforce development organizations
Community leaders
Civic technologists
Independent researchers
AI practitioners
Students and adult learners
Potential funded activities:
Curriculum development
Workshops
Training cohorts
Learning materials
Open educational resources
Community study halls
AI governance playbooks
Responsible AI implementation guides
AI tool evaluations
Research briefs
Knowledge base development
Open-source reference architectures
Local AI readiness assessments
Fellowship-supported writing or research

Final Output Requirements
The final response should produce the complete markdown skill package content.
It should not create scripts.
It should not create executable code.
It should not rely on any operating-system-specific behavior.
It should include all files listed in the file structure.
It should make each file useful as a standalone markdown artifact.
It should be practical enough that another AI workflow can use the opportunity report and proposal handoff brief to write grant proposals.
End the skill with a short “Operational Checklist” that tells the user how to use the skill:
Fill out the ideal grant profile
Fill out the ideal customer / beneficiary profile
Run the opportunity search
Verify primary sources
Score and rank opportunities
Create a quick-apply shortlist
Create proposal handoff briefs for the top opportunities
Pass the handoff brief into the proposal-writing workflow

