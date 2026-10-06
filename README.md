# Breath Mirror 🪞💨

> *An interactive digital mirror installation where breath fogs the glass and touch wipes it clean.*

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Pure Web Tech](https://img.shields.io/badge/Technology-HTML5%20%7C%20Canvas%20%7C%20MediaPipe-black.svg)]()

---

## ✦ The Experience

**Breath Mirror** is a sensory interactive art installation designed for modern browser environments. Standing before your camera, the screen acts as a dark, slate-obsidian mirror reflecting your presence. 

When you exhale toward your microphone, warm condensation billows dynamically from your mouth across the glass. Pinching your thumb and index finger lets you etch messages or draw lines through the steam, while wiping with a closed fist clears broad patches of condensation back to clear glass. 

---

## ✦ Key Features

- **💨 Dynamic Mouth-Tracking Condensation**: Integrates MediaPipe Face Detection to originate condensation puffs directly from your mouth, dispersing and falling naturally across the glass surface.
- **🤏 Precision Pinch & Star Cursor**: Powered by MediaPipe Hands. Smooth two-pass easing and tremor filtration with an arctic ice-star cursor for drawing or writing on the fog.
- **👊 Fist Wipe Clearing**: Ball your hand into a fist to wipe away large areas of moisture like a physical sponge or palm.
- **📸 Two-Hand $L$-Frame Gesture Capture**: Frame your reflection by making an $L$-shape with both hands. Holding the framing viewfinder triggers a 3-second countdown, exposure flash, and saves the snapshot.
- **🎞️ Gallery Film Strip & Watermark**: Captures are automatically cataloged in a live bottom photo reel for quick downloading, stamped with a subtle editorial watermark (`BREATH MIRROR · [Time]`).
- **↩️ Stroke Undo & Mirror Reset**: Revert drawing strokes with <kbd>Z</kbd> or the top-bar undo button, or instantly reset condensation with <kbd>C</kbd>.
- **⏳ Natural Thermodynamic Evaporation**: Condensation gently thins over time when left untouched.
- **🔇 Silent Ambient Focus**: All procedural sound effects have been removed to maintain a quiet, meditative installation experience.
- **⚡ Lightweight & Zero Build Step**: Runs directly in the browser via clean HTML5, Canvas, and CDN-hosted WebAssembly models.

---

## ✦ Controls & Interaction

| Interaction | Action | Gesture / Key |
| :--- | :--- | :--- |
| **Breathe** | Fogs mirror with steam | Exhale into microphone or hold <kbd>Space</kbd> |
| **Pinch to Draw** | Etches clean glass through fog | Pinch index finger & thumb together |
| **Fist to Wipe** | Clears steam with palm | Form a closed fist and wipe across mirror |
| **Frame Capture** | Triggers photo countdown | Form $L$-shapes with both hands (or click shutter button) |
| **Undo Stroke** | Reverts last drawing or wipe | Press <kbd>Z</kbd> or click `↩` button |
| **Reset Mirror** | Re-fogs the entire surface | Press <kbd>C</kbd> or click `✕` button |
| **Save Photo** | Saves reflection snapshot | Press <kbd>S</kbd> or click camera button |
| **Fullscreen** | Toggles distraction-free view | Press <kbd>F</kbd> or click `⛶` button |
| **Diagnostics** | Toggles live telemetry HUD | Press <kbd>D</kbd> |
| **Exit** | Returns to start screen | Press <kbd>Esc</kbd> |

---

## ✦ Getting Started

Because the installation utilizes the browser's MediaDevices API (Camera and Microphone), it must be served over a secure origin (`http://localhost` or `https://`).

### 1. Clone the repository
```bash
git clone https://github.com/Suhaid11/breath-mirror.git
cd breath-mirror
```

### 2. Start a local server
Using Python:
```bash
python -m http.server 8089
```
*(Or use any static web server such as `npx serve`, Live Server, etc.)*

### 3. Open in your browser
Navigate to:
```
http://localhost:8089
```
When prompted, allow **Camera** and **Microphone** access.

---

## ✦ Architecture

```
breath-mirror/
├── index.html          # Entry point with instant redirect
├── breath-mirror.html  # Unified single-file installation engine
└── README.md           # Documentation & interaction guide
```

- **Layer 1 (`#cam`)**: Real-time mirrored camera feed.
- **Layer 2 (`fog`)**: Offscreen density buffer storing condensation levels (`source-over` puff additions, `destination-out` finger/palm erasures).
- **Layer 3 (`#frost`)**: Blurred and brightened camera feed with cool glass tint, masked against the fog buffer via `destination-in`.
- **Layer 4 (`#frame`)**: Viewfinder bracket overlay rendered during two-hand $L$-frame gesture holds.

---

## ✦ License

Distributed under the [MIT License](LICENSE).
