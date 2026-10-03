# 🎛️ Patchbay Core (`@frangedev/patchbay-core`)

> Zero-dependency, framework-free audio UI components inspired by analog mixer consoles and studio hardware. Built entirely with Vanilla Custom Elements, CSS, and HTML5 Canvas. **No React, no Tailwind, no build tools required.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen.svg)]()
[![Web Components](https://img.shields.io/badge/standard-Custom%20Elements%20v1-orange.svg)]()

---

## ⚡ Overview

**Patchbay Core** is a drop-in collection of professional audio UI widgets ported directly from modern studio design paradigms into native browser primitives. Every component handles its own internal animation loops, high-FPS canvas rendering, and touch/mouse interaction without forcing virtual DOM re-renders.

- **Zero Runtime Bloat:** Native ES6 Custom Elements (`HTMLElement`) working in any modern browser.
- **Hardware-Grade Performance:** VU meters and visualizers paint directly via `requestAnimationFrame` on `<canvas>` or optimized SVG elements.
- **Decibel & Real-Unit Accurate:** Faders and meters feature true logarithmic scaling (`dB`), peak hold, and clipping indicators.
- **Bring Your Own Audio:** Decoupled from any specific audio engine—bind directly to Web Audio `AudioNode`, `AnalyserNode`, or custom event callbacks.
- **Fully Themeable:** Controlled entirely through native CSS custom properties.

---

## 📦 Component Suite

| Component | Tag Name | Description |
| :--- | :--- | :--- |
| **Level Meter** | `<audio-meter>` | Vertical/horizontal peak & RMS LED ladder with peak-hold decay and clip indicator |
| **Volume Fader** | `<audio-fader>` | Studio-style linear volume fader with decibel ticks and snap detents |
| **Rotary Knob** | `<audio-knob>` | High-precision continuous/stepped rotary potentiometer with fine-tune modifiers |
| **Parameter Slider** | `<audio-slider>` | Labeled slider with direct numeric input and unit labeling |
| **Channel Strip** | `<audio-strip>` | Composite mixer row combining trim, EQ, fader, pan, mute, and solo switches |
| **Channel Toggle** | `<audio-switch>` | Mute, solo, and monitor mechanical latching/momentary buttons |
| **Bar Visualizer** | `<audio-bar-visualizer>` | Frequency-band visualizer with idle states and mirrored modes |
| **Waveform Scope** | `<audio-waveform>` | Real-time live scrolling oscilloscope canvas |
| **Spectrum Analyzer**| `<audio-spectrum>` | FFT frequency spectrum bar/line graph |
| **Sound Pad** | `<audio-pad>` | MPC-style trigger pad with velocity sensitivity, hotkeys, and progress indicator |
| **Audio Player** | `<audio-player>` | Composable transport bar with play/pause, looping, time readout, and scrub bar |
| **Device Select** | `<audio-device-select>` | Input/output source picker with permission and connection states |

---

## 🚀 Quick Start

### 1. Include via Script Tag or ES Module

```html
<script type="module" src="./dist/patchbay-core.min.js"></script>
<link rel="stylesheet" href="./dist/patchbay-core.css">

```

### 2. Markup Usage

```html
<div class="mixing-console">
  <!-- Volume Fader mapped in dB -->
  <audio-fader 
    min="-60" 
    max="6" 
    value="0" 
    unit="dB" 
    label="MASTER">
  </audio-fader>

  <!-- Stereo Peak & RMS Level Meter -->
  <audio-meter 
    channels="2" 
    peak-hold="true" 
    clip-threshold="-0.1">
  </audio-meter>

  <!-- Real-time Oscilloscope Scope -->
  <audio-waveform 
    fps="60" 
    color="var(--pb-accent)">
  </audio-waveform>
</div>

```

### 3. Binding to Web Audio API

```javascript
// Connect an audio analyser directly to the waveform component
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
const analyser = audioCtx.createAnalyser();

const waveformEl = document.querySelector('audio-waveform');
waveformEl.attachAnalyser(analyser);

```

---

## 🎨 CSS Custom Properties Theme

Customize your studio rack appearance by overriding root tokens:

```css
:root {
  --pb-bg: #0d0e11;
  --pb-surface: #16181d;
  --pb-surface-raised: #21242c;
  --pb-border: #2e323d;
  --pb-text: #8b92a5;
  --pb-text-bright: #f0f2f5;
  --pb-accent: #00ffc4;
  --pb-accent-hover: #1fffc9;
  --pb-meter-green: #10b981;
  --pb-meter-yellow: #f59e0b;
  --pb-meter-red: #ef4444;
  --pb-font: 'JetBrains Mono', monospace;
}

```

---

## 📂 Repository Structure

```text
patchbay-core/
├── index.html                  # Interactive sandbox / mixer showcase
├── src/
│   ├── components/
│   │   ├── audio-meter.js      # Peak/RMS LED ladder element
│   │   ├── audio-fader.js      # Decibel slider element
│   │   ├── audio-knob.js       # Rotary potentiometer element
│   │   ├── audio-switch.js     # Mute/Solo toggle switches
│   │   ├── audio-waveform.js   # Canvas oscilloscope
│   │   ├── audio-spectrum.js   # FFT frequency analyzer
│   │   ├── audio-pad.js        # MPC trigger pad
│   │   └── audio-player.js     # Transport controller
│   ├── utils/
│   │   ├── audio-math.js       # Logarithmic curves & dB conversions
│   │   └── canvas-helper.js    # High-DPI canvas scaling loops
│   ├── styles/
│   │   └── patchbay.css        # Core reset & variable definitions
│   └── index.js                # Component registration entrypoint
└── README.md

```

---

## 🛠️ Local Development

No build steps, bundlers, or node dependencies are required. Clone and serve statically:

```bash
git clone [https://github.com/frangedev/patchbay-core.git](https://github.com/frangedev/patchbay-core.git)
cd patchbay-core

# Serve locally
python3 -m http.server 3000

```

Open `http://localhost:3000` to preview the interactive studio rack.

---

## 📜 License

MIT © [FRANGE](https://github.com/frangedev)
