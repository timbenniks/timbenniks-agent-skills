---
name: sdk-readiness-audit
description: Audit an API surface (OpenAPI 3.0/3.1, GraphQL schema, or REST docs) for SDK readiness and developer experience. Use when asked to evaluate whether an API is SDK friendly, produce a readiness scorecard, list concrete refactors, describe "if we shipped an SDK today" pain points, or suggest OpenAPI fixes and x-* extensions to improve client generation.
---

# SDK readiness audit

Audit whether an API is actually SDK friendly and actionable. Do not generate an SDK. Diagnose gaps and provide concrete fixes.

## Scope

- Accept OpenAPI (URL or local file), GraphQL schema (SDL or introspection), or REST docs (links or markdown)
- Produce a readiness scorecard, prioritized refactors, SDK pain points, and spec fix suggestions
- Avoid guessing; mark unknowns and request missing inputs

## Mandatory intake questions (ask in one concise block)

1. Source of truth
   - OpenAPI URL or local path, GraphQL SDL/introspection, or REST docs link/markdown
2. Target SDK consumers
   - Primary languages or platforms (if any)
   - Primary use cases or top workflows
3. Auth and environments
   - Auth methods, token types, and environments (prod/sandbox)
4. Known pain points
   - Any current client friction or support issues

If the user already provided answers, restate and confirm.

## Workflow

1. Load inputs
   - For OpenAPI, parse: servers, security, tags, paths, components, schemas
   - For GraphQL, parse: types, inputs, enums, connections, directives, deprecations
   - For REST docs, build an endpoint inventory table before scoring
2. Build a surface inventory
   - Endpoints/operations and their purpose
   - Request and response shapes
   - Auth, pagination, errors, versioning, rate limits
3. Evaluate with the rubric
   - Score each category 0 to 5
   - Cite concrete evidence (endpoint names, schema fields, headers)
4. Produce outputs
   - Scorecard
   - Refactors with priority
   - "If we shipped an SDK today" pain points
   - Suggested OpenAPI fixes and x-* extensions
5. Write the audit file
   - Save the full output to `sdk-readiness-audit.md`
6. Call out unknowns
   - List missing or ambiguous areas that block full confidence

## Scoring rubric (0 to 5)

Score each category. Use "unknown" if evidence is missing.

0 = missing or harmful
1 = inconsistent or ad hoc
3 = workable but rough for SDKs
5 = strong and SDK friendly

Categories (weighted):

- Auth and environments (weight 2)
- Errors and error model (weight 2)
- Pagination and collection design (weight 2)
- Naming and resource model
- Consistency and conventions
- Data model quality (types, required/optional, enums, nullability)
- Filtering, sorting, and search
- Versioning and stability
- Idempotency and safety semantics
- Long running operations and async jobs
- Rate limits and retries
- Documentation and examples
- SDK metadata readiness (operationId, tags, schema names)

Overall score (0 to 100):

- Weighted average * 20
- If any critical category (auth, errors, pagination) is <= 2, cap overall at 59 and label "not ready"

## Output format (required)

Write the full output to `sdk-readiness-audit.md`. In chat, provide a brief summary and point to the file.

1. Readiness verdict
   - Ready / Borderline / Not ready
   - Overall score

2. SDK readiness scorecard
   - Table with category, score, evidence, and brief notes

3. Concrete refactors needed
   - Prioritized list with P0/P1/P2
   - Each item includes: current issue, why it hurts SDKs, proposed fix

4. If we shipped an SDK today, here is what would hurt
   - Short bullet list focused on developer friction

5. Suggested OpenAPI fixes and x-* extensions
   - Provide specific fixes and optional vendor extensions
   - Use small YAML snippets when helpful

6. Unknowns and requested follow ups
   - Only if needed

## OpenAPI fixes and x-* extensions (guidance)

Suggest fixes that improve client generation and developer experience. Examples:

- Normalize `operationId` or provide x-sdk-method-name
- Group operations with tags or x-sdk-group
- Define consistent error schema (Problem Details or equivalent)
- Standardize pagination and document in x-pagination
- Mark idempotent operations with x-idempotency
- Mark retryable errors with x-retryable
- Add examples and x-examples per operation
- Clarify rate limit headers with x-rate-limit

Keep extensions minimal and consistent. Do not invent semantics that conflict with the spec.

## GraphQL specific checks

- Prefer consistent connection-based pagination for lists
- Avoid unbounded lists without pagination args
- Use input objects for mutations
- Prefer enums over freeform strings
- Provide clear deprecations
- Document nullability and error behavior

## REST docs specific checks

- Build an explicit endpoint inventory first
- Identify missing details (auth, error schema, pagination, versioning)
- Propose a minimal OpenAPI skeleton to close gaps

## Acceptance criteria

Output is correct only if:

- All intake questions were asked or confirmed
- Evidence is cited for each score
- Refactors are concrete and actionable
- Pain points are clearly stated
- OpenAPI fixes or x-* extensions are suggested where relevant
- Unknowns are explicitly listed when information is missing
- `sdk-readiness-audit.md` was written with the full audit
