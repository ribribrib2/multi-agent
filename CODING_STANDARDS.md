# Coding Standards

## General Principles

- **Simplicity first**: Prefer readable, straightforward code over clever solutions.
- **No dead code**: Remove unused imports, functions, and files. Don't comment out — delete.
- **One responsibility per function/class**: If it does two things, split it.
- **Fail fast, fail loud**: Validate inputs at boundaries. Let internal code trust its callers.

## Language-Specific Standards

When a language is chosen for a component, add a `<language>_STANDARDS.md` file covering:

- Linter/formatter configuration (commit config files to repo)
- Dependency management (lock files committed, no unpinned deps)
- Testing framework and conventions
- Error handling patterns
- Logging conventions

## Code Review Checklist

Every PR should be checked against:

- [ ] **Correctness**: Does it do what the issue describes?
- [ ] **Security**: No hardcoded secrets, SQL injection, XSS, path traversal.
- [ ] **Error handling**: Errors are caught and surfaced meaningfully.
- [ ] **Tests**: New logic is covered by tests.
- [ ] **Readability**: A new team member can understand the code in 5 minutes.
- [ ] **No regressions**: Existing tests pass; no unrelated changes.

## Test Requirements

- **Unit tests**: Required for all business logic.
- **Integration tests**: Required for anything touching external systems (DB, API, filesystem).
- **No skipped tests**: A skipped test is a bug waiting to be filed.
- Tests must be deterministic — no flakes.

## Security

- **Secrets**: Never commit `.env`, credentials, tokens, or keys. Use environment variables or a secret manager.
- **Dependencies**: Pin versions. Audit for known CVEs before adding new dependencies.
- **Input validation**: Validate at all system boundaries (API endpoints, CLI args, file reads).
- **Principle of least privilege**: Services and agents run with minimal permissions.

## Agent-Specific Rules

For AI agents working in this repo:

- **Commit often**: Each meaningful step gets its own commit.
- **No silent changes**: Any behavioral change must have a PR description.
- **Respect the stack**: If the project uses a language/framework, match existing patterns. Don't introduce new ones without justification.
- **Clean worktrees**: Don't leave debug files, temp files, or `.DS_Store` in the repo.
