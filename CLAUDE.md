# stevewang.me

Repository-specific guidance for coding agents.

## What this is

`stevewang.me` — Steve Wang's personal project hub, a static Astro site (home, `/projects/`, `/tools/`, `/lab/`, `/experience/`, plus a 404 page) deployed to AWS Amplify. `stevewang.app` 301-redirects here at Cloudflare; the domain, DNS, and subdomain records for both live in the `## Domains` table of the folder-level `D:\Projects\steve-projects\CLAUDE.md`, which is where they are maintained. It is a project hub, not a blog or resume site: it should answer "What has Steve built?" quickly.

## Commands

```bash
npm run dev       # local dev server
npm run build     # static build to dist/ — the verification step before handoff
npm run preview   # preview the production build
```

There are no tests or linters. Verify content/site changes with `npm run build`; for documentation-only changes, skip builds and verify by reviewing the edited files.

## Architecture

Plain Astro with no integrations or runtime dependencies — keep it that way (no CMS, contact form, analytics backend, or client-side frameworks).

- `src/layouts/BaseLayout.astro` — the one layout: SEO/OG meta, canonical URL (from `site` in `astro.config.mjs`), favicon, wraps pages with `Header`/`Footer`. Pages pass `title`, `description`, and optional `current` ("projects" | "experience") for nav highlighting.
- `src/pages/` — `index.astro`, `projects.astro`, `tools.astro`, `lab.astro`, `experience.astro`, and `404.astro`. Content is hard-coded HTML by design (v1); project cards on `/projects/` use `id` anchors (e.g. `#purchasing-workflow-tools`) that the home page links to. Internal links use trailing slashes (`/projects/`).
- `src/styles/global.css` — the single stylesheet, imported by the layout. Design tokens are CSS variables in `:root` (teal accent `--accent`, amber `--amber`, 8px `--radius`).
- `public/sitemap.xml` is hand-maintained — update it when pages are added or removed.
- Screenshots served by the site live in `public/assets/`; `docs/assets/` holds private originals and the design reference (`concept-homepage.png`).

## docs/ is private and Git-ignored

`docs/PROJECT_PLAN.md` is the authoritative source for positioning, content direction, public copy guardrails, design direction, and deployment notes — read it before content changes, and update it in the same change when positioning, public-facing copy, guardrails, or deployment assumptions shift. But the whole `docs/` folder is intentionally Git-ignored (private planning notes): never commit it, and never copy employer-specific or private planning details from it into committed files or public copy.

`ROADMAP.md` (repo root, tracked, public) is the sanitized counterpart — a shareable summary of direction and principles with no employer, private app URLs, or private workflow detail. Keep it in sync at a high level when the public roadmap shifts, but never mirror private specifics into it. The repo is public, so treat anything committed as published.

## Content guardrails (from the plan)

- Say "purchasing operations" / "foodservice supply chain" — never name the employer, internal portal names, or private workflow details.
- Do not mention job hunting or open-to-work status; the site reads as a durable project hub.
- Keep copy professional, technical, outcome-focused, and concise. No social/blog tone, no oversized marketing sections, no purple gradients or decorative blobs — restrained operations-tool aesthetic.
- Featured framing: Digital Signage CMS = credible production full-stack work; Fuel Tracker / Shared Bill = live personal products; StackVitals = open-source ops dashboard; QuotaStation = private Windows product with no repository or release links; Ordering Dashboard = current purchasing automation focus. Don't promote reporting scripts or plans into headline projects.

## Workflow conventions

General commit, branch, release, security, and working rules live in the user-global `~/.claude/CLAUDE.md`. Project-specific notes:

- **Amplify deploys from `main` on push** (build `npm run build`, output `dist/`).
- **Releases** use `scripts/release.mjs` through the active release skill. The script is the
  authoritative implementation for version fields and repository-specific checks; the
  shared `prep` / `reversion` / `ship` workflow lives only in Steve's global guidance.
- **Changelog:** `CHANGELOG.md` is the release history and follows the changelog rules in Steve's global `CLAUDE.md`, which is where they are explained: user-facing results only, one entry to one line, Keep a Changelog categories in order. `release:prep` finalizes the `[Unreleased]` section into a versioned entry and maintains the compare links.
- A legacy `production` branch exists — it is **not** the deploy branch; do not use or reference it.
