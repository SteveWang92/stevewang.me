# Content guide

Positioning, page structure, design direction, and the copy rules for every page of
stevewang.me. Read it before changing site content and update it in the same change when any
of these shift. Planned work and its progress live in GitHub issues; `CHANGELOG.md` and the
Git tags record what shipped.

## Positioning

A project hub, not a traditional personal website, blog, or resume. It answers one question
quickly:

> What has Steve built?

The strongest positioning is the intersection of full-stack software development,
automation, procurement operations, supply chain workflows, reporting, and practical internal
tooling. Core message: Steve builds practical software for product workflows, purchasing
workflows, procurement systems, and practical automation.

Audience:

- Hiring managers and technical leads evaluating practical software ability
- Business and operations stakeholders looking for useful internal tooling
- Future collaborators who want to understand the kind of problems Steve solves
- Steve, as a durable home for projects and experiments worth showing

The site feels professional, technical, useful, outcome-focused, and low-maintenance. It does
not feel social, blog-first, resume-only, overdesigned, or like a generic developer portfolio.

## Pages

`/`, `/projects/`, `/experience/`, `/tools/`, `/lab/`, and a 404 page. A page such as
`/contact/` is added only when there is real content for it. No blog unless there is a
repeatable writing habit and a clear technical purpose. `public/sitemap.xml` lists every page.

### Home

Makes the positioning obvious within the first viewport:

- Name, with the role lines Full-Stack Developer, Data & Process Automation, and Procurement
  Systems
- A short value statement about practical tools for full-stack products, operations,
  reporting, purchasing workflows, and decision making
