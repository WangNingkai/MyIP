---
name: add-or-enhance-api-endpoint
description: Workflow command scaffold for add-or-enhance-api-endpoint in MyIP.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-enhance-api-endpoint

Use this workflow when working on **add-or-enhance-api-endpoint** in `MyIP`.

## Goal

Adds a new API endpoint or enhances an existing one, including backend logic, API handler, documentation, and sometimes frontend integration.

## Common Files

- `api/*.js`
- `backend-server.js`
- `api/AGENTS.md`
- `AGENTS.md`
- `.env.example`
- `frontend/components/**/*.vue`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create or update api/handler.js for the new endpoint
- Modify backend-server.js to register the new route or middleware
- Update or create documentation in api/AGENTS.md (and/or AGENTS.md)
- If needed, update .env.example for new environment variables
- Update frontend components to consume the new endpoint

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.