# Gurukul Guru Maharaj Visit 2026

A touchscreen event app for the Guru Maharaj Visit (Shree Swaminarayan Gurukul
International School, Gurugram) — Guru gallery, "Know Your Guru" class
competition, the Gurukul Vault, the Divine Diya journey, a live leaderboard,
and an Admin studio. Everything is client-side and stores state in the
browser's `localStorage` — no backend or database required.

## Run locally

```bash
npm install
npm run dev
```

Opens at http://localhost:5173

## Build for production

```bash
npm install
npm run build
```

Static output goes to `dist/`. This is a plain SPA — serve `dist/` with any
static host and rewrite all routes to `/index.html` (already configured for
Vercel and Netlify below).

## Deploy

**Vercel**
- Import this folder as a project (framework preset: Vite).
- Build command: `npm run build`, output directory: `dist`.
- `vercel.json` already includes the SPA rewrite rule.

**Netlify**
- `netlify.toml` is already set up (`npm run build`, publish `dist`, SPA redirect).
- Drag-and-drop the `dist/` folder into Netlify, or connect the repo.

**Any static host (GitHub Pages, S3/CloudFront, Nginx, etc.)**
- Run `npm run build`, upload the contents of `dist/` to your host.
- Make sure unknown paths (`/game`, `/vault`, `/diya`, `/admin`, ...) are
  rewritten to `/index.html` since this is a client-side router (wouter).

## Notes

- All content (Guru gallery entries, quiz questions, Divine Diya question
  bank, scores) is edited from `/admin` and persisted in the browser's
  `localStorage` on the device running the show. There's no shared/remote
  database, so admin edits on one device won't appear on another.
- Before the event, open `/admin` on the actual display device and add the
  Guru entries and questions there.
