{A high-level overview of the app's functionality and target users in one or two sentences.}

## Tech Stack

{Group the stack by architectural role, such as frontend, backend, desktop shell, storage, infrastructure, or developer tooling. Under each group, list only the names of the core technologies that shape how the system is built or run. Do not add descriptions, qualifiers, paths, or explanatory text. This is for an AI agent that can figure out the use cases just from the names. Prefer concise grouped lists over an exhaustive dependency dump.}

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
