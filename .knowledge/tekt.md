# TEKT — Technology Enterprise Knowledge Topology

> A living architecture diagram of the modern enterprise: **Agents · People · Tools · Roles · Processes · Graph · Framework · Platforms**

---

## Overview

The GTM Fabric enterprise operates as a *fleet of AI agents* orchestrated across three interoperability layers — **MCP** (Model Context Protocol), **ACP** (Agent Communication Protocol), and **A2A** (Agent-to-Agent) — to deliver intelligent services to end users (Claude, GPT, custom UIs, etc.).

Each agent is assigned a **Role**, equipped with **Tools**, guided by **Processes**, embedded in a **Graph** of knowledge, operates within a **Framework**, and runs on one or more **Platforms**.

---

## 1. Fleet Architecture — Agents, Protocols & End Users

```mermaid
graph TD
    subgraph End_Users["🧑‍💼 End Users / Consumers"]
        EU1[Claude]
        EU2[GPT / OpenAI]
        EU3[Custom UI / API]
        EU4[Human Operator]
    end

    subgraph Service_Layer["⚡ Service Layer"]
        MCP["MCP\nModel Context Protocol"]
        ACP["ACP\nAgent Communication Protocol"]
        A2A["A2A\nAgent-to-Agent"]
    end

    subgraph Agent_Fleet["🤖 Agent Fleet"]
        AG1[Research Agent]
        AG2[GTM Strategy Agent]
        AG3[Content Agent]
        AG4[Data Analysis Agent]
        AG5[Outreach Agent]
        AG6[Ops Orchestrator Agent]
        AG7[Knowledge Graph Agent]
        AG8[Skills Routing Agent]
    end

    EU1 & EU2 & EU3 & EU4 -->|requests| MCP
    MCP -->|dispatch| ACP
    ACP -->|peer coordination| A2A
    A2A -->|task execution| AG1 & AG2 & AG3 & AG4
    ACP -->|task execution| AG5 & AG6 & AG7 & AG8
```

---

## 2. Agents & People

```mermaid
graph LR
    subgraph People["👥 People"]
        P1[GTM Lead]
        P2[Sales Engineer]
        P3[Content Strategist]
        P4[Data Analyst]
        P5[Ops Manager]
    end

    subgraph Agents["🤖 Agents"]
        A1[Research Agent]
        A2[GTM Strategy Agent]
        A3[Content Agent]
        A4[Data Analysis Agent]
        A5[Outreach Agent]
        A6[Ops Orchestrator Agent]
    end

    P1 -->|directs| A2
    P2 -->|collaborates with| A1
    P3 -->|reviews output of| A3
    P4 -->|validates| A4
    P5 -->|monitors| A6

    A1 -->|feeds insights to| A2
    A2 -->|triggers| A3
    A3 -->|supports| A5
    A4 -->|reports to| P4
    A6 -->|coordinates| A1 & A2 & A3 & A4 & A5
```

---

## 3. Roles

```mermaid
graph TD
    subgraph Roles["🎭 Roles"]
        R1[Orchestrator]
        R2[Researcher]
        R3[Strategist]
        R4[Creator]
        R5[Analyst]
        R6[Executor]
        R7[Monitor]
    end

    R1 -->|assigns tasks to| R2 & R3 & R4 & R5 & R6
    R7 -->|observes| R1 & R2 & R3 & R4 & R5 & R6
    R5 -->|informs| R3
    R3 -->|guides| R4 & R6
```

---

## 4. Tools

```mermaid
graph LR
    subgraph Tools["🔧 Tools"]
        T1[Web Search]
        T2[CRM Integration]
        T3[Data Pipeline]
        T4[LLM API]
        T5[Knowledge Graph DB]
        T6[Email / Outreach Platform]
        T7[Analytics Dashboard]
        T8[Document Store]
        T9[Code Executor]
    end

    subgraph Agents["🤖 Agents"]
        AG1[Research Agent]
        AG2[GTM Strategy Agent]
        AG3[Content Agent]
        AG4[Data Analysis Agent]
        AG5[Outreach Agent]
    end

    AG1 --> T1 & T5 & T8
    AG2 --> T2 & T4 & T8
    AG3 --> T4 & T8
    AG4 --> T3 & T7 & T9
    AG5 --> T6 & T2
```

---

## 5. Processes

```mermaid
flowchart LR
    P1([Capture Signal]) --> P2([Research & Enrich])
    P2 --> P3([Analyse & Synthesise])
    P3 --> P4([Strategy & Planning])
    P4 --> P5([Content & Asset Creation])
    P5 --> P6([Outreach & Activation])
    P6 --> P7([Monitor & Measure])
    P7 -->|feedback loop| P1

    style P1 fill:#4A90D9,color:#fff
    style P7 fill:#7B68EE,color:#fff
```

