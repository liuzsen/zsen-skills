# DOMAINS.md

Use this reference when creating or updating `docs/.zsen/DOMAINS.md`.

## Criteria

Record domains from the architectural perspective, not the folder tree.

Separate:

- Business domains: vertical slices with project-specific language and workflows
- Technical domains: horizontal capabilities that support many business domains

A domain is worth recording when it has at least one of:

- Distinct terminology
- Distinct responsibilities
- A meaningful ownership boundary
- A separate integration boundary
- A repeated workflow centered on a concept

Challenge candidate splits when two areas share the same language, invariants, and lifecycle.

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

## Writing guidance

- Keep each domain description short and concrete.
- Prefer ownership and information flow over package hierarchy.
- Add relationships only when they explain how the system hangs together.
