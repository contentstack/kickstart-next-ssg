---
name: typescript
description: TypeScript and ESLint conventions, path aliases, and where to place new code.
---

# TypeScript – kickstart-next-ssg

## When to use

- Adding `.ts` / `.tsx` files or changing compiler options
- Understanding the `@/` import alias or strictness
- Adjusting ESLint behavior for this project

## Instructions

### Compiler (tsconfig.json)

- `strict: true`, `noEmit: true`, `jsx: "react-jsx"`, `moduleResolution: "bundler"`, `isolatedModules: true`.
- Path alias: `@/*` maps to the repository root — e.g. `@/lib/contentstack`, `@/pages/...`.
- Include pattern covers `**/*.ts`, `**/*.tsx`, and `.next/types/**/*.ts`.

### Layout

- Shared app logic: [lib/](../../lib/) (e.g. Contentstack client, types).
- Routes and page components: [pages/](../../pages/).

### ESLint ([eslint.config.mjs](../../eslint.config.mjs))

- Extends `eslint-config-next` core-web-vitals and TypeScript presets.
- Explicit rule: `@typescript-eslint/no-explicit-any` is **off** (matches existing SDK/metadata typing patterns).
- Global ignores: `.next/`, `out/`, `build/`, `next-env.d.ts`.

### Commands

- `npm run lint` — project ESLint entry point.
