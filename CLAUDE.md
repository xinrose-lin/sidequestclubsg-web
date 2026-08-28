# Claude Code brief — Side Quest Club site

Read `README.md` first; it is the complete spec.

## What's here
- `index.html` — working prototype (high fidelity), deployable as-is. **Keep the sibling `assets/` folder with it**: the trail-walker sprites are constructed at runtime from the path `assets/tomato-hero.png`, so they are not inlined in the bundle and 404 if `assets/` isn't next to `index.html`.
- `source/` — authored source of that prototype: one HTML file with an inline-styled template plus a JS logic class, its `support.js` runtime, and pixel-art assets. Treat it as the reference for exact values and behavior, not as production code.

## Two valid paths

**A. Ship the static prototype now.** `index.html` + `vercel.json` are already a zero-config static site. `npx vercel --prod` from this folder. Good for a first live URL.

**B. Rebuild properly (recommended for anything ongoing).** Scaffold Next.js (App Router) + TypeScript and port the page:
1. One route (`app/page.tsx`) with components `Header`, `Hero`, `WhySection`, `RoadmapTimeline`, `PartySection`, `JoinSection`, `WaitlistModal`, `MascotTrail`.
2. Move assets to `public/assets/`; keep `image-rendering: pixelated` on every one.
3. Load Inter (300/400/600/800) and VT323 via `next/font/google`.
4. Port tokens from the README's table into whatever styling layer the project uses (Tailwind theme extension or CSS variables). Radius is 0 everywhere; shadows are hard offsets, never blurred.
5. `MascotTrail` is a client component owning the SVG paths, pointer/scroll/resize listeners, and follow mode. Clean up every listener on unmount; skip it entirely under `prefers-reduced-motion` and below 860px / coarse pointer.
6. `WaitlistModal` is a client component. Replace the prototype's state-only submit with a real handler: a route handler (`app/api/waitlist/route.ts`) posting to Resend/Mailchimp/a sheet, with loading + error states (the prototype has neither — add them).
7. Keep the two Google Form URLs (README → External links) on the Apply CTAs.

## Non-negotiables
- Keep `text-transform: lowercase` on the body (or lowercase the copy) — the all-caps strings are intentional and render lowercase.
- Copy is final. Don't reword, don't "fix" the intentional casual voice ("tooo!", "ketch-ups", ":)").
- Zero border radius, hard pixel shadows, 3–4px borders. No blurred shadows, no gradients beyond the existing conic checker overlays.
- Preserve the global focus ring (`3px solid #D5A945`, offset 3px) and keep timeline cards keyboard-focusable.
- Add `prefers-reduced-motion` handling — the prototype lacks it.
