# Project Specification

Complete this document before substantial implementation. Replace every placeholder that applies, remove sections that do not apply, and resolve all material review questions.

## Status

- **State:** Draft
- **Owner:** [Name or team]
- **Last reviewed:** [YYYY-MM-DD]

## Goal

[Describe the problem to solve and the outcome the project should produce.]

## Users and Use Cases

- **Primary users:** [Who will use or maintain the project?]
- **Primary use cases:** [What should they be able to accomplish?]
- **Out of scope:** [What will the project intentionally not do?]

## Inputs

| Input | Source | Format | Validation |
| --- | --- | --- | --- |
| [Input name] | [Source] | [Format or type] | [Required checks] |

## Outputs

| Output | Destination | Format | Success condition |
| --- | --- | --- | --- |
| [Output name] | [Location or consumer] | [Format or type] | [Observable result] |

## Functional Requirements

- [ ] [Describe one observable behavior.]
- [ ] [Describe another observable behavior.]

## Quality Requirements

- **Reliability:** [Expected behavior during failures and recovery.]
- **Performance:** [Relevant latency, throughput, memory, or size limits.]
- **Security and privacy:** [Data classification, access, validation, and secret-handling requirements.]
- **Accessibility:** [Applicable accessibility requirements.]
- **Compatibility:** [Supported platforms, runtimes, versions, or interfaces.]
- **Maintainability:** [Documentation, testing, and operational expectations.]

## Constraints

- **Technical:** [Required or prohibited technologies and dependencies.]
- **Operational:** [Deployment, monitoring, support, or cost constraints.]
- **Data:** [Schema, retention, residency, or licensing constraints.]
- **Schedule:** [Relevant milestones or deadlines.]

## Proposed Design

### System Overview

[Describe the high-level architecture and why it is appropriate.]

### Components

| Component | Responsibility | Inputs | Outputs |
| --- | --- | --- | --- |
| [Component] | [Single clear responsibility] | [Inputs] | [Outputs] |

### Data and Control Flow

1. [Describe the first high-level step.]
2. [Describe the next high-level step.]
3. [Describe how the result is verified or delivered.]

### Interfaces

[Describe public APIs, commands, files, events, or user interactions.]

### Error Handling

[Describe expected failure modes, error messages, recovery, retries, and safe defaults.]

### Dependencies

| Dependency | Purpose | Version policy | Rationale |
| --- | --- | --- | --- |
| [Dependency] | [Purpose] | [Pinned/range/system] | [Why it is necessary] |

## Testing and Verification Strategy

- **Unit tests:** [Important isolated behavior.]
- **Integration tests:** [Important boundaries and interactions.]
- **End-to-end tests:** [Critical user workflows, if applicable.]
- **Failure and edge cases:** [Invalid input, empty state, concurrency, permissions, and other risks.]
- **Quality commands:** [Exact test, lint, format, type-check, and build commands.]
- **Manual checks:** [Checks that cannot be automated.]

## Acceptance Criteria

- [ ] [Criterion stated as a specific, observable, verifiable result.]
- [ ] [Criterion stated as a specific, observable, verifiable result.]

## Risks and Open Questions

| Item | Impact | Resolution or owner |
| --- | --- | --- |
| [Risk or question] | [Potential effect] | [Next step or responsible person] |

## Specification Review

Before approving this specification, confirm:

- [ ] No material requirements are missing.
- [ ] Ambiguous language has been clarified.
- [ ] Requirements, constraints, design, and acceptance criteria are internally consistent.
- [ ] Assumptions are supported, explicitly accepted, or recorded as open questions.
- [ ] Every acceptance criterion is clear, observable, and testable.
- [ ] Inputs, outputs, interfaces, failure modes, security, and compatibility have been considered.
- [ ] The testing strategy can verify the complete specification.

## Approval

- **Approved by:** [Name or team]
- **Date:** [YYYY-MM-DD]
- **Notes:** [Conditions or remaining limitations]
