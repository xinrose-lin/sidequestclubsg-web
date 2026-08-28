# Handoff: Side Quest Club — marketing site

## Overview
Single-page marketing site for **Side Quest Club (SQC)**: a nine-week, five-meet cohort that helps young adults with full-time jobs ship the v0 of a side project. The page explains why side quests stall, walks the cohort roadmap, states who it's for, and drives two conversions: an external Google Form application and an in-page waitlist modal.

Signature interaction: a **pixel tomato mascot** that walks an animated dirt trail down the page and, on click, follows the visitor's cursor while drawing the trail behind it.

## About the design files
The files in this bundle are **design references built in HTML** — a working prototype of the intended look and behavior, not production code to lift wholesale.

- `index.html` — bundle with JS, CSS, fonts, and static images inlined. Open it directly or deploy it as-is. Use this to test locally and to ship a first Vercel deployment. It needs the sibling `assets/` folder: the trail-walker sprites are built at runtime from the string path `assets/tomato-hero.png`, so they are not inlined and 404 if `assets/` isn't next to `index.html`.
- `source/SQC Website.dc.html` — the authored source. One component: an inline-styled template plus a JS logic class (refs, mascot trail engine, nav, waitlist state). `source/support.js` is its runtime; `source/assets/` holds the pixel art.

The intended task for a real codebase is to **recreate this design in the target environment** (Next.js/React is the natural fit for Vercel) using that project's conventions — components, styling layer, form handling — rather than pasting the prototype's inline styles. If there is no codebase yet, start a Next.js app and port the page section by section.

## Fidelity
**High fidelity.** Colors, type, spacing, copy, and motion are final. Recreate pixel-for-pixel; every value you need is below or readable in the source file.

## Local test

```bash
cd design_handoff_sqc_website
python3 -m http.server 8000      # or: npx serve .
# open http://localhost:8000
```

`index.html` also works from `file://`. To edit the *source* version, serve the `source/` folder the same way and open `SQC Website.dc.html`.

## Deploy to Vercel

Static, zero-config — the folder root already contains `index.html` and `vercel.json`.

```bash
cd design_handoff_sqc_website
npx vercel            # preview
npx vercel --prod     # production
```

Or push the folder to a Git repo and import it in the Vercel dashboard (Framework preset: **Other**, no build command, output directory `.`).

For a rebuilt Next.js version, replace the root with the app and let Vercel autodetect.

## Screens / views

One scrolling page, sticky header, five sections.

### Header (sticky)
Flex row, `space-between`, padding `clamp(10px,2vw,14px) clamp(14px,4vw,48px)`, background `rgba(14,36,23,.92)` + `backdrop-filter: blur(6px)`, bottom border `3px solid #354B38`, `z-index: 20`.
- Left: `assets/logo-bag.png` (height `clamp(38px,5.4vw,48px)`, `image-rendering: pixelated`) + stacked wordmark "Side Quest Club" (Inter 800, `clamp(14px,3vw,17px)`, `#F4EBD8`) and tagline.
- Right: nav (`#main-nav`) with anchor links to the sections and the Apply link. Below 860px it collapses behind a 3-bar burger button (bars 20×3px, `#F4EBD8`); the logic class toggles it.

### 1. Hero — `#top`
`min-height: clamp(540px,94vh,1000px)`, centered, `overflow: hidden`. Layered background: dark `#1F2F22` field with a repeating conic checker overlay, and a sand band (`#E7DEB4`) across the top `min(442px,54%)`. Visually-hidden `<h1>Side Quest Club</h1>` for a11y; the visible title is set type inside a centered panel (`max-width: 820px`).
- Mascot `assets/tomato-hero.png` perched on the panel (88px wide) with a speech bubble above it.
- CTA row (`display: flex; wrap; gap: clamp(14px,2.4vw,22px)`): primary "apply" → Google Form (`target="_blank" rel="noopener"`), secondary → waitlist modal.

### 2. Why we exist — `#why`
Eyebrow "WHY WE EXIST" (VT323, `clamp(22px,2.8vw,27px)`, `#D5A945`, letter-spacing 1.6px). H2 (Inter 800, `clamp(28px,4.6vw,50px)`, line-height 1.08, letter-spacing -1px, `#F4EBD8`, max-width 700px): "Creating a place where your ideas outside the 9-5 find its life tooo!" Lede in `#B3C6B2`, max-width 600px.
Then eyebrow "WHY SIDE QUESTS STALL" and a card grid `repeat(auto-fit, minmax(230px,1fr))`, gap `clamp(14px,2.2vw,22px)`. Cards: `3px solid #F4EBD8`, background `rgba(23,58,36,.55)`, padding 20px, hover `translateY(-5px)` + background `rgba(23,58,36,.8)`, 180ms ease. Card titles Inter 800 `clamp(17px,2vw,20px)` `#D5A945`; body 15px/1.6 `#B3C6B2`. Cards: NO STRUCTURE / NO ACCOUNTABILITY / NO COMMUNITY.

