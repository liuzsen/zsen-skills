# TERMS.md Format

## TERMS.md Structure

```md
# {Context domain Name for Global}

{One or two sentence description of what this domain is and why it exists.}

## Code Entry Point

{File path of the code entry point (root module, index page). Do not include code snippets, as they go stale fast. Use a placeholder note if there's no code yet}

## Language

**Order**:
{A one or two sentence description of the term}
_Avoid_: Purchase, transaction

**Customer**:
A person or organization that places orders.
_Avoid_: Client, buyer, account
```

## Rules

- **Be opinionated.** When multiple words exist for the same concept, pick the best one and list the others under `_Avoid_`.
- **Keep definitions tight.** One or two sentences max. Define what it IS, not what it does.
- **Only include terms specific to this project's context.** General programming concepts (timeouts, error types, utility patterns) don't belong even if the project uses them extensively. Before adding a term, ask: is this a concept unique to this context, or a general programming concept? Only the former belongs.
- **Group terms under subheadings** when natural clusters emerge. If all terms belong to a single cohesive area, a flat list is fine.
