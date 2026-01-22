# 🧭 C4 Model — System Context Diagrams  
*Level 1 of the C4 Model for the Enterprise Platform*

This document provides System Context diagrams showing how users, external systems, and internal domains interact with the platform.

---

# 1. Enterprise Platform — System Context (C4 Level 1)

```mermaid
flowchart TB
    %% People
    U1([Customer])
    U2([Customer Support Agent])
    U3([Partner / External API Client])

    %% External Systems
    CRM[(CRM System)]
    ERP[(ERP System)]
    PAYGATE[(Payment Gateway)]
    WMS[(Warehouse Management System)]

    %% Platform
    subgraph PLATFORM[Enterprise Platform]
        EXP[Experience APIs]
        PROC[Process APIs]
        SYS[System APIs]
        DOMAINS[Domain Services]
        EVENTS[Event Backbone]
    end

    %% Relationships
    U1 --> EXP
    U2 --> EXP
    U3 --> EXP

    EXP --> PROC
    PROC --> SYS
    PROC --> DOMAINS
    DOMAINS --> EVENTS
    EVENTS --> DOMAINS

    SYS --> CRM
    SYS --> ERP
    SYS --> PAYGATE
    SYS --> WMS
```

# 2. Order Domain — System Context

```mermaid
flowchart TB
    %% Actors
    CUST([Customer])
    AGENT([Support Agent])

    %% External Systems
    ERP[(ERP System)]
    PAYGATE[(Payment Gateway)]
    WMS[(Warehouse System)]

    %% Order Domain
    subgraph ORDER[Order Domain]
        OAPI[Order Process API]
        OSVC[Order Service]
        OEVT[Order Events]
    end

    %% Relationships
    CUST --> OAPI
    AGENT --> OAPI

    OAPI --> OSVC
    OSVC --> OEVT

    OSVC --> PAYGATE
    OSVC --> ERP
    OEVT --> WMS
```

# 3.  Customer Domain — System Context

```mermaid
flowchart TB
    %% Actors
    USER([Customer])
    AGENT([Support Agent])

    %% External Systems
    CRM[(CRM System)]

    %% Customer Domain
    subgraph CUSTDOM[Customer Domain]
        CAPI[Customer Process API]
        CSVCS[Customer Service]
        CEVT[Customer Events]
    end

    %% Relationships
    USER --> CAPI
    AGENT --> CAPI

    CAPI --> CSVCS
    CSVCS --> CEVT
    CSVCS --> CRM
```

# 4. Inventory Domain — System Context

```mermaid
flowchart TB
    %% External Systems
    WMS[(Warehouse Management System)]
    ERP[(ERP System)]

    %% Inventory Domain
    subgraph INV[Inventory Domain]
        IAPI[Inventory Process API]
        ISVC[Inventory Service]
        IEVT[Inventory Events]
    end

    %% Relationships
    IAPI --> ISVC
    ISVC --> IEVT
    ISVC --> WMS
    ISVC --> ERP
```

# 5. Payments Domain — System Context

```mermaid
flowchart TB
    %% External Systems
    PAYGATE[(Payment Gateway)]
    ERP[(ERP System)]

    %% Payments Domain
    subgraph PAY[Payments Domain]
        PAPI[Payment Process API]
        PSVC[Payment Service]
        PEVT[Payment Events]
    end

    %% Relationships
    PAPI --> PSVC
    PSVC --> PEVT
    PSVC --> PAYGATE
    PSVC --> ERP
```

# 6. Related Artifacts
/architecture/integration-architecture.md

/architecture/diagrams/integration-sequence-diagrams.md

/events/event-naming-and-domain-modeling-guide.md

/governance/api-standards-and-governance-guide.md

/strategy/north-star-architecture.md