- A primary link to Projects and a secondary link to Experience
- Featured project previews and a compact proof/outcomes strip
- The Recently shipped strip, described under [Standing rules](#standing-rules)

### Projects

The core evidence page. Each card covers problem or purpose, solution, features, tech stack,
status, and links when available. Cards: Digital Signage CMS, StackVitals, QuotaStation, Fuel
Tracker, Shared Bill, and Ordering Dashboard. Each card has an `id` anchor the home page links
to. Sales analytics work is represented on `/lab/`, not as a project card.

### Experience

Replaces a traditional resume with outcome-oriented experience: a positioning summary,
outcome examples, skill groups, work style, and links to project evidence. Concise and
direct, with no long resume duplication.

### Tools

Small client-side calculators for purchasing work. Each one ships with default demo values
prefilled and computes on page load. A calculator is added only when a day-to-day need is
genuinely useful, never as a stub; a plain sales margin calculator is too generic, and its math
lives inside the cost change impact tool.

### Lab

The lighter counterpart to Projects: smaller experiments and automation worth preserving,
explicitly not headline projects. It is the home for reporting scripts and small tools that
are not promoted into flagship projects.

- A short purpose line at the top signals the lower altitude and states that the scripts run
  privately on internal data ("described here, not hosted").
- Each entry is a `.detail-card` with a `project-meta` category eyebrow, a title, a
  `status-label` (for example "Private · in weekly use"), one paragraph on what it does and one
  on why it exists. No screenshots, tech-stack grids, or code links; that lighter weight keeps
  a lab entry distinct from a project card.
- An entry may carry one collapsed `<details class="lab-demo">` "Demo with sample data"
  section. Demo data is fabricated from scratch (fictional venue names, invented item and
  invoice codes), never sanitized from real exports, because real code formats are
  identifying. Demos stay on a minority of entries so the page stays lighter than Tools. Their
  styles live in `global.css` under `.lab-demo` and `.demo-table*`.
- The Weekly Sales Reporting App entry tells the origin story of the reporting that is now part
  of the Ordering Dashboard and points at that project card for the live capability, so the
  feature list has one home.

## Project framing

Keep the public focus on Digital Signage CMS as credible production full-stack experience,
Fuel Tracker and Shared Bill as live personal products, StackVitals and QuotaStation as
released open-source products, and Ordering Dashboard as the current purchasing automation
focus. Reporting scripts stay supporting background on `/lab/`; a sales analytics plan is not
featured as a standalone project until it is a more complete tool.

### Digital Signage CMS

Production full-stack experience, not a portfolio toy: content management for digital
signage, screen and device workflows, permission control, Stripe payment setup and the related
CMS flows, CRM integration, email notifications and screen monitoring, CI/CD pipelines,
database design and maintenance, Electron and Android/Tizen TV app maintenance, and
coordination with outsourced developers while acting as the only in-house developer.

### StackVitals

An open-source, self-hosted operations dashboard for solo developers with a handful of side
projects. The card links stackvitals.dev, the stackvitals.app demo, and the GitHub repository.

- Uptime, deploy health, cloud cost, AI/CI usage, and domain status
- Opt-in adapters for HTTP health, deploy status (Amplify, GitHub Actions workflows,
  Cloudflare Pages), AWS Cost Explorer, Supabase, Resend, OpenAI, GitHub Actions CI, and
  Cloudflare domains
- Needs Attention panel with project, provider, and error detail; 30-day response-time and
  uptime history; spend and usage trends
- Resend reports sending-domain verification only — delivery counts are not collectable, so it
  is never described as email delivery stats
- Aggregate-only collection, Supabase Auth with row-level security, scheduled GitHub Actions
  collectors, single-owner by design, AGPL-3.0

### QuotaStation

A released, local-first Windows product rather than a generic usage dashboard. The card
carries a GitHub link, a link to the latest release, and the two `--demo` screenshots from the
README.

- Live subscription quota windows, reset times, historical token usage, model activity, and
  API-equivalent cost for Codex and Claude Code over one normalized snapshot
- Tray quick panel, optional taskbar widget, dashboard, and a Claude Code status line laid out
  in Settings
- Usage by day or by session, multi-machine usage and reset history through a shared folder, a
  chosen time zone, and an optional internet-time clock check
- Read-only local data access, local SQLite history, redacted diagnostics, and no prompt or
  source-code upload
- Tauri 2, Rust, React, TypeScript, SQLite; AGPL-3.0 with a per-user Windows installer on every
  release

### Fuel Tracker

A live personal product and AI/API practice project, built because store apps felt too heavy
or missed wanted features.

- AI reads receipt photos for litres, pump price, total, fuel grade, brand, station, and
  purchase time, and reads the odometer from a dashboard photo
- History checks, filtering and search, bulk delete, and a CSV export/import round trip
- Keyboard and screen-reader accessibility
- Cloud web build on AWS Amplify and a portable Windows build, in daily personal use

### Shared Bill

A live personal web app for shared expenses: sign-in, groups with member roles and invites,
weighted splits, settlement calculation, and completed transfers, on a serverless AWS backend.

### Ordering Dashboard

The current automation focus, built from daily purchasing work.

- A desktop app (React + TypeScript over a FastAPI core in a pywebview window) importing
  Excel/ODS workbooks into local SQLite, several files in one run
- Order quantities from target cover in weeks, reserve quantities, supplier MOQ, layer/pallet
  pricing, and packaging constraints, with category order-day cycles and a grouped summary
- Must-order versus can-wait marking, a per-item cover cap, and committed quantities that net
  down recommendations
- A weekly inter-branch replenishment order rounded to layers or pallets over safety stock,
  reviewed afterwards against what shipped
- A daily list of blocking issues, due claims, and urgent lines, opened on the day's first
  launch
- Supplier order emails adjusted line by line and confirmed before they open; CSV/XLSX/PDF
  output and low-stock workbooks by buying group
- Claims tracking with several rebates per supplier and reminders for every unclaimed period
- Weekly sales reporting as a tab over the same database, so one sales import feeds purchasing
  and the weekly report

## Content guardrails

- Say "purchasing operations" or "foodservice supply chain"; never name the employer, its
  branches, suppliers or brands handled, internal portal names, internal codes, or private
  workflow detail. Keep future purchasing tools framed as practical workflow tooling, not a
  finished enterprise platform.
- Fuel Tracker and Shared Bill are deployed and in personal use but not publicly released.
  Their cards carry a "Private release" status and link to no app URL. Rows and cards link to
  `/projects/` anchors, never to private app URLs.
- Position sales reporting as automation and operational visibility, not a data analyst claim.
- Do not mention job hunting, open-to-work status, or a near-term role change. Long-term
  positioning supports software developer, automation engineer, supply chain systems
  developer, procurement systems designer, technical lead, and architecture paths without
  saying Steve is looking.
- Copy is short, professional, technical, and outcome-focused, with no social or blog tone; a
  skill or planned script is not turned into a major project.

## Design direction

A restrained operations-tool aesthetic: crisp white or very light neutral background, charcoal
text, teal primary accent, amber secondary accent for procurement and supply chain cues, thin
borders and dividers, stable rectangular cards with a radius no larger than 8px, and subtle
grid, dashboard, table, and workflow motifs. No purple gradients, decorative blobs or orbs,
dark blurred hero imagery, stock people photos, oversized marketing hero sections, or nested
cards. Design tokens live in `:root` in `src/styles/global.css`.

## Scope

A static Astro site with hard-coded HTML content, no runtime dependencies, and static build
output. Out of scope: blog, CMS, contact form, photo gallery, authentication, analytics
backend, dynamic project database, and a tool hosting platform.

## Skill taxonomy

Skills on `/experience/` are curated by confidence and purpose: the strongest capabilities
first, and technologies used before grouped as working exposure.

- **Core engineering:** Python, JavaScript, TypeScript, React, Redux / state management, React
  Router, Node.js, REST API design, authentication / authorization, role-based access control,
  form validation, file upload handling, image upload / asset management.
- **Backend & data:** MySQL, SQLite, Supabase (Auth, Postgres, row-level security), database
  schema design, database migration, CSV / Excel automation, report generation, data
  import/export, Pandas, NumPy, Swagger / OpenAPI, cron jobs.
- **Production systems:** AWS Amplify, serverless AWS (Cognito, AppSync, DynamoDB, Lambda),
  AWS EC2, S3, Route 53 / DNS, AWS-hosted web apps, Linux server administration, Ubuntu /
  CentOS, Bash / shell scripting, Docker, Docker Compose, Nginx, Git, GitHub, Bitbucket, GitHub
  Actions, CircleCI, Bitbucket Pipelines.
- **Product integrations:** Stripe payment integration, subscription / license workflow, API
  integration, email notification systems, background jobs / scheduled tasks, monitoring /
  alerting, release management, environment configuration.
- **Interface & devices:** admin dashboard UI, CMS development, digital signage systems,
  device/screen management, Electron desktop apps, mobile-responsive UI, charting / data
  visualization, React Testing Library, ESLint / Prettier, SASS / SCSS.
- **Working exposure:** CloudFront, webhooks, query optimization, log analysis, Nginx reverse
  proxy, SSL / HTTPS setup, Android TV and Samsung Tizen app support, AI API integration /
  OpenAI API, Power BI, WordPress, Redis, WebSocket / realtime updates, MQTT / device
  messaging, Cypress, Vitest, Tailwind CSS, Material UI, Postman, OAuth, JWT, Puppeteer,
  Selenium, MySQL and PostgreSQL backup/restore, Oracle SQL, phpMyAdmin.
- **Operations domain:** purchasing workflow, purchase order processing, supplier
  communication, supplier credit claim tracking, rebate calculation, stock review, low-stock
  ordering, cost change tracking, price update workflow, transport booking, sales and category
  reporting, customer purchase trend analysis, lost customer analysis, promotion impact review,
  margin / markup calculation, inventory trend review, supplier/item/category reporting, data
  reconciliation, internal system data maintenance.

## Standing rules

- **Recently shipped** on the home page is a fixed set of five rows — QuotaStation,
  StackVitals, Fuel Tracker, Shared Bill, and Ordering Dashboard — ordered by the date of each
  project's newest release, newest first. No other project joins or replaces them. Each row
  carries that project's latest version number, but its one-line note describes the most
  recent *substantive* release: a patch that only fixes a deploy, a crash, documentation, or
  dependencies keeps the version fresh and leaves the note on the feature release below it.
- Every `/tools/` calculator ships with prefilled demo values and computes on page load.

## Success criteria

- The home page explains the project hub positioning in under 10 seconds.
- Projects are visible without needing a blog or about page.
- Digital Signage CMS reads as credible production full-stack work.
- Fuel Tracker and Shared Bill read as live software without linking to them.
- Sales analytics and procurement work read as real business tooling, even when unfinished.
- The Experience page shows outcomes rather than a static resume dump.
- The site works on desktop and mobile, and `npm run build` passes.
