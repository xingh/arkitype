# Arkitype

## The future will be spoken into existence. 

Having a standard vocabulary, if you are able to articulate what you need to be done and in which order, you have the ability to use code generators, autonomous agent technology to transform those words into software, agents, apps, and even companies. 

We seek to make the easiest way to do this, and by that means, a manner , a systematic approach that can be taught to anyone, anywhere, and with various levels of education. Getting someone to start building properly leads them to continue to build properly. With Agents, we can give people the starting point, and keep updating the standard. 

What does it mean for you as a user? There are different types of vocabulary / primitives / etc that will be published here, but they are not as important as understanding the purpose and flow of basic things. 

![Arkitype:The easiest way to train AI](./.knowledge/assets/arkitype.master.png)


### knowledge 

Knowledge is true and eternal. It is important to have in one place. This could be different things. It could be in different forms. As long as you can agree with team mates that Knowledge is what you all agree on, then AI can treat that as important. It can be technically true outside of time, but for us, it's important to distinguish principles in Knowledge, and process documentation i Knowledge, and how the principles are executed, and the data/information related to that execution. 

### arkitype 

Arkitype is the thing you are creating. It is how it is constituted. The layers and the overrides. The layers for now an be simply Interface, Software, Database, and Infrastructure, implemented in reverse order 01-Infrastructure, 02-Database, 03-Software, 04-Interface because that's how they are built on the Cloud. This could be your own terminology , but as long as you define them , the system should adhere to the spec defined by you. 00-Arkitype is the essence of how this software is configured for a specific purpose. 20 Systems could share the same system layer specs, but have differen 00-Arkitype documents that specify how that system operates. 

### manage

Manage is about about maintainin the history of what needs to be done. It could be to manipulate the Arkitye which gets regenerated the next time. It could also be to use the apparatus that the Arkitype has and execute processes. Whether or not you are using an external tracker, having the state of the task and project, available to everyone on your team and your AI is important to make sure people aren't stepping on each other's toes and are not repeating things. This is important for Humans and AI.

### archive

Archive is keeping a record of what's been done ( so that Manage is clean for operation), or irrelevant but useful to keep old Knowledge or Arkitypes. 


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

