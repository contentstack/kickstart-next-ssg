# Contentstack Kickstart: Next.js SSG – Agent guide

**Universal entry point** for contributors and AI agents. Detailed conventions live in **`skills/*/SKILL.md`**.

## What this repo is

| Field | Detail |
|-------|--------|
| **Name:** | [contentstack/kickstart-next-ssg](https://github.com/contentstack/kickstart-next-ssg) |
| **Purpose:** | Minimal Next.js static-generation sample that connects to Contentstack: Delivery SDK setup, Live Preview, and Visual Builder hooks. |
| **Out of scope (if any):** | Reference app only—not a production framework: no auth, limited error handling, single seeded `page` content model beyond what the stack seed provides. |

## Tech stack (at a glance)

| Area | Details |
|------|---------|
| Language | TypeScript 5, `strict` in [tsconfig.json](tsconfig.json) |
| Build | Next.js ^16; [next.config.mjs](next.config.mjs), [package.json](package.json) scripts |
| Tests | None configured (see [skills/testing/SKILL.md](skills/testing/SKILL.md)) |
| Lint / coverage | ESLint 9, flat config: [eslint.config.mjs](eslint.config.mjs) (`eslint-config-next`); no coverage tool in repo |
| Other | React 19, npm; Tailwind CSS 4 via PostCSS ([postcss.config.mjs](postcss.config.mjs)); Pages Router under [pages/](pages/) |

## Commands (quick reference)

| Command Type | Command |
|--------------|---------|
| Install | `npm install` |
| Build | `npm run build` |
| Dev server | `npm run dev` |
| Production serve | `npm run start` |
| Test | N/A—see [skills/testing/SKILL.md](skills/testing/SKILL.md) |
| Lint | `npm run lint` |

**CI:** Pull-request automation focuses on security and policy, not app build verification:

- [.github/workflows/sca-scan.yml](.github/workflows/sca-scan.yml) — Snyk + `contentstack/sca-policy`
- [.github/workflows/policy-scan.yml](.github/workflows/policy-scan.yml) — `SECURITY.md`, license file/year (public repos)
- [.github/workflows/issues-jira.yml](.github/workflows/issues-jira.yml) — Jira ticket on new GitHub issues

## Where the documentation lives: skills

| Skill | Path | What it covers |
|-------|------|----------------|
| Dev workflow | [skills/dev-workflow/SKILL.md](skills/dev-workflow/SKILL.md) | Setup, env, scripts, PR/CI expectations |
| Contentstack kickstart | [skills/contentstack-kickstart/SKILL.md](skills/contentstack-kickstart/SKILL.md) | SDK, env vars, `getPage`, Live Preview, content model |
| TypeScript | [skills/typescript/SKILL.md](skills/typescript/SKILL.md) | TS/ESLint conventions and layout |
| Testing | [skills/testing/SKILL.md](skills/testing/SKILL.md) | Current test state; guidance if adding tests |
| Code review | [skills/code-review/SKILL.md](skills/code-review/SKILL.md) | PR checklist for this repo |
| Framework | [skills/framework/SKILL.md](skills/framework/SKILL.md) | Next.js Pages Router, Tailwind, images config |

A short list of skill folders is in `skills/README.md` (the table above is the index).

## Using Cursor (optional)

If you use **Cursor**, [.cursor/rules/README.md](.cursor/rules/README.md) only points to **`AGENTS.md`**—same docs as everyone else.
