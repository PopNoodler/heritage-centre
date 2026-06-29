# Testing & Deployment Checklist

Covers the **Testing & Deployment** line of the brief — ensuring smooth operation
for public use before the stations go live.

## A. Functional testing (do on a desktop browser first, then on the tablets)

### Main Interactive App (`main-app/index.html`)
**Home**
- [ ] Both station cards appear and gently pulse.
- [ ] Tapping a card opens the right station; **🏠 Home** returns.

**Fishing Game**
- [ ] Fish swim inside the net and react to taps.
- [ ] Tapping a fish flies it to the basket; the counter and progress bar rise.
- [ ] New fish keep appearing — the net never empties.
- [ ] When the basket hits 6, the **🚤 Take to the Pier!** button lights up and bobs.
- [ ] Tapping it shows confetti + a praise/fun-fact card and adds to the ⭐ score.
- [ ] The 🔊 button mutes/unmutes sound.

**Exhibit Gallery**
- [ ] All exhibits show as cards with titles.
- [ ] Tapping a card opens the full-screen view with description.
- [ ] ‹ / › move between exhibits; ✕ closes.

### Interactive Island Map (`map-app/index.html`)
- [ ] Map fits the screen on load and is centred.
- [ ] Drag pans the map; **+ / −** and pinch zoom; **⤢** resets the view.
- [ ] Every 📍 marker is tappable and opens its info panel with a "Did you know?".
- [ ] ✕ closes the panel; double-tap zooms in.

### Kiosk behaviour (both apps)
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
