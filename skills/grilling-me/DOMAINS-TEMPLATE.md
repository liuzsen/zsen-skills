{Domains are split into technical (e.g., window managent, deployment, UI style) and business. Typically, a tech domain serves as the underlying infrastructure leveraged by all business domains. The distinction lies in the architectural perspective: horizontal vs. vertical. A tech domain cuts across almost all business domains and may lack project-specific terminology, which is to be expected since it may handle purely general programming concepts.}

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
