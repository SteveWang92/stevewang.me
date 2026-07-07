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

- **Pages**: Home, Projects, Career, Tools, 404.
- **Projects**: Digital Signage CMS, Fuel Tracker, Shared Bill, Project Status
  Hub, Purchasing Workflow Tools.
- **Tools** (client-side, no backend): pallet breakdown, price-break
  evaluator, MOQ & pack rounding, order coverage, freight space, rebate
  calculator, cost-change impact.

## Planned

### Lab page (`/lab/`)

A lighter counterpart to Projects, for smaller experiments and automation worth
preserving — explicitly *not* headline projects.

- A short purpose line at the top signalling low altitude ("smaller
  experiments, not flagship work").
- Per entry: title, a one-line "what it does", and a one-line "why it exists".
  No screenshots or full tech-stack grids — the lighter visual weight is what
  distinguishes a lab entry from a flagship project.
- Reuses the existing card styles, so no new CSS.
- Wiring: `src/pages/lab.astro` (BaseLayout, `current="lab"`), a nav link plus
  the `"lab"` value threaded through `Header` and `BaseLayout`, and a
  `public/sitemap.xml` entry.
- Timing: ship only once there are 2–3 real entries — a one-item page reads as
  a stub.

### Further out

- Project content collections and reusable project templates.
- Additional `/tools/` calculators as day-to-day needs surface.
