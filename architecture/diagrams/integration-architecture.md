# Integration Architecture — API‑Led + Event‑Driven 
This document describes the enterprise integration architecture using an API‑led approach combined with an event‑driven backbone. 
It ensures loose coupling, scalability, and consistent integration patterns across domains and systems.

```mermaid
flowchart LR
    A[Experience API] --> B[Process API]
    B --> C[System API - CRM]
    B --> D[System API - ERP]
    B --> E[System API - Payments]
