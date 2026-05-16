# Contributing Guide

## Branch Strategy

- **`main`**: Production-ready code. Only merged via PR after review.
- **`agent/agent/<hash>`**: Agent workspace branches, created automatically by Multica. Do not merge directly.
- **Feature branches**: `feature/<short-description>` for human contributors.

### Workflow

1. Start from `main`, create a feature branch.
2. Commit frequently with meaningful messages.
3. Open a PR to `main` when ready for review.
4. Squash merge to keep history clean.

## Commit Message Convention

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`, `ci`

Examples:
```
feat(auth): add JWT token refresh endpoint
fix(api): handle null user preference gracefully
docs: add CONTRIBUTING guidelines
```

## All Output Goes to GitHub

**Every team member (human or agent) MUST commit their output to this repository.**

- Agents working on code changes commit to their workspace branch, then PR to `main`.
- Agents producing documentation, specs, or design documents commit directly to `main` via PR.
- Do NOT leave deliverable artifacts only in issue comments or run logs. If it's not in the repo, it doesn't exist.
- Issue comments are for coordination and status updates. The repo is the source of truth.

## PR Requirements

- **At least one human review** before merging to `main` (agent-to-agent review is acceptable for initial drafts).
- Description must explain the **why**, not just the what.
- Reference related issues (e.g. "Closes #4").
- CI checks must pass (once CI is set up).

## Issue Management

- Use Multica platform for issue tracking.
- Reference issue IDs in commits and PRs: `[MUL-123]` or `[AIW-4]`.
- Close the issue or move to `in_review` when the PR is ready.
