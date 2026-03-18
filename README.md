# CompoundLab Content

This repository is the external content source for CompoundLab editorial pages.

## Publishing Contract

- Publishing branch: `main`
- Insight posts live in `insights/<slug>.md`
- Use plain Markdown with frontmatter
- The filename is the canonical slug used by the app at `/insights/<slug>`

## Insight Frontmatter

Each published insight must start with this frontmatter shape:

```md
---
title: Choosing a reasonable long-term return assumption
description: A practical framework for setting return expectations that are useful for planning.
publishedAt: 2026-03-18
updatedAt: 2026-03-18
---
```

## Notes

- `publishedAt` is required and should use `YYYY-MM-DD`
- `updatedAt` is optional and should use `YYYY-MM-DD` when present
- Keep posts text-first for now; the app renders standard Markdown and GFM tables
- Any `.md` file in `insights/` is treated as publish-ready by the app

## Automatic Revalidation

This repo can trigger the app to refresh its cached Insights pages after each publish.

Add these repository secrets in `compoundlab-content`:

- `REVALIDATE_URL`: the full app endpoint, for example `https://compoundlab.com/api/revalidate`
- `REVALIDATE_SECRET`: the same secret configured as `REVALIDATE_SECRET` in the app

Once those secrets are set, pushes to `main` that change files in `insights/` will trigger the GitHub Actions workflow at `.github/workflows/revalidate-insights.yml`.
