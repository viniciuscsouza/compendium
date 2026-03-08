## 1. Directory Structure Setup

- [x] 1.1 Create `.github/copilot/` root directory
- [x] 1.2 Create `.github/copilot/skills/` directory
- [x] 1.3 Create `.github/copilot/agents/` directory
- [x] 1.4 Create `.github/copilot/prompts/` directory

## 2. Core Instructions & Rules

- [x] 2.1 Create `.github/copilot-instructions.md` with global rules and loading instructions
- [x] 2.2 Define language-agnostic "Verification First" and "Architecture-First" rules in the root file

## 3. Skills Implementation

- [x] 3.1 Create a template for skill files in `.github/copilot/skills/template.md`
- [x] 3.2 Implement `api-design.md` skill with "Good vs. Bad" examples
- [x] 3.3 Implement `error-handling.md` skill with language-agnostic best practices

## 4. Specialist Agents Implementation

- [x] 4.1 Create a template for agent files in `.github/copilot/agents/template.md`
- [x] 4.2 Implement `architect.md` agent persona instructions
- [x] 4.3 Implement `security-auditor.md` agent persona instructions
- [x] 4.4 Implement `tester.md` agent persona instructions

## 5. Workflow Prompts Implementation

- [x] 5.1 Create a template for prompt files in `.github/copilot/prompts/template.md`
- [x] 5.2 Implement `/verify` workflow prompt template
- [x] 5.3 Implement `/scaffold` workflow prompt template
- [x] 5.4 Implement `/health-check` workflow prompt template

## 6. Validation & Documentation

- [x] 6.1 Verify that GitHub Copilot correctly identifies and loads instructions from the new structure
- [x] 6.2 Document the usage of the new `.github/copilot/` layer in the project's README or a new `AI_GUIDE.md`
