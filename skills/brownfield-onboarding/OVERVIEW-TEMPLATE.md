{A high-level overview of the app's functionality and target users in one or two sentences.}

## Tech Stack

{Just a bulleted list of the main tech stack without descriptions. Anyone interested should already be familiar with their use cases. Group them by some criteria, like frontend, backend and dev-tools.}

## DOCS tree

References to `TERMS.md` can denote either the global terms `docs/.zsen/TERMS.md` or any domain-specific terms file `docs/.zsen/domains/<slug>/TERMS.md`. The same logic applies to `ADR.md`, but the file names are dynamic.

Fill out DOMAINS.md, TERMS.md and ADR.md incrementally as the project evolves.

```
- docs/.zsen
  - OVERVIEW.md   // Current file. Read this first.
  - DOMAINS.md    // Domain index & relationships. Read next.
  - TERMS.md      // System-wide glossary. Reference frequently.
  - adr           // System-wide Architecture Decision Recorde. Reference frequently.
    - 001-<slug>.md
    - 002-<slug>.md
  - domains       // Add a new directory here when introducing a domain.
    - <domain-slug>  // Artifacts within a domain should be loaded on demand
      - TERMS.md
      - adr
        - 001-<slug>.md
        - 002-<slug>.md
```
