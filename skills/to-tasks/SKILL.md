---
name: to-tasks
description: Break a plan or PRD into independently-grabbable tasks using tracer-bullet vertical slices.
disable-model-invocation: true
---

# To Tasks

## Process

### 1. Gather context

Work from whatever is already in the conversation context. Adhere to the existing artifacts, including TERMS.md, ADR.md, and OVERVIEW.md.

### 2. Explore the codebase (optional)

If you have not already explored the codebase, do so to understand the current state of the code.

Look for opportunities to prefactor the code to make the implementation easier. "Make the change easy, then make the easy change."

### 3. Draft vertical slices

Break the plan into **tracer bullet** tasks. Each task is a thin vertical slice that cuts through ALL integration layers end-to-end, NOT a horizontal slice of one layer.

<vertical-slice-rules>

- Each slice delivers a narrow but COMPLETE path through every layer (schema, API, UI, tests)
- A completed slice is demoable or verifiable on its own
- Any prefactoring should be done first

</vertical-slice-rules>

### 4. Quiz the user

Present the proposed breakdown as a numbered list. For each slice, show:

- **Title**: short descriptive name
- **Blocked by**: which other slices (if any) must complete first
- **User stories covered**: which user stories this addresses (if the source material has them)

Ask the user:

- Does the granularity feel right? (too coarse / too fine)
- Are the dependency relationships correct?
- Should any slices be merged or split further?

Iterate until the user approves the breakdown.

### 5. Publish the tasks to the local task tracker

Create a `tasks` directory in the same folder as the PRD. For each approved slice, generate a task file at `.local/.zsen/<slug>/tasks/<number>-<task-title>.md`. Use the format in TASK-TEMPLATE.md. Put them in dependency order(blockers first) so you can reference real task identifiers in the "Blocked by" field.
