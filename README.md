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
| Categories as nested lists that start collapsed | Progressive disclosure: open only what you need |
| Active layers shown as chips, coloured by category | See at a glance what's on the map; remove a layer with one tap |
| Search, filter by category and sort | Get to a specific layer fast as the list grows |
| "On site" tags and a hint about intersecting layers | Surfaces what actually affects this site first |

**3. Mobile.** The original challenge was desktop only. Here the map comes first:
- a floating search bar
- category chips that jump straight to a section
- a draggable bottom sheet with three resting positions and flick gestures

## Built with Claude Code

The original concept existed only as Figma wireframes. I used Claude Code to turn it into a real, interactive prototype and then kept refining it the way I would with an engineer: by describing changes in plain language and reviewing the result in a browser.

Along the way we:
- rebuilt the static mock-up as a working MapLibre map with real layer geometry
- added the responsive mobile layout, bottom sheet and gestures
- made the filter menu fully keyboard-accessible, and ran a design audit (contrast, tap targets, semantics) and fixed what it found
- iterated on details in quick loops: the rail, the top bar, chip colours, and a logo that went through several rounds
- published it with GitHub Pages

**What I learned**
- **Fast for layout, interaction and polish.** Changes that would take a round trip with an engineer took minutes, and I could test real behaviour instead of simulating it in Figma.
- **Precise feedback matters.** Vague requests ("make it better") led to guesses, while specific ones ("line the sheet up with the top of the search bar") landed first time.
- **Visual craft still needs a designer's eye.** The logo took several rounds of direction before it worked.
- **You still own the judgement:** what to build, what "good" looks like, and when something is done.

## Try it

- **Desktop:** tick layers, filter and sort, collapse the panel with the rail button, and double-click the project name to rename it.
- **Mobile:** tap a category chip, then drag or flick the bottom sheet.
- **Recordings:** add `?taps` to the URL to show touch indicators when screen-recording.

It's a single static `index.html` with no build step. To run it locally:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.
