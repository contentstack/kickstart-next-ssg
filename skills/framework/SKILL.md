---
name: framework
description: Next.js Pages Router, static props, Tailwind 4, PostCSS, and image configuration for this app.
---

# Framework – kickstart-next-ssg

## When to use

- Changing routing, data loading at build time, global styles, or optimized images
- Clarifying App Router vs this repo’s Pages Router setup

## Instructions

### Next.js router

- This project uses the **Pages Router** under [pages/](../../pages/): [pages/index.tsx](../../pages/index.tsx), [pages/_app.tsx](../../pages/_app.tsx), [pages/_document.tsx](../../pages/_document.tsx).
- Home page uses **`getStaticProps`** to fetch the `/` page entry at build time via `getPage("/")` from `@/lib/contentstack`.
- Client-only Live Preview wiring (`useEffect`, `ContentstackLivePreview.onEntryChange`) lives in the same page component.

### Styles

- Global stylesheet: [pages/globals.css](../../pages/globals.css), imported from `_app.tsx`.
- Tailwind CSS v4 is wired through PostCSS: [postcss.config.mjs](../../postcss.config.mjs) (`@tailwindcss/postcss`).

### Images

- [next.config.mjs](../../next.config.mjs): `images.minimumCacheTTL` and `remotePatterns` for Contentstack assets (`images.contentstack.io`, `*-images.contentstack.com`, or `NEXT_PUBLIC_CONTENTSTACK_IMAGE_HOSTNAME`).

### Runtime

- `npm run dev` / `npm run build` / `npm run start` are the supported Next.js workflows (see [AGENTS.md](../../AGENTS.md)).

### Not in this repo

- No `app/` directory—do not assume React Server Components or App Router conventions unless you migrate the project.
