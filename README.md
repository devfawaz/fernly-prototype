# Fernly — Project Dashboard (design concept)

> **Disclaimer:** This is an unofficial design exercise. Fernly is a fictional product and brand, not affiliated with, endorsed by, or representative of any company. Place names and planning references are used for illustration only.

**Live prototype:** https://devfawaz.github.io/fernly-prototype/

## What is Fernly?

Fernly is an imagined biodiversity-intelligence tool for land and development projects. Planners, ecologists and developers use it to understand what a site affects before they build: which protected areas, habitats, waterways, carbon stores and development constraints sit on or near it.

For each project, Fernly brings the relevant environmental data together in one place:

- **Spatial layers:** mapped datasets grouped into five categories (Compliance & Conservation, Habitat & Land Use, Water & Hydrology, Climate & Carbon, Development Constraints), each flagged when it intersects the site.
- **Ecosystem charts:** summaries of species, habitat condition and land cover, alongside the map.

The name and mark come from the fern fiddlehead, new growth unfurling, which fits a product about understanding land before it changes.

## What this prototype shows

The project dashboard: a single site (Blackwattle Bay Renewal, Sydney) with its layers mapped around it.

- **Desktop:** a narrow navigation rail, a layer panel you can open and close, and a floating project bar. You can rename the project by double-clicking its name.
- **Mobile:** a map-first layout with a full-width header, a floating search bar, category chips that jump to a section, and a draggable bottom sheet.
- **Layers:** tick a layer to highlight its areas on a live MapLibre map, show labels and numbers, and see which layers intersect the site.
- **Finding data:** filter by category from a keyboard-accessible dropdown, and search across layers and charts.

Add `?taps` to the URL to show touch indicators when making screen recordings.

## Run locally

It's a single static `index.html` file, so there's no build step:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.
