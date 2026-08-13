# AI Agent Context

This repository is the Astro source for `https://amir-h-rassafi.github.io/`.

## Current Site Shape

- Framework: Astro
- Host: GitHub Pages
- Deploy path: GitHub Actions workflow in `.github/workflows/deploy.yml`
- Main page: `src/pages/index.astro`
- Global styles: `src/styles/global.css`
- Public assets: `public/`
- Analytics: Google Analytics tag `G-15X1490YRK` in `src/pages/index.astro`

## Astro Structure Rules

Follow Astro's documented project structure:

- Put routes in `src/pages/`.
- Put reusable Astro UI in `src/components/` when a section becomes reusable.
- Put shared layouts in `src/layouts/` when adding multiple pages.
- Put global/shared CSS in `src/styles/`.
- Put static files that should be copied unchanged in `public/`.
- Do not reintroduce root-level `index.html`, `style.css`, or hand-written static-site entrypoints.

For writing/blog content:

- Prefer Astro Content Collections.
- Define collections in `src/content.config.ts`.
- Store local Markdown/MDX content under `src/content/` or load remote content at build time.
- Beehiiv is the intended source of truth. Medium/Substack should be treated as mirrors, not canonical sources.
- Do not put Beehiiv API keys in browser code. Use GitHub Actions secrets for private API access.

Useful Astro docs:

- Project structure: https://docs.astro.build/en/basics/project-structure/
- Content collections: https://docs.astro.build/en/guides/content-collections/
- Content loader API: https://docs.astro.build/en/reference/content-loader-reference/

## Golden Rules For AI-Driven Work

1. Keep the site static-first.
   Build content into HTML at Astro build time. Avoid client-side fetching unless the feature genuinely requires live data.

2. Keep source-of-truth boundaries explicit.
   Beehiiv owns writing/newsletter content. The website presents it. Medium and Substack are mirrors. Do not duplicate content manually unless it is marked as a temporary snapshot.

3. Keep every change deployable and small.
   Run `npm run build` before finishing. Avoid experimental animation/framework code unless it is isolated, documented, and actually used.

## Verification Checklist

Before ending an implementation:

- Run `npm run build`.
- Confirm there are no unused experimental dependencies.
- Confirm analytics tag `G-15X1490YRK` remains if editing `src/pages/index.astro`.
- Confirm GitHub Pages workflow still targets Node 22.
- Confirm new routes live under `src/pages/`.
