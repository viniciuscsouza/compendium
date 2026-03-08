# Skill: Error Handling

Language-agnostic best practices for handling errors and exceptions.

## Good vs. Bad Patterns

### Explicit Exceptions

- ✅ **Good**: Throw specific exceptions with clear messages.
- ❌ **Bad**: Use generic exceptions like `Exception` or `Error`.

### Defensive Programming

- ✅ **Good**: Validate inputs early and fail fast.
- ❌ **Bad**: Let invalid data propagate deep into the business logic.

## Decision Guide

- **If a failure is recoverable**: Use a retry mechanism or provide a fallback.
- **If a failure is fatal**: Log the full stack trace and stop execution gracefully.
