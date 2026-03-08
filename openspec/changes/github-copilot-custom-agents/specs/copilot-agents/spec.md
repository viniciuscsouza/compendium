## ADDED Requirements

### Requirement: Persona-Based Instructions
The system SHALL support specialized agents (e.g., Architect, Security Auditor, Tester) via Markdown files in `.github/copilot/agents/`.

#### Scenario: Agent Specialization
- **WHEN** a user asks for a security review
- **THEN** Copilot SHALL be instructed to refer to `.github/copilot/agents/security-auditor.md` for role-specific guidance

### Requirement: Role-Driven Decision Making
Each agent SHALL include specific decision-making rules for its domain.

#### Scenario: Architecture Review
- **WHEN** the Architect agent is consulted for a new service design
- **THEN** it SHALL provide feedback based on the project's specific architectural patterns (e.g., DDD, Microservices)

### Requirement: Agent Activation Keywords
Agents SHALL be mapped to specific intent keywords (e.g., "Review as Security Auditor", "Ask Architect").

#### Scenario: Intent Recognition
- **WHEN** a developer's prompt includes "review security"
- **THEN** Copilot SHALL activate the corresponding agent instructions
