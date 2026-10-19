# sidequests.tech

Source for [sidequests.tech](https://sidequests.tech): a hand-written landing page (`public/index.html`) plus a Markdown blog at `/blog`, built with [Astro](https://astro.build) and hosted on GitHub Pages.

Requires Node 24 (see `.nvmrc`).

## Develop

```sh
npm install
npm run dev
```

`npm run build` writes the site to `dist/`; `npm run preview` serves it.

## Write a post

Add a Markdown file to `src/content/blog/`. The filename becomes the URL (`my-post.md` is `/blog/my-post/`).

```md
---
title: "Post title"
description: "One sentence summary, used in the list, RSS and social cards."
pubDate: 2026-10-19
updated: 2026-10-25   # optional
tags: ["powershell"]  # optional
draft: true           # optional, default false; drafts are not built
---
```

## Deploy

Push to `main`. The workflow in `.github/workflows/deploy.yml` builds and publishes to GitHub Pages. In the repo settings, Pages > Source must be set to "GitHub Actions". The custom domain comes from `public/CNAME`.

## Author and licence

Robin Pieterse. MIT, see `LICENSE`.
