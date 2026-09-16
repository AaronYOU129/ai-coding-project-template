# AI-Assisted Development Workflow

AI can accelerate implementation, but reliable development still requires explicit requirements, sound design, controlled execution, and careful verification.

This workflow keeps important information in project files rather than relying only on conversational context.

```text
Specification → Work Planning → Implementation → Verification
```

These stages are sequential but iterative. If implementation or verification reveals a problem, return to the earliest affected stage and update the relevant project file.

## Stage 1 — Specification

Before designing or implementing substantial work, complete `specification.md`.

Define:

- **Goal:** What problem needs to be solved?
- **Users and use cases:** Who needs the result, and how will they use it?
- **Inputs:** What data, files, parameters, services, or user actions are required?
- **Outputs:** What artifacts or behaviors should be produced?
- **Requirements:** What observable behavior and quality characteristics are required?
- **Constraints:** What technical, operational, privacy, security, compatibility, or methodological limits apply?
- **Design:** What components, interfaces, dependencies, data flow, and error-handling strategy will be used?
- **Testing strategy:** How will important behavior and failure modes be checked?
- **Acceptance criteria:** What specific evidence will demonstrate completion?

Review the specification for missing requirements, ambiguity, inconsistency, incorrect assumptions, and unclear acceptance criteria.

The agent should ask for clarification when an ambiguity could materially change the result. Minor assumptions may be made only when they are safe, reversible, and clearly stated.

Do not begin substantial implementation until material specification issues are resolved and the acceptance criteria are sufficiently clear.

## Stage 2 — Work Planning

Translate the approved specification into small, independently verifiable work items in `progress.md`.

Each work item should identify:

- the intended outcome;
- relevant inputs and dependencies;
- files or components allowed to change;
- applicable acceptance criteria;
- exact verification commands or checks.

A work item should be small enough to implement and verify within a focused session, but large enough to produce meaningful behavior.

Record decisions that materially affect architecture, methodology, interfaces, dependencies, security, privacy, operations, or compatibility in `decision-log.md`.

## Stage 3 — Implementation

At the beginning of an implementation session, the agent should:

1. Read `AGENTS.md` and the relevant project files.
2. Identify the next incomplete work item in `progress.md`.
3. Inspect the existing implementation and tests.
4. Confirm the files that may be modified.
5. Identify material ambiguities before writing code.

During implementation, the agent should:

- make the smallest change that fully satisfies the work item;
- follow `docs/coding-principles.md`;
- avoid unrelated modifications;
- preserve established interfaces unless change is required;
- add or update tests alongside behavioral changes;
- record material assumptions and design changes;
- stop and ask before materially expanding the agreed scope.

After implementation, the agent should:

1. Run the relevant tests and quality checks.
2. Compare the actual result with the acceptance criteria.
3. Update `progress.md` only for verified work.
4. Update `decision-log.md` when a material decision was made.
5. Report completed work and remaining limitations.

## Single-Agent and Multi-Agent Work

Use a single agent when:

- the project is small;
- tasks are tightly coupled;
- several tasks modify the same files;
- coordination would cost more than parallel execution would save.

Use multiple agents only when work items are sufficiently independent.

In a multi-agent workflow:

- the main agent manages requirements, interfaces, dependencies, integration, and overall progress;
- each agent receives an explicit goal, allowed files, acceptance criteria, and verification commands;
- agents do not modify overlapping files concurrently unless their work is explicitly coordinated;
- the main agent reviews and verifies the integrated result.

Multiple agents reduce context size, but they do not remove the need for integration review.

## Stage 4 — Verification

A task is complete only when its result has been verified. Code generation alone does not constitute completion.

Verification should include:

- running relevant automated tests;
- running applicable lint, formatting, type-check, and build commands;
- checking important outputs manually when appropriate;
- confirming that every applicable acceptance criterion is satisfied;
- reviewing expected behavior, error handling, and important edge cases;
- confirming that documentation remains accurate;
- checking the final diff for unrelated changes and regressions;
- confirming that no credentials, secrets, private data, or local configuration were introduced.

Verification commands must be adapted to the project's actual technology stack and recorded in `specification.md` and `README.md`.

If a check cannot be run, the completion report must state:

- which check was not run;
- why it could not be run;
- what remains unverified.

If verification fails, record the failure in `progress.md` and continue from the smallest affected unit.

## Context Management

To keep AI sessions focused:

- store requirements, design decisions, assumptions, and progress in project files;
- do not rely on conversational memory for critical information;
- read only the files relevant to the current task after completing the required reading;
- keep work boundaries explicit;
- update project files when decisions change.

## Prompting Principle

A task prompt should identify:

- the goal;
- relevant project files;
- files allowed to change;
- constraints;
- acceptance criteria;
- required tests and quality checks;
- expected completion report.

The agent should ask questions when unresolved ambiguity could materially affect the result. It may proceed with minor, safe, and reversible assumptions only when those assumptions are explicitly documented.

## Completion Principle

AI-assisted development is complete only when:

```text
The specification is satisfied,
the implementation is understandable,
the required checks pass,
and the result has been verified.
```
