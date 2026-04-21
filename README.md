# 🎬 Documentary Portfolio Template

> *A cinematic, single-file developer portfolio template inspired by documentary filmmaking aesthetics — built with zero dependencies.*

---

## 📌 Overview

The **Documentary Portfolio Template** is a fully self-contained, single-file (`index.html`) personal portfolio designed to feel like a high-production documentary. Every section is treated as an act or archival exhibit, complete with camera-recording overlays, letterbox bars, real-time timecodes, scroll-triggered cinematic animations, and a particle-canvas background.

Originally built by **Girish Lade**, this template can be forked and customized to showcase any developer, designer, or creative professional.

---

## ✨ Features

### 🎥 Cinematic UI & Atmosphere
- **Letterbox Bars** — Fixed top and bottom black bars for a widescreen cinematic feel
- **Camera Recording Overlay** — Live `REC` indicator with blinking red dot, ISO value, aperture (`F 2.8`), and audio channel display
- **Real-Time Timecode** — Ticks at 24 fps (cinematic standard), starting at `01:00:00:00` for a "raw footage" aesthetic
- **Film Noise Overlay** — Subtle SVG fractalNoise texture layered over the page at 4% opacity
- **Vignette Effect** — Full-viewport inset box-shadow to darken edges like a camera lens
- **Energy Flash** — Orange glow sweep animation on page load

### 🧩 Sections (Documentary Acts)
- **Hero / Subject Profile** — Lower-third style nameplate with `SUBJECT PROFILE // RECORDING` badge, letter-by-letter title animation, and rotating energy rings around an SVG avatar
- **ACT I — The Origin** — Cinematic subtitle-style narration with staggered reveal, narrator voice-over label in documentary yellow
- **EXHIBIT A — Capability Matrix** — 4-column responsive skills grid with 3D tilt-on-hover effect and gradient border glow
- **ACT II — Active Operations** — Alternating timeline with animated node connectors and archival stamps
- **ACT III — The Horizon** — Archival tape quote section with scroll-triggered staggered line reveals
- **Closing Credits** — Full-screen dark credits roll with cinematic typography

### 🎞️ Animations & Interactions
- **Typewriter Effect** — Variable-speed typing for the hero subtitle (simulates human typing cadence)
- **Focus Reveal** — Sections blur-in from `blur(15px)` to sharp as they enter the viewport
- **Reveal-Up** — Elements slide up from 40px with a cubic-bezier ease on scroll
- **Staggered Delays** — `.delay-1`, `.delay-2`, `.delay-3` utility classes for sequential animation
- **3D Card Tilt** — Skill cards rotate on `mousemove` using `perspective(1000px) rotateX/Y`
- **Particle Canvas** — Floating orange and cyan particles rendered via HTML5 Canvas API
- **Scroll-Triggered Observer** — All reveal animations are driven by `IntersectionObserver` (threshold 20%)
- **Narrative Line Stagger** — Subtitle/narration lines appear sequentially with 400ms between each line

### 🎨 Visual Design
- **Color-Coded Accent System** — Orange (`#ff5e00`) for titles and active states; Cyan (`#00e5ff`) for tech/data elements; Red (`#ff3333`) for camera/recording indicators
- **Documentary Yellow** — `#ffd700` for speaker labels (standard documentary convention)
- **Cinematic Typography** — Three distinct typefaces serving specific narrative roles
- **SVG Avatar** — Inline cyberpunk-style silhouette with animated scan line, HUD elements, and rim lighting

### 📱 Responsive Design
- Fluid hero layout switches from side-by-side to stacked on screens ≤ 968px
- Timeline repositions from centered dual-column to single left-aligned column on mobile
- Avatar scales from 350×350px to 280×280px
- All font sizes use `clamp()` for fluid scaling across devices

---

## 🛠️ Dev Stack

| Layer | Technology |
|---|---|
| **Structure** | HTML5 (semantic) |
| **Styling** | CSS3 (custom properties, keyframes, grid, flexbox) |
| **Logic** | Vanilla JavaScript (ES6+) |
| **Rendering** | HTML5 Canvas API |
| **Observation** | Intersection Observer API |
| **Typography** | Google Fonts (self-loading via `<link>`) |
| **Icons / Art** | Inline SVG |
| **Dependencies** | **None** — zero npm, zero frameworks |

