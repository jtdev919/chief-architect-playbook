# 📚 Event Catalog Template

A standardized template for documenting all enterprise events, including ownership, schema, versioning, consumers, and operational metadata.  
Use this template for every event published to the event backbone.

---

## 🏷️ Event Summary

**Event Name:**  
**Topic Name:**  
**Domain:**  
**Event Type:** (Domain / Integration / Platform)  
**Version:**  
**Owner (Team/Service):**  
**Status:** (Active / Deprecated / Draft)  

---

## 🧱 Event Purpose

**Description:**  
A concise explanation of what business fact this event represents and why it exists.

**When is it emitted:**  
Describe the business or system trigger.

**Why it matters:**  
Explain downstream impact, consumers, or business value.

---

## 🧩 Schema Definition

### **Schema (JSON Schema Reference)**  
_Link to schema in the Event Schema Registry_

### **Example Payload**
```json
{
  "eventId": "uuid",
  "eventType": "OrderCreated",
  "eventVersion": "v1",
  "eventTimestamp": "2025-01-01T12:00:00Z",
  "source": "order-service",
  "data": {
    "orderId": "12345",
    "customerId": "98765",
    "totalAmount": 199.99
  },
  "metadata": {
    "correlationId": "abc-123",
    "traceId": "xyz-789"
  }
}
```## 🔢 Versioning

**Current Version:**  
**Previous Versions:**  
**Deprecation Notes:**  

### Change History

| Version | Change Description | Date | Author |
|---------|--------------------|------|--------|
| v1      | Initial version    |      |        |

---

## 🔄 Event Semantics

### Event Meaning
Describe the business meaning of the event.

### Field Definitions

| Field          | Type   | Description               | Required |
|----------------|--------|---------------------------|----------|
| eventId        | string | Unique event identifier   | Yes      |
| eventTimestamp | string | ISO‑8601 timestamp        | Yes      |
| ...            | ...    | ...                       | ...      |

---

## 🧭 Producers

**Producer Service:**  
**Producer Domain:**  
**Emission Frequency:** (Real‑time / Batch / Scheduled)  
**Emission Pattern:** (Outbox / Direct Publish / CDC / Orchestration)  

---

## 🎯 Consumers

List all known consumers and their purpose.

| Consumer Service | Domain | Purpose | Notes |
|------------------|--------|---------|-------|
|                  |        |         |       |

---

## 🧪 Validation & Testing

### Contract Tests
- Link to consumer contract tests  
- Link to producer contract tests  

### Schema Validation
- JSON Schema validation status  
- Backward compatibility checks  

---

## 📊 Operational Metadata

### SLAs
- Delivery guarantee (At‑least‑once / Exactly‑once / Best‑effort)  
- Latency expectations  
- Retention period  

### Monitoring
- Dashboards  
- Alerts  
- Lag thresholds  

### Dead‑Letter Handling
- DLQ topic  
- Retry policy  

---

## 🔐 Security & Compliance

- Data classification (PII / PCI / Public / Internal)  
- Encryption requirements  
- Access control rules  
- Audit logging requirements  

---

## 📄 Related Artifacts

- Schema Registry Entry  
- API Standards & Governance Guide  
- Event Schema Standards & Registry Rules  
- Integration Architecture  
- ADRs related to this event  
