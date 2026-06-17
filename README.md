# 🎙 StoryCast Microsite

A fully accessible podcast microsite built with semantic HTML5, Sass (BEM + cascade layers), and responsive design including container queries.

## 🔗 Live Pages

| Page | Description |
|---|---|
| `index.html` | Home — hero, featured episodes, about teaser |
| `episode.html` | Episode player — video, audio, transcript |
| `about.html` | About — mission statement, team grid |

---

## 📁 Project Structure

```
storycast/
├── index.html              ← Home page
├── episode.html            ← Episode player page
├── about.html              ← About & team page
├── story/
│   └── the-last-signal.html ← Story detail page
├── css/
│   └── main.css            ← Compiled CSS (cascade layers)
├── sass/
│   ├── main.scss           ← Entry point with @layer
│   ├── _colors.scss        ← Color tokens
│   ├── _typography.scss    ← Typography tokens
│   ├── _spacing.scss       ← Spacing & breakpoint tokens
│   ├── _reset.scss         ← CSS reset + .sr-only utility
│   ├── _layout.scss        ← Page-level layout primitives
│   ├── _components.scss    ← BEM components
│   └── _responsive.scss    ← Media queries & container queries
├── captions/
│   ├── episode1.vtt        ← Video/audio captions (WebVTT)
│   └── episode1-desc.vtt   ← Audio descriptions (WebVTT)
├── assets/
│   └── images/             ← Local images (optional)
└── docs/
    ├── ia.md               ← Information architecture & sitemap
    └── mockup-notes.md     ← Hi-fi mockups & design rationale
```

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Frank00067/storycast.git
```

### 2. Open the project

```bash
cd storycast
```

### 3. Run in browser

**On Windows:**
```bash
start chrome index.html
```

**On Mac:**
```bash
open index.html
```

**Or simply:** double-click `index.html` in your file explorer — it opens directly in your default browser. No server or install needed.



To compile Sass after editing `.scss` files:

```bash
# Install Sass globally
npm install -g sass

# Compile
sass sass/main.scss css/main.css

# Watch for changes
sass --watch sass/main.scss css/main.css
```

---

## ✅ Rubric Coverage

### 1. Semantic Structure
- Correct HTML5 tags throughout: `<header>`, `<main>`, `<nav>`, `<article>`, `<figure>`, `<aside>`, `<section>`, `<footer>`
- Logical heading hierarchy (H1 → H2 → H3) on every page — no skips
- `<video>` with `<track kind="captions">` and `<track kind="descriptions">`
- `<audio>` wrapped in `<figure>` with `<figcaption>` and `<track>`
- `<dl>` for episode metadata (duration, published date)

### 2. Sass & CSS Architecture
- 7 Sass partials with clear single responsibilities
- Color tokens in `_colors.scss`, typography in `_typography.scss`, spacing in `_spacing.scss`
- BEM naming on every component (`.episode-card__title`, `.nav__link--active`, etc.)
- `@layer` cascade layers: `reset → tokens → layout → components → responsive`
- Modern CSS: `clamp()`, `min()`, `aspect-ratio`, `container-type`

### 3. Responsive Design
- Mobile nav collapses to hamburger (≤ 768px)
- Fluid typography with `clamp()`
- Responsive container: `width: min(90%, 1200px)`
- Container queries on `.episode-card` (both `min-width` and `max-width`)
- Episode sidebar grid layout at 1024px+
- Hero CTA and footer stack on mobile (≤ 480px)

### 4. Accessibility — WCAG AA
- Skip link on every page
- `aria-current="page"` on active nav link
- `aria-expanded` / `aria-controls` on mobile nav toggle
- Captions on by default (`default` attribute on `<track>`)
- Full scrollable transcript: `role="region"`, `tabindex="0"`, `aria-label`
- `aria-describedby` linking audio player to transcript note
- `:focus-visible` outlines on all interactive elements
- Colour contrast: body text 15:1 (AAA), primary 5.2:1 (AA), muted text 4.6:1 (AA)

### 5. Research & Documentation
- `docs/ia.md` — sitemap, content hierarchy per page, navigation flow, user journeys
- `docs/mockup-notes.md` — ASCII hi-fi mockups for all 3 pages (desktop + mobile), colour palette rationale, accessibility decisions table, Sass architecture decisions

---

## 🎨 Design Tokens

| Token | Value | Usage |
|---|---|---|
| Background | `#0f0f0f` | Page background |
| Surface | `#1a1a2e` | Cards, nav, footer |
| Primary | `#e94560` | CTAs, active links, badges |
| Accent | `#f5a623` | Labels, tags, eyebrows |
| Text | `#f0f0f0` | Body copy |
| Muted | `#a0a0b0` | Secondary text |
| Border | `#2e2e4e` | Dividers, card borders |

---

## ♿ Accessibility Features

| Feature | Implementation |
|---|---|
| Skip link | Visible on focus, links to `#main-content` |
| Captions | WebVTT on `<video>` and `<audio>`, default on |
| Audio descriptions | `<track kind="descriptions">` on video |
| Full transcript | Scrollable region below audio player |
| Keyboard navigation | All interactive elements Tab-accessible |
| Screen reader support | ARIA roles, labels, and live regions |
| Focus indicators | `outline` on `:focus-visible` across all elements |

---

## © 2026 StoryCast. All rights reserved.
