# Domain Model Diagram  
A domain-driven view of key business entities and relationships.

```mermaid
classDiagram
    class Order {
        +orderId
        +customerId
        +items
        +status
        +createdAt
    }

    class Customer {
        +customerId
        +name
        +email
        +preferences
    }

    class InventoryItem {
        +sku
        +quantityAvailable
        +location
    }

    Order --> Customer : belongs to
    Order --> InventoryItem : reserves