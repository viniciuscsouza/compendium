## ADDED Requirements

### Requirement: Modular Skills Structure
The system SHALL provide a modular directory structure at `.github/copilot/skills/` for domain-specific knowledge.

#### Scenario: Categorized Knowledge
- **WHEN** a developer adds a new skill file (e.g., `error-handling.md`)
- **THEN** Copilot SHALL be instructed to reference that file for tasks related to error handling

### Requirement: "Good vs. Bad" Patterns
Skill files SHALL contain explicit "Good" and "Bad" code examples to ground Copilot's understanding of project standards.

#### Scenario: Code Correction
- **WHEN** a skill file defines a "Bad" pattern for API design
- **THEN** Copilot SHALL identify and suggest refactoring for that pattern when encountered in code

### Requirement: Language-Agnostic Skills
Skill files SHALL be written in a language-agnostic manner unless specifically targeting a language's unique features.

#### Scenario: Multi-language Support
- **WHEN** a project uses multiple languages (e.g., Python and JavaScript)
- **THEN** a skill file like `naming-conventions.md` SHALL provide guidance applicable to both
