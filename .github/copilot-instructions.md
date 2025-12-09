# Copilot Instructions — insilico.software

Purpose: give AI coding agents the minimal, concrete knowledge to be productive in this Astro-based static site.

- **Big picture**: This repo is an Astro (v5) static site starter. Pages live under `src/pages`, reusable UI lives under `src/components`, layout wrappers under `src/layouts`, and static assets under `src/assets`. There is no backend or API code in this repository by default — treat it as a frontend/static site project.

- **Key files**:
  - `package.json` — scripts: `npm run dev` (local dev server), `npm run build` (produces `./dist`), `npm run preview` (preview built site), `npm run astro` (run Astro CLI). Example: `npm run dev` starts the site on `localhost:4321`.
  - `astro.config.mjs` — project configuration for Astro. Changes here affect build behavior and require restarting the dev server.
  - `src/pages/index.astro`, `src/components/Welcome.astro`, `src/layouts/Layout.astro` — canonical examples of page, component and layout patterns.

- **Conventions & patterns (explicit)**:
  - Files use ESM (`"type": "module"` in `package.json`). Use `import` / `export` syntax.
  - Component pattern: `.astro` components are imported with relative paths. Assets (images, svgs) are imported and used via the `.src` property, e.g. `import astroLogo from '../assets/astro.svg'` then `<img src={astroLogo.src} />` (see `src/components/Welcome.astro`).
  - Scoped styles are expressed inside `.astro` files with `<style>` blocks; prefer those for small components. Global styles are not present by default.
  - Keep components small and layout-focused; `src/layouts/Layout.astro` wraps pages.

- **Developer workflows (commands & tips)**:
  - Install deps: `npm install`
  - Local development: `npm run dev` (visit `http://localhost:4321`). Restart after `astro.config.mjs` changes.
  - Build for production: `npm run build` — output folder is `./dist/`.
  - Preview a build: `npm run preview`
  - Use the Astro CLI: `npm run astro -- <command>` (for example `npm run astro -- add`)

- **Editing guidance (what AI agents should do)**:
  - When adding a page, create `src/pages/<name>.astro` with frontmatter and a `<Layout>` wrapper if appropriate (see `index.astro`).
  - When adding a component, put it under `src/components` and import it from pages/layouts with relative paths.
  - When adding assets, place them under `src/assets` and import them (do not reference `public/` unless you want a static public path).
  - Do not introduce server-only packages (Express, Fastify, etc.) without adding/adjusting `astro.config.mjs` and `package.json` scripts — this repo is static-first.
  - Keep changes minimal and self-contained; prefer small focused commits/PRs.

- **Patterns found in codebase (concrete examples)**:
  - Image import + `.src` usage: `src/components/Welcome.astro` — `import astroLogo from '../assets/astro.svg'` then `<img src={astroLogo.src} />`.
  - Layout usage: `src/pages/index.astro` wraps content with `<Layout>...</Layout>` imported from `src/layouts/Layout.astro`.

- **What to avoid / assumptions**:
  - There are no test frameworks or CI configs in the starter; do not assume tests exist.
  - There are no server routes or database connections; avoid proposing server-side integrations unless user requests them.

- **When you need more context**:
  - Inspect `package.json` and `astro.config.mjs` for build/runtime changes.
  - Check `src/pages`, `src/components`, and `src/layouts` for style and component patterns before large refactors.

If any of this is incorrect for your fork (you've added APIs, tests, or different build scripts), tell me and I'll update these instructions. Want me to add a small example page or component next?