---

## 6. Knowledge Graph

```mermaid
graph TD
    KG_CENTER((Knowledge\nGraph))

    KG_CENTER --- ENT1[Company]
    KG_CENTER --- ENT2[Contact / Person]
    KG_CENTER --- ENT3[Deal / Opportunity]
    KG_CENTER --- ENT4[Segment / ICP]
    KG_CENTER --- ENT5[Intent Signal]
    KG_CENTER --- ENT6[Content Asset]
    KG_CENTER --- ENT7[Campaign]

    ENT1 --- ENT2
    ENT2 --- ENT3
    ENT3 --- ENT4
    ENT4 --- ENT5
    ENT5 --- ENT7
    ENT7 --- ENT6
```

---

## 7. Framework

```mermaid
graph TD
    subgraph Framework["📐 GTM Fabric Framework"]
        F1[Identify\nICP & Signals]
        F2[Enrich\nData & Context]
        F3[Orchestrate\nAgent Workflows]
        F4[Execute\nOutreach & Content]
        F5[Measure\nOutcomes & KPIs]
        F6[Iterate\nFeedback & Learning]
    end

    F1 --> F2 --> F3 --> F4 --> F5 --> F6 --> F1
```

---

## 8. Platforms

```mermaid
graph LR
    subgraph Platforms["🏗️ Platforms"]
        PL1[Cloud Infra\nAWS / GCP / Azure]
        PL2[LLM Provider\nAnthropic / OpenAI]
        PL3[CRM\nSalesforce / HubSpot]
        PL4[Data Warehouse\nSnowflake / BigQuery]
        PL5[Vector DB\nPinecone / Weaviate]
        PL6[Messaging\nSlack / Email]
        PL7[Observability\nDatadog / Grafana]
        PL8[Workflow Engine\nTemporal / n8n]
    end

    subgraph Agents["🤖 Agents"]
        AG1[Research Agent]
        AG2[GTM Strategy Agent]
        AG3[Content Agent]
        AG4[Data Analysis Agent]
        AG5[Outreach Agent]
        AG6[Ops Orchestrator Agent]
    end

    AG1 & AG7[Knowledge Graph Agent] --> PL5
    AG2 --> PL3 & PL2
    AG3 --> PL2
    AG4 --> PL4
    AG5 --> PL6 & PL3
    AG6 --> PL8 & PL7
    PL1 -.->|hosts| PL2 & PL4 & PL5 & PL8
```

---

## 9. Skills Taxonomy

Skills are atomic capabilities that agents combine to fulfill Roles and execute Processes.

```mermaid
mindmap
  root((Skills))
    Research
      Web Search
      Document Retrieval
      Signal Detection
    Analysis
      Data Synthesis
      Segmentation
      Forecasting
    Strategy
      ICP Mapping
      Messaging Framework
      Competitive Intel
    Creation
      Copywriting
      Summarisation
      Personalisation
    Execution
      Email Sequencing
      CRM Updates
      Calendar Booking
    Orchestration
      Task Routing
      Agent Coordination
      Workflow Management
    Observation
      KPI Monitoring
      Anomaly Detection
      Reporting
```

---

## 10. End-to-End Service Flow

```mermaid
sequenceDiagram
    participant User as 🧑 End User (Claude / UI)
    participant MCP as MCP Gateway
    participant Orch as Orchestrator Agent
    participant Res as Research Agent
    participant Strat as Strategy Agent
    participant Exec as Execution Agent
    participant KB as Knowledge Graph

    User->>MCP: Submit intent / task
    MCP->>Orch: Route request
    Orch->>KB: Fetch relevant context
    KB-->>Orch: Context + entities
    Orch->>Res: Delegate research
    Res-->>Orch: Research results
    Orch->>Strat: Delegate strategy synthesis
    Strat-->>Orch: Strategy plan
    Orch->>Exec: Delegate execution
    Exec-->>Orch: Execution status
    Orch->>KB: Update graph with new data
    Orch-->>MCP: Return result
    MCP-->>User: Deliver output
```

---

## Glossary

| Term | Definition |
|------|-----------|
| **MCP** | Model Context Protocol — standard for tool-calling and context exchange between LLMs and servers |
| **ACP** | Agent Communication Protocol — standard for inter-agent messaging and task delegation |
| **A2A** | Agent-to-Agent — direct peer coordination between autonomous agents |
| **ICP** | Ideal Customer Profile |
| **KG** | Knowledge Graph — graph database of entities and relationships |
| **Skill** | An atomic capability (e.g., web search, CRM update) assignable to an agent |
| **Fleet** | A coordinated group of agents operating under shared orchestration |
