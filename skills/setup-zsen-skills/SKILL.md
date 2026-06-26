---
name: setup-zsen-skills
description: Bootstrap a repo for zsen-skills. Use when Codex should initialize the canonical `docs/.zsen` tree from `$zsen-skills-spec`, establish the agent-doc rule, and then ask the user whether to continue into the time-consuming `/brownfield-onboarding` workflow.
disable-model-invocation: true
---

# Setup Zsen's Skills

This skill is a lightweight bootstrapper.

Treat `$zsen-skills-spec` as the source of truth for the zsen docs structure and artifact conventions.

Do not explore the codebase to infer domains, terms, ADRs, or overview content here. That work belongs to `/brownfield-onboarding`.

## Process

### 1. Initialize the zsen docs tree

Consult `$zsen-skills-spec` and create any missing parts of the canonical `docs/.zsen` tree.

For a fresh setup, initialize:

```text
docs/.zsen
├── OVERVIEW.md
├── DOMAINS.md
├── TERMS.md
├── adr
│   └── .keep
└── domains
    └── .keep
```

Create missing files as empty placeholders. Do not try to fill them here.

### 2. Establish the agent-doc rule

Pick the file to edit:

- If you're using `CLAUDE.md`, edit it
- If you're using `AGENTS.md`, edit it
- If neither exists, ask the user which one to create

Never create `AGENTS.md` when `CLAUDE.md` already exists, or vice versa.

If an `## Agent docs` block already exists in the chosen file, update it in place instead of appending a duplicate.

Use this block:

```md
## Agent docs

See `docs/.zsen/OVERVIEW.md` for the project overview, terms, and ADRs.
```

### 3. Offer brownfield onboarding

After bootstrap is complete, ask the user whether to continue with `/brownfield-onboarding`.

Be explicit that `/brownfield-onboarding` is time-consuming because it surveys the repo, fills `OVERVIEW.md`, confirms the domain map with the user, extracts domain-local terms and ADRs, and then rolls the shared understanding up into the global artifacts.

If the user says yes, proceed into `/brownfield-onboarding`.

If the user says no, stop after setup and tell them the repo is ready for onboarding later.

### 4. clean up

Clean up `.keep` files that are no longer needed after the `brownfield-onboarding` process.

## Done

Tell the user:

- The zsen docs tree is initialized
- Which agent file was updated or created
- Whether `/brownfield-onboarding` was deferred or approved as the next step
