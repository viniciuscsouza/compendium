# Workflow: /verify

Multi-step verification process to ensure code correctness and quality.

## Instructions for the AI

1. **Build/Compile**: Check if the recent changes compile successfully.
2. **Linter Check**: Identify and report any new linting or style violations.
3. **Tests Run**: Run relevant automated tests. If any fail, suggest a fix.
4. **Security Audit**: Perform a targeted security review of the changes.
5. **Architectural Review**: Ensure the implementation follows project patterns.

## Expected Output

### Verification Report
- **Build**: [Pass/Fail]
- **Lint**: [Pass/Fail/Warnings]
- **Tests**: [Pass/Fail]
- **Security**: [Summary of findings]
- **Architecture**: [Review comments]
