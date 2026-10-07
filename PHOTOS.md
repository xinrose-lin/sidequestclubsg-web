# Where to put each polaroid photo

Overwrite the file with the **same filename** — no code changes needed. Keep the extension (`.jpg` / `.png`) or edit the `src` in the HTML if you change it. Photos are cropped to fit (4:3 on the home page, square on Quest Day), so landscape photos with people near the centre work best. Aim for about 1200px wide and under 300KB each.

Folder: `deploy/assets/photos/`

## Home page (`index.html`) — roadmap, beside each week
| File | Beside | Current caption |
|---|---|---|
| home-week-1.png | Week 1 (right) | QUEST V0 SCOPING! |
| home-week-2.jpg | Week 2 (left) | IDEAS PITCH |
| home-week-3.jpg | Week 3 (right) | FIRESIDE CHAT |
| home-week-4.jpg | Week 4 (left) | FIND YOUR AUDIENCE! |
| home-week-5.png | Week 5 (right) | COMING SOON ON 17 OCT! (placeholder "?") |

## Quest Day page (`quest-day.html`) — pinned beside the title
| File | Position | Current caption |
|---|---|---|
| questday-1.jpg | left, upper | SIDEQUESTERS! |
| questday-2.jpg | left, lower | SQC X THERESA SYN! |
| questday-3.jpg | right, upper | SQC X RAGTECH! |
| questday-4.png | right, lower | HTHTs :) |

## Change a caption
Open the page's HTML, search for the caption text (e.g. `FIRESIDE CHAT`) and edit the text inside `<figcaption>`.

## Gallery page
Polaroids there are placeholders ("DROP PHOTO HERE"). People and handles live in the `PEOPLE` list near the bottom of `gallery.html`. To publish without it, see `HIDE-GALLERY.md`.
