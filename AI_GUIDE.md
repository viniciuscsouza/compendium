# AI Development Guide (GitHub Copilot)

This project uses a structured instruction layer to ensure GitHub Copilot provides high-quality, architecturally consistent, and secure code suggestions.

## How it Works

The system is organized into three main areas under `.github/copilot/`:

1.  **Skills** (`/skills/`): Modular domain knowledge (e.g., API Design, Error Handling) with "Good vs. Bad" patterns.
2.  **Agents** (`/agents/`): Specialist personas (Architect, Security Auditor, Tester) that provide role-specific guidance.
3.  **Workflows** (`/prompts/`): Standardized, multi-step prompt templates for complex tasks like `/verify` or `/scaffold`.

## Best Practices for Developers

- **Reference Skills**: When working on a specific domain, you can prompt Copilot: *"Follow the guidance in .github/copilot/skills/api-design.md to implement this endpoint."*
- **Activate Agents**: For deep reviews, use: *"Review this PR as a .github/copilot/agents/security-auditor.md."*
- **Use Workflows**: Copy-paste the content of a workflow prompt from `.github/copilot/prompts/` to perform complex operations like `/verify`.

## Global Rules

Copilot is instructed to always follow these rules:
- **Verification First**: Every change must have a verification plan.
- **Architecture-First**: Propose the design before writing code.
- **Minimalism**: Focus on the task at hand without unrelated changes.

## Contributing

To add a new skill, agent, or workflow:
1.  Use the `template.md` file in the corresponding directory.
2.  Follow the established structure (e.g., "Good vs. Bad" for skills).
3.  Ensure the content is language-agnostic unless specific to a project's stack.
