# Siriraj SiWay Map

Static web prototype for hospital wayfinding at Siriraj.

## Project Structure
- `index.html` - main single-page app UI and client logic
- `siriraj_map.png` - map image used as background
- `data/siriraj_data_location.json` - runtime data source (loaded by `fetch`)
- `siriraj_data_location.xlsx` - editable source data
- `scripts/sync_locations_from_xlsx.py` - converts Excel -> JSON
- `.github/workflows/deploy-pages.yml` - GitHub Pages deployment workflow

## Run Locally
Use a local HTTP server (required for `fetch`):

```bash
python3 -m http.server 8000
```

Then open:
- `http://localhost:8000`

## Update Location Data
1. Edit `siriraj_data_location.xlsx`
2. Sync to JSON:

```bash
python3 scripts/sync_locations_from_xlsx.py
```

This regenerates `data/siriraj_data_location.json` used by the app.

## Deploy to GitHub Pages
This repo is configured for GitHub Actions deployment.

1. Push to branch `main`
2. In GitHub: `Settings > Pages`
3. Set source to `GitHub Actions`
4. Check the `Actions` tab for workflow status

## Notes
- Some locations may not have coordinates; those can still be searched and viewed, but navigation is disabled.
- Map pins are rendered only for records with valid `map_x` and `map_y`.
