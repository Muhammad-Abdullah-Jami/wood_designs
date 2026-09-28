# Furniture plans

Static site with build drawings for custom home furniture, made to share with my father, a carpenter and a welder by link. It is deployed on Vercel. There is no build step, framework or package.json. Every page is one self-contained HTML file with inline CSS and JS.

## Structure

```
index.html                     landing page linking both plans
cabinet/index.html             PC side cabinet: three.js 3D model, SVG drawings, cut list
sofa-table/index.html          sofa table + doors + bedroom floor plan drawing sheet (static SVG)
sofa-table/sofa-table-sheet.pdf / .png   printable exports of the sofa table sheet
vercel.json                    cleanUrls, so /cabinet and /sofa-table work
```

## Deploy

```
npx vercel          # preview
npx vercel --prod   # production
```

Or push to GitHub and import the repo in Vercel with framework preset "Other", no build command, output directory `.` (root).

Local preview: `npx serve .`

## Conventions

- Units are inches everywhere, with mm in brackets where the carpenter needs them. Fractions use ¼ ½ ¾ ⅛ glyphs.
- Material is 18 mm (¾″, modelled as 0.75″) MDF, pre-laminated, PVC edge tape on visible edges. Sheets are 8 × 4 ft (96 × 48″). A saw kerf is ⅛″.
- Pages support light and dark themes through CSS custom properties on `:root`, overridden under `prefers-color-scheme: dark` and `[data-theme]`.
- Only external resources are Google Fonts and three.js r128 from cdnjs (`https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js`). r128 has no OrbitControls in the UMD build, so the camera controls are hand-written pointer, wheel and pinch handlers.
- Keep pages mobile-friendly: they are mostly opened on phones via WhatsApp.

## Plan 1: PC side cabinet (`cabinet/index.html`)

Sits beside my PC desk (desk top is about 30″ from the floor, desk is 24″ deep). Located in the Islamabad/Rawalpindi area, a high seismic zone.

**Orientation: the cabinet stands to the RIGHT of the desk** (the desk already exists and is not moving). The PC bay is at the cabinet's **left** end (nearest the desk, so power and monitor leads stay short) and the 9″ cubby column at the **right** end. The whole layout was mirrored on 2026-09-28 to fix this; before that the plan assumed the cabinet sat to the left of the desk. The cut list is unaffected by the mirror, since every part keeps its size and only positions change.

The PC is a fish-tank case and **its glass panel faces the FRONT**, square out of the cabinet, not sideways. (It briefly faced left during the mirror fix; corrected same day.) In the model both side panels are solid and the front face is the glass. The PC prop does *not* mirror with the cabinet — mirroring it would flip the glass to the wrong face.

Overall 32″ W × 24″ D (carcass 23¾″) × 72″ H, on 6 adjustable M10 levelling feet (about 1½″, ±½″).

- Lower half: closed MDF cabinet, body 1½″ to 30″, two full-overlay doors, centre divider, 3 adjustable shelves, 5 mm hardboard back with vents and cable holes. Contents: spare server laptop, cords, extension boards, small PC UPS (never big inverter batteries).
- Cabinet top at 30″ = desk height. PC stands here in the right bay.
- Upper half: welded 1″ square steel tube frame, bolted to the cabinet top.
  - Right column (x 22–31), 9″ clear: cubbies with shelves at 38″ and 46″ on 1″ angle ledges.
  - PC bay on the left (x 1–21), 20″ clear wide, 23″ clear high (30″ to 53″). PC sits x 2–20, so 1″ clear each side.
  - Rear ledge at 38″, 20 × 5″ (x 1–21), behind the PC, for devices in the rear ports, plus a phone stood up on charge or an external hard drive. Leaves a 3″ cable gap.
  - Full-width middle shelf at 54″, top board at 71¼–72″.
  - Rail rings at 30″ (front bar is the 1″ PC anti-slide lip), 53″, 70¼″. Flat-bar X braces on the back of the left column and the top section.
- Earthquake: anti-tip wall brackets at the top rail, heavy stuff low, anti-slip mat under PC.

PC size as I gave it: 14″ long × 18″ wide × 18″ high. **Open question:** true front-to-back depth. The model assumes 14″ deep. If it is 18″, the rear ledge (part K) becomes 3″ deep.

MDF cut list (needs **two** 8 × 4 sheets; one is not enough):

| Key | Part | Qty | Inches | mm |
|---|---|---|---|---|
| A | Cabinet top | 1 | 32 × 23¾ | 813 × 603 |
| B | Cabinet sides | 2 | 27¾ × 23¾ | 705 × 603 |
| C | Cabinet bottom | 1 | 30½ × 23¾ | 775 × 603 |
| D | Centre divider | 1 | 27 × 23½ | 686 × 597 |
| E | Cabinet shelves | 3 | 14¾ × 22 | 375 × 559 |
| F | Doors | 2 | 15⅞ × 27½ | 403 × 699 |
| G | Middle shelf | 1 | 32 × 23¾ | 813 × 603 |
| H | Top | 1 | 32 × 23¾ | 813 × 603 |
| J | Cubby shelves | 2 | 9 × 23¾ | 229 × 603 |
| K | Rear ledge | 1 | 20 × 5 | 508 × 127 |

Geometry lives in the `parts` array in the script (`P(kind, x0,x1, y0,y1, z0,z1)`, inches, x = left→right, y = floor→up, z = back→front). The 3D model, front and side SVG elevations are all generated from it, so change dimensions there and the drawings follow. The cut list table, sheet layout and dimension labels are hand-written and must be updated separately.

## Plan 2: Sofa table sheet (`sofa-table/index.html`)

A single drawing sheet (static SVG, no JS) with seven views: isometric, bedroom floor plan, front elevation, top plan, section A–A, sheet 1 cutting layout, and what-fits-where notes.

- Sofa table 47 × 24 × 16½″ (height assumed), 18 mm MDF, two equal open compartments 22 7/16″ wide × 6″ clear, four splayed black tapered legs about 9 1/16″ on angled plates.
- Sheet 1 (trimmed to 47 × 95″) yields the table plus two doors 17 11/16 × 40″.
- Gun box on the wall goes on sheet 2: 47″ outside, 45 9/16″ inside, 6″ deep. Height is still undecided (gun's tallest point + 2″).
- Bedroom 14′-0″ × 11′-6″ with a 6′ × 6½′ bed. **Known clash:** the sofa-to-bed aisle is 2′-6″, so the 24″-deep table leaves only 6″ to walk past.

Open questions: sofa cushion height (sets leg length), gun height (sets gun box and sheet 2 layout), whether to make the table shallower or move it to fix the aisle clash.

## Ideas / todo

- Add a "back to all plans" link on each plan page.
- Print stylesheet for the cabinet page (A4, drawings + cut list only, hide the 3D viewer).
- Draw sheet 2 for the sofa-table project once the gun height is known.
- Optional Urdu labels for the carpenter.
