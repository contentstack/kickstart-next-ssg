---
name: code-review
description: Pull-request checklist for security, Contentstack credentials, sanitization, and image configuration.
---

# Code review – kickstart-next-ssg

## When to use

- Before approving or merging a pull request
- Auditing changes that touch env vars, CMS integration, or user-facing HTML

## Instructions

### Secrets and configuration

- No real `.env` values or delivery/preview tokens committed; use placeholders in docs only.
- New `NEXT_PUBLIC_*` keys are exposed to the browser—avoid putting sensitive server-only secrets behind that prefix.

### Contentstack

- Token scopes and preview settings stay aligned with [README.md](../../README.md) (preview-capable delivery token, Live Preview environment).

### Security and dependencies

- PRs trigger SCA ([.github/workflows/sca-scan.yml](../../.github/workflows/sca-scan.yml)); be explicit about new dependencies and known advisories.
- Public repos: `SECURITY.md` and license file expectations per [.github/workflows/policy-scan.yml](../../.github/workflows/policy-scan.yml).

### HTML and XSS

- Rich text and block copy use `dangerouslySetInnerHTML` only after `isomorphic-dompurify` in [pages/index.tsx](../../pages/index.tsx); preserve or improve sanitization when changing markup.

### Images

- New remote image domains must be reflected in [next.config.mjs](../../next.config.mjs) `images.remotePatterns` (or env-driven hostname) so `next/image` does not break at runtime.

### Quality

- Run `npm run lint` locally for substantive TS/React changes.
