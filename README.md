# OOTS Business Procedures — Interactive Map

A single self-contained HTML + JavaScript app that shows the OOTS (Once-Only Technical
System) business procedures from CSAT as an **interactive left-to-right tree**, with a
**user-selectable root**, expand/collapse, search, filters and a **metrics dashboard**.

Everything runs client-side in the browser. There is no backend, build step or database —
the dataset is embedded in `index.html` and parsed in the page.

## Features

- **Pivotable root** — root the tree by Procedure, Requirement, Member State, Domain,
  SDG category or Lifecycle status. Switching the root rebuilds the tree.
- **Left-to-right layered tree** (Cytoscape.js + dagre). Shared requirements draw multiple
  incoming edges, so evidence **reuse is visible**.
- **Expand / collapse** per node, plus **Expand all** / **Collapse all**.
- **Search** procedures, requirements, MS, domain — matches highlight, the rest dim;
  press Enter to zoom to matches.
- **Filters** (combine AND across categories, OR within): Member State, SDG, Domain,
  Lifecycle status, and a Has / No requirements toggle. Filters update the tree and metrics live.
- **Metrics dashboard** — global coverage, lifecycle-status and domain bars, most-reused
  requirements, top procedures by requirement count, and a sortable per-Member-State table
  (click a row to filter to that MS). A "global" toggle ignores filters.
- **Detail panel** on click, per node type. Null authorities create no nodes; nulls show
  "Not specified".
- Nice-to-haves: Reset view, Dagre/Breadthfirst layout switch, Export PNG, and last
  root/filters remembered in `localStorage` (only when served over http(s)).

## Run it

Just **double-click `index.html`** — it works offline. An internet connection is only
needed the first time so the Cytoscape / dagre libraries load from their CDN.

## Deploy to GitHub Pages

1. Create a free GitHub account if you don't have one.
2. Create a new **public** repository, e.g. `oots-map`.
3. Use **Add file → Upload files** to upload `index.html` (and this `README.md`). Commit.
4. Go to **Settings → Pages**.
5. Source = **Deploy from a branch**; Branch = `main`; Folder = **/ (root)**. Save.
6. After ~1 minute the site is live at `https://<username>.github.io/oots-map/`.

That URL is the demo link. The same `index.html` also works double-clicked offline as a fallback.

## The data

77 procedures (76 from CSAT + 1 Airtable master). 30 have requirements, 47 are empty
(≈39% coverage), 97 requirement instances across 23 distinct requirements. 15 Member
States; domains Population / Education / Business / Professional Qualifications; lifecycle
status Draft 68 / In review 6 / Published 2 / Airtable 1. All figures in the app are
computed from the embedded data, not hardcoded.
