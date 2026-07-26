# Demolition Esports — Trident Tournament Tracker

A single-page, live-updating stats site for Demolition Esports' BGMI
"Trident" tournament. It pulls its data straight from your "IGNITE"
Google Sheet on every page load and every 60 seconds after that — no
backend, no build step, just a static site.

## Files
- `index.html` — the whole site (HTML + CSS + JS in one file)
- `images/` — logo + all 4 player photos (keep these filenames as-is,
  or update the `PLAYER_META` block in `index.html` if you rename them)

## 1. Before you host it: sheet sharing
For the page to read your sheet live from a browser, it needs to be
viewable without signing in:

**Google Sheet → Share → General access → "Anyone with the link" → Viewer**

You don't need to publish it to the web — link-viewable is enough.
Your yellow (manual-entry) cells stay exactly as editable as before;
this only affects *read* access for the published link.

## 2. Hosting on GitHub Pages
1. Create a new GitHub repo (public).
2. Upload `index.html` and the `images/` folder to the repo root.
3. Repo → Settings → Pages → Deploy from branch → `main` / `/ (root)`.
4. Your site goes live at `https://<your-username>.github.io/<repo-name>/`.

Every time you edit a yellow cell in the sheet, refresh the page (or
just wait — it auto-refreshes every 60 seconds) and the numbers,
tables and charts update automatically.

## 3. What's on each tab
Tabs mirror your Google Sheet exactly:
- **Introduction** — the 4 player cards (photo, role, bio)
- **Main Tournament Sheet** — match-by-match kills/position/points table + charts
- **Overall Performance** — aggregate stat comparison across all 4 players
- **Phoenix / MotuB / Monarch / Joker** — each player's photo, bio, career
  stats, and live per-match charts (damage, finishes/assists/MVPs, survival time)
- **Position Points** — placement + points earned per match

## 4. If it shows "Offline" / can't sync
This almost always means the sheet isn't shared as "Anyone with the
link → Viewer" yet (step 1 above). Fix the sharing setting, then hit
the Refresh button in the top right of the page.

## 5. Customizing
Everything lives in one file, `index.html`:
- Colors/fonts: the `:root { --bg: ...; --red: ...; }` block near the top
- Sheet IDs/tab gids: the `GIDS` object in the `<script>` section
- Refresh interval: `REFRESH_MS` (currently 60000 = 60s)
- Player photo mapping: `PLAYER_META`
