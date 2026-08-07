# Arkitype
![Arkitype:The easiest way to train AI](./.knowledge/assets/arkitype.cover.1.png)
Arkitype organizes the durable context needed to build and operate a long-running system.

![Arkitype:The easiest way to train AI](./.knowledge/assets/arkitype.cover.2.png)
Arkitype is a systematic approach to building agents, agent fleets, and intelligent teams.

## Getting started

Open this repository in a Dev Container to get a ready-to-use environment with the [Claude Code](https://claude.com/claude-code) CLI preinstalled:

1. Install [VS Code](https://code.visualstudio.com/), the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers), and Docker.
2. Clone this repo and choose **Reopen in Container** when prompted.
3. Run `claude` in the terminal to start working with the prompts and skills in `.arkitype/` and `.claude/`.

The same `.devcontainer/devcontainer.json` also works in GitHub Codespaces, and can be reused in GitHub Actions runners via [`devcontainers/ci`](https://github.com/devcontainers/ci). See `.manage/2026.08.06.devcontainer.migration.plan.md` for the full migration plan.

## Use as a Claude Code plugin library

This repo is also a Claude Code plugin marketplace. From any Claude Code session:

```
/plugin marketplace add xingh/arkitype
/plugin install arkitype@arkitype
```

That installs the `arkitype` plugin: the `/arkitype:extract` codebase-extraction command, three skills (`rfp-proposal-responder`, `domain-to-diligence`, `opportunity-finder`), and three agents (`project-arkitekt`, `project-manager`, `project-cleaner`). See `plugins/arkitype/README.md` for details.

## Workspace layout

- `.knowledge/` contains enduring knowledge that can later feed a knowledge graph.
- `.arkitype/` contains the system architecture and related specifications.
- `.manage/` contains day-to-day project and process work. Date-prefixed items use the `YYYY.MM.DD` format.
- `.archive/` contains completed work in timestamped folders.

This structure separates lasting knowledge, architectural decisions, active operations, and completed work so that each remains easy to find over the lifetime of the system.


## See Tekt.md 
[Tekt.md](https://tekt.md) - Is built / generated using the Arkitype meta language. 
- [00-ARKITYPE](https://tekt.md/00-arkitype/) - The Arkitype can be configured at this level. What tools should this instance of Tekt have, can be defined here. 
- [01-INFRASTRUCTURE](https://tekt.md/01-infrastructure/) - Where and how to run this system. Changes to where it should run and how can be defined here. 
- [03-DATABASE](https://tekt.md/02-database/) - Where and how data should be managed, for processes. Any changes to the data layer, and how data is to be managed can be defined here. 
- [03-SOFTWARE](https://tekt.md/03-software/) - Where, how, and what processes are executed, when, for whom. Any changes to how workflows are managed, should be defined here. 
- [04-INTERFACE](https://tekt.md/04-interface/) - Where, how, and what type of interfaces for whom. 

