# Bounce Financial Apps — website

Internal launcher page that links out to Bounce's client-facing calculator apps. Used almost
entirely on desktop, by advisers, internally — so it prioritises density and speed over marketing
polish. No descriptions, no hero copy.

## What this project is

- A **single static `index.html`** — all HTML, CSS, and JS inline. No framework, no build step,
  no `package.json`. The global "React + Vite / jsPDF" defaults in `~/.claude/CLAUDE.md` do **not**
  apply here.
- Each linked app (Budget Calculator, Cashflow Calculator, etc.) is a **separate** repo/site
  hosted on its own Netlify or GitHub Pages URL. This repo is just the index.

## Deploy

- GitHub: `github.com/benbrett1/bounce-financial-apps-website`, branch `master`.
- Netlify site `bounce-financial-apps` → https://bounce-financial-apps.netlify.app
- Continuous deployment is linked: **every push to `master` auto-deploys to production.** No build
  command; Netlify just publishes the repo root (`netlify.toml` → `publish = "."`).
- Preview locally with the "Static Server (serve)" config in `.claude/launch.json`.

## Adding a new app

Add an `<a class="card">` inside `#grid`, keeping the list **alphabetical by app name**:

```html
<a class="card" href="https://APP-URL/" target="_blank" rel="noopener noreferrer">
  <div class="card-icon">
    <svg viewBox="0 0 24 24"><!-- 1.75px stroke line icon --></svg>
  </div>
  <div class="card-title">App Name</div>
</a>
```

- Icon colours cycle yellow → orange → magenta automatically via `:nth-child(3n+…)` — don't set
  per-card colours.
- **Coming-soon app:** use `<div class="card soon">` (not `<a>`), and nest the title with a
  `<div class="badge">Coming soon</div>` sibling. It renders muted and non-clickable.
- The header search box filters cards live by title substring (`/` focuses it, `Esc` clears).
  Nothing to wire up — it picks up new `.card` elements on load.

## Brand

Colours and typeface (Poppins on-screen) per `~/.claude/brand/bounce-financial/brand.md`.
Footer carries the standard AFSL line: "Australian Financial Services Licence No. 529109".
