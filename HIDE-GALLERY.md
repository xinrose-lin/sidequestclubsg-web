# Gallery: currently hidden

The Gallery is **hidden** right now:
- The page lives at `parked/gallery.html`, outside `deploy/`, so it is not published. `/gallery` returns "not found".
- The "Gallery" nav link has been removed from `deploy/index.html` and `deploy/quest-day.html`.
- The authored source is still in `source/Gallery.dc.html`.

## Unhide it
1. Move the page back into the deploy folder:
   ```bash
   mv parked/gallery.html deploy/gallery.html
   ```
2. Put the nav link back in both pages. Open each file, find the `Quest Day` link inside `<nav id="main-nav">`, and paste the line right after it (before the "Join waitlist" button).

   `deploy/index.html` — this one has `onClick="{{ closeNav }}"` so the mobile menu closes:
   ```html
   <a href="gallery.html" onClick="{{ closeNav }}" style="font-family:'Inter',sans-serif; font-weight:600; font-size:13px; letter-spacing:.4px; color:#B3C6B2; white-space:nowrap;" style-hover="color:#D5A945">Gallery</a>
   ```
   `deploy/quest-day.html`:
   ```html
   <a href="gallery.html" style="font-family:'Inter',sans-serif; font-weight:600; font-size:13px; letter-spacing:.4px; color:#B3C6B2; white-space:nowrap;" style-hover="color:#D5A945">Gallery</a>
   ```
3. Check: `grep -c gallery.html deploy/index.html deploy/quest-day.html` should print `1` for each.
4. Test locally (`npx wrangler dev`, then open http://localhost:8787), then deploy.
