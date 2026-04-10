---
name: dev-workflow
description: Setup, scripts, environment variables, and pull-request CI expectations for this repo.
---

# Dev workflow – kickstart-next-ssg

## When to use

- Onboarding or reproducing a local run
- Adding or changing npm scripts
- Understanding what runs on pull requests (vs local build)

## Instructions

### Prerequisites

- Node.js compatible with Next.js 16 (use a current LTS)
- npm (lockfile: `package-lock.json`)

### First-time setup

1. Clone the repo and run `npm install`.
2. Copy or create a `.env` (or `.env.local`) using the variables documented in the root [README.md](../../README.md) and summarized in [AGENTS.md](../../AGENTS.md).
3. Seed a Contentstack stack with the CLI flow in [README.md](../../README.md) (`contentstack/kickstart-stack-seed`) if you do not already have matching content types and entries.

### Scripts (from `package.json`)

- `npm run dev` — Next.js development server (default port 3000).
- `npm run build` — production build.
- `npm run start` — serve the production build (run after `build`).
- `npm run lint` — ESLint over `.ts` and `.tsx` (`eslint . --ext .ts,.tsx`).

### Pull-request automation

- **SCA:** [.github/workflows/sca-scan.yml](../../.github/workflows/sca-scan.yml) runs Snyk on Node and `contentstack/sca-policy`; does not replace local `npm run lint` or `npm run build`.
- **Policy:** [.github/workflows/policy-scan.yml](../../.github/workflows/policy-scan.yml) checks `SECURITY.md` and license files for public repositories.
- **Issues:** [.github/workflows/issues-jira.yml](../../.github/workflows/issues-jira.yml) creates Jira tickets from new GitHub issues (repository automation).

Branch naming is not enforced in this repository; follow your team’s Git conventions.
