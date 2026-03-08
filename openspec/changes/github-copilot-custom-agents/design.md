## Context

GitHub Copilot currently provides suggestions based on broad language knowledge but lacks awareness of specific project architectures, "Good vs. Bad" coding patterns, and specialized developer personas unless explicitly prompted. The `dotnet-claude-kit` demonstrated a successful model for providing this context through modular "skills" and "agents". This design adapts that model for GitHub Copilot in a language-agnostic way.

## Goals / Non-Goals

**Goals:**
- Create a modular, language-agnostic directory structure for GitHub Copilot instructions (`.github/copilot/`).
- Implement a hierarchical system where a root instruction file points to specialized agents and skills.
- Define standardized templates for skills (knowledge), agents (personas), and prompts (workflows).
- Ensure the system is easily extensible for any programming language or project type.

**Non-Goals:**
- Creating .NET-specific skills or agents.
- Building external tools or MCP servers (focusing strictly on Copilot's native instruction capabilities).
- Modifying Copilot's core behavior beyond what is possible via instructions.

## Decisions

- **Directory Structure**: All configuration will live under `.github/copilot/` to avoid cluttering the root and to clearly separate AI instructions from CI/CD or other GitHub metadata.
- **Root Entry Point**: `.github/copilot-instructions.md` will be the primary source of truth. It will contain global rules and instructions for Copilot to "load" specific files from the subdirectories based on the task at hand.
- **Modular Skills**: Skills will be individual Markdown files in `.github/copilot/skills/`. This allows Copilot to only ingest relevant domain knowledge, saving context tokens.
- **Persona-Based Agents**: Specialist personas will reside in `.github/copilot/agents/`. These are activated by the user or by Copilot itself when it recognizes a specific role (e.g., Security Audit) is required.
- **Prompt Library**: Common multi-step workflows will be documented in `.github/copilot/prompts/` as reference templates for the user to copy-paste or for Copilot to refer to when a "slash command" like workflow is requested.

## Risks / Trade-offs

- **[Risk] Context Overflow** → [Mitigation] Keep skill and agent files focused and concise. Instruct Copilot to read specific files only when relevant to the current file or task.
- **[Risk] Instruction Drift** → [Mitigation] Establish a "Source of Truth" hierarchy where global rules always take precedence over specialist advice.
- **[Risk] Copilot Inconsistency** → [Mitigation] Use clear, normative language (SHALL/MUST) and provide "Good vs. Bad" code blocks to ground the AI's understanding.
