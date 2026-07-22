# El Paso Housing — Field Index

A single landing page that indexes every standalone housing data report in this project, grouped by topic, with a short synthesized narrative up top.

**Live file:** `el-paso-housing-index-v3.html` — a self-contained HTML file (no build step, no dependencies to install). Open it directly in a browser or deploy it as-is.

## What this is

Each report in this project (Missing Middle Housing, Migration, Housing Unit Change, etc.) lives on its own GitHub Pages site. This page doesn't replace any of them — it's the front door that ties them together: a short "state of housing in El Paso" summary, followed by every report grouped into four categories, each with its own one-paragraph finding.

## Structure

```
Hero
 ├─ Eyebrow + headline ("The State of Housing in El Paso")
 ├─ 3-sentence narrative dek
 └─ 4-stat strip (vacancy, income gap, price premium, permit decline)

Demand    — who's moving to and buying in El Paso
Supply    — what's getting built, and where
Market    — prices, rents, and transactions
Tools     — policy levers / simulators

Footer — data source note
```

Each category section has the same shape: a colored eyebrow pill, a bold headline with a highlighted phrase, a 2–3 sentence finding, then a grid of report cards.

## Design system

Matches the visual style of the individual reports (e.g. the Missing Middle Housing page):

| Element | Choice |
|---|---|
| Display type | Archivo Black (headlines, stat numbers) |
| Body type | DM Sans |
| Background | Cream (`#F7F1E2`) |
| Cards | Thick black border + hard offset drop-shadow ("sticker" style), no blur |
| Category colors | Demand = yellow · Supply = mint · Market = salmon · Tools = lavender |
| Emphasis | `<mark class="hl">` yellow-highlighter spans on key numbers/phrases |

All colors and fonts are set as CSS custom properties (`:root` and a few utility classes) at the top of the `<style>` block, so a palette or font swap only touches one place.

## How to add a new report

There's no data array to edit for this version — each card is hand-written HTML inside its category's `<div class="cardgrid">`. To add one:

1. Find the right category section (`id="demand"`, `id="supply"`, `id="market"`, or `id="tools"`).
2. Copy an existing `<a class="card pop">...</a>` block inside that section's `.cardgrid`.
3. Update the `href`, the small `.tag` (dataset size / label), the `<h3>` title, and the one-line `<p>` finding (keep it under ~25 words to match the others).
4. If it changes the category's overall story, consider a small edit to that section's `.cat-finding` paragraph — but this is optional.

If a report doesn't fit one of the four categories yet, or you want a "Coming Soon" placeholder while a report is still in progress, use:

```html
<div class="card soon pop">
  <div class="tag">Untitled Report</div>
  <h3>Reserved slot</h3>
  <p>One-line description of what's coming.</p>
  <div class="go">Not yet published</div>
</div>
```

## Current reports (14)

**Demand**
- Desert Drift (Migration)
- El Paso Homebuyer Analysis (First-Time Buyers)
- The El Paso Housing Matrix (Buyer Insights)
- The Hidden Households of El Paso (Doubling Up)
- Priced Out, Not Doubled Up (Household Composition, part two)

**Supply**
- Field Ledger (Housing Unit Change)
- New Growth vs. Old Core (Housing Growth)
- Is El Paso's Housing Stock Filtering?

**Market**
- It Pays to Be Patient (MLS Sales)
- El Paso Rental Market Trends (Rent Data)
- Corporate & Investor-Owned Property

**Tools**
- The Case for Missing Middle Housing
- Urban Lot Splitter
- El Paso Housing Strategy Simulator
- Why the Rent Isn't the Problem (AMI Feasibility)

## Data sources

Census/ACS (including PUMS), HUD income limits and USPS vacancy data, HMDA, MLS, RentCast, Regrid, and Data Axle mover records. Each individual report documents its own methodology in full; this index only summarizes.

## Deployment

This is a static HTML file — drop it into any GitHub Pages repo (e.g. as `index.html` at the root, or alongside the other report folders) and it will render with no build step.
