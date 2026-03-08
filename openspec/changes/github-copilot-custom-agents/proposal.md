## Why

GitHub Copilot often lacks the structured "knowledge and action layer" provided by specialized kits like `dotnet-claude-kit`, leading to inconsistent advice or generic code generation. This change introduces a language-agnostic framework of modular skills, specialist agents, and standardized prompts to ensure Copilot follows specific architectural patterns, security best practices, and project standards.

## What Changes

- **Global Instructions**: Update or create `.github/copilot-instructions.md` to serve as the root configuration for all custom agents and skills.
- **Skills System**: Create `.github/copilot/skills/` containing modular Markdown files (e.g., `api-design.md`, `error-handling.md`) that define "Good vs. Bad" examples and anti-patterns.
- **Specialist Agents**: Create `.github/copilot/agents/` with persona-specific instructions (e.g., `architect.md`, `security-auditor.md`) that Copilot can activate based on context.
- **Workflow Prompts**: Create `.github/copilot/prompts/` with standardized, multi-step prompt templates for tasks like `/verify`, `/scaffold`, and `/health-check`.
- **Instructional Hierarchy**: Establish a clear structure where Copilot is instructed to prioritize these local "source of truth" files before generating code.

## Capabilities

### New Capabilities
- `copilot-skills`: A library of modular domain knowledge files for consistent coding standards across different technical areas.
- `copilot-agents`: Specialized personas that provide focused advice and code reviews based on specific roles (e.g., Security, Architecture).
- `copilot-workflows`: Standardized, multi-step interaction patterns that orchestrate agents and skills for complex tasks.
- `copilot-rules`: A core set of global, language-agnostic constraints (e.g., "Verification First", "Architecture Proposing") enforced via root instructions.

### Modified Capabilities
- (None - this is a new implementation)

## Impact

- **Developers**: Improved accuracy and consistency of GitHub Copilot suggestions.
- **Project Structure**: Addition of a `.github/copilot/` directory containing configuration and instruction files.
- **Tooling**: Copilot will now have access to explicit project rules and "Good vs. Bad" patterns, reducing technical debt.
