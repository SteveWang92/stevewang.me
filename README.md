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

AWS Amplify builds and deploys the `main` branch on every push, using `amplify.yml`
(`npm run build`, output `dist/`). Day-to-day work lands on `dev`, and releases merge `dev`
into `main` through a reviewed release pull request.

## Documentation

- [`docs/CONTENT_GUIDE.md`](docs/CONTENT_GUIDE.md) — positioning, page structure, content
  rules, and design direction
- [`CHANGELOG.md`](CHANGELOG.md) — release history
- Planned work lives in GitHub issues.
