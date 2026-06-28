# Project Working Notes

- Work and write commits like a human maintainer. Keep changes focused, avoid generated-looking prose, and split unrelated work into separate Conventional Commits.
- Keep responses and repository context concise. Read only the files needed for the task.
- Do not use optional skills or plugins unless the user asks for them.
- Treat `docs/PROJECT_PLAN.md` as the source of truth for positioning, content direction, public copy guardrails, and deployment notes.
- If a change affects positioning, public-facing project copy, content guardrails, or deployment assumptions, update `docs/PROJECT_PLAN.md` in the same change.
- This is an Astro static site. Use `npm run dev` for local work and `npm run build` for verification before handing off content or deployment changes.
- For documentation-only changes, do not run tests or builds; verify by reviewing the edited files instead.
- Use short-lived `feat/*` branches for future work, merge them into `dev` for a combined manual check, and leave the final `dev` to `main` merge as the manual Amplify production deploy trigger.
- Amplify production deploys from `main`. Do not refer to `production` as the deploy branch for this project.
- Never commit provider credentials, AWS secrets, API keys, or `.env` files.
