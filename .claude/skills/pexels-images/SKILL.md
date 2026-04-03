---
name: pexels-images
description: Fetches background photos from Pexels API for pitch decks and HTML presentations. Use when generating visual slides that need atmospheric photography. Called by other skills (pitch-deck, investor-brief, html-presentation) — not typically invoked directly.
---

# Pexels Images Skill

Fetches high-quality landscape photos from Pexels at generation time and embeds them directly into HTML slides as background images.

## API Configuration

- **API Key:** Read from environment variable `PEXELS_API_KEY`
- **Endpoint:** `https://api.pexels.com/v1/search`
- **Auth header:** `Authorization: $PEXELS_API_KEY`
- **Default params:** `orientation=landscape&per_page=1`

### How to fetch

Use `curl` via Bash:
```bash
curl -s -H "Authorization: $PEXELS_API_KEY" \
  "https://api.pexels.com/v1/search?query=SEARCH_TERM&per_page=1&orientation=landscape"
```

Parse the JSON response and extract: `photos[0].src.large2x` (primary) or `photos[0].src.large` (fallback).

Also extract: `photos[0].photographer` for the credit line.

## When to Use Photos

Creatively decide the best visual treatment **per slide**. Not every slide needs a photo. Choose from:

| Layout | When to use | CSS approach |
|---|---|---|
| **Full-bleed background** | Title slides, emotional hooks, "Why Now" | `background-image` covering entire slide |
| **Split layout** | Problem/pain slides, market context | 50/50 — photo left, content right (or vice versa) |
| **Atmospheric overlay** | Slides with stats or key numbers | Photo at 15-25% opacity behind content |
| **Section divider** | Between major sections | Full-bleed with large centered text overlay |

## Slides That NEVER Get Photos

These slide types must use solid backgrounds only (brand colors, gradients, or patterns):

- **Team** — people slides use bios/names, not stock photos of strangers
- **Advisors & Partners** — same reason
- **Solution** — focus on diagrams, process flows, or product visuals
- **Traction / References** — data and logos, not decoration
- **Competitor Landscape** — tables and matrices need clean backgrounds
- **Business Model** — pricing and unit economics need clarity
- **Key Financials** — numbers need full legibility

## Dark Gradient Veil (MANDATORY)

Every photo used as a background MUST have a dark gradient overlay for text legibility:

```css
/* Full-bleed or section divider */
background: linear-gradient(
  135deg,
  rgba(8, 10, 24, 0.82) 0%,
  rgba(8, 10, 24, 0.65) 50%,
  rgba(8, 10, 24, 0.78) 100%
), url('PHOTO_URL');
background-size: cover;
background-position: center;

/* Atmospheric overlay (subtle) */
background: linear-gradient(
  180deg,
  rgba(8, 10, 24, 0.88) 0%,
  rgba(8, 10, 24, 0.75) 100%
), url('PHOTO_URL');
background-size: cover;
background-position: center;
```

## Photo Credit (MANDATORY)

Every slide with a photo must include a discreet photographer credit:

```html
<span style="position: absolute; bottom: 8px; right: 12px; font-size: 9px; opacity: 0.18; color: #ffffff;">
  Photo: [Photographer Name] / Pexels
</span>
```

## Search Query Strategy

Choose evocative, abstract queries — not literal descriptions of slide content:

| Slide topic | Good query | Bad query |
|---|---|---|
| Title / opening | `technology abstract dark` | `company logo` |
| The Pain | `corporate office stress` | `problem` |
| Why Now / Timing | `sunrise horizon future` | `clock` |
| Market Opportunity | `city skyline aerial night` | `market` |
| Go To Market | `highway speed motion` | `sales` |
| The Ask | `handshake business partnership` | `money` |
| Deep Dive section | `data center technology blue` | `deep` |

Always add `dark` or `moody` to queries when slides use dark backgrounds — this ensures photos blend naturally.

## Fallback Behavior

If the Pexels API call fails (network error, invalid key, empty results):

1. **Do NOT block generation** — continue without the photo
2. Use solid fallback background: `background: #0D0F1E;`
3. Log a note in the generation output: "Pexels API unavailable — using solid backgrounds"
4. The document must still look polished without photos

## Caching / Efficiency

- Fetch all needed photos at the start of generation (batch the curl calls)
- Use `per_page=3` and pick the best match from results if the first photo doesn't fit
- Never fetch more than 10 photos per document
- Embed the Pexels CDN URLs directly in HTML — do not download images locally

## Integration With Other Skills

This skill is called by:
- `pitch-deck` — for client-facing sales decks
- `investor-brief` — for investor presentations
- `html-presentation` — for any HTML visual output

When another skill calls pexels-images, it should:
1. Determine which slides are eligible for photos (exclude the NEVER list)
2. Generate appropriate search queries per slide
3. Fetch photos via curl
4. Apply the correct layout, veil, and credit
