---
name: devex-prd-generator
description: Generate a DevEx-grade PRD from messy intent or fuzzy goals. Use when asked to turn raw ideas into a structured PRD focused on developer experience (DX/DevEx), SDKs, APIs, CLIs, tooling, onboarding, or platform adoption; include problem framing, developer journey impact, non-goals, success metrics, API/SDK/docs implications, and a rollout/adoption plan.
---

# DevEx PRD generator

Turn a messy idea into a DevEx-grade PRD. Prioritize developer productivity, friction removal, and adoption mechanics over generic product narrative.

## Scope

- Accept raw intent, notes, or a vague goal
- Produce the required DevEx PRD sections
- Avoid hand-wavy outcomes; make impacts measurable
- Mark unknowns and ask follow-up questions

## Mandatory intake questions (ask in one concise block)

1. Raw intent (one sentence is fine)
2. Target developers (internal/external, roles, seniority)
3. Primary workflows or jobs-to-be-done (top 1 to 3)
4. Current pain points or friction (where do devs get stuck)
5. Constraints (platforms, timelines, dependencies, compliance)
6. Existing surfaces that might change (API, SDKs, CLI, docs, tools)
7. Success signals (if known)
8. Must-not-change or out-of-scope areas

If the user already provided answers, restate and confirm before proceeding.

## Workflow

1. Parse the intent into a DevEx problem statement
2. Identify the developer journey and where friction occurs
3. Define the desired journey delta (before vs after)
4. Clarify non-goals to prevent scope creep
5. Translate the idea into concrete API/SDK/docs implications
6. Define success metrics (leading + lagging)
7. Propose a rollout and adoption plan (phased + comms)
8. Call out assumptions, risks, and open questions if inputs are missing

## Quality bar (DevEx-grade)

- Tie every claim to a developer task, workflow, or outcome
- Use “before / after” language for journey impact
- Prefer specific changes (endpoints, methods, docs pages) over vague improvements
- Make non-goals explicit and defensible
- Include adoption mechanics (migration, enablement, deprecation)
- Keep the document crisp; avoid generic product-speak

## Output format (required)

1. Problem framing
   - Context and why now
   - Who is impacted and how
   - Root causes or constraints
   - Desired outcome in one sentence

2. Developer journey impact
   - Current journey (steps + pain points)
   - Proposed journey (steps + deltas)
   - Touchpoints affected (API, SDK, CLI, docs, tooling)
   - Expected time or effort savings

3. Non-goals (crucial)
   - Explicit list with brief rationale

4. Success metrics
   - Leading indicators (adoption, activation, usage)
   - Lagging indicators (support tickets, time-to-first-success, retention)
   - Measurement method or source (if known)

5. API, SDK, docs implications
   - API changes (new endpoints, breaking changes, versioning)
   - SDK changes (methods, typing, ergonomics, errors)
   - CLI/tooling changes (commands, flags, output)
   - Docs and samples (new guides, updates, migration docs)

6. Rollout and adoption plan
   - Phases (alpha/beta/GA or pilot plan)
   - Migration path and compatibility strategy
   - Communication plan (what, when, to whom)
   - Enablement (samples, templates, onboarding, internal champions)

7. Assumptions, risks, and open questions (only if needed)
   - Bullet list; ask for missing inputs

## Acceptance criteria

Output is correct only if:

- All required sections are present
- Non-goals are explicit and concrete
- Journey impact is expressed as before/after
- Success metrics are measurable
- API/SDK/docs implications are actionable
- Rollout plan addresses adoption and migration
