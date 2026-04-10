---
name: testing
description: Test tooling status for this repo and practical notes if you introduce automated tests.
---

# Testing – kickstart-next-ssg

## When to use

- Checking whether CI or npm runs tests (it does not, yet)
- Planning unit, component, or E2E tests for this kickstart

## Instructions

### Current state

- There is **no** test script in [package.json](../../package.json).
- There are **no** `*.test.*`, `*.spec.*`, or `__tests__` directories in the repository.
- GitHub Actions workflows do not run `npm test`; PR checks are security/policy focused (see [AGENTS.md](../../AGENTS.md)).

### If you add tests

- Pick a runner and add it to `devDependencies` and `package.json` scripts—do not document a framework as “already installed” until it appears in `package.json`.
- Common options for this stack: **Vitest** or **Jest** with **React Testing Library** for components; **Playwright** for end-to-end flows against `npm run dev`.
- Co-locate or use a `tests/` (or `__tests__/`) directory and keep fixtures free of real API keys; use env files that are gitignored.
