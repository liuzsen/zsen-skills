# Artifact Boundaries

Use these rules to decide where information belongs.

## Global artifacts

### `docs/.zsen/TERMS.md`

Use for terms that are:

- Used across multiple domains
- Required to explain the system as a whole
- Foundational business or technical concepts that later domain docs rely on

Do not use for:

- Vocabulary meaningful only inside one domain
- Implementation jargon that has no project-specific meaning
- Domain-local aliases that would add noise globally

### `docs/.zsen/adr/*.md`

Use for decisions that are:

- System-wide in scope
- Shared by multiple domains
- About architecture, deployment, cross-domain integration, or ownership boundaries

Do not use for:

- Decisions local to one domain's workflow, model, or strategy
- Obvious choices with no real trade-off
- Reversible implementation details

## Domain-local artifacts

### `docs/.zsen/domains/<domain-slug>/TERMS.md`

Use for:

- Vocabulary local to one domain
- Synonyms that need to be disambiguated only within that domain
- Concepts that would distract from the system-wide glossary

### `docs/.zsen/domains/<domain-slug>/adr/*.md`

Use for:

- Decisions mostly local to one domain
- Trade-offs in a domain model, workflow, or boundary
- Domain-specific constraints that future readers would otherwise miss

## Promotion rule

When unsure, prefer domain-local artifacts.

Promote a term or decision to the global docs only when multiple domains genuinely depend on it.
