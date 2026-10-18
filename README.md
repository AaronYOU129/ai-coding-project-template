# AI Coding Project Template

A reusable GitHub template that helps AI coding agents understand what you actually want, plan before implementation, stay within scope, and verify the final result against your intended outcome.

**Intent → Clarification → Specification → Plan → Implementation → Testing → Verification**

## Why use this template?

AI coding often fails not because the code is invalid, but because the agent misunderstood the goal, made hidden assumptions, expanded the scope, lost important context, or verified the wrong thing.

This template keeps requirements, design decisions, progress, and verification criteria inside the repository so the coding agent can repeatedly refer back to the same source of truth.

The goal is not simply to help AI write code, but to help AI build the thing you actually meant to build.

## What's included?

- `AGENTS.md` — shared instructions for coding agents
- `specification.md` — requirements, design, constraints, and acceptance criteria
- `progress.md` — current status, verified progress, and next work
- `decision-log.md` — important technical and methodological decisions
- `docs/coding-principles.md` — coding principles for readable, testable, and maintainable code
- `docs/ai-assisted-development-workflow.md` — the workflow agents should follow from specification to verification
- `ruff.toml` — linter limits that enforce function size rules for Python code

## Supported coding agents

This template is designed to work with:

- OpenAI Codex
- Claude Code
- Cursor
- GitHub Copilot
- other coding agents that can read repository-level instructions and project context

## Quick Start

1. Click **Use this template**.
2. Select **Create a new repository**.
3. Describe the project you want to build.
4. Complete or review `specification.md`.
5. Ask your coding agent to read `AGENTS.md` before substantial implementation.

Example prompt:

> Read `AGENTS.md` and `specification.md`. First, restate my intended outcome and identify any ambiguity or hidden assumptions that could materially change the result. Then help me finalize the specification, break the work into small testable tasks, implement within scope, run the relevant checks, and verify the final result against the intended outcome.

## How it works

```text
Intent
    ↓
Clarification
    ↓
Specification
    ↓
Plan
    ↓
Small testable tasks
    ↓
Implementation
    ↓
Testing
    ↓
Verification
    ↓
Compare against intended outcome
```

## Core principles

The workflow is built around a few simple rules:

- Understand the intended outcome before substantial implementation.
- Resolve material ambiguity before coding.
- Keep important project context in repository files rather than only in chat.
- Break substantial work into small, independently verifiable tasks.
- Make the smallest change that fully satisfies the requirements.
- Avoid unrelated changes and unnecessary complexity.
- Do not treat passing tests as sufficient when the final result does not match the intended outcome.
- Never claim completion without verification.

## FAQ

### What problem does this template solve?

AI coding often fails not because the code is invalid, but because the agent misunderstood the goal, started implementation too early, made hidden assumptions, expanded the scope, lost important context, or verified the wrong thing.

This template gives coding agents a structured workflow for understanding intent, turning it into an explicit specification, implementing within scope, and verifying the final result against the original intended outcome.

### Why use this template instead of just asking an AI coding agent to write the code?

AI coding agents can generate code quickly, but speed alone does not guarantee that the result matches what the user actually intended.

Without a clear project structure, important requirements may remain implicit in chat, assumptions may go undocumented, scope may drift, and the agent may treat passing tests as sufficient even when the final behavior does not solve the right problem.

This template keeps intent, requirements, decisions, progress, and verification criteria inside the repository so the agent can repeatedly refer back to the same source of truth.

The goal is not simply to help AI write code, but to help AI build the thing you actually meant to build.

### How does this template help AI understand what I actually want?

Before substantial implementation, the agent is expected to identify:

- the intended outcome;
- functional and quality requirements;
- constraints;
- explicit non-goals;
- assumptions;
- open questions;
- and acceptance criteria.

If an ambiguity could materially change the result, it should be clarified before coding begins.

Minor assumptions should be safe, reversible, and explicitly documented.

### Why not keep all project context in chat?

