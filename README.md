# Breath Mirror 🪞💨

> *An interactive digital mirror installation where breath fogs the glass and touch wipes it clean.*

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Pure Web Tech](https://img.shields.io/badge/Technology-HTML5%20%7C%20Canvas%20%7C%20Web%20Audio%20%7C%20MediaPipe-black.svg)]()

---

## ✦ The Experience

**Breath Mirror** is a minimalist, sensory interactive art installation designed for browser environments. Standing in front of the screen, the display functions as a dark, elegant obsidian mirror reflecting your likeness. 

When you exhale toward your microphone, warm condensation billows across the glass surface. Pinching your fingers allows you to draw, etch messages, or wipe the moisture away to reveal your reflection beneath—accompanied by authentic wet-glass friction acoustics. If left untouched, the steam gradually and naturally evaporates from the outer perimeters inward, mimicking true physical thermodynamics.

---

## ✦ Key Features

- **💨 Acoustic Breath Detection**: Real-time microphone audio DSP with bandpass and high-pass filtering (~800Hz) calibrated to isolate air exhalations from ambient room noise.
- **🤏 Scale-Invariant Pinch Tracking**: Powered by MediaPipe Hands. Pinch tracking is dynamically normalized against hand anatomical landmarks (wrist-to-knuckle ratio), delivering consistent, responsive writing whether standing 1 foot or 6 feet from the camera.
- **🧼 Tactile Wet-Glass Acoustics**: Procedurally synthesized friction and squeak audio generated in real-time via the Web Audio API without requiring any external audio files. Velocity modulates tone pitch and volume.
- **⏳ Natural Thermodynamic Evaporation**: Organic condensation clearing that gently evaporates steam if no new breath is introduced for 10 seconds.
- **📸 Two-Hand Framing Capture ($L$-Frame)**: Make an $L$-shape with both hands to activate a stabilized viewfinder bracket. Holding the frame for 1.5 seconds initiates a 3-second countdown, exposure flash, analog shutter sound, and saves the reflection to an exhibition contact sheet.
- **🏷️ Editorial Watermark Export**: Downloaded snapshots are stamped with a subtle editorial typography watermark (`BREATH MIRROR · [Time]`).
- **⚡ Lightweight & Zero Build Step**: Runs directly in any modern browser without npm packages, bundlers, or frameworks.

---

## ✦ Controls & Interaction

| Interaction | Action | Gesture / Key |
| :--- | :--- | :--- |
| **Breathe** | Fogs the mirror with condensation | Blow into microphone or press <kbd>Space</kbd> |
| **Pinch to Write** | Clears steam to write or draw | Pinch index finger & thumb together |
| **Capture Photo** | Activates viewfinder and shutter | Form $L$-shapes with both hands (or hold) |
| **Undo Stroke** | Reverts the last wiped stroke | Click `↩ undo` |
| **Clear Mirror** | Instantly wipes all condensation | Click `✕ clear` |
| **Toggle Fullscreen** | Distraction-free gallery presentation | Press <kbd>F</kbd> |

---

## ✦ Getting Started

Because the installation utilizes the browser's MediaDevices API (Camera and Microphone), it must be served over a secure origin (`http://localhost` or `https://`).

### 1. Clone the repository
```bash
git clone https://github.com/Suhaid11/breath-mirror.git
cd breath-mirror
```

### 2. Start a local server
Using Python (built into macOS, Linux, and Windows):
```bash
python -m http.server 8089
```
*(Or use any static web server such as `npx serve`, Live Server in VS Code, etc.)*

### 3. Open in your browser
Navigate to:
```
http://localhost:8089
```
When prompted by the browser, grant access to your **Camera** and **Microphone**.

---

## ✦ Architecture & Technology

```
breath-mirror/
├── index.html          # Lightweight entry point with instant redirect
├── breath-mirror.html  # Complete single-file installation engine
└── README.md           # Documentation & installation guide
```

- **Rendering Layer**: Dual-buffered HTML5 Canvas composited with optical diffusion filters (`blur`, `brightness`) and `destination-out` feathering for realistic droplet displacement.
- **Computer Vision**: Google MediaPipe Hands running client-side via WebAssembly/CDN.
- **Audio DSP**: Web Audio API AudioContext utilizing `BiquadFilterNode`, `AnalyserNode`, and dynamic frequency ramp oscillators.

---

## ✦ License

Distributed under the [MIT License](LICENSE).
