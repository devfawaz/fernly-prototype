# Fernly — Spatial Data Dashboard

**Live prototype:** https://devfawaz.github.io/fernly-prototype/

> **Disclaimer:** Fernly is a fictional brand. This is an unofficial design concept, not affiliated with or representative of any company. Place names and planning references are for illustration only.

Fernly began as a take-home design challenge for a biodiversity data startup. I redesigned their project dashboard, the screen where sustainability teams explore environmental data around a development site. Later I used it to test a second idea: can a product designer take a Figma concept all the way to a working, responsive prototype by pairing with [Claude Code](https://claude.com/claude-code)?

## The problem

The dashboard puts environmental data for a project site on a map: protected areas, habitats, waterways, carbon, development constraints. As more spatial layers were added, it became hard to use:

- **Overcrowded UI.** A long, flat list of layers made navigation and filtering slow.
- **High cognitive load.** Charts, legends and layers were mixed together with no clear structure.
- **No quick path to answers.** Users on tight deadlines couldn't quickly find the data that mattered for their assessment.

> *How might we create a scalable solution that reduces cognitive load, so users can easily navigate and interpret a growing number of spatial layers?*

## What I designed

**1. Structure before screens.** I split the biodiversity data into two groups, based on the needs of two personas (a sustainability manager and an ESG consultant):
- **Spatial layers,** grouped by how people use them: Compliance & Conservation, Habitat & Land Use, Water & Hydrology, Climate & Carbon, and Development Constraints.
- **Ecosystem charts:** species, ecosystem condition and local biodiversity.

**2. Key decisions**

| Decision | Why |
|---|---|
| Project details moved into a bar floating over the map | Frees the side panel for the data itself |
| Layers and charts on separate tabs | Breaks the information into manageable chunks, with less scrolling |
| A segmented control for chart types (Species, Condition, Biodiversity) | One chart group at a time keeps the panel short; search still shows every matching chart |
| Categories as nested lists that start collapsed | Progressive disclosure: open only what you need |
| Active layers shown as chips, coloured by category | See at a glance what's on the map; remove a layer with one tap |
| Search, filter by category and sort | Get to a specific layer fast as the list grows |
| Click a map shape for a details card: layer, category, whether it is on site, and a link to view it in the panel | Connects the map and the list, so users can go from "what is this?" to its full details in one step |
| Opacity slider per layer: white track filled in the layer's own colour with a white handle, and flat grey while the layer is off | Overlapping layers stay readable, so you can fade context to let a key layer stand out. A custom-drawn slider looks the same for every layer, instead of the browser shading it differently for each colour |
| Drag categories into your own order; a "Custom" sort appears only once you do | People work in different orders, and the option only shows up when it means something |
| "On site" tags and a hint about intersecting layers | Surfaces what actually affects this site first |
| Risk-first defaults: a new project switches on up to 3 layers that intersect the site, regulatory triggers (threatened communities, protected areas, species) before footprint constraints (flood, contamination) | The first view answers "could anything stop or change this project?", and a site with no compliance hits says so |

**3. Mobile.** The original challenge was desktop only. Here the map comes first:
- a floating search bar
- category chips that jump straight to a section
- a draggable bottom sheet with three resting positions and flick gestures
- press and hold anywhere on a category header, then drag, to reorder categories (the desktop grip handles are mouse-only, so touch has its own long-press gesture)

## Built with Claude Code

The original concept existed only as Figma wireframes. I used Claude Code to turn it into a real, interactive prototype and then kept refining it the way I would with an engineer: by describing changes in plain language and reviewing the result in a browser.

Along the way we:
- rebuilt the static mock-up as a working MapLibre map with real layer geometry
- added the responsive mobile layout, bottom sheet and gestures
- ran a design audit and fixed its main findings: the whole layer list (checkboxes, switches, categories, filter) now works with a keyboard and a screen reader, controls have proper labels, and low-contrast text was darkened
- iterated on details in quick loops: the rail, the top bar, chip colours, and a logo that went through several rounds
- published it with GitHub Pages

**What I learned**
- **Fast for layout, interaction and polish.** Changes that would take a round trip with an engineer took minutes, and I could test real behaviour instead of simulating it in Figma.
- **Precise feedback matters.** Vague requests ("make it better") led to guesses, while specific ones ("line the sheet up with the top of the search bar") landed first time.
- **Visual craft still needs a designer's eye.** The logo took several rounds of direction before it worked.
- **You still own the judgement:** what to build, what "good" looks like, and when something is done.

## Try it

- **Desktop:** tick layers, adjust a layer's opacity, click a shape on the map for its details, drag a category by its grip to reorder it, filter and sort, collapse the panel with the rail button, and double-click the project name to rename it.
- **Mobile:** tap a category chip or a shape on the map, drag or flick the bottom sheet, and press and hold a category to reorder it.
- **Recordings:** add `?taps` to the URL to show touch indicators when screen-recording.

It's a single static `index.html` with no build step. To run it locally:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

---

© 2026 Muhammed Fawaz. All rights reserved. Shared for portfolio review only; see [LICENSE](LICENSE).

Icons from [Phosphor](https://phosphoricons.com) (MIT licence).
