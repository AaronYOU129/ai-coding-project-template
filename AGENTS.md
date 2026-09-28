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
- `README.md` is the reader-facing repository landing page: it explains the
  project's purpose, value, and current status; provides the shortest starting path;
  and links to detailed documentation without duplicating it.

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

### Comments and Rationale

Code comments must preserve reasoning that a future reader cannot reliably recover from
the code alone. Their purpose is to explain constraints and intent, prevent accidental
reversal of deliberate choices, and make methodological and safety-critical behavior
auditable.

- Add a concise comment when code implements a non-obvious methodological choice,
  statistical assumption, safety or spending constraint, compatibility workaround,
  reproducibility requirement, or important edge-case policy.
- Explain **why** the choice exists and, when useful, what would break or become invalid
  if it were changed. Do not merely translate the next line of code into prose.
- Keep each inline comment to 15 words or fewer and understandable within five seconds.
  Move longer reasoning to a docstring or `decision-log.md`, leaving a short pointer.
- Keep the required module header and use function docstrings to state each function's
  contract; use inline comments only where naming and structure cannot communicate the
  rationale clearly enough.
- Do not add comments to obvious assignments, standard library operations, or readable
  control flow solely to increase the number of comments. Excess commentary obscures
  the decisions that actually matter.
- Update or remove a comment whenever the corresponding behavior changes. A stale
  rationale is a correctness defect, not harmless documentation debt.
- During code review, treat unexplained surprising logic as incomplete even when tests
  pass; either simplify the logic or document the reason it must remain surprising.

### Pipeline Module Headers

For a pipeline with three or more dependent stages, include both `Key Steps` and
`Main Flow` in the module docstring. They serve different readers and must not duplicate
the same information.

- `Key Steps` explains what happens in four to seven short, numbered, plain-language
  stages. Keep one action per step and omit function names unless essential.
- `Main Flow` shows where the behavior lives by mapping actual function names, important
  branches, retries, and terminal outputs in a compact indented tree.
- A reader should understand the workflow from `Key Steps`, then know where to inspect
  the implementation from `Main Flow`.
- Keep simple, linear scripts on the standard five-field header; do not add a diagram
  when it would merely repeat two or three obvious statements.

Use this structure for non-trivial pipelines:

```text
Purpose:
    Why the script exists and why its important choices were made.

Inputs:
    Required inputs and paths.

Outputs:
    Generated artifacts and paths.

Key Steps:
    1. Validate inputs and recover saved state.
    2. Build deterministic work items.
    3. Execute pending work within safety limits.
    4. Persist and validate every terminal outcome.

Main Flow:
    main_workflow()
        -> validate_inputs()
        -> build_items()
        -> execute_item()
            |-- retryable failure -> retry
            |-- terminal failure  -> failures output
            `-- success           -> results output
        -> validate_outputs()

How to Run:
    Exact command.
```

### README and Repository Documentation

Treat `README.md` as the landing page for a first-time repository visitor, not as a
changelog, experiment diary, or complete operations manual.

- Open with what the project does, why it matters, and its current status.
- Give readers clear paths to inspect results, reproduce analysis without external
  calls, or rerun the full workflow when applicable.
- Put the shortest safe, no-cost starting path before commands that require credentials,
  external services, approval, or spending.
- Keep API procedures, human-annotation instructions, recovery procedures, historical
  exceptions, and audit details in focused files under `docs/`; link to them from the
  README.
- Use relative links for files within the repository.
- Avoid duplicated commands, chronological narration, and stale language describing
  completed phases as future work.
- Add badges only when they represent active, verifiable repository services.
- Update the README whenever setup, public commands, outputs, project status, or
  supported interfaces change.
- Verify reader paths, relative links, referenced files, current project status, and
  no-cost commands against the actual repository before completion.
- Do not execute paid or externally mutating commands solely to verify documentation.

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
6. Confirm that documentation remains accurate; for README changes, verify its reader
   paths, relative links, referenced files, current status, and safe commands.
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
