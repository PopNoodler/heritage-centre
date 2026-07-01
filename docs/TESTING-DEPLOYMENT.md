# Testing & Deployment Checklist

Covers the **Testing & Deployment** line of the brief — ensuring smooth operation
for public use before the stations go live.

## A. Functional testing (do on a desktop browser first, then on the tablets)

### Main Interactive App (`main-app/index.html`)
**Home**
- [ ] All three station cards appear and gently pulse.
- [ ] Tapping a card opens the right station; **🏠 Home** returns.

**Herring Game**
- [ ] Silver herring swim inside the net and react to taps (facing their direction).
- [ ] Tapping a herring flies it to the creel; counter and progress bar rise.
- [ ] The net **empties as you catch** and does not refill until taken to the pier.
- [ ] When the net is cleared, **Take to the Pier!** lights up; tapping it shows
      confetti + a Barra fact, advances the ⭐ score, and **changes the weather**.
- [ ] Weather goes overcast → rain → sunshine; the **3rd haul** shows "Well done!".
- [ ] Facts don't repeat until all have been shown. The 🔊 button mutes/unmutes.

**Build a Blackhouse**
- [ ] Tapping the button (or the house) adds each part in turn: walls → frame →
      thatch → ropes → fire → family/cow, with a real fact and a filled progress dot.
- [ ] After the last step a "Sgoinneil! Well done!" card appears; **Build again** resets.

**Exhibit Gallery**
- [ ] All exhibits show as cards with titles.
- [ ] Tapping a card opens the full-screen view with description.
- [ ] ‹ / › move between exhibits; ✕ closes.

### Interactive Island Map (`map-app/index.html`)
- [ ] The real Barra basemap loads (sepia antique chart) and fits the screen.
- [ ] Drag pans; **+ / −** and pinch zoom; **⤢** resets; double-tap zooms in.
- [ ] Markers stay a constant size; names appear once zoomed in.
- [ ] Every marker is tappable and opens its info panel with a "Did you know?".
- [ ] ✕ — or tapping the sea away from a marker — closes the panel.
- [ ] Heritage places (bronze) and hotels/campsites (blue) are both present.

### Accessibility (both apps)
- [ ] The **♿ button** (top-right) opens a small menu with a **High contrast**
      toggle that turns on/off and shows its state.
- [ ] The choice **persists** after an idle reset and is **shared** between the two
      apps on the same tablet (set once, applies to both stations' browser).
- [ ] High contrast switches the reading surfaces to black-on-white.

### Attract / screensaver (both apps)
- [ ] After ~90 s idle the app returns home; ~25 s later a full-screen **attract
      loop** appears (Barra invite + rotating facts + "scan at home" QR code).
- [ ] Touching anywhere dismisses it instantly and returns to the app.

### Usage statistics (staff only — both apps)
- [ ] **Five quick taps in the top-right corner** (or add `#stats` to the URL)
      opens the usage panel: sessions, first/last used and per-feature counts.
      (Tapping the visible ♿ accessibility button there does not count.)
- [ ] **Copy data** puts the JSON on the clipboard; **Reset** clears it (with a
      confirm). Counts are anonymous, on-device only, and shared across both apps.

### Kiosk behaviour (all apps)
- [ ] After ~90 s untouched, the app returns to its home/overview by itself.
- [ ] No way to leave the app: back button, nav bar and gestures do nothing
      (verify after kiosk lockdown — see KIOSK-SETUP.md).

## B. Device testing

- [ ] Test on the **actual Lenovo M10 (10.1″)** and **Lenovo 13″** in landscape.
- [ ] Touch targets are comfortably large for small children (game) and for
      visitors of all abilities (map buttons).
- [ ] Performance is smooth — fish animation and map panning don't stutter.
- [ ] Screen stays on; tablet survives a reboot and auto-relaunches the app.
- [ ] Run each station for a sustained period (e.g. 1 hr) to check for slowdowns.

## C. Content review before launch

- [ ] Replace placeholder illustrations with **real exhibit photos**
      (see `main-app/assets/README.md`) — edit `main-app/exhibits.js`.
- [ ] The **island map** is the real Isle of Barra with real POIs. Have a local
      reviewer check the facts, Gaelic spellings and marker positions; tweak in the
      `POIS` list near the top of `map-app/index.html` (x/y, names, descriptions,
      icons, photos).
- [ ] Proofread all titles, descriptions and fun facts.
- [ ] Confirm the children's game tone suits ages 4–8 (it is fail-free and positive).

## D. Go-live

1. Lock each tablet per **KIOSK-SETUP.md** and mount in its stand.
2. Power on, confirm the correct app auto-launches full-screen.
3. Do one final walk-up test as a visitor would.
4. Hand staff the **Kiosk PIN** and the one-page "If something goes wrong" notes below.

## If something goes wrong (staff quick reference)

| Symptom | Fix |
|---|---|
| App frozen / odd state | Wait 90 s (auto-resets) or enter Kiosk PIN → reload. |
| Black screen | Check USB-C power in the stand; press power button. |
| Wrong app showing | Enter Kiosk PIN → check Start URL in Fully Kiosk. |
| Needs full restart | Enter PIN → exit kiosk → reboot tablet (auto-relaunches). |

## Optional (post-installation, per brief notes)

- Maintenance / content updates: swap photos and edit text, then recopy the folder.
- Periodic check that all three stations are powered and responsive.
