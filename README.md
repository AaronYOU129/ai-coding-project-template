# AI Coding Project Template

A reusable GitHub template for reliable AI-assisted software development with Codex, Claude Code, Cursor, and other coding agents.

It helps developers turn project requirements into tested and verified software through a structured workflow:

**Requirements → Specification → Design → Implementation → Testing → Verification**

## Why use this template?

AI coding agents can write code quickly, but they can also start implementation too early, lose project context, misunderstand requirements, or declare a task complete without sufficient verification.

This template provides a lightweight structure that keeps the coding agent aligned with the project's requirements, design, implementation plan, and acceptance criteria.

## What's included?

- `AGENTS.md` — shared instructions for coding agents
- `specification.md` — requirements, design, constraints, and acceptance criteria
- `progress.md` — implementation progress and remaining work
- `decision-log.md` — important technical decisions
- `docs/coding-principles.md` — coding principles for AI-assisted development
- `docs/ai-assisted-development-workflow.md` — the development workflow agents should follow

## Supported coding agents

This template is designed to work with:

- OpenAI Codex
- Claude Code
- Cursor
- GitHub Copilot
- other coding agents that can read repository-level instructions

## Quick Start

1. Click **Use this template**.
2. Select **Create a new repository**.
3. Describe your project in the generated repository.
4. Complete `specification.md` before substantial implementation.
5. Ask your coding agent to read `AGENTS.md` and follow the project workflow.

Example prompt:

> Read `AGENTS.md` and `specification.md`. Help me clarify the requirements, design the solution, break the work into small testable tasks, implement it, run the relevant tests, and verify the result against the acceptance criteria.

## How it works

```text
Requirements
    ↓
Specification
    ↓
Design
    ↓
Small testable tasks
    ↓
Implementation
    ↓
Testing
    ↓
Verification
    ↓
Progress and decision tracking



# Project Name

Replace this heading with the project name and summarize the project in one sentence.

## Purpose

Describe the problem this project solves, who it serves, and the intended outcome.

## Requirements

List the main functional requirements, quality requirements, constraints, and explicit non-goals.

Before implementation, record the complete requirements, design, and acceptance criteria in [`specification.md`](specification.md).

## Setup

Document the supported environment, required dependencies, installation commands, configuration, and any external services.

```text
Add setup commands here.
```

Never commit credentials or secrets. Use environment variables or an approved secret manager.

## Usage

Show the commands or steps needed to run the project and include representative usage examples.

```text
Add usage examples here.
```

## Development

Before substantial implementation:

1. Complete [`specification.md`](specification.md).
2. Review [`AGENTS.md`](AGENTS.md).
3. Follow:
   - [`docs/coding-principles.md`](docs/coding-principles.md)
   - [`docs/ai-assisted-development-workflow.md`](docs/ai-assisted-development-workflow.md)
4. Track project status in [`progress.md`](progress.md).
5. Record material decisions in [`decision-log.md`](decision-log.md).

When Codex is started from this repository, it automatically reads the root `AGENTS.md`. Other coding agents should be instructed to read it before beginning work if they do not discover it automatically.

Add the project-specific commands for tests, linting, formatting, type checking, and builds here once the technology stack is selected.

## License

This project is available under the terms in [`LICENSE`](LICENSE).
