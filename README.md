# CRT / Analog Video Look Tool

This project is a browser-based editor that applies CRT, VHS, camcorder, broadcast, and film-style degradation to still images and videos, with real-time preview and export.

## What the tool does

- Loads **images or videos** as the source media.
- Applies a large set of analog/retro simulation effects in real time (scanlines, multiple display masks including phosphor/aperture/shadow-mask/LCD/OLED/plasma patterns, warp, jitter, chroma delay, dropouts, ghosting, interlacing, RF interference, film grain/dust/scratches, and more).
- Lets you quickly start from **presets** and then fine tune with direct sliders.
- Supports **preset intensity**, preset filtering/search, and “dirty” state detection when your current settings deviate from the chosen preset.
- Includes **macro controls** that move multiple low-level parameters together for faster stylization.
- Provides optional **on-screen display overlays** (timestamp/corners/font style/colors/thickness) to mimic camcorder/CCTV/broadcast HUDs.
- Includes **compare controls** (view original vs processed) while tuning.
- Exports processed output as:
  - **MP4** (muxed in-browser)
  - **WebM** (real-time recording path, with optional source audio)
  - **Still image snapshot**

Everything runs client-side in the browser (no backend service required by default).

## How it works (high level)

- `index.html` defines the UI panels for source, presets, controls, preview, OSD, and export.
- `src/app.js` contains:
  - the main render pipeline (`CRTRenderer`)
  - interaction/state logic
  - preset loading/application/filtering
  - export flows (MP4/WebM/still)
- `src/presets.js` provides a preset library.
- `styles.css` defines the full editor layout and visual style.

## Run locally

Because this is a web app, run it through a local HTTP server instead of opening `index.html` directly.

```bash
cd /workspace/lmebroswergpu
python3 -m http.server 4173
```

Then open:

- `http://localhost:4173`

## Basic workflow

1. Load a source image/video.
2. Pick a preset.
3. Adjust macro controls and/or individual sliders.
4. (Optional) Configure OSD overlays and compare mode.
5. Export MP4, WebM, or a still image.

## Notes

- MP4 export uses a CDN dependency for muxing.
- For best UX, use a modern Chromium/Firefox browser with hardware acceleration enabled.
