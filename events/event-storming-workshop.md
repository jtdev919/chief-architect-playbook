# 🟧 Event Storming Workshop Template

A structured template for running Event Storming sessions to discover domains, identify aggregates, define events, and map end‑to‑end business workflows.

---

# 🧭 1. Workshop Overview

**Workshop Name:**  
**Facilitator:**  
**Date:**  
**Participants (Domains + Roles):**  
**Scope / Problem Statement:**  

**Objectives:**
- Identify domain events  
- Map business workflows end‑to‑end  
- Discover bounded contexts  
- Identify aggregates, commands, and policies  
- Surface integration points and pain points  

---

# 🟧 2. Workshop Stages

## Stage 1 — Big Picture Event Storming
Goal: Capture all domain events across the workflow.

**Activities:**
- Brainstorm events using orange sticky notes  
- Place events on a timeline  
- Identify major business milestones  

**Outputs:**
- Initial event timeline  
- High‑level domain understanding  

---

## Stage 2 — Identify Commands (Blue Notes)
Goal: Understand what triggers each event.

**For each event:**
- What action caused this event?  
- Who or what initiated it?  

**Outputs:**
- Command → Event relationships  
- Clear understanding of triggers  

---

## Stage 3 — Identify Aggregates (Yellow Notes)
Goal: Group events around business entities that enforce invariants.

**Questions:**
- Which entity owns this event?  
- What business rules apply?  

**Outputs:**
- Aggregate list  
- Event‑to‑aggregate mapping  

---

## Stage 4 — Identify Policies (Purple Notes)
Goal: Capture business rules and reactions.

**Examples:**
- When OrderCreated → ReserveInventory  
- When PaymentFailed → CancelOrder  

**Outputs:**
- Policy list  
- Event‑driven reactions  

---

## Stage 5 — Identify Read Models / Queries (Green Notes)
Goal: Capture information needs.

**Examples:**
- “Show customer order history”  
- “Check inventory availability”  

**Outputs:**
- Read model list  
- Query requirements  

---

## Stage 6 — Identify External Systems (Pink Notes)
Goal: Surface integration points.

**Examples:**
- CRM  
- ERP  
- Payment gateway  
- Warehouse system  

**Outputs:**
- System interaction map  
- API + event integration points  

---

## Stage 7 — Identify Pain Points (Red Notes)
Goal: Capture bottlenecks, risks, and inefficiencies.

**Examples:**
- Manual approvals  
- Batch processes  
- Data inconsistencies  

**Outputs:**
- Pain point list  
- Opportunities for automation  

---

# 🧩 3. Event Storming Canvas

Use this structure during the workshop:

[Commands] → [Events] → [Aggregates] → [Policies] → [External Systems] → [Read Models]


---

# 🧱 4. Event Catalog Extraction

After the workshop, extract:

- Event names  
- Event definitions  
- Event producers  
- Event consumers  
- Event schemas  
- Event versions  
- Domain boundaries  

This feeds directly into the **Event Catalog** and **Event Schema Registry**.

---

# 🏛️ 5. Domain Modeling Outputs

From the workshop, document:

### **Bounded Contexts**
- Orders  
- Customers  
- Inventory  
- Payments  

### **Aggregates**
- Order  
- Customer  
- InventoryItem  
- Payment  

### **Commands**
- CreateOrder  
- UpdateCustomerEmail  
- ReserveInventory  

### **Events**
- OrderCreated  
- CustomerEmailUpdated  
- InventoryReserved  

---

# 🧪 6. Validation Checklist

- [ ] Events use business language  
- [ ] Events use past tense  
- [ ] Aggregates identified  
- [ ] Commands mapped to events  
- [ ] Policies documented  
- [ ] External systems identified  
- [ ] Pain points captured  
- [ ] Bounded contexts defined  
- [ ] Integration points documented  

---

# 📄 7. Related Artifacts

- `/events/event-catalog-template.md`  
- `/events/event-review-checklist.md`  
- `/governance/event-schema-standards.md`  
- `/architecture/integration-architecture.md`  
- `/architecture/reference-architectures/api-led-event-driven-multi-region.md`  
