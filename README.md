# Nexus Homepage

A dark browser start page built with plain HTML, CSS, and JavaScript. No frameworks, no build tools — open the file and it works.

**Built by Kairos** | **Live demo:** https://hacker-homepage.vercel.app

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
║  │  /  Search the web…          →   │    ║
║  └──────────────────────────────────┘    ║
║  ┌────────┐ ┌────────┐ ┌────────┐       ║
║  │YouTube │ │ GitHub │ │ Gmail  │       ║
║  ├────────┤ ├────────┤ ├────────┤       ║
║  │ChatGPT │ │LinkedIn│ │   X    │       ║
║  └────────┘ └────────┘ └────────┘       ║
║  sys.online   Asia/Kolkata·UTC+5   W9   ║
╚══════════════════════════════════════════╝
```

---

## What's in it

- Live clock with a seconds progress bar
- Search bar (Google by default — easy to swap)
- Six quick-link cards: YouTube, GitHub, Gmail, ChatGPT, LinkedIn, X
- Subtle matrix rain and floating particle layer in the background
- Status bar showing your timezone and ISO week number
- A glowing custom cursor that follows your mouse
- Keyboard shortcut: `/` focuses search, `Escape` blurs it

The design is meant to stay on screen all day without being distracting. The background effects are deliberately low-intensity.

---

## Getting started

No install needed. Open `index.html` directly in any modern browser.

If you hit file:// quirks, run a local server instead:

```bash
npx serve .
# or
python3 -m http.server 3000
```

---

## Set it as your start page

**Chrome / Edge**
Settings → On startup → Open a specific page → add the full file path

**Firefox**
Settings → Home → Homepage and new windows → Custom URLs → paste the file path

**Safari**
Preferences → General → Homepage → paste the file path

---

## Customizing

**Accent color**

Edit the CSS variable in `style.css`:
```css
:root {
  --accent: #5de8d8;
}
```

**Quick links**

In `index.html`, copy or delete any `.link-card` block inside `.links-grid`. Swap the SVG path and `href` to point wherever you want.

**Search engine**

In `script.js`, find `doSearch` inside the `Search` module:
```js
// DuckDuckGo
window.open(`https://duckduckgo.com/?q=${encodeURIComponent(q)}`, ...);

// Brave Search
window.open(`https://search.brave.com/search?q=${encodeURIComponent(q)}`, ...);
```

**Matrix rain intensity**

```js
const INTERVAL = 90; // higher = slower and more subtle
```
```css
#matrix-canvas { opacity: 0.035; } /* lower = nearly invisible */
```

**Particle count**

```js
const COUNT = 38; /* reduce if the page feels heavy on older hardware */
```

---

## File structure

```
nexus-homepage/
├── index.html    — markup, ARIA labels, SVG icons
├── style.css     — all styles, CSS variables, animations, responsive layout
├── script.js     — 8 self-contained IIFE modules
└── README.md
```

The JavaScript is split into eight modules: `Clock`, `Search`, `CursorGlow`, `MatrixRain`, `Particles`, `StatusBar`, `Shortcuts`, and `LinkStagger`. Each handles one thing and nothing else.

---

## Browser support

Works in Chrome 76+, Edge 79+, Firefox 103+, Safari 14+, and Opera 63+.

Browsers that don't support `backdrop-filter` fall back to a semi-transparent dark panel. The page still works fine.

---

## Accessibility notes

- ARIA labels on all sections and interactive elements
- `aria-live` regions on the clock and search hint
- All animations disabled when `prefers-reduced-motion` is on
- Minimum 88px tap targets on mobile
- Focus-visible outlines on all keyboard-navigable elements

---

## Responsive layout

| Breakpoint | Quick links grid |
|---|---|
| Desktop (> 768px) | 3 columns |
| Tablet (768px) | 2 columns |
| Mobile (480px) | 2 columns, URL labels hidden |

---

## Tech

Plain HTML, CSS, and vanilla JavaScript (ES2020). Google Fonts loaded via `<link>`. No npm, no build step, no dependencies.

---

MIT License — use it, change it, ship it. See [LICENSE](./LICENSE).
