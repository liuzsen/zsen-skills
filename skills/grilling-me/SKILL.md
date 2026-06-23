---
name: grilling-me
description: A relentless interview to sharpen a plan or design, which also creates docs (ADR's and glossary) as we go.
disable-model-invocation: true
---

Interview me relentlessly about every aspect of this plan until we reach a shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one-by-one. For each question, provide your recommended answer.

Ask the questions one at a time, waiting for feedback on each question before continuing. Asking multiple questions at once is bewildering.

If a question can be answered by exploring the codebase or docs, explore them instead.

## Domain Modeling

Actively build and sharpen the project's domain model as you design. This is the active discipline — challenging terms, inventing edge-case scenarios, and writing the glossary and decisions down the moment they crystallise.

## During the session

### Challenge against the glossary

When the user uses a term that conflicts with the existing language in TERMS.md, call it out immediately. "Your glossary defines 'cancellation' as X, but you seem to mean Y — which is it?"

### Sharpen fuzzy language

When the user uses vague or overloaded terms, propose a precise canonical term. "You're saying 'account' — do you mean the Customer or the User? Those are different things."

### Discuss concrete scenarios

When domain relationships are being discussed, stress-test them with specific scenarios. Invent scenarios that probe edge cases and force the user to be precise about the boundaries between concepts.

### Cross-reference with code

When the user states how something works, check whether the code agrees. If you find a contradiction, surface it: "Your code cancels entire Orders, but you just said partial cancellation is possible — which is right?"

### Update TERMS.md inline

When a term is resolved, update TERMS.md right there. Don't batch these up — capture them as they happen. Use the format in TERMS-FORMAT.md.

TERMS.md should be totally devoid of implementation details. Do not treat TERMS.md as a spec, a scratch pad, or a repository for implementation decisions. It is a glossary and nothing else.

### Update DOMAINS.md

Update DOMAINS.md whenever a domain is added or modified. Use the format in DOMAINS-TEMPLATE.md

## Offer ADRs sparingly

Only offer to create an ADR when all three are true:

1. Hard to reverse — the cost of changing your mind later is meaningful. If a decision is easy to reverse, skip it — you'll just reverse it.
2. Surprising without context — a future reader will wonder "why did they do it this way?". If it's not surprising, nobody will wonder why.
3. The result of a real trade-off — there were genuine alternatives and you picked one for specific reasons. If there was no real alternative, there's nothing to record beyond "we did the obvious thing."

If any of the three is missing, skip the ADR. Use the format in ADR-FORMAT.md.

### What qualifies

- **Architectural shape.** "We're using a monorepo." "The write model is event-sourced, the read model is projected into Postgres."
- **Integration patterns between contexts.** "Ordering and Billing communicate via domain events, not synchronous HTTP."
- **Technology choices that carry lock-in.** Database, message bus, auth provider, deployment target. Not every library — just the ones that would take a quarter to swap out.
- **Boundary and scope decisions.** "Customer data is owned by the Customer context; other contexts reference it by ID only." The explicit no-s are as valuable as the yes-s.
- **Deliberate deviations from the obvious path.** "We're using manual SQL instead of an ORM because X." Anything where a reasonable reader would assume the opposite. These stop the next engineer from "fixing" something that was deliberate.
- **Constraints not visible in the code.** "We can't use AWS because of compliance requirements." "Response times must be under 200ms because of the partner API contract."
- **Rejected alternatives when the rejection is non-obvious.** If you considered GraphQL and picked REST for subtle reasons, record it — otherwise someone will suggest GraphQL again in six months.
