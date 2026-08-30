# SuperLega Predictor — Frontend

React + TypeScript + Tailwind CSS dashboard for the SuperLega Predictor project.

## Setup

Requires Node.js (18+) and the backend API running (see `/backend`).

```bash
npm install
cp .env.example .env   # adjust VITE_API_BASE_URL if your backend isn't on localhost:8000
npm run dev
```

Opens at `http://localhost:5173`. Make sure the FastAPI backend is running first
(`uvicorn main:app` from the `/backend` folder) or every page will show a
"couldn't reach the prediction server" error.

## Build

```bash
npm run build
npm run preview   # serve the production build locally to sanity-check it
```

## Pages

- **Home** (`/`) — overview, current model snapshot
- **Match Predictor** (`/predictor`) — pick two teams, get a live prediction with supporting stats
- **Predictions** (`/predictions`) — build and sort a comparison table of multiple matchups
- **Teams** (`/teams`, `/teams/:teamName`) — team directory and individual profiles
- **Model Performance** (`/model`) — accuracy, log loss, brier score, and calibration for every trained model

## A note on the Predictions page

There's no live 2026-27 fixture list loaded yet (that's a later phase of the project — see the
main brief, Phase 10). Rather than fake it with static data, this page lets you build your own
comparison table from real, live predictions. Once a real upcoming-schedule endpoint exists on
the backend, this page is a natural place to switch to showing it automatically.

## Design notes

Color palette, typography, and the "scoreboard" motif are documented inline as comments in
`tailwind.config.ts` and `src/components/Scoreboard.tsx` — the split-probability scoreboard is
the app's signature visual element, reused across the homepage, match predictor, and predictions
table.

## Verification status

Every `.tsx`/`.ts` file in this project was checked for syntax correctness. Full type-checking
against React's actual type definitions could not be run in the environment this was built in
(no package registry access), so **run `npm install && npm run build` yourself before deploying**
to catch anything a syntax-only check couldn't — package resolution, prop-type mismatches, etc.
