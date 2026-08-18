# Roadmap

Public roadmap for **stevewang.me**, a personal project hub. Detailed planning
notes are kept privately and out of version control; this file is the shareable
summary of direction and the principles that govern changes.

## What this is

A project hub — not a blog or a resume — that answers "What has Steve built?"
quickly. Static [Astro](https://astro.build) site with no runtime dependencies,
deployed to AWS Amplify.

## Principles

- **Restrained operations-tool aesthetic**: light background, charcoal text,
  teal primary accent, amber secondary accent, thin borders, cards no rounder
  than 8px. No purple gradients, decorative blobs, or oversized marketing
  sections.
- **Copy is professional, technical, outcome-focused, and concise** — no
  social or blog tone.
- **Stays static and low-maintenance**: no CMS, contact form, analytics
  backend, or client-side frameworks.
- **Every `/tools/` calculator ships with prefilled demo values** and computes
  on page load, so a visitor sees a worked result without typing anything.

## Current state

- **Pages**: Home, Projects, Experience, Tools, Lab, 404.
- **Projects**: Digital Signage CMS, QuotaStation, StackVitals, Fuel Tracker,
  Shared Bill, Ordering Dashboard.
- **Tools** (client-side, no backend): pallet breakdown, price-break
  evaluator, MOQ & pack rounding, order coverage, freight space, rebate
  calculator, cost-change impact.
- **Lab** (`/lab/`): a lighter counterpart to Projects for smaller automation
  worth preserving — description-only entries (title, what it does, why it
  exists; no screenshots or tech-stack grids). Current entries: weekly sales
  reporting app, lapsed-customer reports, post-promotion impact report,
  messy-spreadsheet shipment extractor. These run privately on internal data
  and are described, not hosted. Two entries include a collapsed "demo with
  sample data" section — an interactive lapsed-customer demo and a before/after
  extraction example — running entirely in the browser on fabricated data.
  New entries follow the same shape and keep the lighter visual weight that
  distinguishes them from flagship projects.

## Planned

### Further out

- Project content collections and reusable project templates.
- Additional `/tools/` calculators as day-to-day needs surface.
