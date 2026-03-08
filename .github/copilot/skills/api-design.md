# Skill: API Design

Guidelines for creating RESTful and consistent APIs.

## Good vs. Bad Patterns

### Endpoint Naming

- ✅ **Good**: Use plural nouns for collections (`/users`, `/orders`)
- ❌ **Bad**: Use verbs in the URL (`/getUsers`, `/createOrder`)

### Error Status Codes

- ✅ **Good**: Use 400 for validation errors, 401 for auth, 404 for not found
- ❌ **Bad**: Always return 200 with an error object inside

## Decision Guide

- **If creating a new endpoint**: Check if it fits an existing resource collection first.
- **If returning multiple items**: ALWAYS include pagination metadata.
