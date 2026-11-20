# AI & Digital Infrastructure in Africa — Resource Database

A static website (GitHub Pages) plus a daily GitHub Action that collects news, academic papers and reports into `resources.json`.

## Setup
1. Create a GitHub repo and upload everything in this folder (keep the `.github/workflows/` path).
2. **Settings → Pages**: deploy from branch `main`, folder `/ (root)`.
3. **Settings → Actions → General → Workflow permissions**: choose *Read and write*.
4. **Actions → "Update resource database" → Run workflow** (first fill; then it runs daily).

## What you can edit
| File | What to change |
|---|---|
| `fetch_resources.py` → `CONFIG` | outlets, news search queries, RSS feeds, academic queries, themes, countries, look-back periods |
| `manual_resources.json` | add hand-picked items: `{"title":"…","url":"https://…","type":"Report","source":"World Bank","date":"2026-05-01","desc":"…"}` (optional `theme`, `country` override auto-tagging) |
| `index.html` | institute links (search for `TODO`), colours (`:root`), layout |
| `.github/workflows/update.yml` | schedule (`cron`) |

Themes, countries and sources appear as filters automatically from the data, so no front-end edits are needed when you change them.

## Notes
- Data accumulates: new items are added daily, duplicates are skipped by URL, news older than ~18 months is pruned (papers and reports are kept).
- Tagging is keyword-based, so some items will be mis-tagged. Fix a specific one by adding it to `manual_resources.json` with explicit `theme`/`country`.
- Paywalled outlets (FT, Bloomberg, NYT) show headline and link only.
