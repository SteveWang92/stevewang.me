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

There are no tests or linters. Verify content/site changes with `npm run build`; for documentation-only changes, skip builds and verify by reviewing the edited files. `.github/workflows/ci.yml` runs the same build on the `dev` -> `main` pull request and on the push that lands on `main`, which is the only check between a broken build and the live site.

## Architecture

Plain Astro with no integrations or runtime dependencies — keep it that way (no CMS, contact form, analytics backend, or client-side frameworks).

- `src/layouts/BaseLayout.astro` — the one layout: SEO/OG meta, canonical URL (from `site` in `astro.config.mjs`), favicon, wraps pages with `Header`/`Footer`. Pages pass `title`, `description`, and optional `current` ("projects" | "experience") for nav highlighting.
- `src/pages/` — `index.astro`, `projects.astro`, `tools.astro`, `lab.astro`, `experience.astro`, and `404.astro`. Content is hard-coded HTML by design; project cards on `/projects/` use `id` anchors (e.g. `#purchasing-workflow-tools`) that the home page links to. Internal links use trailing slashes (`/projects/`).
- `src/styles/global.css` — the single stylesheet, imported by the layout. Design tokens are CSS variables in `:root` (teal accent `--accent`, amber `--amber`, 8px `--radius`).
- `public/sitemap.xml` is hand-maintained — update it when pages are added or removed.
- Screenshots served by the site live in `public/assets/`.

## Documentation

`docs/CONTENT_GUIDE.md` (tracked, public) owns positioning, page structure, project framing, content guardrails, design direction, and the standing rules such as Recently shipped — read it before content changes and update it in the same change when any of those shift. Planned work and its progress live in GitHub issues.

Local-only files carry `.local` in the file or folder name and are ignored by `*.local.*` / `*.local/`. `docs/PRIVATE_CONTEXT.local.md` holds the employer context, the private sources behind `/lab/` entries, and the internal names public copy must avoid; `docs/assets.local/` holds private screenshot originals and the design reference. Never copy anything from them into committed files or public copy. The repo is public, so treat anything committed as published.

## Workflow conventions

General commit, branch, release, security, and working rules live in the user-global `~/.claude/CLAUDE.md`. Project-specific notes:

- **Amplify deploys from `main` on push.** `amplify.yml` at the repository root owns that build — it pins Node 24.18.1, runs `npm run build`, and publishes `dist/` — and takes precedence over whatever build spec the Amplify console still holds.
- **Releases** run through the globally installed `changedeck` CLI via the active release
  skill; `changedeck.json` lists the version fields, and the shared `prep` / `reversion` /
  `ship` workflow lives only in Steve's global guidance.
- **Release prompt:** the live site changes only when `main` does, so after any user-visible
  content change lands on `dev`, remind Steve that `## [Unreleased]` in `CHANGELOG.md` is
  waiting for a release; release only when he asks.
- **Changelog:** `CHANGELOG.md` is the release history; its wording rules live in Steve's global `CLAUDE.md`. `release:prep` finalizes the `[Unreleased]` section into a versioned entry and maintains the compare links.
- A legacy `production` branch exists — it is **not** the deploy branch; do not use or reference it.
