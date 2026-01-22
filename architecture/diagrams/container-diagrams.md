# 🧱 C4 Model — Container Diagrams  
*Level 2 view of the Enterprise Platform*

These diagrams show the main containers (APIs, services, data stores, event backbone, and external systems) and how they interact.

---

## 1. Enterprise Platform — Container Diagram

```mermaid
flowchart TB
    %% Users
    CUST([Customer])
    AGENT([Support Agent])
    PARTNER([Partner / External Client])

    %% Channels
    subgraph CH[Channels]
        WEB[Web App]
        MOB[Mobile App]
        PARTNERAPP[Partner Integration]
    end

    %% Experience Layer
    subgraph EXP[Experience APIs]
        EXP_API[Experience API Gateway]
    end

    %% Process Layer
    subgraph PROC[Process APIs]
        ORD_PROC[Order Process API]
        CUST_PROC[Customer Process API]
        INV_PROC[Inventory Process API]
        PAY_PROC[Payment Process API]
    end

    %% Domain Services
    subgraph DOM[Domain Services]
        ORD_SVC[Order Service]
        CUST_SVC[Customer Service]
        INV_SVC[Inventory Service]
        PAY_SVC[Payment Service]
    end

    %% Data Stores
    subgraph DATA[Data Stores]
        ORD_DB[(Order DB)]
        CUST_DB[(Customer DB)]
        INV_DB[(Inventory DB)]
        PAY_DB[(Payment DB)]
        LAKE[(Data Lakehouse)]
    end

    %% Event Backbone
    subgraph EVT[Event Backbone]
        BUS[Event Bus / Event Mesh]
    end

    %% External Systems
    CRM[(CRM System)]
    ERP[(ERP System)]
    PAYGATE[(Payment Gateway)]
    WMS[(Warehouse System)]

    %% Relationships
    CUST --> WEB
    CUST --> MOB
    AGENT --> WEB
    PARTNER --> PARTNERAPP

    WEB --> EXP_API
    MOB --> EXP_API
    PARTNERAPP --> EXP_API

    EXP_API --> ORD_PROC
    EXP_API --> CUST_PROC
    EXP_API --> INV_PROC
    EXP_API --> PAY_PROC

    ORD_PROC --> ORD_SVC
    CUST_PROC --> CUST_SVC
    INV_PROC --> INV_SVC
    PAY_PROC --> PAY_SVC

    ORD_SVC --> ORD_DB
    CUST_SVC --> CUST_DB
    INV_SVC --> INV_DB
    PAY_SVC --> PAY_DB

    ORD_SVC --> BUS
    CUST_SVC --> BUS
    INV_SVC --> BUS
    PAY_SVC --> BUS

    BUS --> ORD_SVC
    BUS --> CUST_SVC
    BUS --> INV_SVC
    BUS --> PAY_SVC

    CUST_SVC --> CRM
    ORD_SVC --> ERP
    INV_SVC --> ERP
    INV_SVC --> WMS
    PAY_SVC --> PAYGATE

    LAKE --- ORD_DB
    LAKE --- CUST_DB
    LAKE --- INV_DB
    LAKE --- PAY_DB
```

## 2. Order Domain — Container Diagram

```mermaid
flowchart TB
    %% Entry
    EXP_API[Experience API Gateway]

    %% Process API
    subgraph PROC[Order Process API]
        ORD_PROC[Order Process API]
    end

    %% Domain Service + DB + Outbox
    subgraph ORD_DOMAIN[Order Domain]
        ORD_SVC[Order Service]
        ORD_DB[(Order DB)]
        OUTBOX[(Outbox Table)]
    end

    %% Event Backbone
    subgraph EVT[Event Backbone]
        BUS[Event Bus]
    end

    %% External Systems
    ERP[(ERP System)]
    PAYGATE[(Payment Gateway)]
    INV_SVC[Inventory Service]

    %% Relationships
    EXP_API --> ORD_PROC
    ORD_PROC --> ORD_SVC

    ORD_SVC --> ORD_DB
    ORD_SVC --> OUTBOX

    OUTBOX --> BUS
    BUS --> INV_SVC
    BUS --> ERP

    ORD_SVC --> PAYGATE
```

## 3. Customer Domain — Container Diagram

```mermaid
flowchart TB
    EXP_API[Experience API Gateway]

    subgraph PROC[Customer Process API]
        CUST_PROC[Customer Process API]
    end

    subgraph CUST_DOMAIN[Customer Domain]
        CUST_SVC[Customer Service]
        CUST_DB[(Customer DB)]
    end

    subgraph EVT[Event Backbone]
        BUS[Event Bus]
    end

    CRM[(CRM System)]

    EXP_API --> CUST_PROC
    CUST_PROC --> CUST_SVC

    CUST_SVC --> CUST_DB
    CUST_SVC --> BUS
    BUS --> CRM
```

## 4. Inventory Domain — Container Diagram

```mermaid
flowchart TB
    EXP_API[Experience API Gateway]

    subgraph PROC[Inventory Process API]
        INV_PROC[Inventory Process API]
    end

    subgraph INV_DOMAIN[Inventory Domain]
        INV_SVC[Inventory Service]
        INV_DB[(Inventory DB)]
    end

    subgraph EVT[Event Backbone]
        BUS[Event Bus]
    end

    WMS[(Warehouse System)]
    ERP[(ERP System)]

    EXP_API --> INV_PROC
    INV_PROC --> INV_SVC

    INV_SVC --> INV_DB
    INV_SVC --> BUS
    INV_SVC --> WMS
    INV_SVC --> ERP

    BUS --> INV_SVC
```

## 5. Payments Domain — Container Diagram

```mermaid
flowchart TB
    EXP_API[Experience API Gateway]

    subgraph PROC[Payment Process API]
        PAY_PROC[Payment Process API]
    end

    subgraph PAY_DOMAIN[Payments Domain]
        PAY_SVC[Payment Service]
        PAY_DB[(Payment DB)]
    end

    subgraph EVT[Event Backbone]
        BUS[Event Bus]
    end

    PAYGATE[(Payment Gateway)]
    ERP[(ERP System)]

    EXP_API --> PAY_PROC
    PAY_PROC --> PAY_SVC

    PAY_SVC --> PAY_DB
    PAY_SVC --> BUS
    PAY_SVC --> PAYGATE
    PAY_SVC --> ERP

    BUS --> PAY_SVC
```

## 6. Related Artifacts
/architecture/diagrams/system-context.md

/architecture/diagrams/integration-sequence-diagrams.md

/architecture/integration-architecture.md

/events/event-naming-and-domain-modeling-guide.md

/governance/api-standards-and-governance-guide.md