# ADRs

Use this reference when creating or updating ADRs in either:

- `docs/.zsen/adr/`
- `docs/.zsen/domains/<domain-slug>/adr/`

Use [artifact-boundaries.md](artifact-boundaries.md) to decide whether a decision belongs globally or inside a domain.

## Criteria

Record an ADR only when all three are true:

1. Hard to reverse — the cost of changing your mind later is meaningful. If a decision is easy to reverse, skip it — you'll just reverse it.
2. Surprising without context — a future reader will wonder "why did they do it this way?". If it's not surprising, nobody will wonder why.
3. The result of a real trade-off — there were genuine alternatives and you picked one for specific reasons. If there was no real alternative, there's nothing to record beyond "we did the obvious thing."

Typical ADR-worthy topics:

- **Architectural shape.** "We're using a monorepo." "The write model is event-sourced, the read model is projected into Postgres."
- **Integration patterns between contexts.** "Ordering and Billing communicate via domain events, not synchronous HTTP."
- **Technology choices that carry lock-in.** Database, message bus, auth provider, deployment target. Not every library — just the ones that would take a quarter to swap out.
- **Boundary and scope decisions.** "Customer data is owned by the Customer context; other contexts reference it by ID only." The explicit no-s are as valuable as the yes-s.
- **Deliberate deviations from the obvious path.** "We're using manual SQL instead of an ORM because X." Anything where a reasonable reader would assume the opposite. These stop the next engineer from "fixing" something that was deliberate.
- **Constraints not visible in the code.** "We can't use AWS because of compliance requirements." "Response times must be under 200ms because of the partner API contract."
- **Rejected alternatives when the rejection is non-obvious.** If you considered GraphQL and picked REST for subtle reasons, record it — otherwise someone will suggest GraphQL again in six months.

## Numbering

- Prefer sequential numbering with four digits: `0001-slug.md`, `0002-slug.md`
- Scan the target `adr/` directory for the highest existing number and increment by one
- Keep global and each domain's numbering independent

## Template

```md
# {Short title of the decision}

{1-3 sentences: what's the context, what did we decide, and why.}
```

### Optional sections

Only include these when they add real value:

- `Status` frontmatter: `proposed | accepted | deprecated | superseded by ADR-NNNN`
- `Considered Options`
- `Consequences`
