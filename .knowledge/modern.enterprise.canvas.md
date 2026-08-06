# Modern Enterprise Canvas

> A structured view of the modern enterprise through eight lenses: **People · Process · Information · Systems · Interfaces · Workflows · Databases · Platforms**

---

## Overview

The Modern Enterprise Canvas maps every dimension of an organisation onto a single coherent model. Each lens is a distinct concern; together they form a complete picture of how work gets done, how data flows, and how technology supports human outcomes.

---

## 1. Canvas at a Glance

```mermaid
graph TD
    subgraph Canvas["🗺️ Modern Enterprise Canvas"]
        PP[👥 People]
        PR[⚙️ Process]
        IN[📄 Information]
        SY[🖥️ Systems]
        IF[🔌 Interfaces]
        WF[🔄 Workflows]
        DB[🗄️ Databases]
        PL[🏗️ Platforms]
    end

    PP -->|execute| PR
    PR -->|generate & consume| IN
    IN -->|stored in| DB
    DB -->|accessed via| SY
    SY -->|exposed through| IF
    IF -->|orchestrated by| WF
    WF -->|runs on| PL
    PL -->|enables| PP
```

---

## 2. People

People are the primary actors — they set strategy, execute decisions, and collaborate across the enterprise.

```mermaid
graph LR
    subgraph People["👥 People"]
        direction TB
        E1[Executive / Leadership]
        E2[Product & Strategy]
        E3[Sales & GTM]
        E4[Marketing]
        E5[Engineering]
        E6[Data & Analytics]
        E7[Customer Success]
        E8[Operations]
    end

    E1 -->|directs| E2 & E3 & E4 & E8
    E2 -->|informs| E3 & E5
    E3 <-->|aligns with| E4
    E5 -->|builds for| E3 & E4 & E7
    E6 -->|supports| E1 & E2 & E3 & E4
    E7 -->|feeds insights to| E2 & E6
```

---

## 3. Process

Processes are the repeatable sequences of activities that convert inputs into outcomes.

```mermaid
flowchart LR
    subgraph Core_Processes["⚙️ Core Enterprise Processes"]
        direction LR
        C1([Lead Generation]) --> C2([Qualification])
        C2 --> C3([Discovery & Proposal])
        C3 --> C4([Negotiation & Close])
        C4 --> C5([Onboarding])
        C5 --> C6([Delivery & Success])
        C6 --> C7([Renewal / Expansion])
        C7 -->|loop| C1
    end

    subgraph Support_Processes["🔧 Support Processes"]
        S1([Finance & Billing])
        S2([HR & Talent])
        S3([IT & Security])
        S4([Legal & Compliance])
    end

    C4 --> S1
    C5 --> S3
    C1 --> S4
```

---

## 4. Information

Information is the lifeblood of the enterprise — it flows through every layer.

```mermaid
graph TD
    subgraph Information["📄 Information"]
        I1[Customer Data]
        I2[Product Data]
        I3[Market Intelligence]
        I4[Financial Data]
        I5[Operational Metrics]
        I6[Content Assets]
        I7[Compliance Records]
    end

    subgraph Producers["✏️ Producers"]
        PR1[CRM Events]
        PR2[Product Usage]
        PR3[External Feeds]
        PR4[ERP / Finance]
    end

    subgraph Consumers["👁️ Consumers"]
        CO1[Sales Team]
        CO2[Exec Dashboards]
        CO3[AI Agents]
        CO4[Customer Portal]
    end

    PR1 -->|generates| I1
    PR2 -->|generates| I2 & I5
    PR3 -->|generates| I3
    PR4 -->|generates| I4

    I1 & I2 & I3 -->|consumed by| CO1 & CO3
    I4 & I5 -->|consumed by| CO2
    I6 -->|served to| CO4
```

---

## 5. Systems

Systems are the applications and services that process, store, and transmit information.

```mermaid
graph LR
    subgraph Systems["🖥️ Systems"]
        SY1[CRM\nSalesforce / HubSpot]
        SY2[ERP\nSAP / NetSuite]
        SY3[Marketing Automation\nMarketo / HubSpot]
        SY4[Customer Support\nZendesk / Intercom]
        SY5[Product Analytics\nMixpanel / Amplitude]
        SY6[BI / Reporting\nLooker / Tableau]
        SY7[Communication\nSlack / Teams]
        SY8[Document Management\nConfluence / Notion]
        SY9[AI Fabric\nEnterprise Agents]
    end

    SY1 <-->|bi-directional sync| SY3
    SY1 <-->|deal data| SY2
    SY4 -->|usage signals| SY5
    SY5 -->|metrics| SY6
    SY1 & SY2 & SY3 & SY4 & SY5 -->|feeds| SY6
    SY9 -->|reads & writes| SY1 & SY3 & SY4 & SY8
    SY7 -->|notifications from| SY1 & SY4 & SY9
```

---

## 6. Interfaces

Interfaces are the surfaces through which people and systems interact.

```mermaid
graph TD
    subgraph Interfaces["🔌 Interfaces"]
        IF1[Web Application / SPA]
        IF2[Mobile App]
        IF3[REST / GraphQL API]
        IF4[CLI / Terminal]
        IF5[Chat / Conversational UI\nSlack Bot, Claude, etc.]
        IF6[Dashboard / BI Reports]
        IF7[Email / Notification]
        IF8[Webhook / Event Stream]
        IF9[MCP Tool Surface]
    end

    subgraph Users["👤 Users"]
        U1[Internal Employee]
        U2[External Customer]
        U3[Partner / Vendor]
        U4[AI Agent]
    end

    U1 --> IF1 & IF4 & IF5 & IF6
    U2 --> IF1 & IF2 & IF7
    U3 --> IF3 & IF7
    U4 --> IF3 & IF8 & IF9
```