Chat is useful for interaction, but important project context can become fragmented, implicit, or lost across long conversations and separate coding sessions.

This template stores important information in repository files such as:

- `AGENTS.md`
- `specification.md`
- `progress.md`
- `decision-log.md`

This gives the coding agent persistent project context that can be reviewed and updated over time.

### How does this reduce the chance that AI builds the wrong thing?

The workflow requires the coding agent to:

1. understand the intended outcome;
2. identify ambiguity and hidden assumptions;
3. define explicit requirements and acceptance criteria;
4. plan before substantial implementation;
5. break the work into small, verifiable tasks;
6. stay within the agreed scope;
7. test the implementation;
8. review the final changes;
9. verify the result against the original specification and intended outcome.

Passing tests alone is not considered sufficient if the result does not solve the problem the user actually intended to solve.

### Why use `AGENTS.md`?

`AGENTS.md` provides persistent repository-level instructions for coding agents.

It defines how the agent should approach:

- requirements;
- specification review;
- scope control;
- implementation;
- testing;
- verification;
- progress tracking;
- and completion reporting.

This makes the expected development behavior part of the repository rather than relying only on temporary prompts.

### What is `specification.md` for?

`specification.md` turns an informal request into an explicit description of what should be built.

It records the project goal, users, inputs, outputs, requirements, constraints, proposed design, testing strategy, risks, and acceptance criteria.

The purpose is to reduce ambiguity before substantial implementation begins.

### What is `progress.md` for?

`progress.md` keeps track of the current project state and the next incomplete work.

Coding agents should work on small, independently verifiable items and only mark work complete after the relevant result has been verified.

This helps prevent long coding sessions from losing track of what has actually been completed.

### What is `decision-log.md` for?

`decision-log.md` records decisions that materially affect the project, such as architecture, interfaces, dependencies, methodology, security, compatibility, or important tradeoffs.

This helps future coding sessions understand not only what was decided, but why the decision was made.

### Does this template work with Codex, Claude Code, and Cursor?

Yes.

The template is designed around repository-level instructions and persistent project files, so it can be used with OpenAI Codex, Claude Code, Cursor, GitHub Copilot, and other coding agents that can read repository context.

Different tools may discover project instructions differently, so agents that do not automatically read `AGENTS.md` should be explicitly instructed to read it before substantial work.

### Does the AI need to ask questions before every coding task?

No.

The agent should ask questions when unresolved ambiguity could materially affect the result.

For minor details that are safe, reversible, and unlikely to change the intended outcome, the agent may proceed with an explicit assumption.

The goal is to avoid both unnecessary interruptions and dangerous guessing.

### Does the agent always need a full specification before writing code?

Not for every tiny change.

Small, obvious, low-risk tasks can remain lightweight.

For substantial implementation, the important requirements, constraints, design choices, and acceptance criteria should be sufficiently clear before coding begins.

The amount of specification should scale with the complexity and risk of the task.

### Does passing all tests mean the task is complete?

Not necessarily.

Tests only verify what they were designed to check.

A task is complete only when the implementation satisfies the specification, the relevant checks have been run, the acceptance criteria have been verified, and the final behavior matches the intended outcome.

### How does this template prevent unnecessary code changes?

The agent is instructed to make the smallest change that fully satisfies the requirements.

It should avoid modifying unrelated files, preserve established interfaces unless change is required, and stop before materially expanding the agreed scope.

The final diff should also be reviewed for unrelated changes and unnecessary complexity.

### Can this template be used for small projects?

Yes.

The workflow is designed to be lightweight when the task is simple and more structured when the task is complex.

You do not need to fill every section of every file for a small project.

Use only the level of structure needed to make the intended outcome clear and verifiable.

### Can this template be used for large projects?

Yes.

For larger projects, `specification.md`, `progress.md`, and `decision-log.md` become more important because they preserve context across longer development cycles and multiple coding sessions.

