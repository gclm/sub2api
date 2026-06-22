---
name: add-or-enhance-admin-frontend-feature
description: Workflow command scaffold for add-or-enhance-admin-frontend-feature in sub2api.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-enhance-admin-frontend-feature

Use this workflow when working on **add-or-enhance-admin-frontend-feature** in `sub2api`.

## Goal

Adds or enhances an admin feature in the frontend, typically involving UI changes, i18n updates, and new or updated tests.

## Common Files

- `frontend/src/views/admin/*.vue`
- `frontend/src/components/admin/**/*.vue`
- `frontend/src/i18n/locales/en.ts`
- `frontend/src/i18n/locales/zh.ts`
- `frontend/src/api/admin/*.ts`
- `frontend/src/views/admin/__tests__/*.spec.ts`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or create Vue component(s) under frontend/src/views/admin or frontend/src/components/admin
- Update i18n translation files (frontend/src/i18n/locales/en.ts, zh.ts)
- Add or update related API files (frontend/src/api/admin/*.ts)
- Write or update frontend tests (frontend/src/views/admin/__tests__/*.spec.ts, frontend/src/components/admin/**/__tests__/*.spec.ts)

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.