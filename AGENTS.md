# Shared Agent Instructions

## Required Reading

Before starting any task, read:

- `specification.md`
- `progress.md`
- `decision-log.md`
- `docs/coding-principles.md`
- `docs/ai-assisted-development-workflow.md`

Follow the applicable specification, principles, and workflow throughout the task.

## Project Source of Truth

- `specification.md` defines the requirements, constraints, architecture, interfaces, and acceptance criteria.
- `progress.md` records current project status and the next incomplete work.
- `decision-log.md` records material decisions and their rationale.
- `docs/coding-principles.md` defines the coding standards.
- `docs/ai-assisted-development-workflow.md` defines the development process.
- `README.md` explains setup, usage, and project orientation.

If these files conflict, stop and resolve the conflict in the appropriate source-of-truth file before implementation.

## Before Starting Work

1. Identify the requested outcome, inputs, outputs, constraints, and acceptance criteria.
2. Review the relevant sections of `specification.md`.
3. Inspect the existing implementation and tests.
4. Identify the files that may need to change.
5. Ask for clarification when ambiguity could materially affect the result.
6. State minor, safe, and reversible assumptions explicitly.

Before substantial implementation, review the specification for:

- missing requirements;
- ambiguity;
- internal inconsistency;
- incorrect or unsupported assumptions;
- unclear or untestable acceptance criteria.

Do not begin substantial implementation until material specification problems are resolved.

## Authorization and Scope

A request to explain, review, diagnose, or propose a plan does not automatically authorize code changes.

When implementation is authorized:

- make the smallest change that fully satisfies the requirements;
- do not modify unrelated files;
- preserve established interfaces unless a change is required;
- stop and ask before materially expanding the agreed scope;
- never commit credentials, API keys, private data, confidential outputs, or local configuration.

## Implementation Rules

- Keep high-level workflow separate from implementation details.
- Give each function one clear responsibility.
- Prefer explicit, readable code over clever shortcuts.
- Use early returns to reduce unnecessary nesting.
- Handle invalid inputs and important edge cases explicitly.
- Use consistent, descriptive, and searchable names.
- Add or update tests alongside behavioral changes.
- Record material assumptions, limitations, and design changes.
- Do not introduce a dependency unless it provides clear value.

Follow the detailed standards in `docs/coding-principles.md`.

## Progress and Decisions

- Work on the next incomplete item in `progress.md` unless instructed otherwise.
- Keep work items small and independently verifiable.
- Update `progress.md` only after verifying the relevant result.
- Record decisions that materially affect architecture, methodology, interfaces, dependencies, security, or compatibility in `decision-log.md`.
- Never mark an item complete before its acceptance criteria are satisfied.

## Agent Coordination

Use a single agent for small or tightly coupled work. Use multiple agents only when tasks are sufficiently independent and parallel work provides a clear benefit.

When using multiple agents:

- give each agent a bounded goal, inputs, outputs, allowed files, and acceptance criteria;
- prevent agents from modifying overlapping files concurrently;
- keep integration responsibility with the main agent;
- review and verify the combined result before completion.

## Verification Before Completion

Before declaring a non-trivial coding task complete:

1. Identify the applicable acceptance criteria in `specification.md`.
2. Run the repository's relevant tests, linting, formatting checks, type checks, and build commands.
3. Verify each acceptance criterion against the actual system state.
4. Test expected behavior and important failure or edge cases.
5. Review the final diff for:
   - unrelated changes;
   - incomplete implementation;
   - incorrect assumptions;
   - regressions;
   - unnecessary complexity;
   - security or compatibility risks.
6. Confirm that documentation remains accurate.
7. Confirm that no credentials, secrets, private data, or local configuration were introduced.
8. Do not treat passing tests as sufficient when the tests do not cover the complete specification.

Never claim that a task or check passed unless it was actually verified successfully. If a required check cannot be performed, state what was not checked, why, and what remains uncertain.

## Completion Report

At the end of a task, provide a concise report containing:

1. What changed.
2. Which files changed.
3. What was verified, including commands and results.
4. Which acceptance criteria were confirmed.
5. Assumptions, limitations, and anything that remains unverified.
6. The next relevant step, only if one remains.

Code generation alone does not constitute completion. A task is complete only when the requirements are satisfied and the result has been verified.
