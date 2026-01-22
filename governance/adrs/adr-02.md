# ADR 002 — Use Outbox Pattern for Reliable Event Publishing

**Status:** Accepted  
**Date:** 2026‑01‑22  
**Owner:** Platform Engineering  

---

## 1. Context

Services must publish events reliably without risking data inconsistency between the service database and the event bus. Direct publishing introduces race conditions and failure scenarios where:

- The DB write succeeds but event publish fails  
- The event publishes but the DB write fails  
- Retries cause duplicate events  

We need a consistent, repeatable pattern.

---

## 2. Decision

We will adopt the **Outbox Pattern** as the standard mechanism for event publishing across all domain services.

Events will be written to a local outbox table within the same transaction as the domain change, then asynchronously forwarded to the event bus.

---

## 3. Rationale

- Guarantees **atomicity** between DB write and event publish  
- Enables **idempotent** event delivery  
- Supports **event replay**  
- Works across all languages and frameworks  
- Aligns with multi‑region replication strategy  

---

## 4. Consequences

### Positive
- Eliminates dual‑write inconsistencies  
- Improves reliability and traceability  
- Simplifies consumer expectations  

### Negative
- Requires outbox processing infrastructure  
- Slight increase in storage and operational overhead  

---

## 5. Alternatives Considered

### 1. Direct Publish  
Rejected due to inconsistency risks.

### 2. Transactional Messaging (XA)  
Rejected due to complexity and lack of cloud support.

---

## 6. Related Artifacts

- Event Schema Standards  
- Integration Architecture  
- Multi‑Region Failover Playbook  
