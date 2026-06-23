---
name: setup-zsen-skills
description: Configure this repo for the engineering skills — set up domain doc layout. Run once before first use of the other engineering skills.
disable-model-invocation: true
---

# Setup Zsen's Skills

This is a prompt-driven skill, not a deterministic script. Explore, present what you found, confirm with the user, then write.

## Process

### 1. Explore

Look at the current repo to understand its starting state. Read whatever exists;
don't assume:

- `AGENTS.md` and `CLAUDE.md` at the repo root — does either exist? Is there already an `## Agent docs` section in either?

### 2. Build doc tree

Create the following directory tree and initialize any missing files as empty:

```
- docs
  - OVERVIEW.md   // docs entry point
  - DOMAINS.md    // domain indexing and relationship
  - TERMS.md      // system-wide
  - ADR.md        // system-wide
  - terms         // create a file when a new domain(tech or business) is added
    - .keep        // keep the directory
  - adr
    - .keep         // keep the directory
```

### 3. Fill OVERVIEW

Draft the content for user's approval. Fill OVERVIEW.md based on OVERVIEW-TEMPLATE.md.

### 4. Write Agent rules

**Pick the file to edit:**

- If you are using `CLAUDE.md`, edit it.
- if you are using `AGENTS.md`, edit it.
- If neither exists, ask the user which one to create.

Never create `AGENTS.md` when `CLAUDE.md` already exists (or vice versa) — always edit the one you are using.

If an `## Agent docs` block already exists in the chosen file, update its contents in-place rather than appending a duplicate. Don't overwrite user edits to the surrounding sections.

The block:

```markdown
## Agent docs

See `docs/OVERVIEW.md` for a quick project overview.
```

### 5. Done

Tell the user the setup is complete.
