# Team Alignment Specification

## Overview

This document defines how team members (human and AI agents) coordinate, deliver, and align on work within the multi-agent project.

## 1. Output Delivery to GitHub

**Rule: If it's not in the repo, it doesn't exist.**

- All deliverables — code, docs, configs, specs — must be committed to GitHub.
- Issue comments are for coordination, status updates, and discussion only.
- Agents commit to their workspace branch (`agent/agent/<hash>`) and open a PR to `main`.
- Humans commit to feature branches (`feature/<description>`) and open a PR to `main`.
- Do not leave artifacts only in Multica run logs or issue attachments.

### What Counts as Output

| Type | Deliverable | Location |
|------|-------------|----------|
| Code | Source files, tests, configs | `src/`, `tests/`, etc. |
| Docs | Specs, guides, decisions | `docs/` or repo root |
| Config | Build, lint, CI, Docker | Repo root or `.github/` |
| Design | Architecture diagrams, RFCs | `docs/design/` |
| Data | Migration scripts, fixtures | `migrations/`, `fixtures/` |

## 2. Upstream/Downstream Alignment

### Upstream (Dependencies You Consume)

Before starting work:

1. **Identify dependencies**: What APIs, services, or specs do you depend on?
2. **Verify availability**: Are upstream interfaces stable and documented?
3. **Pin versions**: Never depend on `main` or `latest` without a pin.
4. **Contract-first**: Define the interface you expect. If it doesn't exist, create an RFC first.

### Downstream (Consumers of Your Work)

Before delivering:

1. **Document the interface**: What does a consumer need to know to use your output?
2. **Backward compatibility**: Breaking changes require a migration path and version bump.
3. **Notify consumers**: Update downstream docs or open issues in dependent projects.
4. **Smoke test**: Verify your output works in the integration context, not just isolation.

### Cross-Team Synchronization

| Scenario | Alignment Mechanism |
|----------|-------------------|
| Shared API | API contract in `docs/api/`, versioned. Changes need consensus. |
| Shared data model | Schema in `docs/schema/`. Breaking changes require migration plan. |
| Feature dependency | Blocker issues linked; upstream marks `done` before downstream starts. |
| Cross-team PR | Both team leads approve before merge. |

## 3. Communication Protocol

### Issue Comments

- Use issue comments for: status updates, blockers, questions, handoffs.
- Use `mention://agent/...` links sparingly — they trigger another agent run. Only mention when you need them to take action.
- End comments with a clear state: what's done, what's blocked, what's next.

### Agent Handoffs

When passing work between agents:

1. **Commit your output** to your workspace branch.
2. **Comment on the issue** with what you delivered and where to find it.
3. **Mention the next agent** only if they need to take over.
4. **Update the issue status** appropriately.

### Human Handoffs

When passing work to a human:

1. **PR is ready** with clear description.
2. **Comment on the issue** with a summary of what changed and why.
3. **No `@mention` needed** — the human subscribed to the issue will see it.

## 4. Quality Gates

Every deliverable must pass:

| Gate | Criteria |
|------|----------|
| **Completeness** | Addresses the issue description fully. |
| **Correctness** | Works as described, edge cases handled. |
| **Reviewability** | PR is focused, small, and self-contained. |
| **Maintainability** | Follows coding standards, documented where non-obvious. |
| **Testability** | Covered by tests or test plan provided. |

## 5. Definition of Done

A task is **done** when:

- [ ] Code/docs are committed to a branch.
- [ ] PR is merged to `main`.
- [ ] Tests pass (existing + new).
- [ ] Issue status is updated to `done`.
- [ ] Downstream consumers are notified if applicable.
