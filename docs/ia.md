# StoryCast — Information Architecture

## Sitemap

```
StoryCast (root)
├── index.html          ← Home
│   ├── Hero (CTA → Episodes, About)
│   ├── Featured Episodes (→ episode.html)
│   └── About Teaser (→ about.html)
│
├── episode.html        ← Episode Player
│   ├── Video player (with captions + audio descriptions)
│   ├── Audio-only player
│   ├── Full transcript
│   └── More Episodes sidebar
│
└── about.html          ← About
    ├── Mission statement
    └── Team grid
```

## Content Hierarchy

### Home (index.html)
```
h1  → "Stories Worth Hearing"          (page identity)
  h2  → "Featured Episodes"            (content section)
    h3  → [Episode title × 3]          (individual items)
  h2  → "Independent Storytelling"     (about teaser)
```

### Episode (episode.html)
```
h1  → "The Last Signal"                (episode identity)
  h2  → "Listen: Audio Version"        (player section)
    h3  → "Full Transcript"            (nested content)
  h2  → "More Episodes"               (sidebar)
    h3  → [Episode title × 2]
```

### About (about.html)
```
h1  → "We believe in the power of audio"   (page identity)
  h2  → "Our Mission"                       (content section)
  h2  → "Meet the Team"                     (content section)
    h3  → [Team member name × 4]            (individual items)
```

## Navigation Flow

```
[Home] ←→ [Episodes] ←→ [About]
  ↓
[Episode Player]
  ↓
[More Episodes] → [Episode Player]
```

## Key User Journeys

1. **Discover → Listen**: Home → Featured Episodes → Episode Player → Play
2. **Browse → Explore**: Home → About → Back to Episodes
3. **Direct Access**: Any page accessible from global nav in 1 click
