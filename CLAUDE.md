# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This is the **GitHub Pages hosting repo** for `sf666.github.io` (remote: `git@github.com:sf666/sf666.github.io.git`). It contains only **pre-built static output** — there is no application source code, no `package.json`, and no build/test/lint tooling in-tree.

The single deployed site is **NextCP/2 documentation**, under `nextcp2/`. It is a static build produced by **Astro v5.9.4 + Starlight v0.34.4** and served at `https://sf666.github.io/nextcp2/`. The Astro source project (the `.md`/`.mdx` content, `astro.config`, etc.) lives in a **separate repository** that is not present here.

`.nojekyll` (empty file at repo root) disables Jekyll processing so GitHub Pages serves the `_astro/` and `pagefind/` directories verbatim.

## Working in this repo

- **Do not hand-edit the generated HTML/CSS/JS** in `nextcp2/` to make content changes. The correct workflow is to edit the source in the upstream Astro/Starlight project, rebuild, and copy the build output here. This repo just receives the result (commit history is a series of "docs update" commits).
- All asset URLs are absolute and hard-coded to the **`/nextcp2/` base path** (e.g. `href="/nextcp2/_astro/..."`). Any rebuild must use the same Astro `base: '/nextcp2'` setting or every link breaks.
- Deployment is automatic: pushing to the default branch publishes via GitHub Pages. There is no CI/build step to run locally.

## Layout of `nextcp2/`

- `index.html`, `404.html` — site entry and fallback pages.
- `_astro/` — hashed, bundled CSS/JS assets (Astro output). Treat as opaque build artifacts.
- `pagefind/` — Pagefind client-side search index and runtime; regenerated at build time.
- Content sections, each a directory of `<topic>/index.html` pages: `overview/`, `quick_install/` (incl. `docker`), `integration/` (`openhab`, `rest_api`), `user_interface/` (`radio`, `music_library`, `player_queue`, `now_listening`, `my_albums`, `app_settings`).
