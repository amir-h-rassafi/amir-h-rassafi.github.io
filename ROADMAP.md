# Astro + Beehiiv Roadmap

This plan keeps `https://amir-h-rassafi.github.io/` as the canonical personal website. Astro owns the website, GitHub Pages hosts it, and Beehiiv is used only for newsletter capture and email delivery.

## Research Summary

- Astro routes come from `src/pages`; the homepage is `src/pages/index.astro`.
- Astro project structure should include `src/`, `public/`, `package.json`, `astro.config.mjs`, and `tsconfig.json`.
- Static assets that should be copied unchanged can live in `public/`.
- For a username GitHub Pages repo like `amir-h-rassafi.github.io`, configure `site: "https://amir-h-rassafi.github.io"` and do not set a `base`.
- Astro's official GitHub Pages deployment path uses GitHub Actions with `withastro/action` and `actions/deploy-pages`.
- Beehiiv external subscribe forms are embedded with a script tag. Inline forms render where the script is pasted.

Sources:

- Astro project structure: https://docs.astro.build/en/basics/project-structure/
- Astro GitHub Pages deployment: https://v4.docs.astro.build/en/guides/deploy/github/
- Beehiiv embedded subscribe forms: https://www.beehiiv.com/support/article/12977090590487-creating-an-embedded-subscribe-form

## Milestone 1: Astro Foundation

Goal: replace the current hand-written static page with a professional Astro homepage while preserving every existing destination.

Deliverables:

- Add Astro project config and npm scripts.
- Build `src/pages/index.astro` as the new homepage.
- Preserve CV, Twitter/X, LinkedIn, GitHub, Stack Overflow, Instagram, Skype, email, IDPay, and YouTube links.
- Preserve Google Analytics tracking ID and outbound link click events.
- Use the existing photo asset in `public/`.
- Add GitHub Actions deployment for GitHub Pages.

Success criteria:

- `npm run build` succeeds.
- The homepage still provides every existing link.
- The design no longer depends on the old animated background.

## Milestone 2: Content Baseline

Goal: make the site useful as a professional hub before adding newsletter growth.

Deliverables:

- Add a short bio once final wording is available.
- Add selected projects or work highlights.
- Add clear SEO metadata, Open Graph metadata, and a favicon.
- Decide whether the CV link should stay external or be mirrored into `public/`.

Success criteria:

- A visitor can quickly understand who Amir is and where to go next.
- The site has a stable canonical URL and share metadata.

## Milestone 3: Beehiiv Signup

Goal: make the site the source of newsletter subscribers while Beehiiv handles the backend.

Deliverables:

- Create a Beehiiv inline form named `website-homepage-inline` or similar.
- Add a `NewsletterSignup.astro` component.
- Paste the Beehiiv embed script into the component.
- Use a Beehiiv success message first; add redirect behavior only if there is a real post-signup page.
- Confirm Beehiiv acquisition/source metadata is recorded clearly.

Success criteria:

- Visitors can subscribe without leaving the site.
- Beehiiv shows the signup source as the website form.

## Milestone 4: Beehiiv Writing Listing

Goal: keep Beehiiv as the writing/newsletter source of truth while the Astro site lists published posts cleanly.

Deliverables:

- Keep `/blog/` on Astro as the website-owned writing surface.
- Pull published Beehiiv posts at build time using Beehiiv RSS or API.
- Prefer Beehiiv API if available; store `BEEHIIV_API_KEY` in GitHub Actions secrets and never expose it in browser JavaScript.
- Render a static latest-post list on `/blog/` next to the working Beehiiv subscribe form.
- Link each post to its Beehiiv `web_url` first; render full post pages in Astro only if there is a clear need.
- Treat Medium and Substack as mirrors, not source of truth.

Success criteria:

- Publishing in Beehiiv updates the static Astro post list after the next build.
- Visitors can subscribe and browse real published writing from the same `/blog/` page.
- No API key or private Beehiiv data is shipped to the browser.

## Milestone 5: Domain Strategy

Goal: decide how the public website and Beehiiv-hosted publication should coexist if a custom domain is added.

Deliverables:

- Keep the root/apex domain or GitHub Pages URL owned by Astro.
- If using a custom domain later, use a Beehiiv subdomain such as `newsletter.example.com` rather than trying to make Beehiiv own `/blog/`.
- Do not iframe the Beehiiv publication into Astro.
- Keep `/blog/` as the Astro page that lists Beehiiv content and embeds the subscribe form.
- Document DNS requirements before changing domains; Beehiiv custom domain setup can require multiple DNS records and may take up to 72 hours to verify.

Success criteria:

- The site has one clear canonical homepage.
- Beehiiv can still host/share its own post URLs when useful.
- The user experience from homepage to blog does not feel like a disconnected redirect.

## Milestone 6: Polish And Measurement

Goal: improve performance, accessibility, and maintainability.

Deliverables:

- Replace third-party icon CSS with local SVG/icon components if performance or privacy becomes a concern.
- Review analytics/privacy posture.
- Add `robots.txt`, sitemap, and stronger social preview metadata.
- Add validation checks as the site grows.

Success criteria:

- The site remains fast, accessible, and easy to update.
- Newsletter signup and outbound links are measurable.