### Fonts Loaded

| Font | Weights | Role |
|---|---|---|
| `Montserrat` | 200, 400, 700, 900 | Headings, titles, UI labels |
| `Inter` | 300, 400, 500 | Body text, descriptions |
| `Cinzel` | 500, 700 | Cinematic serif text, credits, captions |

---

## 📊 Stats

| Metric | Value |
|---|---|
| **Files** | 1 (`index.html`) |
| **External Dependencies** | 0 |
| **Lines of Code** | ~1,330 |
| **CSS Lines** | ~870 |
| **JS Lines** | ~230 |
| **HTML Lines** | ~230 |
| **CSS Custom Properties** | 8 design tokens |
| **Animations / Keyframes** | 9 (`recBlink`, `rotateRing`, `scrollDown`, `fadeIn`, `blink`, `slowPulse`, `scrollDown`, energy flash, scan line) |
| **Particle Count** | Up to 100 (responsive: `window.innerWidth / 15`) |
| **Timecode Frame Rate** | 24 fps |
| **Responsive Breakpoint** | 968px |

---

## ⚙️ Configuration

### CSS Design Tokens
All colors and fonts are defined as CSS custom properties in `:root` for easy global theming:

```css
:root {
    --bg-color:            #0e0e0e;           /* Page background */
    --accent-orange:       #ff5e00;           /* Primary accent — titles, active states */
    --accent-orange-glow:  rgba(255,94,0,0.4);/* Orange glow shadows */
    --accent-blue:         #00e5ff;           /* Secondary accent — tech/data elements */
    --accent-blue-glow:    rgba(0,229,255,0.4);/* Cyan glow shadows */
    --text-main:           #f0f0f0;           /* Primary text */
    --text-muted:          #888888;           /* Secondary/muted text */
    --font-heading:        'Montserrat', sans-serif;
    --font-body:           'Inter', sans-serif;
    --font-cinematic:      'Cinzel', serif;
}
```

### Particle System
Controlled inside the `initParticles()` function in the `<script>` block:

| Setting | Location | Default | Description |
|---|---|---|---|
| Max particle count | `Math.min(window.innerWidth / 15, 100)` | 100 | Scales with viewport width |
| Particle size | `Math.random() * 1.5 + 0.5` | 0.5–2px | Randomized per particle |
| Vertical speed | `(Math.random() * 0.5 + 0.1) * -1` | Upward drift | Slow upward float |
| Color ratio | `Math.random() > 0.8` | 20% cyan, 80% orange | Controls orange/cyan split |
| Opacity | `Math.random() * 0.5` | 0–0.5 | Randomized per particle |

### Timecode
Starts at `01:00:00:00` and counts at 24 fps. To change the starting hour, edit `hr` in the timecode block:

```js
let hr = 1; // Change start hour here
```

### Intersection Observer
Threshold for triggering scroll animations is set globally:

```js
const observerOptions = {
    threshold: 0.2  // Trigger when 20% of element is in viewport
};
```

Narrative line stagger interval (time between each line appearing):

```js
setTimeout(() => { line.classList.add('active'); }, idx * 400); // 400ms per line
```

### Typewriter Subtitle
Edit the subtitle text and typing speed in the script block:

```js
const subtitleText = "UI/UX Developer • AI Innovator • Founder";
// Speed: Math.random() * 50 + 50  →  50–100ms per character
```

### 3D Card Tilt Sensitivity
Maximum rotation angle for skill cards on hover:

```js
const rotateX = ((y - centerY) / centerY) * -10; // Max ±10 degrees
const rotateY = ((x - centerX) / centerX) * 10;
```

---

## 🚀 Getting Started

### Prerequisites
- Any modern web browser (Chrome, Firefox, Safari, Edge)
- A text editor (VS Code recommended)
- No Node.js, npm, or build tools required

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/girishlade111/Documentary-Portfolio-Template-.git

# 2. Navigate into the project folder
cd Documentary-Portfolio-Template-

