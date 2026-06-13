# StoryCast — Mockup Notes & Design Rationale

## Visual Direction

**Theme:** Dark, cinematic, audio-first. Inspired by podcast apps (Overcast, Pocket Casts)
and documentary streaming platforms. The palette uses near-black backgrounds with
high-contrast accent colours to meet WCAG AA contrast ratios.

**Palette rationale:**
- `#0f0f0f` background — reduces eye strain for late-night listening sessions
- `#e94560` primary — high contrast against dark backgrounds (ratio > 4.5:1)
- `#f5a623` accent — warm amber for labels/tags, visually distinct from primary
- `#f0f0f0` body text on dark bg — contrast ratio ~15:1 (exceeds AA and AAA)

---

## Page Mockups (High-Fidelity Descriptions)

### Home — index.html

```
┌──────────────────────────────────────────────────────┐
│  🎙 StoryCast          Home  Episodes  About          │  ← nav
├──────────────────────────────────────────────────────┤
│                                                      │
│         NEW EPISODES EVERY WEEK                      │
│    Stories Worth Hearing                             │  ← h1, hero
│    StoryCast brings you original audio dramas...     │
│    [ Listen Now ]  [ About the Show ]                │
│                                                      │
├──────────────────────────────────────────────────────┤
│  LATEST RELEASES                                     │
│  Featured Episodes                                   │  ← h2
│                                                      │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐           │
│  │  [img]   │  │  [img]   │  │  [img]   │           │
│  │ Title    │  │ Title    │  │ Title    │  ← cards  │
│  │ Desc...  │  │ Desc...  │  │ Desc...  │           │
│  │ 42min    │  │ 58min    │  │ 28min    │           │
│  └──────────┘  └──────────┘  └──────────┘           │
├──────────────────────────────────────────────────────┤
│  WHO WE ARE / Independent Storytelling               │  ← h2
│  [ Meet the Team ]                                   │
├──────────────────────────────────────────────────────┤
│  © 2025 StoryCast    Home · Episodes · About         │  ← footer
└──────────────────────────────────────────────────────┘
```

**Mobile (< 480px):** Cards stack vertically. Hero CTA buttons stack. Nav collapses to hamburger.

---

### Episode Page — episode.html

```
Desktop (≥ 1024px):
┌─────────────────────────────────┬──────────────┐
│  AUDIO DRAMA / The Last Signal  │  More        │
│  ┌─────────────────────────┐    │  Episodes    │
│  │   VIDEO PLAYER           │    │  ────────── │
│  │   [16:9 ratio]           │    │  [Card]     │
│  └─────────────────────────┘    │  [Card]     │
│  Audio player ▶                 │              │
│  Description text               │              │
│  ─────────────────────────────  │              │
│  Full Transcript ▼              │              │
└─────────────────────────────────┴──────────────┘

Mobile: Single column, sidebar moves below player.
```

---

### About Page — about.html

```
┌──────────────────────────────────────────────────────┐
│  We believe in the power of audio                    │  ← h1
│  StoryCast started in 2022...                        │
├──────────────────────────────────────────────────────┤
│  WHY WE EXIST / Our Mission                          │  ← h2
│  Body text...                                        │
├──────────────────────────────────────────────────────┤
│  THE PEOPLE / Meet the Team                          │  ← h2
│                                                      │
│  ┌───────┐  ┌───────┐  ┌───────┐  ┌───────┐        │
│  │ [img] │  │ [img] │  │ [img] │  │ [img] │        │
│  │ Name  │  │ Name  │  │ Name  │  │ Name  │        │
│  │ Role  │  │ Role  │  │ Role  │  │ Role  │        │
│  └───────┘  └───────┘  └───────┘  └───────┘        │
└──────────────────────────────────────────────────────┘
```

---

## Accessibility Decisions

| Decision | Reasoning |
|---|---|
| Skip link at top of every page | Keyboard users bypass repeated nav |
| `aria-current="page"` on active nav link | Screen readers announce current location |
| `aria-expanded` on mobile nav toggle | State communicated to assistive tech |
| `<dl>` for episode metadata (duration, date) | Semantically correct key-value pairs |
| `<figure>` + `figcaption` wrapping video | Associates caption text with media |
| `<track kind="captions">` with `default` | Captions on by default, no user action needed |
| `<track kind="descriptions">` | Audio descriptions for visual content |
| Full transcript in scrollable `<div role="region">` | WCAG 1.2.3 / 1.2.8 compliance |
| `tabindex="0"` on transcript region | Keyboard-scrollable without tabbing through all text |
| `focus-visible` outlines on all interactive elements | WCAG 2.4.7 — visible focus |
| Color contrast: primary `#e94560` on `#0f0f0f` | Passes WCAG AA (ratio 5.2:1) |

---

## Sass Architecture Decisions

| Decision | Reasoning |
|---|---|
| `@layer` cascade layers | Prevents specificity conflicts across partials |
| Design tokens in `_tokens.scss` | Single source of truth for all values |
| BEM naming throughout | Predictable, encapsulated component styles |
| `clamp()` for font sizes | Fluid typography without breakpoint jumps |
| Container queries on `.episode-card` | Component adapts to its container, not viewport |
| `min()` for `.container` width | Responsive container without a media query |
