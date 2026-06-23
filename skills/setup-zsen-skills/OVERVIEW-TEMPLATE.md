{A high-level overview of the app's functionality and target users in one or two sentences.}

## Tech Stack

{Just a bulleted list of the main tech stack without descriptions. Anyone interested should already be familiar with their use cases. Group them by some criteria, like frontend, backend and dev-tools.}

## DOCS tree

References to `TERMS.md` can denote either the global terms `docs/TERMS.md` or any domain-specific terms file within the `docs/terms/` directory. The same logic applies to `ADR.md`

Fill out DOMAINS.md, TERMS.md and ADR.md incrementally as the project evolves.

```
- docs
  - OVERVIEW.md   // Current file. Read this first.
  - DOMAINS.md    // Domain index & relationships. Read next.
  - TERMS.md      // System-wide glossary. Reference frequently.
  - ADR.md        // System-wide Architecture Decision Recorde. Reference frequently.
  - terms         // Add a new <domain>.md here when introducing a domain.
    - windowing.md  // Tech domain example. Read on demand
    - billing.md    // Business domain example, Read on demand
  - adr
    - windowing     // List ADRs when working within a specific domain.
      - 001-<slug>.md   // Domain specific ADR. Read as needed
      - 002-<slug>.md
    - billing
      - 001-<slug>.md
      - 002-<slug>.md
```
