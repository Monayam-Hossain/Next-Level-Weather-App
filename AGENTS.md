# AGENTS.md

Client-only React 19 + Vite 8 + Tailwind v4 weather app. Data comes from the free Open-Meteo APIs (no keys, no backend); deployed to Vercel as an SPA.

## Commands

- `npm run dev` — Vite dev server (HMR)
- `npm run build` — production build into `dist/` (gitignored; do not edit)
- `npm run preview` — serve the built app
- `npm run lint` — ESLint over everything, including `src/template`

There are no tests and no typecheck script; the project is plain JS/JSX despite `@types/*` dev deps. Do not invent test commands.

`npm run lint` currently fails at baseline: `src/template/components/WeatherCard.jsx:5` uses `getWeatherTheme` without importing it. That directory is stale scaffold/reference code, not the live app. Don't treat that error as caused by your change, and don't "fix" the live components to silence it.

## Layout and entrypoints

- `src/main.jsx` → `src/App.jsx` (router) → `src/layouts/MainLayout.jsx` → pages.
- Routes: `/` (`pages/Home.jsx`) and `/weather` (`pages/Weather.jsx`).
- `src/components/` is the live UI. `src/services/` has the two fetch calls. `src/utils/` holds weather→theme mapping and recommendation logic.
- `src/template/` is outdated duplicate code. Its only live use is `WeatherType.jsx` importing `../template/components/WeatherLottie`; all other imports resolve to `src/components/WeatherLottie.jsx`. Editing one does not change the other — check the import before touching either.

## Non-obvious behavior

- Uses `react-router` v8 (single package): routers from `"react-router"`, `RouterProvider` from `"react-router/dom"`. `react-router-dom` is not installed.
- `/weather` gets its entire input from router state: `useLocation().state.location` (`{name, lat, lon}` passed by `LocationModal`). There are no URL params and no fallback fetch. Direct navigation/refresh on `/weather` leaves `state` null and crashes — consider this when changing routing or `vercel.json` rewrites.
- `Weather.jsx` fetches on mount/place change and renders `null`-tolerant children (`weather?.…`); components must keep tolerating missing weather. `getRecommandations(null)` returns `null` and `RecommandationCard` renders nothing.
- WMO weather codes are mapped in `src/services/get-weather.js`. A new condition needs, in order: an entry there, a matching key in `src/utils/getTheme.js`, and a JSON file under `public/animations/weather/` (or `advice/` for recommendations). Lottie loads by URL string via `LottieLight src=...`, so animations must stay in `public/`, not be imported.
- `src/utils/getTheme.js` keys must match `icon` values (`clear`, `clear_night`, `partly_cloudy`, `cloudy`, `fog`, `rain`, `snow`, `storm`). Unknown keys fall back to the neutral theme.
- Naming is intentionally inconsistent and easy to trip over: file `RecommandationCard.jsx` exports `RecommendationCard`, the helper is `getRecommandations`, and the directory/file typo "Recommandation" is pervasive. Match existing names unless doing a deliberate rename.
- `src/index.css` contains only `@import "tailwindcss";`. Classes used in components such as `pill`, `panel`, `font-display`, `text-slate`, `bg-sky-soft`, `text-sky-deep`, `bg-rec-*`, `border-line`, `animate-rise`, `shadow-sm-soft`, `tracking-tightx` are not defined by Tailwind defaults or any local CSS. Don't assume they render; use explicit Tailwind utilities/inline styles (the color themes are inline style objects).
- Everything runs in the browser: no env files, server, or secrets. API failures surface only in the UI/console.

## Conventions

- Double quotes and semicolons in newer files; the scaffold files use single quotes/no semicolons. Follow the file you edit.
- `vercel.json` rewrites all paths to `index.html`; adding a real route still requires the client router entry in `src/App.jsx`.
- `README.md` is the untouched Vite template and does not describe this app.
