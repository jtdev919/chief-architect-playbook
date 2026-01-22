# 🔄 Integration Sequence Diagrams  
*API + Event Workflows Across Domains*

This document provides sequence diagrams illustrating how APIs and events collaborate across domains to support key business workflows.

---

# 1. Order Creation (API Command → Event Publish)

A synchronous API call triggers a domain event using the Outbox Pattern.

```mermaid
sequenceDiagram
    autonumber
    participant C as Client
    participant EXP as Experience API
    participant PROC as Order Process API
    participant ORD as Order Service
    participant DB as Order DB + Outbox
    participant BUS as Event Bus
    participant INV as Inventory Service

    C->>EXP: POST /orders
    EXP->>PROC: CreateOrder()
    PROC->>ORD: createOrder()
    ORD->>DB: Write Order + Outbox(Event: OrderCreated)
    DB-->>ORD: Success
    ORD-->>PROC: Order Created
    PROC-->>EXP: 201 Created
    EXP-->>C: Order Confirmation

    Note over DB,BUS: Outbox Processor (async)
    DB->>BUS: Publish OrderCreated
    BUS->>INV: OrderCreated Event
    INV->>INV: Reserve Inventory
```

# 2. Inventory Reservation (Event → API Call)
A domain event triggers downstream API orchestration.

```mermaid
sequenceDiagram
    autonumber
    participant BUS as Event Bus
    participant INV as Inventory Service
    participant PROC as Shipping Process API
    participant SHIP as Shipping Service

    BUS->>INV: InventoryReserved Event
    INV->>PROC: POST /shipping/start
    PROC->>SHIP: initiateShipping()
    SHIP-->>PROC: Shipping Started
    PROC-->>INV: 202 Accepted
```

# 3. Payment Workflow (Fully Event‑Driven)
A chain of events drives the entire workflow without synchronous orchestration.

```mermaid
sequenceDiagram
    autonumber
    participant ORD as Order Service
    participant BUS as Event Bus
    participant PAY as Payment Service
    participant INV as Inventory Service
    participant SHIP as Shipping Service

    ORD->>BUS: OrderCreated
    BUS->>PAY: OrderCreated
    PAY->>BUS: PaymentAuthorized
    BUS->>INV: PaymentAuthorized
    INV->>BUS: InventoryReserved
    BUS->>SHIP: InventoryReserved
    SHIP->>BUS: ShipmentScheduled
    BUS->>ORD: ShipmentScheduled
    ORD->>ORD: Update Order Status
```
# 4.  Multi‑Region Failover (API + Events)
Illustrates how a global API gateway and replicated event backbone work together.

```mermaid
sequenceDiagram
    autonumber
    participant C as Client
    participant G as Global API Gateway
    participant R1 as Region A API
    participant R2 as Region B API
    participant BUS1 as Event Bus (Region A)
    participant BUS2 as Event Bus (Region B)

    C->>G: POST /orders
    G->>R1: Route to Region A
    R1->>BUS1: OrderCreated
    BUS1->>BUS2: Replicate Event
    BUS2->>R2: Update Read Models

    Note over G,R2: If Region A fails
    G->>R2: Route traffic to Region B
```

