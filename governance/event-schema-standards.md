# 📘 Event Schema Standards & Registry Rules

A unified set of standards for defining, validating, publishing, and governing event schemas across the enterprise. Ensures consistency, interoperability, and long‑term maintainability for event‑driven systems.

---

# 🧭 1. Purpose & Scope

This guide defines:
- Event naming conventions  
- Schema structure and required fields  
- Versioning rules  
- Backward compatibility expectations  
- Registry publishing workflow  
- Validation and governance requirements  

Applies to:
- Domain events  
- Integration events  
- Platform events  
- Internal and external event producers  

---

# 🧱 2. Event Design Principles

### **1. Domain‑Driven**
Events represent meaningful business facts, not technical noise.

### **2. Immutable**
Events are append‑only and never updated or deleted.

### **3. Backward Compatible**
Consumers must not break when new fields are added.

### **4. Canonical**
Shared data fields follow enterprise canonical definitions.

### **5. Self‑Describing**
Events contain enough metadata for consumers to process them independently.

---

# 🧩 3. Event Naming Conventions

### **Event Names**
Use **PascalCase** and past tense:

OrderCreated
CustomerUpdated
InventoryReserved
PaymentFailed


### **Topic Naming**
Use **kebab‑case** with domain prefix:

<domain>.<event-name>.<version>


---

# 🧱 4. Event Schema Structure

All events must follow this structure:

```json
{
  "eventId": "uuid",
  "eventType": "OrderCreated",
  "eventVersion": "v1",
  "eventTimestamp": "2025-01-01T12:00:00Z",
  "source": "order-service",
  "data": {
    "...": "domain-specific fields"
  },
  "metadata": {
    "correlationId": "uuid",
    "traceId": "uuid"
  }
}
```
## Required Fields

- **eventId** — unique identifier  
- **eventType** — name of the event  
- **eventVersion** — semantic version  
- **eventTimestamp** — ISO‑8601 timestamp  
- **source** — producing service  
- **data** — domain payload  
- **metadata** — tracing and correlation  

---

## 🔢 5. Versioning Rules

### Non‑Breaking Changes (Minor)
Allowed without bumping major version:
- Adding new optional fields  
- Adding new metadata fields  
- Adding new event types  

### Breaking Changes (Major)
Require new major version:
- Removing fields  
- Changing field meaning  
- Changing data types  
- Renaming fields  
- Changing event structure  

### Version Format
v1
v2
v3


### Deprecation Policy
- Support at least **two active versions**  
- Provide **90‑day notice** before sunsetting  

---

## 🧪 6. Schema Validation Rules

All schemas must:
- Validate against JSON Schema  
- Include type definitions  
- Include required/optional field definitions  
- Include example payloads  
- Pass automated schema linting  
- Pass backward‑compatibility checks  

---

## 🏛️ 7. Event Registry Requirements

All events must be published to the **Enterprise Event Schema Registry**.

### Registry Stores
- JSON schema  
- Example payloads  
- Version history  
- Deprecation status  
- Producer service  
- Consumer list  

### Registry Rules
- No event may be published without schema validation  
- No breaking change may overwrite an existing version  
- All schemas must include documentation  
- All schemas must include examples  

---

## 🔄 8. Publishing Workflow

### Step 1 — Draft Schema
Producer defines:
- Event name  
- Topic name  
- Schema  
- Example payload  

### Step 2 — Automated Validation
Checks:
- JSON Schema validity  
- Naming conventions  
- Versioning rules  
- Backward compatibility  

### Step 3 — Architecture Review
Architecture validates:
- Domain alignment  
- Canonical model usage  
- Reuse opportunities  
- Governance compliance  

### Step 4 — Publish to Registry
Schema is:
- Added to registry  
- Version tagged  
- Documentation generated  

### Step 5 — Notify Consumers
- Slack/email notification  
- Changelog updated  
- Migration guidance (if applicable)  

---

## 📊 9. KPIs & Success Measures

### Schema Quality
- % of events with complete schemas  
- % passing backward‑compatibility checks  

### Reuse
- # of consumers per event  
- Reduction in duplicate event types  

### Performance
- Event propagation latency  
- Consumer lag metrics  

### Governance
- % of events registered  
- % of events with versioning compliance  

---

## 📄 10. Related Artifacts

- `/governance/api-standards-and-governance-guide.md`  
- `/architecture/reference-architectures/api-led-event-driven-multi-region.md`  
- `/governance/architecture-operating-model.md`  
- `/governance/adr-template.md`  

