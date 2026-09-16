# Human-Centered Coding Principles

Good code is not only correct. It should also be readable, modular, testable, maintainable, and reproducible.

Code is written for computers to execute, but it is also written for people to read, understand, review, and maintain.

These principles are defaults rather than rigid rules. A principle may be adjusted when doing so makes the code clearer, safer, or better suited to the task, but important deviations should be documented.

## 1. File Structure and Reproducibility

Every major pipeline script should be understandable without reading its full implementation.

Pipeline scripts should begin with a module docstring using the following format:

```text
Purpose:    What the script does, why it exists, and why important
            methodological choices were made.
Inputs:     Required inputs, configuration parameters, and
            project-relative paths.
Outputs:    Generated artifacts and their expected locations.
Key Steps:  The high-level logical workflow without merely
            repeating function names.
How to Run: The command needed to execute the script.
```

The `Purpose` section should explain why important methodological choices were made, not merely restate the code.

A reader should be able to understand the script within 30 seconds by reading its header.

Code should be reproducible from scratch:

- Declare dependencies and supported software versions.
- Use project-relative or configurable paths instead of machine-specific paths.
- Set and document random seeds when randomness affects the results.
- Avoid hidden manual steps and undocumented dependencies.
- Keep input and output locations explicit and consistent.
- Provide clear commands for reproducing important outputs.

Organize research and data pipelines around the following structure:

```text
Data → Processing → Estimation → Output
```

## 2. Function Design

- Give each function one clear responsibility.
- Keep functions small when doing so improves clarity.
- Split functions that combine meaningfully different responsibilities.
- Use high-level functions to describe the workflow.
- Use lower-level functions to handle implementation details.
- Make code read like a newspaper: show the main logic first and the details later.
- Avoid tiny wrapper functions that add no semantic value.

## 3. Control Flow

- Use early returns to reduce unnecessary nesting.
- Handle invalid inputs, edge cases, and exceptional cases before the main path.
- Prefer flat, readable control flow over deeply nested conditionals.
- Keep the expected path—the happy path—visually obvious.
- Make failure states explicit instead of silently ignoring them.

## 4. Abstraction

- Keep one level of abstraction within each function whenever practical.
- Do not mix business logic, numerical details, input/output operations, logging, and formatting unless the function is small and linear.
- Separate loading, validation, cleaning, computation, plotting, and exporting when they have meaningfully different responsibilities.
- Introduce abstractions only when they improve clarity, reuse, or testability.
- Prefer simple functions and standard data structures before introducing complex frameworks.
- Extract genuinely shared logic into reusable modules, but do not introduce abstractions merely to eliminate a few repeated lines.

## 5. Naming

- Choose names that reflect the purpose of the code.
- Describe what a variable, function, or object represents, not merely how it is implemented.
- Use pronounceable and searchable names.
- Use consistent terminology throughout the project.
- Prefer clear and specific names over short, ambiguous abbreviations.
- Use domain terminology consistently across code, documentation, tables, and figures.

## 6. Readability

- Write code for people first, not only for the interpreter.
- Prefer explicit, readable code over clever shortcuts.
- Make the main flow understandable without requiring the reader to inspect every implementation detail.
- Use comments to explain why a decision was made, not to repeat what the code already says.
- Do not use comments to compensate for unclear naming or structure.
- Keep documentation synchronized with the actual behavior of the code.

## 7. Testing and Validation

- Test important behavior, edge cases, and known failure modes.
- Prefer testing observable behavior over implementation details.
- Validate assumptions about schemas, units, ranges, identifiers, and missing values at system boundaries.
- For numerical work, compare results with known values, analytical solutions, or trusted reference implementations when possible.
- Add a regression test when fixing a bug.
- Treat test coverage as a diagnostic tool, not as the final objective.
- Do not weaken or delete valid tests merely to make a change pass.

## 8. Error Handling and Logging

- Fail early when required inputs or assumptions are invalid.
- Raise specific exceptions with actionable messages.
- Never ignore an exception without documenting why doing so is safe.
- Log enough context to diagnose failures without exposing secrets or sensitive data.
- Use retries only for transient failures.
- Apply bounded exponential backoff when retries are necessary.
- Make expensive, long-running jobs resumable when practical.

## 9. Configuration, Dependencies, and Secrets

- Keep configuration separate from core logic.
- Store non-sensitive defaults in documented configuration files.
- Store secrets in environment variables or an approved secret manager.
- Never place credentials or API keys directly in source code.
- Record dependencies in the appropriate dependency file.
- Use dependency lock files when appropriate.
- Document required external services, system dependencies, and setup steps.
- Do not commit private data or confidential outputs.

## 10. Refactoring Guardrails

- Refactor when doing so improves clarity, responsibility boundaries, reuse, or testability.
- Split large functions when they combine meaningfully different responsibilities.
- Do not create tiny wrappers with no semantic value.
- Do not over-engineer short, linear code that is already easy to understand.
- Refactor incrementally and protect existing behavior with tests.
- Prefer the simplest design that satisfies the current requirements.
