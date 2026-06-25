# TERMS.md

Use this reference when creating or updating either:

- `docs/.zsen/TERMS.md`
- `docs/.zsen/domains/<domain-slug>/TERMS.md`

Use [artifact-boundaries.md](artifact-boundaries.md) to decide whether a term belongs globally or inside a domain.

## Criteria

Include only terms specific to the project's context.

Before adding a term, ask:

- Is this a concept unique to this system or domain?
- Is there competing language that should be normalized?
- Would future readers misunderstand the codebase without a canonical definition?

Do not include general programming concepts unless the project has given them domain-specific meaning.

## Template

```md
# {Context Domain Name or Global}

{One or two sentence description of what this context is, what it is not (if necessary), and why it exists.}

## Code Entry Point

{File path for the root module, entry page relative to the workspace root. If no code exist yet, use a placeholder note. Format as a bulleted list if there are multiple files.}

## TERMS

**Order**:
{A one or two sentence description of the term}
_Avoid_: Purchase, transaction

**Customer**:
A person or organization that places orders.
_Avoid_: Client, buyer, account
```

## Writing guidance

- Be opinionated. When multiple words exist for the same concept, pick the best one and list the others under _Avoid_.
- Keep definitions tight. One or two sentences max. Define what it IS, not what it does.
- Only include terms specific to this project's context. General programming concepts (timeouts, error types, utility patterns) don't belong even if the project uses them extensively. Before adding a term, ask: is this a concept unique to this context, or a general programming concept? Only the former belongs.
- Group terms under subheadings when natural clusters emerge. If all terms belong to a single cohesive area, a flat list is fine.
