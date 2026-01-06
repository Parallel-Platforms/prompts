# API Design Review Prompt

> Review API designs for RESTful best practices,
> consistency, and developer experience.

---

## Prompt

Review the API design I provide. Evaluate it against REST
best practices and provide improvement recommendations.

### Review Criteria

#### 1. Resource Naming

- **Nouns, not verbs** — `/users` not `/getUsers`
- **Plural resources** — `/orders` not `/order`
- **Kebab-case** — `/user-profiles` not `/userProfiles`
- **Hierarchical relationships** — `/users/{id}/orders`
- **No file extensions** — `/users` not `/users.json`

#### 2. HTTP Methods

| Method | Purpose              | Idempotent | Safe |
| ------ | -------------------- | ---------- | ---- |
| GET    | Retrieve resource(s) | Yes        | Yes  |
| POST   | Create resource      | No         | No   |
| PUT    | Replace resource     | Yes        | No   |
| PATCH  | Partial update       | No         | No   |
| DELETE | Remove resource      | Yes        | No   |

#### 3. Status Codes

| Code | When to Use                              |
| ---- | ---------------------------------------- |
| 200  | Success with body                        |
| 201  | Created (return new resource)            |
| 204  | Success, no content                      |
| 400  | Bad request (client error)               |
| 401  | Unauthorized (no/invalid auth)           |
| 403  | Forbidden (valid auth, no permission)    |
| 404  | Not found                                |
| 409  | Conflict (duplicate, state conflict)     |
| 422  | Unprocessable entity (validation failed) |
| 429  | Rate limited                             |
| 500  | Server error                             |

#### 4. Request/Response Design

- **Consistent field naming** — camelCase or snake_case, not
  mixed
- **Timestamps** — ISO 8601 format (`2024-01-15T10:30:00Z`)
- **Pagination** — Offset/limit or cursor-based
- **Filtering** — Query params for filters
- **Sorting** — `?sort=created_at:desc`
- **Sparse fieldsets** — `?fields=id,name,email`

#### 5. Error Responses

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Request validation failed",
    "details": [
      {
        "field": "email",
        "message": "Invalid email format"
      }
    ]
  }
}
```

### Review Report Format

```markdown
## API Design Review

**Overall Assessment:** [Good / Needs Improvement / Major
Issues]

### Endpoints Reviewed

| Endpoint   | Method | Issues         |
| ---------- | ------ | -------------- |
| `/users`   | GET    | ✅ None        |
| `/getUser` | GET    | 🔴 Verb in URL |

### Issues Found

#### 🔴 Critical

**Issue:** [Description] **Current:** `GET /getUsers`
**Recommended:** `GET /users` **Reason:** [Why this matters]

#### 🟡 Important

[Same format]

#### 🔵 Suggestions

[Same format]

### Security Checklist

- [ ] Authentication required on protected endpoints
- [ ] Authorization checked for resource ownership
- [ ] Rate limiting in place
- [ ] Input validation on all endpoints
- [ ] No sensitive data in URLs (use body/headers)
- [ ] HTTPS enforced
- [ ] CORS configured appropriately

### Consistency Checklist

- [ ] Consistent naming convention across all endpoints
- [ ] Consistent response envelope structure
- [ ] Consistent error response format
- [ ] Consistent pagination approach
- [ ] Consistent date/time format

### Documentation Recommendations

- [ ] OpenAPI/Swagger spec provided
- [ ] Example requests for each endpoint
- [ ] Example responses (success and error)
- [ ] Authentication guide
- [ ] Rate limit documentation
```

### Questions to Consider

1. Who are the API consumers? (Internal, partners, public)
2. What's the versioning strategy? (`/v1/`, header, query
   param)
3. How will breaking changes be handled?
4. What's the expected scale? (Rate limiting, caching)
5. How will the API evolve? (Extensibility)