# 3. Open in browser
open index.html
# or simply drag index.html into your browser
```

For live reload during editing, use VS Code's **Live Server** extension:
1. Install the **Live Server** extension in VS Code
2. Right-click `index.html` → **Open with Live Server**

---

## 🎛️ Customization Instructions

### 1. Update Personal Information
In `index.html`, find and replace these values:

| Element | Selector / Location | Default Value |
|---|---|---|
| Page title | `<title>` tag | `Girish Lade \| Building the Future with AI` |
| Hero name | `<h1 id="main-title">` | `GIRISH LADE` |
| Hero caption | `<p id="hero-caption">` | `FILE NO: AI-882 // CLASSIFIED INTEL` |
| Subtitle roles | `subtitleText` in JS | `UI/UX Developer • AI Innovator • Founder` |
| Origin narration | `.subtitle-cc` spans in `#origin` | Solapur origin story |
| Skills | `.skill-list li` in `#skills` | HTML5, React, Node.js, AWS, Unity, etc. |
| Timeline items | `.timeline-content` in `#mission` | AI Infrastructure, Lotion AI, Developer Tooling |
| Vision quote | `.subtitle-cc` spans in `#vision` | Empowering developers quote |
| Closing text | `.closing-main` and `.closing-sub` | "THIS IS JUST THE BEGINNING" |

### 2. Replace the Avatar
The avatar is an inline SVG. To use a real photo, replace the entire `<svg class="avatar">` block with:

```html
<img class="avatar" src="your-photo.jpg" alt="Your Name" />
```

### 3. Add / Remove Skill Cards
Copy any `.skill-card` block and update the `.skill-category` title and `<li>` items. Update the `.archival-stamp` text (e.g., `SYS-05`) to keep the numbering sequential.

### 4. Add / Remove Timeline Items
Copy any `.timeline-item` block inside `<div class="timeline">`. The CSS automatically alternates left/right placement using `:nth-child(even)`.

### 5. Change the Color Theme
Update the two accent variables in `:root`:

```css
--accent-orange: #ff5e00;  /* Replace with your primary color */
--accent-blue:   #00e5ff;  /* Replace with your secondary color */
```

### 6. Deploy

**GitHub Pages:**
```bash
# Push to main branch, then enable GitHub Pages in repo Settings → Pages → Deploy from branch (main / root)
```

**Netlify / Vercel:**
- Drag and drop the project folder onto [netlify.com/drop](https://app.netlify.com/drop) or import via Git in [vercel.com](https://vercel.com)

**Any Static Host:**
Upload `index.html` to any web server or CDN — no server-side logic required.

---

## 📐 Project Structure

```
Documentary-Portfolio-Template-/
│
├── index.html          # Entire application — HTML + CSS + JS in one file
└── README.md           # This file
```

All styles live inside a `<style>` block in `<head>`. All JavaScript lives inside a `<script>` block at the end of `<body>`.

---

## 🔑 Key Design Decisions

- **🗂️ Single-file architecture** — Zero build step, zero dependencies, instant deployment anywhere
- **🎞️ Documentary narrative structure** — Sections are labeled as Acts and Exhibits to guide the viewer through a story
- **🖥️ Camera UI layer** — Fixed overlays (letterbox, REC, timecode) sit in the highest z-index layer (`z-index: 9996–9999`) so they always appear on top of content
- **⚡ Performance-first animations** — All animations use `opacity`, `transform`, and `filter` (GPU-composited properties) to avoid layout thrashing
- **🔭 IntersectionObserver** — Animations only fire when elements enter the viewport, avoiding wasted computation on off-screen elements

---

## 🌐 Browser Compatibility

| Browser | Support |
|---|---|
| Chrome 80+ | ✅ Full |
| Firefox 75+ | ✅ Full |
| Safari 14+ | ✅ Full |
| Edge 80+ | ✅ Full |
| Internet Explorer | ❌ Not supported |

> **Note:** The CSS `-webkit-mask-composite: destination-out` gradient border technique requires a modern WebKit or Blink engine for the animated border rings on skill cards.

---

## 📄 License

This template is open source and free to use for personal and commercial projects. Attribution is appreciated but not required.

---

*Built with obsessive attention to cinematic detail by **Girish Lade** — AI Developer, Founder, Builder.*