---

## 7. Workflows

Workflows define how tasks, approvals, and automations move through the enterprise.

```mermaid
flowchart TD
    subgraph Trigger["🚀 Triggers"]
        T1[User Action]
        T2[Scheduled Job]
        T3[External Event / Webhook]
        T4[AI Agent Decision]
    end

    subgraph Workflow_Engine["🔄 Workflow Engine"]
        W1[Route & Assign]
        W2[Validate & Enrich]
        W3[Human Approval\nif required]
        W4[Execute Action]
        W5[Notify & Log]
    end

    subgraph Outcomes["✅ Outcomes"]
        O1[Record Updated]
        O2[Message Sent]
        O3[Report Generated]
        O4[Service Provisioned]
    end

    T1 & T2 & T3 & T4 --> W1
    W1 --> W2
    W2 -->|approval required?| W3
    W2 -->|auto-approve| W4
    W3 -->|approved| W4
    W4 --> W5
    W5 --> O1 & O2 & O3 & O4
```

---

## 8. Databases

Databases store and organise the information assets of the enterprise.

```mermaid
graph LR
    subgraph Databases["🗄️ Databases"]
        DB1[Relational DB\nPostgres / MySQL]
        DB2[Document Store\nMongoDB / Firestore]
        DB3[Data Warehouse\nSnowflake / BigQuery]
        DB4[Vector Database\nPinecone / Weaviate]
        DB5[Graph Database\nNeo4j / Amazon Neptune]
        DB6[Cache\nRedis / Memcached]
        DB7[Object / File Storage\nS3 / GCS]
        DB8[Search Index\nElasticsearch / OpenSearch]
    end

    DB1 -->|ETL / ELT| DB3
    DB2 -->|sync| DB3
    DB3 -->|embeddings pipeline| DB4
    DB5 -->|entity relationships| DB4
    DB6 -.->|caches reads from| DB1 & DB2
    DB7 -->|metadata index| DB8
    DB4 & DB5 -->|AI / agent context| DB3
```

---

## 9. Platforms

Platforms are the foundational infrastructure layers that all other components run on.

```mermaid
graph TD
    subgraph Platforms["🏗️ Platforms"]
        PL1[Cloud Provider\nAWS / GCP / Azure]
        PL2[Container Orchestration\nKubernetes / ECS]
        PL3[CI/CD\nGitHub Actions / CircleCI]
        PL4[Observability\nDatadog / Grafana / OTel]
        PL5[Identity & Access\nOkta / Auth0]
        PL6[Data Platform\nSnowflake / Databricks]
        PL7[AI / LLM Platform\nAnthropic / OpenAI / Bedrock]
        PL8[Integration / iPaaS\nMuleSoft / n8n / Zapier]
        PL9[Enterprise\nAgent Orchestration Layer]
    end

    PL1 -->|hosts| PL2 & PL6 & PL7
    PL2 -->|runs| PL3 & PL4 & PL9
    PL5 -->|secures| PL2 & PL6 & PL7 & PL9
    PL7 -->|powers| PL9
    PL8 -->|connects| PL9
    PL4 -->|monitors| PL2 & PL6 & PL7 & PL9
```

---

## 10. Full Enterprise Relationship Map

```mermaid
graph TD
    PP[👥 People]
    PR[⚙️ Process]
    IN[📄 Information]
    SY[🖥️ Systems]
    IF[🔌 Interfaces]
    WF[🔄 Workflows]
    DB[🗄️ Databases]
    PL[🏗️ Platforms]

    PP -->|"follow & improve"| PR
    PP -->|"create & consume"| IN
    PP -->|"operate"| SY
    PP -->|"interact through"| IF

    PR -->|"produces"| IN
    PR -->|"implemented in"| WF

    IN -->|"persisted in"| DB
    IN -->|"surfaced by"| IF

    SY -->|"query/write"| DB
    SY -->|"expose"| IF
    SY -->|"run on"| PL

    IF -->|"triggers"| WF
    IF -->|"runs on"| PL

    WF -->|"reads/writes"| DB
    WF -->|"runs on"| PL
    WF -->|"calls"| SY

    DB -->|"hosted on"| PL

    style PP fill:#4A90D9,color:#fff
    style PR fill:#7B68EE,color:#fff
    style IN fill:#50C878,color:#fff
    style SY fill:#FF7F50,color:#fff
    style IF fill:#FFD700,color:#333
    style WF fill:#DA70D6,color:#fff
    style DB fill:#20B2AA,color:#fff
    style PL fill:#708090,color:#fff
```

---

## Canvas Summary Table

| Dimension | Description | Key Examples |
|-----------|-------------|-------------|
| **People** | Human actors who drive and consume enterprise activity | Executives, Sales, Engineering, Ops |
| **Process** | Repeatable sequences converting inputs to outputs | Lead-to-Cash, Onboarding, Support |
| **Information** | Data and knowledge assets flowing through the enterprise | Customer data, metrics, content |
| **Systems** | Applications and services processing information | CRM, ERP, Marketing Automation |
| **Interfaces** | Surfaces where people and systems interact | Web app, API, Chat UI, MCP |
| **Workflows** | Automated or semi-automated task orchestration | Approval flows, integrations, triggers |
| **Databases** | Structured storage for all data assets | Relational, Vector, Graph, Warehouse |
| **Platforms** | Infrastructure layers hosting all capabilities | Cloud, Kubernetes, LLM, AI Fabric |
