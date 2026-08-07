# Arkitype Plugin

Arkitype workflows packaged as a Claude Code plugin. Install from the marketplace at the repo root:

```
/plugin marketplace add xingh/arkitype
/plugin install arkitype@arkitype
```

## What's inside

| Component | Name | What it does |
|---|---|---|
| Command | `/arkitype:extract` | Reverse-engineer the current codebase into the five-file Arkitype specification set (`.arkitype/00-04` + `agent.local.md`) |
| Skill | `rfp-proposal-responder` | Turn solicitation PDFs into a compliance checklist, full draft proposal, and cost/timeline estimate (state/local, federal, and nonprofit tracks) |
| Skill | `domain-to-diligence` | Analyze a company from its domain name into a scored, confidence-tagged investment memo with a PE-style verdict |
| Skill | `opportunity-finder` | Find, verify, score, and package grants/fellowships/awards, ending in shortlists and proposal handoff briefs |
| Agent | `project-arkitekt` | Initialize a project with the Arkitype folder structure and gather its specification |
| Agent | `project-manager` | Decompose complex tasks, delegate, and coordinate multi-step workflows |
| Agent | `project-cleaner` | End-of-session verification, commits, and archival of management files |

## Source of truth

The plugin content under `plugins/arkitype/` is the canonical, installable copy of each prompt. The documents in `.arkitype/` are the original method specifications and research the skills were distilled from — kept as source material, not loaded by the plugin. Skills are self-contained so they work in any project once the plugin is installed.
