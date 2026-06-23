{Domains are split into technical and business. Typically, a tech domain serves as the underlying infrastructure leveraged by all business domains. Consequently, it may lack project-specific terminology, which is to be expected since it may handle purely general programming concepts. If a domain has neither terms nor ADRs, it shouldn't exist.}

## Template

```md
## Domains

- Ordering: receives and tracks customer orders
- Billing: generates invoices and processes payments
- Fulfillment: manages warehouse picking and shipping

## Relationships

- **Ordering → Fulfillment**: Ordering emits `OrderPlaced` events; Fulfillment consumes them to start picking
- **Fulfillment → Billing**: Fulfillment emits `ShipmentDispatched` events; Billing consumes them to generate invoices
- **Ordering ↔ Billing**: Shared types for `CustomerId` and `Money`
```
