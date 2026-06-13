# changelog

Self-hosted changelog powered by [Openchangelog](https://openchangelog.com), deployed on Coolify (Blackstone / Hetzner) at **https://changelog.gaviso.one**.

## How it works

- `docker-compose.yml` — runs `ghcr.io/jonashiltl/openchangelog`, mounting the two files below (read-only).
- `openchangelog.yml` — site config (title, color scheme, etc.). Served at container `/etc/openchangelog.yml`.
- `release-notes/` — one Markdown file per release. Mounted at container `/release-notes`.

No database. State is this repo.

## Adding a release note

Create a new file in `release-notes/` with frontmatter:

```markdown
---
title: Release 1.2.0
description: Short summary shown in listings.
publishedAt: 2026-06-13
tags:
  - Feature
---

Markdown body…
```

`publishedAt` is ISO 8601. Commit + push to `main`; Coolify redeploys and the entry appears.

## Deploy

Coolify watches `main`. Push to redeploy, or trigger a manual deploy from the Coolify dashboard.