### 3. The roadmap — `#cohort`
Eyebrow "THE ROADMAP · ONE COHORT". H2 "Nine weeks. Five meets. Your idea's v0 shipped." Lede "Week by week, your idea finds its shape — and you discover new paths of your own :)".
Zig-zag timeline: `<ol>` (no list style), gap `clamp(44px,7vh,90px)`; each `<li>` is `width: min(500px,100%)` and alternates `margin-right: auto` / `margin-left: auto` (`data-quest-anchor="right|left"`). Each card `<article tabindex="0">`: background `#FBF5E4`, border `4px solid #2A3D2E`, shadow `9px 9px 0 rgba(8,24,15,.45)`, padding `clamp(22px,3.4vw,32px)`; hover/focus `translate(-4px,-4px)` + shadow `14px 14px 0 rgba(8,24,15,.5)`. Header row holds the week label and meet badge; the dirt trail SVG threads between the alternating cards.

### 4. The party — `#party`
Eyebrow "THE PARTY". H2 "Built for people with a full-time job and a restless idea." Grid `repeat(auto-fit, minmax(240px,1fr))`, gap `clamp(16px,2.4vw,26px)`. Cards: `3px solid #2A3D2E` on `#FBF5E4`, padding 24px, hover `translateY(-5px)`. Titles Inter 800 `clamp(17px,2vw,20px)` `#B8492F`; body 16px/1.6 `#566B57`.
- STRUCTURE — nine-week arc, a meet every two weeks.
- ACCOUNTABILITY — regular ketch-ups, feedback, final showcase.
- COMMUNITY — under 15 per cohort.

### 5. Join — `#join`
Centered, dark, checkered. 130px mascot, then VT323 lines "PILOT COHORT'S IDEAS ARE BREWING…" (`#D5A945`) and "STAY TUNED!" (`#B3C6B2`), then a CTA row.

### Waitlist modal
Cream card (`#FBF5E4`), dark border, hard offset shadow. Two states driven by `waitlistSent`:
1. Form: kicker "JOIN THE WAITLIST" (`#B8492F`), H2 "Get the early news…", body copy, `EMAIL` label + `#wl-email` (`type="email" required autocomplete="email" inputmode="email"`, placeholder `you@email.com`), fine print "About one email a month. No spam, unsubscribe anytime.", submit button (`#B8492F` fill, `3px solid #2A3D2E`).
2. Confirmation: mascot, "QUEST LOG UPDATED", "You're on the waitlist.", the submitted address echoed in `<strong>`, and a close button.
Escape closes the modal. **No backend** — the prototype only stores the email in component state. Wire it to a real list (Vercel serverless route → Resend/Mailchimp/Sheets) during implementation.

## Interactions & behavior
- **Mascot trail.** A full-page absolute SVG (`z-index: 3`, `opacity: .5`) draws four stacked paths: hidden geometry path, brown shadow stroke (20px, `#5E4A33`, `.3`), the dirt-pattern stroke (14px, 8×8 pixel `<pattern>` in sand tones, `.72`), and a cream tint stroke (14px, `.12`). All strokes use `stroke-linecap: butt` / `linejoin: miter` for a pixel look. The viewBox is resized to the root box on mount and resize.
- **Follow mode.** Clicking the mascot starts following: `mousemove` extends the trail toward the cursor, `scroll` re-extends, and a fixed bottom-right "STOP FOLLOWING ✕" button (dark fill, cream border, 4px hard shadow, hover lifts 2px) or `Escape` ends it and returns the tomato to the default trail.
- **Idle.** After inactivity a "zzz" stack (VT323, `#D5A945`, 18/15/12px) fades in above the mascot, 400ms opacity transition; a speech bubble ("Hooray!!" and status messages) fades/slides in with `.35s cubic-bezier(.2,.8,.2,1)`.
- **Bob.** `@keyframes sqcBob` — ±7px vertical, used on perched pixel elements.
- **Hover.** Cards lift 5px (180ms) or 4px with a growing hard shadow; links go `#B8492F` → `#D5A945`.
- **Focus.** Global `*:focus-visible { outline: 3px solid #D5A945; outline-offset: 3px }`. Timeline cards are focusable and get the hover treatment on focus.
- **Responsive.** `scroll-behavior: smooth`. `[data-desktop-only]` is hidden below 860px or on coarse pointers (decorative pixel art and the trail flourish are desktop-only). `[data-oneline]` gets `white-space: nowrap` above 900px. Decor sprites are pruned on resize.
- **Reduced motion.** Not implemented in the prototype — add `prefers-reduced-motion` guards that disable the trail, bob, and follow mode.

