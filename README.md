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
- User page: `http://localhost:8000/index.html`
- Admin page: `http://localhost:8000/admin.html`

## Update Location Data
1. Edit `siriraj_data_location.xlsx`
2. Sync to JSON:

```bash
python3 scripts/sync_locations_from_xlsx.py
```

This regenerates `data/siriraj_data_location.json` used by the app.

## Data Model for Growth
The JSON now supports building-level and unit-level records.

Key fields for future clinic/ward data:
- `entity_type`: `building` or `unit`
- `unit_type`: examples `clinic`, `ward`, `service`, `building`
- `building_id`: parent building id for a clinic/ward/service
- `building_name_th`: display building name
- `floor_label`: floor shown to users, such as `ชั้น 2`
- `room`: optional room or counter name
- `lat` / `lon`: Google Maps destination for the building entrance
- `google_maps_url`: generated from `lat` / `lon`

Google Maps should be used to reach the building. The app displays floor and room information after the user selects a destination.

## Deploy to GitHub Pages
This repo is configured for GitHub Actions deployment.

1. Push to branch `main`
2. In GitHub: `Settings > Pages`
3. Set source to `GitHub Actions`
4. Check the `Actions` tab for workflow status

After deployment:
- User page: `https://<username>.github.io/siriraj_siway_map/`
- Admin page: `https://<username>.github.io/siriraj_siway_map/admin.html`

## Notes
- Some locations may not have coordinates; those can still be searched and viewed, but navigation is disabled.
- Map pins are rendered only for records with valid `map_x` and `map_y`.
