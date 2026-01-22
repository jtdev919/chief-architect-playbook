# 📝 Event Review Checklist

A standardized checklist used during architecture reviews to ensure all events meet enterprise quality, governance, and interoperability requirements before being published to the event backbone.

---

## ✅ 1. Event Definition

- [ ] Event name follows naming conventions (PascalCase, past tense)  
- [ ] Topic name follows `<domain>.<event-name>.<version>` format  
- [ ] Event meaning is clearly defined  
- [ ] Event represents a true business fact (not a technical signal)  
- [ ] Event is immutable and append‑only  

---

## 🧱 2. Schema Quality

- [ ] JSON Schema provided  
- [ ] Schema includes required fields  
- [ ] Schema includes optional fields  
- [ ] Field types are correct and consistent  
- [ ] Canonical data model used where applicable  
- [ ] Example payload provided  
- [ ] Schema passes automated validation  
- [ ] Schema passes backward‑compatibility checks  

---

## 🔢 3. Versioning

- [ ] Version follows `v1`, `v2`, `v3` format  
- [ ] No breaking changes introduced without major version bump  
- [ ] Deprecation notes included (if applicable)  
- [ ] Previous versions documented  

---

## 🧩 4. Event Semantics

- [ ] Event meaning is clear and unambiguous  
- [ ] Field definitions documented  
- [ ] Required vs optional fields clearly identified  
- [ ] Metadata includes correlationId and traceId  
- [ ] Event timestamp uses ISO‑8601 format  

---

## 🧭 5. Producers

- [ ] Producer service identified  
- [ ] Producer domain identified  
- [ ] Emission pattern documented (Outbox / Direct Publish / CDC / Orchestration)  
- [ ] Emission frequency documented (Real‑time / Batch / Scheduled)  
- [ ] Producer contract tests provided  

---

## 🎯 6. Consumers

- [ ] Known consumers listed  
- [ ] Consumer purposes documented  
- [ ] Consumer contract tests provided  
- [ ] No consumer‑specific fields included in the event  

---

## 🔐 7. Security & Compliance

- [ ] Data classification documented (PII / PCI / Public / Internal)  
- [ ] Sensitive fields encrypted or tokenized  
- [ ] Access control rules defined  
- [ ] Audit logging requirements met  
- [ ] No prohibited data included  

---

## 📊 8. Operational Readiness

- [ ] Delivery guarantee defined (At‑least‑once / Exactly‑once / Best‑effort)  
- [ ] Retention period defined  
- [ ] Monitoring dashboards created  
- [ ] Alerts configured (lag, failures, DLQ)  
- [ ] DLQ topic defined  
- [ ] Retry policy documented  

---

## 🔄 9. Registry Requirements

- [ ] Schema published to Event Schema Registry  
- [ ] Version tagged  
- [ ] Documentation generated  
- [ ] Changelog updated  
- [ ] Consumers notified  

---

## 📄 10. Related Artifacts

- Event Schema  
- Example Payload  
- Producer Contract Tests  
- Consumer Contract Tests  
- ADRs related to this event  
- API Standards & Governance Guide  
- Event Schema Standards & Registry Rules  

