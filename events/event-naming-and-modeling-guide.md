# 🏷️ Event Naming & Domain Modeling Guide

A unified guide for naming events and modeling domains across the enterprise. Ensures consistency, clarity, and alignment with domain‑driven design (DDD) and event‑driven architecture (EDA) principles.

---

# 🧭 1. Purpose

This guide defines:
- How to name events consistently  
- How to model domains, aggregates, and entities  
- How to align events with domain boundaries  
- How to avoid anti‑patterns in event naming and modeling  

Applies to:
- Domain events  
- Integration events  
- Platform events  
- All domain‑aligned services  

---

# 🧱 2. Event Naming Principles

### **1. Use Business Language**
Events must reflect business terminology, not technical jargon.

### **2. Use Past Tense**
Events represent something that *already happened*.

Examples:
- OrderCreated  
- CustomerUpdated  
- PaymentAuthorized  

### **3. Use PascalCase**
Consistent formatting across all domains.

### **4. One Event = One Business Fact**
Avoid bundling multiple facts into a single event.

### **5. Avoid CRUD Names**
❌ CustomerInserted  
❌ OrderModified  
❌ ProductDeleted  

Use domain‑meaningful names instead:
✔️ CustomerRegistered  
✔️ OrderCancelled  
✔️ ProductDiscontinued  

---

# 🧩 3. Event Naming Structure

### **Format**
<Aggregate><Action><PastTense>


### **Examples**
- OrderCreated  
- InventoryReserved  
- CustomerEmailUpdated  
- PaymentFailed  

### **Anti‑Patterns**
❌ OrderEvent  
❌ CustomerNotification  
❌ DataChanged  

These provide no semantic meaning.

---

# 🏛️ 4. Domain Modeling Principles (DDD)

### **1. Identify Bounded Contexts**
Each domain has clear boundaries:
- Orders  
- Customers  
- Inventory  
- Payments  

### **2. Model Aggregates**
Aggregates enforce business invariants.

Examples:
- Order  
- Customer  
- Product  
- Invoice  

### **3. Entities vs Value Objects**
**Entities**  
- Have identity  
- Change over time  
- Example: Customer, Order, Payment  

**Value Objects**  
- No identity  
- Immutable  
- Example: Money, Address, SKU  

### **4. Ubiquitous Language**
Use the same terms across:
- APIs  
- Events  
- Documentation  
- Code  

---

# 🧩 5. Mapping Events to Domain Models

### **1. Events Belong to Aggregates**
Each event must map to a specific aggregate.

Example:
OrderCreated → Order aggregate
CustomerUpdated → Customer aggregate


### **2. Events Reflect State Transitions**
Events describe meaningful changes in aggregate state.

### **3. Events Should Not Expose Internal Details**
Avoid leaking internal implementation details.

---

# 🔄 6. Event Categories

### **Domain Events**
Represent business facts within a bounded context.
- OrderCreated  
- CustomerRegistered  

### **Integration Events**
Used for cross‑system synchronization.
- CustomerSyncedToCRM  
- InventoryAdjusted  

### **Platform Events**
Represent platform‑level activities.
- DeploymentCompleted  
- CacheInvalidated  

---

# 🧪 7. Event Modeling Checklist

- [ ] Event name uses business language  
- [ ] Event name uses past tense  
- [ ] Event belongs to a bounded context  
- [ ] Event maps to an aggregate  
- [ ] Event represents a single business fact  
- [ ] Event schema follows standards  
- [ ] Event does not expose internal details  
- [ ] Event is immutable  
- [ ] Event is backward compatible  

---

# 🧱 8. Domain Modeling Checklist

- [ ] Bounded contexts identified  
- [ ] Aggregates defined  
- [ ] Entities vs value objects clarified  
- [ ] Invariants documented  
- [ ] Ubiquitous language established  
- [ ] Domain events mapped to aggregates  
- [ ] Integration events separated from domain events  

---

# 📄 9. Examples

### **Order Domain**
**Aggregate:** Order  
**Events:**
- OrderCreated  
- OrderPaid  
- OrderShipped  
- OrderCancelled  

### **Customer Domain**
**Aggregate:** Customer  
**Events:**
- CustomerRegistered  
- CustomerEmailUpdated  
- CustomerDeactivated  

### **Inventory Domain**
**Aggregate:** InventoryItem  
**Events:**
- InventoryReserved  
- InventoryReleased  
- InventoryAdjusted  

---

# 📊 10. Anti‑Patterns to Avoid

### **1. Technical Event Names**
❌ RowInserted  
❌ TableUpdated  

### **2. Overloaded Events**
❌ OrderChanged (too vague)

### **3. Events That Don’t Represent Facts**
❌ OrderProcessingStarted (process, not fact)

### **4. Events That Represent Commands**
❌ CreateOrder  
❌ UpdateCustomer  

Commands ≠ Events.

---

# 📄 11. Related Artifacts

- `/events/event-catalog-template.md`  
- `/events/event-review-checklist.md`  
- `/governance/event-schema-standards.md`  
- `/governance/api-standards-and-governance-guide.md`  
- `/architecture/integration-architecture.md`  
