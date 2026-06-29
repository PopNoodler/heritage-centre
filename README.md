# Heritage Centre — Interactive Kiosk Software

Software delivery for the Heritage Centre interactive tablet stations described in
*Heritage Centre Software & Hardware Costs*. Three visitor experiences, built to run
**offline** in **kiosk mode** on the project's Android tablets.

## What's included

| # | Station | App | Runs on |
|---|---|---|---|
| 1 | Children's fishing game **+** exhibit image gallery | `main-app/` | 2× Lenovo Tab M10 10.1″ |
| 2 | Interactive island map | `map-app/` | 1× Lenovo 13″ Android tablet |

Plus full setup & launch documentation in `docs/`.

### 1. Main Interactive App — `main-app/index.html`
- **Children's historical fishing game** (ages 4–8): tap the fish swimming in the net
  to drop them into your basket, then send the boat to the **pier** when it's full.
  Fail-free, colourful, with gentle sounds, praise and "did you know?" heritage facts.
- **Exhibit gallery**: a grid of exhibits with a full-screen viewer and descriptions.
- Big home screen to switch between the two; touch-friendly, optimised for 10.1″.

### 2. Interactive Island Map — `map-app/index.html`
- A **top-down map of the Isle of Barra & Vatersay** (Outer Hebrides), drawn to be
  recognisable: the Eoligarry peninsula to the north, the Tràigh Mhòr airport beach,
  Castlebay in the south, Heaval's high ground, and Vatersay across its causeway.
- Zoomable, pannable (drag, pinch, +/− buttons, double-tap, reset) with a compass rose.
- **Real points of interest** — Kisimul Castle, Castlebay, Dualchas Heritage Centre
  ("you are here"), Heaval, Barra Airport, Cille Bharra, Ardmhor ferry, Northbay,
  Dùn Bharpa, the west-coast beaches and Vatersay — each with Gaelic name, description
  and a "did you know?" fact.
- Designed for the larger 13″ screen.

## Design notes
- **Celtic / Hebridean visual identity** across all three stations: a parchment-and-bronze
  palette, woven Celtic-knot borders, triquetra emblems, a muted moorland-and-Atlantic
  colour scheme and serif typography, with Gaelic alongside English throughout.
- **Offline-first**: pure HTML/CSS/JS, no internet, no CDN, no build step. Everything
  needed is in this folder — ideal for locked-down kiosk tablets.
- **Kiosk-friendly**: each app auto-returns to its home screen after 90 s of
  inactivity, so a station is always ready for the next visitor.
- **Single self-contained file per app**: both `main-app/index.html` and
  `map-app/index.html` inline all their CSS, JavaScript and data, so each runs from a
  single file with no sibling dependencies — robust on phones, tablets and kiosk
  browsers alike.
- **Editable content**: exhibit text/photos in the `EXHIBITS` array inside
  `main-app/index.html`; map points in the `POIS` list inside `map-app/index.html`.
  Placeholder illustrations are generated in-app and can be swapped for real
  photographs (see `main-app/assets/README.md`).

## Try it now (desktop)
Open `index.html` (the launcher) in any modern browser, or open an app directly:
- `main-app/index.html`
- `map-app/index.html`

> Best viewed full-screen in landscape. For touch, a tablet or a browser's device
> emulation gives the truest feel.

## Deploying to the tablets
1. **`docs/KIOSK-SETUP.md`** — copy files, install a kiosk browser (Fully Kiosk
   recommended), lock to a single app, disable navigation, auto-launch on boot.
2. **`docs/TESTING-DEPLOYMENT.md`** — full test checklist and a staff "if something
   goes wrong" quick reference.

## Folder structure
```
HeritageCentre/
├─ index.html              ← launcher / preview (testing only)
├─ README.md               ← this file
├─ main-app/               ← Station 1 (10.1″ tablets)
│  ├─ index.html           ← single self-contained file (game + gallery + data)
│  └─ assets/              ← drop real exhibit photos here
├─ map-app/                ← Station 2 (13″ tablet)
│  └─ index.html           ← map + points of interest (edit POIS here)
└─ docs/
   ├─ KIOSK-SETUP.md
   └─ TESTING-DEPLOYMENT.md
```

## Mapping to the brief
| Brief line item | Delivered here |
|---|---|
| Main Interactive App (fishing game + gallery, 2 tablets) | `main-app/` |
| Interactive Map App (1 tablet) | `map-app/` |
| Tablet Configuration & Kiosk Setup | `docs/KIOSK-SETUP.md` |
| Testing & Deployment | `docs/TESTING-DEPLOYMENT.md` |

## Before go-live
The island map is already set to the **real Isle of Barra** with real points of
interest. Before launch: double-check the local facts/spellings, and (optionally)
swap the generated illustrations for real photographs — exhibit photos via
`main-app/assets/README.md`, and POI photos by adding a `photo:` field in the `POIS`
list in `map-app/index.html`. Marker positions can be nudged by editing each POI's
`x` / `y` on the 1600 × 1000 map.
