# C4 Diagram — Level 3: Component View (Order Service)  
This diagram shows the internal components of the Order Service.

```mermaid
C4Component
    title Order Service — Component View (L3)

    Container(orderSvc, "Order Service", "Microservice", "Handles order lifecycle")

    Component(apiController, "API Controller", "REST Controller", "Handles incoming API requests")
    Component(orderProcessor, "Order Processor", "Business Logic", "Validates and processes orders")
    Component(eventPublisher, "Event Publisher", "Messaging Adapter", "Publishes domain events")
    Component(repo, "Order Repository", "Database Access Layer", "Reads/writes order data")

    Rel(apiController, orderProcessor, "Invokes")
    Rel(orderProcessor, repo, "Reads/writes")
    Rel(orderProcessor, eventPublisher, "Emits events")