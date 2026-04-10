---
name: contentstack-kickstart
description: Contentstack Delivery SDK, environment variables, Live Preview, and the seeded page model in this kickstart.
---

# Contentstack kickstart – kickstart-next-ssg

## When to use

- Changing how the app fetches or displays CMS content
- Debugging Live Preview or Visual Builder integration
- Extending TypeScript types for new fields or content types

## Instructions

### Entry points

- Stack and helpers: [lib/contentstack.ts](../../lib/contentstack.ts) — `stack`, `initLivePreview()`, `getPage(url)`
- CMS-aligned types: [lib/types.ts](../../lib/types.ts) — e.g. `Page`, `Block`, `File`

### Stack configuration

- Built with `@contentstack/delivery-sdk` `contentstack.stack({ ... })` using `NEXT_PUBLIC_CONTENTSTACK_API_KEY`, `NEXT_PUBLIC_CONTENTSTACK_DELIVERY_TOKEN`, `NEXT_PUBLIC_CONTENTSTACK_ENVIRONMENT`, and region-related settings.
- Optional overrides for hosts/CDN (internal or custom): `NEXT_PUBLIC_CONTENTSTACK_CONTENT_DELIVERY`, `NEXT_PUBLIC_CONTENTSTACK_PREVIEW_HOST`, `NEXT_PUBLIC_CONTENTSTACK_CONTENT_APPLICATION`, `NEXT_PUBLIC_CONTENTSTACK_PREVIEW` (boolean string), `NEXT_PUBLIC_CONTENTSTACK_PREVIEW_TOKEN`.
- Region resolution uses helpers from `@timbenniks/contentstack-endpoints` aligned with `NEXT_PUBLIC_CONTENTSTACK_REGION`.

### Fetching content

- `getPage(url)` queries content type **`page`**, field **`url`**, equality match via `QueryOperation.EQUALS`, then returns the first entry.
- When `NEXT_PUBLIC_CONTENTSTACK_PREVIEW === 'true'`, `contentstack.Utils.addEditableTags` is applied to the entry for in-editor overlays.

### Live Preview (client)

- [pages/index.tsx](../../pages/index.tsx): `initLivePreview()` runs in `useEffect`; `ContentstackLivePreview.onEntryChange` refetches the home page so the UI updates in preview.
- `initLivePreview` in `lib/contentstack.ts` uses `@contentstack/live-preview-utils` with `mode: "builder"`, stack details from env, optional application host from env/endpoints, and edit button enabled (with `outsideLivePreviewPortal` excluded).

### Seeded stack and tokens

- CLI seed and token setup are documented in root [README.md](../../README.md) (delivery token with preview scope, Live Preview environment).

### Images and URLs

- Remote image hostnames for `next/image` are configured in [next.config.mjs](../../next.config.mjs); optional `NEXT_PUBLIC_CONTENTSTACK_IMAGE_HOSTNAME` narrows or replaces defaults.
