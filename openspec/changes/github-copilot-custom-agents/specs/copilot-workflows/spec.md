## ADDED Requirements

### Requirement: Standardized Multi-Step Workflows
The system SHALL provide a library of standardized prompt templates in `.github/copilot/prompts/` for common workflows (e.g., `/verify`, `/scaffold`).

#### Scenario: Code Verification Workflow
- **WHEN** a developer requests code verification (e.g., using `/verify` or a similar prompt)
- **THEN** Copilot SHALL be instructed to follow a multi-step verification process (build, lint, test, security review)

### Requirement: Structured Step-by-Step Instructions
Each workflow prompt SHALL be broken down into discrete steps for the AI to follow.

#### Scenario: New Component Scaffolding
- **WHEN** a developer uses the `/scaffold` prompt for a new component
- **THEN** Copilot SHALL follow the defined steps (create directory, generate interface, implement logic, add tests)

### Requirement: Task-Specific Output Templates
Workflows SHALL define expected output formats (e.g., "Verification Report", "Scaffolding Checklist").

#### Scenario: Verification Reporting
- **WHEN** a verification workflow completes
- **THEN** Copilot SHALL present a summary of results in the defined report format