## State
- `following` (bool) + `pts[]`, `shown`, `target`, `cursor`, `baseLen` — trail geometry.
- `mobile` (bool) from `matchMedia('(max-width: 860px)')`.
- `navOpen` (bool) — burger menu.
- `waitlistOpen`, `waitlistSent`, `waitlistEmail` — modal flow.
No data fetching. Only real integrations needed: waitlist email capture, and the two external Google Form URLs.

## External links
- Apply form: `https://docs.google.com/forms/d/e/1FAIpQLSe41BedRCd2ouJ6u03e3gESe2nb243uZAy0PdLm048At0XK0g/viewform`
- Hero CTA form: `https://docs.google.com/forms/d/e/1FAIpQLScJu145SOp4CtmJv8zU8C38vMC6S4b2aGCgHKyugJb9L8fuPQ/viewform`

## Design tokens

**Color**
| Token | Hex | Use |
|---|---|---|
| Forest base | `#1F2F22` | page/section background |
| Deep forest | `#1B2A1D` | body backdrop |
| Header wash | `rgba(14,36,23,.92)` | sticky header |
| Card forest | `rgba(23,58,36,.55)` / `.8` hover | dark cards |
| Border forest | `#2A3D2E` | card borders, dark buttons |
| Border muted | `#354B38` | header rule |
| Sprite green | `#49644B` | pixel decor |
| Cream | `#F4EBD8` | text on dark, light borders |
| Paper | `#FBF5E4` | light cards, bubbles, modal |
| Gold | `#D5A945` | eyebrows, accents, focus ring, link hover |
| Tomato | `#B8492F` | primary buttons, links, kickers |
| Sage text | `#B3C6B2` | body on dark |
| Slate green text | `#566B57` / `#4A6A4D` / `#4F6F52` | body on paper |
| Sand band | `#E7DEB4` | hero band |
| Dirt pattern | `#E3D8AE` `#F0E6C6` `#CFC095` `#D8CCA2` | trail 8×8 pattern |
| Trail shadow | `#5E4A33` | trail underlay |
| Ink | `#3D2A1D` | default body color |

**Type** — Inter 300/400/600/800 for UI and headings; VT323 (pixel) for eyebrows, mascot chatter, and the join section. Global `text-transform: lowercase` on `body` (inherited by form controls) — the ALL-CAPS strings in the source render lowercase by design; keep that rule or lowercase the copy.
- H1 (visually hidden) / H2: Inter 800, `clamp(28px,4.6vw,52px)`, line-height 1.08–1.15, letter-spacing -1px.
- Card title: Inter 800, `clamp(17px,2vw,20px)`, letter-spacing .2px.
- Body: 15–16px / 1.6, lede `clamp(16px,2.1vw,19px)`.
- Eyebrow: VT323, `clamp(22px,2.8vw,27px)`, letter-spacing 1.2–1.6px.
- Small/UI: Inter 300, 13–14px, letter-spacing 1px.
- `text-wrap: pretty` on paragraphs, `balance` on headings.

**Space & shape** — section padding `clamp(60px,12vh,150px)` block / `clamp(20px,5vw,64px)` inline; content `max-width: 1120px` centered. Grid gaps `clamp(14px,2.4vw,26px)`. **Radius: 0 everywhere.** Borders 3px (4px on timeline cards). Shadows are hard offsets, never blurred: `4px 4px 0 rgba(12,32,20,.4)`, `9px 9px 0 rgba(8,24,15,.45)`, `14px 14px 0 rgba(8,24,15,.5)`.

## Assets
All in `source/assets/`, pixel art, always rendered with `image-rendering: pixelated`.
- `tomato-hero.png` — mascot (hero perch 88px, trail walker 52px, cursor sprite 34px, join section 130px, modal 74px)
- `logo-bag.png` — header mark
- `logo-tomato.png`, `logo-backpack.png`, `tomato-cutout.png` — alternates, not currently on the page

Fonts load from Google Fonts (`Inter:wght@300;400;600;800` + `VT323`); they are inlined in `index.html` so it works offline.

## Files
```
design_handoff_sqc_website/
├── index.html                  deployable prototype (needs ./assets)
├── assets/*.png                runtime-loaded sprites — must sit beside index.html
├── vercel.json                 static config
├── CLAUDE.md                   task brief for Claude Code
├── README.md
└── source/
    ├── SQC Website.dc.html     authored source (template + logic class)
    ├── support.js              runtime for the source file
    └── assets/*.png
```
