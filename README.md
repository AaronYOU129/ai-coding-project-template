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
