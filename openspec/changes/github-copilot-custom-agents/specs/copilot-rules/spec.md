## ADDED Requirements

### Requirement: Global Instruction Root
The system SHALL provide a central configuration file at `.github/copilot-instructions.md` for global rules and constraints.

#### Scenario: Rule Precedence
- **WHEN** a global rule (e.g., "Verification First") is defined in the root instruction file
- **THEN** Copilot SHALL prioritize it over any local or generic AI knowledge

### Requirement: Language-Agnostic Constraints
Global rules SHALL be defined in a language-agnostic manner unless specifically targeting a language's unique features.

#### Scenario: Language Independence
- **WHEN** a rule like "Never use deprecated functions" is defined
- **THEN** Copilot SHALL apply it consistently across all programming languages used in the project

### Requirement: Systematic Instruction Loading
The root instruction file SHALL instruct Copilot to load relevant files from `.github/copilot/` based on context.

#### Scenario: Contextual Loading
- **WHEN** a developer is working on a new feature design
- **THEN** Copilot SHALL be instructed to refer to `.github/copilot/agents/architect.md` and `.github/copilot/skills/api-design.md`
