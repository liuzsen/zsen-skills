---
name: brownfield-onboarding
description: Onboard into an existing codebase by surveying code and docs, filling `OVERVIEW.md`, confirming the domain map with the user, extracting domain-local terms and ADRs, then filling the global zsen artifacts.
disable-model-invocation: true
---

# Brownfield Onboarding

Start from the repository, not from assumptions. Read code, docs, config, tests, and commit-visible structure first. Ask the user only the questions that remain ambiguous after exploration.

This skill is about workflow, not artifact policy. Use `/zsen-skills-spec` as the canonical reference for:

- The `docs/.zsen` directory tree
- What belongs in global vs domain-local artifacts
- `DOMAINS.md` criteria and template
- `TERMS.md` criteria and template
- ADR criteria, numbering, and template

## Goals

Produce a compact onboarding pass that answers:

- What is this project, who is it for, and what is its high-level shape?
- What domains exist here?
- What terms and decisions belong inside each domain?
- What terms and decisions should be promoted into the global artifacts?
- What is still unclear and requires human confirmation?

## Working stance

- Prefer observation over invention.
- Treat code as the strongest signal of current reality.
- Treat docs as intent unless the code contradicts them.
- Surface contradictions immediately.
- Ask one question at a time, and only after doing the local reading that could have answered it.
- For each user question, provide your recommended answer based on the evidence you found.
- Keep the human in the loop while defining the domain map, then continue autonomously through domain-local extraction and global roll-up.
- When writing or classifying artifacts, defer to `/zsen-skills-spec`.
- Update artifacts incrementally as understanding hardens, but keep the workflow order straight: confirm the domain map first, extract domain-local artifacts second, and fill the global roll-up last.

## Process

### 1. Survey the repo

Find the project entry points and map the major evidence sources before asking anything:

- Root docs: `README*`, `docs/**`, architecture notes, ADR folders, runbooks
- Agent docs: `AGENTS.md`, `CLAUDE.md`, `.github/copilot-instructions.md`
- Source roots: `src/**`, `app/**`, `server/**`, `packages/**`, `services/**`
- Config that reveals shape: package manifests, workspace files, build files, routing, infra, env examples
- Tests that reveal vocabulary and behavior

Build a rough map of:

- Runtime boundaries
- Deployment units
- External integrations
- Business flows
- Repeated nouns in docs, code, schema names, route names, UI labels, and test names

### 2. Fill `OVERVIEW.md`

Draft `docs/.zsen/OVERVIEW.md` from the repo evidence you gathered.

Use `OVERVIEW-TEMPLATE.md` as the content template.

Keep the overview high-level. Capture what the project is, who it serves, the main tech stack, and how a reader should navigate the zsen docs tree.

### 3. Extract candidate domains

Infer candidate domains from behavior and ownership, not folder names alone.

Use `/zsen-skills-spec` for the domain criteria and `DOMAINS.md` format.

### 4. Extract candidate terms

Mine candidate terms from:

- Type names
- Schema and table names
- Route names
- UI labels
- Test names
- Glossaries that already exist
- Repeated nouns in comments and docs

Use `/zsen-skills-spec` to decide whether each term belongs in a domain-local `TERMS.md` or the global glossary.

### 5. Infer candidate ADRs

Look for decisions that are already baked into the codebase or docs:

- Architectural shape
- Integration style
- Data ownership boundaries
- Deployment topology
- Technology choices with real lock-in
- Deliberate deviations from the obvious path

Use `/zsen-skills-spec` to decide whether a decision deserves an ADR and whether it belongs globally or within a domain.

If the code implies a decision but the rationale is missing, draft it as a hypothesis and ask the user to confirm or correct it.

### 6. Confirm the domain map with the user

Before writing artifacts, present the candidate domain map to the user and resolve only the domain-shaping ambiguities:

- Which proposed domains are real
- Which areas should be merged or split
- Which technical domains matter enough to track
- Which names should become the canonical domain labels

Ask one question at a time, provide your recommended answer, and update your working domain map as the user responds.

Do not ask the user to select domains one by one for deep-dives. Once the domain map is confirmed, proceed through the domains yourself.

### 7. Extract domain-local artifacts

After the domain map is confirmed, visit each meaningful domain and extract its local knowledge from code, docs, tests, schemas, and integrations.

For each domain:

- Identify domain-local vocabulary and write it using the `/zsen-skills-spec` terms rules and template
- Identify domain-local decisions and write them using the `/zsen-skills-spec` ADR rules and template
- Ask the user only if the domain still has an ambiguity that cannot be resolved from repo evidence

Targeted follow-up questions must:

- Reference the evidence that created the ambiguity
- Explain why the answer matters to the domain map, domain-local artifacts, or global roll-up
- Include your recommended answer

Good questions usually resolve:

- Competing names for the same concept
- Missing business meaning behind a technical label
- Whether two areas are separate domains or one
- Whether an architectural choice was intentional or accidental
- Whether stale docs or dead code should still count as current truth

If a question can be answered by reading another file, do that instead of asking.

Continue until every meaningful domain has been processed or the remaining ones clearly add no local vocabulary or decisions worth recording.

### 8. Fill the global artifacts

After the domain-local pass, roll the shared understanding up into the global artifacts:

- Update `DOMAINS.md`
- Promote only cross-domain vocabulary into the global `TERMS.md`
- Promote only system-wide decisions into global ADRs

Use `/zsen-skills-spec` for the promotion rules.

## Conflict resolution

When sources disagree, resolve them in this order:

1. Running behavior and tests
2. Code structure and invariants
3. Recent docs near the code
4. High-level docs
5. User recollection

Do not silently reconcile contradictions. Surface them and ask.

## Output standard

Before ending the onboarding pass, make sure you can summarize:

- What the project is and how the zsen docs should be navigated
- The top-level domain map
- Which domain-local terms and ADRs were created
- What was promoted into the global artifacts
- The remaining uncertainties, if any

The artifacts should be crisp enough that later skills can rely on them without re-discovering the repo from scratch.
