# Workflow: /health-check

Check for technical debt, inconsistencies, and potential maintenance issues.

## Instructions for the AI

1. **Rule Violation Check**: Scan for any violations of the global rules defined in `.github/copilot-instructions.md`.
2. **Skill Alignment**: Compare recent changes with the guidance in relevant skill files (e.g., `error-handling.md`).
3. **Dead Code Detection**: Identify any unused functions, variables, or imports.
4. **Complexity Analysis**: Highlight modules or functions with high cyclomatic complexity.
5. **Testing Health**: Identify critical paths without sufficient test coverage.

## Expected Output

### Health Report
- **Global Rules Compliance**: [Summary]
- **Skill Alignment**: [Summary]
- **Technical Debt**: [List of findings]
- **Actionable Improvements**: [Suggested refactorings]
