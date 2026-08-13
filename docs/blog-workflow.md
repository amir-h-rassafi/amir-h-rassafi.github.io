# Blog And Newsletter Workflow

This site should eventually list writing from Beehiiv while keeping the website fast and static.

## Intended Content Flow

```text
Beehiiv publication
  -> Beehiiv RSS or API
  -> Astro build
  -> static homepage writing list and /writing archive
  -> Medium/Substack mirror links
```

## First Implementation

Use Beehiiv RSS first if the publication exposes a stable public feed.

- No API key is needed.
- GitHub Pages can build static HTML from the feed.
- `/blog/` can show the latest published posts above or beside the subscribe form.
- The homepage should stay simple and only link to `/blog/` unless there are real posts worth featuring.
- Each listed item should link to the Beehiiv-hosted `web_url` until full Astro-rendered posts are justified.

Recommended structure:

```text
src/content.config.ts
src/pages/writing/index.astro
src/components/WritingList.astro
src/components/SubscribeForm.astro
```

If local posts are added before Beehiiv is ready, use:

```text
src/content/blog/*.md
```

and define a `blog` collection in `src/content.config.ts`.

## Later Implementation

Use Beehiiv API when RSS is not enough or when richer post metadata is needed.

- Use Beehiiv `GET /v2/publications/:publicationId/posts` at build time.
- Store `BEEHIIV_API_KEY` in GitHub Actions secrets.
- Store `BEEHIIV_PUBLICATION_ID` in GitHub Actions variables or repository config.
- Never expose the key in frontend JavaScript.
- Fetch posts during `npm run build` or through a controlled GitHub Action.
- Commit no generated secrets, raw API responses, or private subscriber data.
- Render only published/public posts.

## Domain Notes

Keep Astro/GitHub Pages as the canonical website and `/blog/` as the website-owned blog surface.

- If a custom domain is added later, point the root/apex or `www` domain to Astro.
- Use a Beehiiv subdomain such as `newsletter.example.com` for Beehiiv-hosted publication pages if needed.
- Do not iframe the Beehiiv publication into `/blog/`; list posts natively in Astro and link out to Beehiiv post URLs.
- Beehiiv custom domain setup belongs in DNS/domain planning, not in the Astro route structure.

## Definition Of Done For A Writing Feature

- The homepage lists only real published content.
- The canonical source is clear.
- Medium/Substack are labeled as mirrors if shown.
- `npm run build` passes.
- No placeholder newsletter/signup UI is visible unless it works.
