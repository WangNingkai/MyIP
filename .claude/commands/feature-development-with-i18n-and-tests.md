---
name: feature-development-with-i18n-and-tests
description: Workflow command scaffold for feature-development-with-i18n-and-tests in MyIP.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /feature-development-with-i18n-and-tests

Use this workflow when working on **feature-development-with-i18n-and-tests** in `MyIP`.

## Goal

Implements or refactors a feature, updating Vue components, localization files for multiple languages, and associated tests.

## Common Files

- `frontend/components/**/*.vue`
- `frontend/locales/en.json`
- `frontend/locales/fr.json`
- `frontend/locales/tr.json`
- `frontend/locales/zh.json`
- `tests/*.js`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or create frontend/components/*.vue files for the feature
- Update frontend/locales/en.json, fr.json, tr.json, zh.json with new or changed strings
- Update or add relevant test files (tests/*.js)
- Update frontend/data/changelog.json if the feature is user-facing
- Update package.json version if needed

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.