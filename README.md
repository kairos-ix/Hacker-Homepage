# NEXUS — Glassmorphism Cyber Homepage

> A professional, dark-themed browser start page built with pure HTML, CSS, and Vanilla JavaScript. No frameworks. No dependencies. Just clean, fast, elegant code.

**Built by Sahil Maurya** &nbsp;|&nbsp; 🌐 **[Live Demo → hacker-homepage.vercel.app](https://hacker-homepage.vercel.app/)**

---

## 🌐 Live Demo

**[https://hacker-homepage.vercel.app/](https://hacker-homepage.vercel.app/)**

Deployed on Vercel — instant load, globally distributed.

---

## Preview

```
╔══════════════════════════════════════════╗
║          NEXUS  //  terminal ready       ║
║  ┌──────────────────────────────────┐    ║
║  │        21 : 45 : 33              │    ║
║  │   Friday · February 27, 2025     │    ║
║  └──────────────────────────────────┘    ║
║  ┌──────────────────────────────────┐    ║
║  │  🔍  Search the web…         →   │    ║
║  └──────────────────────────────────┘    ║
║  ┌────────┐ ┌────────┐ ┌────────┐       ║
║  │YouTube │ │ GitHub │ │ Gmail  │       ║
║  ├────────┤ ├────────┤ ├────────┤       ║
║  │ChatGPT │ │LinkedIn│ │   X    │       ║
║  └────────┘ └────────┘ └────────┘       ║
║  ● sys.online   Asia/Kolkata·UTC+5   W9 ║
╚══════════════════════════════════════════╝
```

---

## Features

### Visual Design
- Deep blue-green animated gradient background (`#0a1628` → `#2c5364`)
- Glassmorphism panels with `backdrop-filter: blur(20px)` and soft teal glow
- Very faint matrix-style code rain (opacity 0.035) — subtle, not gimmicky
- Floating soft teal particle layer for depth
- Smooth staggered fade-in animations on all components
- Gentle floating animation on the clock card
- Full CSS design token system via custom properties (`--accent`, `--glass-bg`, etc.)

### Components

**Clock Card** — Live digital clock updating every second with HH:MM:SS display, full date string, and a seconds progress bar that fills across the width.

**Search Panel** — Animated typewriter placeholder cycling through five phrases. Searches Google in a new tab on Enter or button click. Cyan glow ring on focus.

**Quick Access Grid** — Six glass link cards (YouTube, GitHub, Gmail, ChatGPT, LinkedIn, X/Twitter) with inline SVG icons, hover scale + glow effects, and staggered entry animation. All open in new tabs.

**Status Bar** — Auto-detected timezone with UTC offset, ISO week number, and an animated pulsing online indicator.

**Custom Cursor** — A lerp-smoothed glowing teal orb that follows the mouse and expands over interactive elements. Automatically disabled on touch devices.

### Interactivity
- `/` keyboard shortcut focuses the search input from anywhere on the page
- `Escape` blurs the search input
- All animations use `requestAnimationFrame` — zero `setInterval` lag on canvas effects
- Matrix rain is throttled to ~11fps to stay lightweight

### Accessibility
- Full ARIA labels on all sections and interactive elements
- `aria-live` regions on clock and search hint
- `prefers-reduced-motion` media query disables all animations
- Minimum 88px tap targets on mobile
- Focus-visible outlines on all keyboard-navigable elements

### Responsive Layout

| Breakpoint | Quick Links Grid | Notes |
|---|---|---|
| Desktop (> 768px) | 3 columns | Centered, max-width 900px |
| Tablet (≤ 768px) | 2 columns | Slightly reduced padding |
| Mobile (≤ 480px) | 2 columns | URL labels hidden, larger tap targets |

No horizontal scroll. No overflow. Relative units throughout (`rem`, `%`, `vw`, `vh`, `clamp()`).

---

## File Structure

```
nexus-homepage/
├── index.html      # Semantic HTML structure, ARIA, SVG icons
├── style.css       # All styles — CSS variables, glass, animations, responsive
├── script.js       # 8 modular IIFE JS modules
└── README.md       # This file
```

### JavaScript Modules (`script.js`)

| Module | Responsibility |
|---|---|
| `Clock` | Live time, date, seconds bar |
| `Search` | Typewriter placeholder, Google search |
| `CursorGlow` | Lerp cursor orb, hover expand |
| `MatrixRain` | Canvas code rain, throttled RAF |
| `Particles` | Canvas floating dots, pulsing alpha |
| `StatusBar` | Timezone, UTC offset, week number |
| `Shortcuts` | `/` and `Escape` keyboard bindings |
| `LinkStagger` | JS-driven staggered card entry |

---

## Usage

### As a Browser Start Page

**Chrome / Edge**
1. Go to `Settings → On startup → Open a specific page`
2. Click "Add a new page" and enter the full local path:
   `file:///path/to/nexus-homepage/index.html`

**Firefox**
1. Go to `Settings → Home → Homepage and new windows`
2. Select "Custom URLs" and enter the file path

**Safari**
1. Go to `Preferences → General → Homepage`
2. Enter the file path

### Local Development

No build tools required. Just open `index.html` in any modern browser:

```bash
# Option 1 — Open directly
open index.html

# Option 2 — Serve locally (avoids any file:// quirks)
npx serve .
# or
python3 -m http.server 3000
```

---

## Customisation

### Change Accent Color
Edit the CSS variable in `style.css`:
```css
:root {
  --accent: #5de8d8;  /* change this to any color */
}
```

### Add / Remove Quick Links
In `index.html`, duplicate or remove any `.link-card` block inside `.links-grid`. Replace the SVG path and `href` as needed.

### Change Search Engine
In `script.js`, find the `doSearch` function inside the `Search` module and replace the URL:
```js
// Google (default)
window.open(`https://www.google.com/search?q=${encodeURIComponent(q)}`, ...);

// DuckDuckGo
window.open(`https://duckduckgo.com/?q=${encodeURIComponent(q)}`, ...);

// Brave Search
window.open(`https://search.brave.com/search?q=${encodeURIComponent(q)}`, ...);
```

### Adjust Matrix Rain Intensity
In `script.js`, inside the `MatrixRain` module:
```js
const INTERVAL = 90;  // higher = slower/more subtle
```
In `style.css`:
```css
#matrix-canvas { opacity: 0.035; }  /* lower = more invisible */
```

### Adjust Particle Count
In `script.js`, inside the `Particles` module:
```js
const COUNT = 38;  /* lower for better performance on older devices */
```

---

## Browser Support

Works in all modern browsers that support `backdrop-filter`:

| Browser | Support |
|---|---|
| Chrome 76+ | ✅ Full |
| Edge 79+ | ✅ Full |
| Firefox 103+ | ✅ Full |
| Safari 14+ | ✅ Full |
| Opera 63+ | ✅ Full |

Older browsers that don't support `backdrop-filter` will gracefully fall back to a semi-transparent dark panel — the page remains fully functional.

---

## Tech Stack

- **HTML5** — Semantic, accessible markup
- **CSS3** — Custom properties, Grid, Flexbox, `backdrop-filter`, `clamp()`, keyframe animations
- **Vanilla JavaScript (ES2020)** — IIFE modules, `requestAnimationFrame`, Canvas 2D API
- **Google Fonts** — JetBrains Mono + Syne (loaded via `<link>`, no JS dependency)
- **Zero frameworks. Zero npm. Zero build step.**

---

## Performance Notes

- Canvas effects throttled to avoid GPU pressure
- `requestAnimationFrame` used for all animation loops — never `setInterval` on visuals
- Fonts preconnected for fast load
- Matrix rain and particles are intentionally low-intensity — designed for all-day use without distraction
- All transitions use `cubic-bezier(0.4, 0, 0.2, 1)` for smooth 60fps feel

---

## License

MIT — free to use, modify, and distribute.

---

*crafted by **Kairos***
