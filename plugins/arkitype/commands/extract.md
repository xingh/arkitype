---
description: Reverse-engineer the current codebase into a complete Arkitype file set (.arkitype/00-04 + agent.local.md) sufficient for another agent to regenerate the system
---

# Arkitype Extraction

You are an AI software agent with access to this repository's full source code. Your task is to reverse-engineer this codebase into a complete Arkitype file set: five markdown files that, when handed to another AI build agent with no access to this repository, are sufficient to regenerate the entire system — same schema, same components, same behavior.

Do not summarize the codebase. Specify it.

This process is a starting point, not a fixed script. It cannot know what tools you have. Your first job is to adapt it to yourself.

## Phase 0 — Capability Self-Assessment

Before touching the codebase, take inventory of your own environment and record it. Determine honestly:

- Which tools you have: file listing, search, file reads, shell execution, package installation, network access, ability to run the dev server, ability to run the database, ability to capture screenshots or render pages.
- Which of these instructions you can execute fully, which only partially, and which not at all.
- For each instruction you cannot execute, decide a compensation strategy. Examples: cannot run the site → derive interface behavior from source and templates, and say so; cannot connect to the live database → treat migrations as the schema of record; no network access → document third-party integrations from code and env references without verifying endpoints.

Then improve this process for your situation: where the method below assumes a capability you lack, substitute your compensation strategy; where you have capabilities beyond what is assumed (e.g., you can run tests, query the live DB, or diff against a deployed site), use them to raise the fidelity of the extraction and note that you did. You do not need permission to deviate — you need to record every deviation in `agent.local.md` so nothing is silently degraded.

The output of Phase 0 is the first draft of `.arkitype/agent.local.md` (specified below). Write it before extraction begins, and keep it updated as you work.

## Phase 1 — Exploration

Explore the repository exhaustively using whatever tools you confirmed in Phase 0. Read, at minimum: the package manifest and lockfile-declared framework versions, all infrastructure and deployment config (Dockerfiles, compose files, hosting config, CI), the full database schema (migrations, ORM models, or SQL), all environment variable references, every route or page, every shared component, all API handlers and server logic, and any seed or fixture data.

If your environment allows running the site and capturing screenshots, save key views (home, one listing page, one detail page) to `.arkitype/assets/` and reference them by filename in 04. If not, skip this entirely and record the gap in `agent.local.md` — the written specification must stand alone either way.

## Phase 2 — Output

Create the directory `.arkitype/` and populate the five specification files plus `agent.local.md`. Use markdown prose for explanation and fenced YAML codeblocks for all structured specification. YAML is the canonical format — a regenerating agent should be able to work from the codeblocks alone.

### `.arkitype/00-arkitype.md` — Identity & Site Profile

Everything specific to *this* site, and nothing architectural. Contains a single `SITE PROFILE` YAML block: site name, domain, tagline, purpose, audience, brand tokens (colors, fonts, logo reference), content domain and taxonomy values, external service endpoints, feature toggles, and any constellation membership (sibling sites, mothership/product role, cross-navigation targets). This is the only file that changes between sites built on the same architecture. If you find hardcoded values scattered through the codebase that belong here (site name in a header component, colors in CSS), lift them into the profile and note in 01–04 that they are consumed from the profile.

### `.arkitype/01-infrastructure.md` — Infrastructure

Runtime and hosting, specified generically. YAML blocks for: framework and version, package manager, build and start commands, hosting target, environment variables (names, purposes, example values — never real secrets), and both infrastructure modes where applicable: Mode A (local Docker Compose — include the full compose specification) and Mode B (existing hosted endpoints — include discovery/connection config). Include CI/deploy steps if present. Nothing site-specific: reference the SITE PROFILE for any per-site values.

### `.arkitype/02-database.md` — Database

The complete schema as YAML: every table/collection, every column with type, constraints, defaults, indexes, foreign keys, and enums. Include RLS policies or access rules if present. Include seed data: either the actual seed rows as YAML if small, or a precise description of seed shape and a representative sample if large. State explicitly that the schema is identical across all sites in the constellation and only row-level data differs. Name your schema source of record (live DB, migrations, or ORM models) per your Phase 0 assessment.

### `.arkitype/03-software.md` — Software

Server-side and application logic: API routes and handlers (path, method, input, output, behavior), data-fetching patterns, authentication/authorization flow, background jobs, ingestion pipelines, third-party integrations (name the service, the operations used, and where credentials come from), and business rules. Specify each as YAML with enough behavioral detail that an agent can reimplement it without seeing the original code. Capability toggles belong here: name each toggle, what it enables, and its default.

### `.arkitype/04-interface.md` — Interface

Every page and route: purpose, layout, data it displays, and interactions. Every shared component: name, props, behavior, and where it is used — including any `ConstellationGrid` or cross-site navigation component. Design system: spacing, typography scale, color usage (referencing profile tokens), responsive behavior. Reference `.arkitype/assets/` screenshots by filename where they exist; where behavior was derived from source without rendering, mark it `verified: static-analysis` rather than `verified: observed`.

### `.arkitype/agent.local.md` — Agent Capability Record

The handoff letter from you to the regenerating agent. This file is environment-local, not part of the portable 00–04 architecture, and is never assumed identical between sites or agents. It exists so the next agent knows what it is inheriting and what it may or may not have itself. YAML blocks for:

- `extracting_agent`: your identity/model, host tool (e.g., Claude Code, Cursor, Replit, Lovable), and date of extraction.
- `capabilities_used`: the tools you actually used, mapped to what each produced (e.g., shell → ran migrations to confirm schema; browser → captured assets).
- `capabilities_missing`: what you could not do, the compensation strategy used, and which files or sections are affected — with a confidence note per gap.
- `build_toolchain`: what appears to have been used to build the original site (framework, generators, AI build tools if evidenced, formatters, CI), so the regenerating agent knows the site's provenance.
- `regeneration_requirements`: the minimum capabilities the next agent needs to regenerate faithfully (e.g., can run Docker for Mode A, has network for Mode B, can execute SQL seeds), and graceful fallbacks for each if it lacks them.
- `verification_status`: which parts of the spec were observed running versus derived from static analysis.
- `readme_deviations`: every place you adapted this process in Phase 0, and why.

## Rules

1. Files 01–04 must contain nothing unique to this site. Anything site-specific goes in the SITE PROFILE in 00, and 01–04 consume it by reference. Test: could 01–04 be reused verbatim for a sibling site by swapping only 00? `agent.local.md` is exempt — it is local by design.
2. Prefer toggles over forks. If the codebase contains conditional capabilities, express them as named toggles in 03, not as alternative architectures.
3. Surface assumptions, don't resolve them silently. Where the codebase is ambiguous or a decision appears unmade (e.g., search backend, approval flow), record it in the relevant file under an `open_decisions` YAML key rather than inventing an answer.
4. Degrade loudly, never silently. Any capability gap that lowered extraction fidelity must appear in `agent.local.md` under `capabilities_missing`. A regenerating agent trusting an unmarked section must be safe in doing so.
5. No secrets. Environment variable names and shapes only.
6. Verify completeness before finishing: walk the repository tree once more and confirm every route, table, integration, and component appears somewhere in the five files, and that `agent.local.md` accounts for every deviation and gap. The regenerating agent has only these files — if it isn't written down, it doesn't exist.

When complete, list the files you created, summarize the open decisions you surfaced, and state your overall confidence in regeneration fidelity based on `verification_status`.
