# stevewang.me

Personal project hub for Steve Wang, built with Astro.

## Commands

```bash
npm install
npm run dev
npm run build
npm run preview
```

## Deploy

Production hosting uses AWS Amplify from the `main` branch.

Use short-lived `feat/*` branches for future work, merge them into `dev` for a
combined manual check, then merge `dev` into `main` as the manual production
deploy trigger.

Build command: `npm run build`

Output directory: `dist`

DNS is managed separately through Route 53. Configure your hosting provider to serve the generated `dist` output for the same primary domain used in `astro.config.mjs`.
