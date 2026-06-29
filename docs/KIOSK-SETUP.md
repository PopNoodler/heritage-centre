# Kiosk Setup Guide — Heritage Centre Tablets

This guide covers **Tablet Configuration & Kiosk Setup** from the project brief:
lock devices into kiosk mode, auto-launch the app, and disable system navigation
so the tablets are safe for unattended public use.

## Devices in this project

| Station | Device | App to load |
|---|---|---|
| Children's game + gallery (×2) | Lenovo Tab M10 10.1″ (Android) | `main-app/index.html` |
| Interactive island map (×1) | Lenovo 13″ Android Tablet | `map-app/index.html` |

All three apps are **fully self-contained and offline** — no internet connection is
required once the files are on the device.

---

## Step 1 — Put the app files on each tablet

1. Copy the **whole `HeritageCentre` folder** onto the tablet's internal storage
   (e.g. via USB-C file transfer), or host it and let the kiosk browser cache it.
   - Game/gallery tablets need: `main-app/` (index.html, app.js, exhibits.js, assets/)
   - Map tablet needs: `map-app/` (index.html)
2. Note the local file path, e.g.
   `file:///storage/emulated/0/HeritageCentre/main-app/index.html`

> Tip: keep the folder structure intact — `app.js` and `exhibits.js` must sit next
> to `main-app/index.html`.

## Step 2 — Install a kiosk browser

The recommended tool for Android kiosk web apps is **Fully Kiosk Browser & Lockdown**
(free for basic use; one-off licence unlocks all lockdown features — well within the
project's configuration budget).

Alternatives: Android **Screen Pinning** (built-in, basic) or a dedicated MDM.
Fully Kiosk is recommended because it does everything the brief asks for in one place.

## Step 3 — Configure Fully Kiosk Browser (per tablet)

Open **Fully Kiosk → Settings** and set:

**Web Content Settings**
- *Start URL* → the app path for that tablet (see table above).

**Web Auto Reload**
- *Reload on Idle (sec)* → optional; the apps already return to their home screen
  after 90 s of inactivity, so this can be left off.

**Device Management → Kiosk Mode (single app)**
- *Enable Kiosk Mode* → **ON**
- Set a *Kiosk PIN* (record it for staff — needed to exit).

**Web Auto Content / Navigation**
- *Disable status bar / navigation bar* → **ON** (hides Android nav — meets
  "disable system navigation").
- *Disable hardware keys / back button* → **ON**.
- *Disable swipe & gestures* → **ON**.
- *Keep Screen On* → **ON** (tablets are continuously powered via the stands).

**Launch on Boot**
- *Start on Boot* → **ON** so the app auto-launches if the tablet restarts
  (meets "auto-launch apps").

**Motion / Power**
- Optionally enable *Screensaver/Daydream* off, and keep brightness fixed.

## Step 4 — Android-level hardening (recommended)

- Put the tablet into a **dedicated kiosk / supervised user** with no Play Store.
- Disable notifications and system update pop-ups for that user.
- Set screen timeout to **Never** (stands provide continuous power).
- Set screen orientation to **Landscape** and lock rotation
  (apps are designed landscape-first).
- Enable **auto-restart on power loss** if the device supports it.

## Step 5 — Mount and power

- Fit each tablet into its **AboveTEK anti-theft floor stand**.
- Route the **USB-C power adaptor** through the stand for continuous power
  (no battery worries for all-day public use).

---

## Exiting kiosk mode (for staff)

In Fully Kiosk: tap the screen rapidly in a corner (or use the configured gesture)
and enter the **Kiosk PIN**. Record the PIN somewhere safe for staff.

## Quick checklist (per tablet)

- [ ] Files copied, app opens from local path
- [ ] Correct Start URL set
- [ ] Kiosk mode ON + PIN set
- [ ] Nav bar / back / gestures disabled
- [ ] Start on boot ON, keep screen on ON
- [ ] Landscape locked, screen timeout never
- [ ] Mounted in stand, powered via USB-C
