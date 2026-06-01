---
name: add-or-enhance-admin-api-endpoint
description: Workflow command scaffold for add-or-enhance-admin-api-endpoint in sub2api.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-enhance-admin-api-endpoint

Use this workflow when working on **add-or-enhance-admin-api-endpoint** in `sub2api`.

## Goal

Adds or enhances an admin API endpoint, involving backend handler, server route, and often corresponding frontend API and UI updates.

## Common Files

- `backend/internal/handler/admin/*_handler.go`
- `backend/internal/server/routes/admin.go`
- `backend/internal/service/*.go`
- `backend/internal/repository/*.go`
- `frontend/src/api/admin/*.ts`
- `frontend/src/components/admin/**/*.vue`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or create backend handler file (backend/internal/handler/admin/*_handler.go)
- Update backend routing (backend/internal/server/routes/admin.go)
- Optionally update or add service/repository logic (backend/internal/service/, backend/internal/repository/)
- Update or add frontend API file (frontend/src/api/admin/*.ts)
- Update or create related frontend component(s) (frontend/src/components/admin/, frontend/src/views/admin/)

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.