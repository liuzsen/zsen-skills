---
name: grilling-me
description: A relentless interview to sharpen a plan or design, which also creates docs (ADR's and glossary) as we go.
disable-model-invocation: true
---

Interview me relentlessly about every aspect of this plan until we reach a shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one-by-one. For each question, provide your recommended answer.

Ask the questions one at a time, waiting for feedback on each question before continuing. Asking multiple questions at once is bewildering.

If a question can be answered by exploring the codebase or docs, explore them instead.

## Domain Modeling

Actively build and sharpen the project's domain model as you design. This is the active discipline — challenging terms, inventing edge-case scenarios, and writing the glossary and decisions down the moment they crystallise.

## During the session

### Challenge against the glossary

When the user uses a term that conflicts with the existing language in TERMS.md, call it out immediately. "Your glossary defines 'cancellation' as X, but you seem to mean Y — which is it?"

### Sharpen fuzzy language

When the user uses vague or overloaded terms, propose a precise canonical term. "You're saying 'account' — do you mean the Customer or the User? Those are different things."

### Discuss concrete scenarios

When domain relationships are being discussed, stress-test them with specific scenarios. Invent scenarios that probe edge cases and force the user to be precise about the boundaries between concepts.

### Cross-reference with code

When the user states how something works, check whether the code agrees. If you find a contradiction, surface it: "Your code cancels entire Orders, but you just said partial cancellation is possible — which is right?"

### Update artifacts inline

Update or create domain-specific/global artifacts.

Use the skill `/zsen-skills-spec` to identify, capture, and propose ADRs, terminology, and new domains to the user. Commit them to writing immediately upon user's approval.
