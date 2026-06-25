# Zsen Docs Tree

This is the canonical zsen docs layout for new repos.

```text
docs/.zsen
├── OVERVIEW.md
├── DOMAINS.md
├── TERMS.md
├── adr
│   ├── 0001-<slug>.md
│   └── 0002-<slug>.md
└── domains
    └── <domain-slug>
        ├── TERMS.md
        └── adr
            ├── 0001-<slug>.md
            └── 0002-<slug>.md
```

## Intent

- `OVERVIEW.md`: entry point for humans and agents
- `DOMAINS.md`: top-level map of business and technical domains plus their relationships
- `TERMS.md`: system-wide glossary only
- `adr/`: system-wide architecture decisions as numbered files
- `domains/<domain-slug>/TERMS.md`: domain-local glossary
- `domains/<domain-slug>/adr/`: domain-local decisions

## Notes

- Prefer numbered ADR files under `adr/` for new setups.
- Domain directories should be loaded on demand.
