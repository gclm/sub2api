```markdown
# sub2api Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches the core development patterns, coding conventions, and common workflows for contributing to the **sub2api** project. The repository is primarily written in Go, with a frontend in TypeScript/Vue. It covers backend API development, frontend admin features, gateway refactoring, and robust testing practices. By following these guidelines, you can efficiently add features, fix bugs, and maintain code quality in sub2api.

---

## Coding Conventions

### File Naming

- **Go files:** Use `snake_case` (e.g., `openai_gateway_handler.go`)
- **Frontend files:** Use `snake_case` for TypeScript and Vue files (e.g., `usage_view.vue`, `admin_api.ts`)
- **Test files:** Suffix with `_test.go` (Go) or `.spec.ts` (frontend)

### Imports

- **Go:** Mixed style (grouped and single-line)
    ```go
    import (
        "context"
        "net/http"
        myutil "sub2api/internal/util"
    )
    ```
- **TypeScript:** Standard ES module imports
    ```ts
    import { fetchUsage } from './api/admin/usage_api'
    ```

### Exports

- **Go:** Named exports (capitalize exported functions/types)
    ```go
    func HandleGatewayRequest(w http.ResponseWriter, r *http.Request) { ... }
    ```
- **TypeScript:** Named exports
    ```ts
    export function fetchUsage(params: UsageParams) { ... }
    ```

### Commit Messages

- Use prefixes: `refactor:`, `fix:`, `feat:`, `perf:`
- Keep messages concise (~52 characters)
    ```
    fix: handle nil pointer in gateway error response
    ```

---

## Workflows

### Add or Enhance Admin Frontend Feature

**Trigger:** When adding or improving an admin UI feature (e.g., tooltips, usage views).  
**Command:** `/new-admin-frontend-feature`

1. Edit or create Vue component(s) under `frontend/src/views/admin/` or `frontend/src/components/admin/`.
2. Update i18n translation files:
    - `frontend/src/i18n/locales/en.ts`
    - `frontend/src/i18n/locales/zh.ts`
3. Add or update related API files in `frontend/src/api/admin/`.
4. Write or update frontend tests:
    - `frontend/src/views/admin/__tests__/*.spec.ts`
    - `frontend/src/components/admin/**/__tests__/*.spec.ts`

**Example:**
```vue
<!-- frontend/src/components/admin/usage_tooltip.vue -->
<template>
  <span>{{ $t('usage.tooltip') }}</span>
</template>
```
```ts
// frontend/src/api/admin/usage_api.ts
export function fetchUsage(params) {
  return http.get('/admin/usage', { params });
}
```

---

### Add or Enhance Admin API Endpoint

**Trigger:** When adding or extending an admin API endpoint (e.g., sync models, usage filters).  
**Command:** `/new-admin-api-endpoint`

1. Edit or create backend handler file in `backend/internal/handler/admin/*_handler.go`.
2. Update backend routing in `backend/internal/server/routes/admin.go`.
3. Optionally update/add service/repository logic:
    - `backend/internal/service/`
    - `backend/internal/repository/`
4. Update/add frontend API file in `frontend/src/api/admin/`.
5. Update/create related frontend component(s) in `frontend/src/components/admin/` or `frontend/src/views/admin/`.

**Example:**
```go
// backend/internal/handler/admin/usage_handler.go
func HandleAdminUsage(w http.ResponseWriter, r *http.Request) { ... }
```
```go
// backend/internal/server/routes/admin.go
router.HandleFunc("/admin/usage", HandleAdminUsage).Methods("GET")
```

---

### Gateway Refactor Cycle

**Trigger:** When optimizing or refactoring gateway backend logic (request/response/memory handling).  
**Command:** `/refactor-gateway`

1. Edit multiple files in `backend/internal/handler/` and `backend/internal/service/` related to gateway logic.
2. Update or add tests in `backend/internal/service/` (e.g., `*_test.go`, `*_benchmark_test.go`).
3. Make incremental commits, each targeting a specific aspect (e.g., request body retention, error handling).

**Example:**
```go
// backend/internal/service/gateway_request.go
func retainRequestBody(req *http.Request) error { ... }
```
```go
// backend/internal/service/gateway_request_test.go
func TestRetainRequestBody(t *testing.T) { ... }
```

---

### Bugfix with Targeted Test Update

**Trigger:** When fixing a backend bug and ensuring it's covered by a test.  
**Command:** `/bugfix-with-test`

1. Edit the relevant backend service or handler file:
    - `backend/internal/service/*.go`
    - `backend/internal/handler/*.go`
2. Update or add a test file:
    - `backend/internal/service/*_test.go`
    - `backend/internal/handler/*_test.go`

**Example:**
```go
// backend/internal/service/usage_service.go
func (s *UsageService) CalculateUsage(...) error { ... }
```
```go
// backend/internal/service/usage_service_test.go
func TestCalculateUsageHandlesNil(t *testing.T) { ... }
```

---

## Testing Patterns

- **Backend (Go):**
    - Test files use `_test.go` suffix.
    - Use Go's `testing` package.
    - Benchmark tests use `_benchmark_test.go`.

    ```go
    func TestGatewayHandler(t *testing.T) { ... }
    ```

- **Frontend:**
    - Uses `vitest` framework.
    - Test files use `.spec.ts` suffix.
    - Tests are colocated under `__tests__` directories.

    ```ts
    // frontend/src/views/admin/__tests__/usage_view.spec.ts
    import { describe, it, expect } from 'vitest'
    ```

---

## Commands

| Command                     | Purpose                                                        |
|-----------------------------|----------------------------------------------------------------|
| /new-admin-frontend-feature | Add or enhance an admin frontend feature (UI, i18n, tests)     |
| /new-admin-api-endpoint     | Add or enhance an admin API endpoint (backend, frontend, UI)   |
| /refactor-gateway           | Perform a gateway backend refactor cycle                       |
| /bugfix-with-test           | Fix a backend bug and update/add a corresponding test          |
```