Large projects should also be broken into small, independently verifiable work items.

### Can multiple coding agents work on the same project?

Yes, when the work can be safely divided.

Each agent should receive a bounded goal, allowed files, relevant inputs, acceptance criteria, and verification requirements.

Agents should avoid modifying overlapping files concurrently unless their work is explicitly coordinated.

A main agent or human should remain responsible for integration and final verification.

### When is a coding task considered complete?

A task is complete only when:

- the intended outcome is clear;
- the implementation satisfies the specification;
- the required tests and quality checks have been run;
- the applicable acceptance criteria have been verified;
- the changes remain within the agreed scope;
- relevant documentation and progress files are updated;
- and the final result matches the original intended outcome.

Code generation alone does not constitute completion.

---

# Project Name

Replace this heading with the project name and summarize the project in one sentence.

## Purpose

Describe:

- the problem this project solves;
- who it serves;
- the intended outcome;
- and what success looks like.

## Requirements

List the main:

- functional requirements;
- quality requirements;
- constraints;
- explicit non-goals;
- and acceptance criteria.

Before substantial implementation, record the complete requirements, design, and acceptance criteria in [`specification.md`](specification.md).

## Setup

Document:

- supported environments;
- required dependencies;
- installation commands;
- configuration;
- required environment variables;
- and external services.

```text
Add setup commands here.
```

Never commit credentials or secrets. Use environment variables or an approved secret manager.

## Usage

Show the commands or steps needed to run the project.

Include representative examples where useful.

```text
Add usage examples here.
```

## Development

Before substantial implementation:

1. Read [`AGENTS.md`](AGENTS.md).
2. Complete or review [`specification.md`](specification.md).
3. Follow:
   - [`docs/coding-principles.md`](docs/coding-principles.md)
   - [`docs/ai-assisted-development-workflow.md`](docs/ai-assisted-development-workflow.md)
4. Break substantial work into small, independently verifiable tasks.
5. Track verified progress in [`progress.md`](progress.md).
6. Record material decisions in [`decision-log.md`](decision-log.md).
7. Run the relevant tests and quality checks before declaring completion.
8. Verify the result against the original intended outcome and acceptance criteria.

When Codex is started from this repository, it can use the root `AGENTS.md` as repository-level instructions.

Other coding agents should be instructed to read `AGENTS.md` before beginning substantial work if they do not discover it automatically.

## Testing and Verification

Document the exact commands used for:

```text
Tests:
Lint:
Format:
Type check:
Build:
Other verification:
```

Verification should cover more than whether the code runs.

Confirm that:

- the expected behavior works;
- important edge cases and failure modes have been checked;
- applicable acceptance criteria are satisfied;
- unrelated behavior was not changed;
- documentation remains accurate;
- and the final result matches the intended outcome.

If a required check cannot be run, record:

- what was not checked;
- why it could not be checked;
- and what remains uncertain.

## Project Status

Use [`progress.md`](progress.md) to record:

- the current phase;
- the current focus;
- verified completed work;
- blockers;
- and the next concrete action.

Do not mark work complete until the relevant result has been verified.

## Decisions

Use [`decision-log.md`](decision-log.md) for decisions that materially affect:

- architecture;
- methodology;
- interfaces;
- dependencies;
- security;
- privacy;
- compatibility;
- operations;
- or other important tradeoffs.

Do not use the decision log for routine implementation details.

## Completion

Before considering a non-trivial task complete:

1. Confirm the intended outcome.
2. Verify the applicable acceptance criteria.
3. Run the relevant automated checks.
4. Review important edge cases and failure modes.
5. Review the final diff for unrelated changes and unnecessary complexity.
6. Confirm that documentation and progress tracking are current.
7. Confirm that no secrets, private data, or local configuration were introduced.
8. Compare the final result against the original intended outcome.

A task is complete only when the required behavior has been implemented and verified.

## License

This project is available under the terms in [`LICENSE`](LICENSE).
