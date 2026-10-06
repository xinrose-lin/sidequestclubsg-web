# Claude Code brief — Side Quest Club site

Read `README.md` first; it is the complete spec.

## What's here
- `deploy/` — the working prototype (high fidelity) as three self-contained static pages plus `assets/`. It can be deployed to Cloudflare Pages as-is. Keep `assets/` beside the HTML because the sprites load at runtime.
- `source/` — the authored source of those pages. Use it as the reference for exact values and behaviour. It is not production code.

## Two valid paths

**A. Ship the static prototype now.** `npx wrangler pages deploy deploy --project-name=side-quest-club`.

**B. Rebuild properly (recommended).** Scaffold **Astro** (static output, deploys to Cloudflare Pages with zero config):
1. Pages: `src/pages/index.astro`, `quest-day.astro`, `gallery.astro`. Share a `BaseLayout` (head, fonts, header/nav, footer).
2. Components: `Header`, `Hero`, `WhySection`, `RoadmapTimeline`, `PartySection`, `JoinSection`, `WaitlistModal`. Make `MascotTrail` an island script (vanilla TS) that owns the SVG, listeners and follow mode. Skip it under `prefers-reduced-motion`, below 860px and on coarse pointers.
3. Move the assets to `public/assets/`. Keep `image-rendering: pixelated` on every one.
4. Self-host Inter (300/400/600/800) and VT323 with `@fontsource`.
5. Move the design tokens from the README into CSS custom properties in one `tokens.css`.
6. Waitlist: a Cloudflare Pages Function (`functions/api/waitlist.ts`) that posts to the email provider. Add loading and error states.
7. Keep the Google Form URLs on the Apply/RSVP CTAs.
8. Add a `<title>`, a meta description and an OG image to each page.

## Non-negotiables
- Keep `text-transform: lowercase` on the body (or lowercase the copy) — the all-caps strings are intentional and render lowercase.
- Copy is final. Don't reword, don't "fix" the intentional casual voice ("tooo!", "ketch-ups", ":)").
- Zero border radius, hard pixel shadows, 3–4px borders. No blurred shadows, no gradients beyond the existing conic checker overlays.
- Preserve the global focus ring (`3px solid #D5A945`, offset 3px) and keep timeline cards keyboard-focusable.
- Add `prefers-reduced-motion` handling — the prototype lacks it.
