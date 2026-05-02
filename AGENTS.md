# Repository Guidelines

## Project Structure & Module Organization
This repository currently ships as a single-page, static prototype in `index.html`.

- `index.html`: UI markup, CSS styles, in-browser app state, search logic, map rendering, and mock admin views.
- No build output, package manager config, or test directory is present yet.

When expanding the project, keep concerns separated:
- `src/` for app logic and UI modules.
- `assets/` for images/icons.
- `tests/` for automated tests.

## Build, Test, and Development Commands
No project-specific build tooling is configured. Use a local static server for development.

- `python3 -m http.server 8000`: Run locally and open `http://localhost:8000`.
- `open http://localhost:8000` (macOS): Launch the demo page in a browser.

If tooling is added later (lint/test/build), document the commands here and in the PR that introduces them.

## Coding Style & Naming Conventions
Follow existing style in `index.html`:

- Use 2-space indentation in HTML, CSS, and JavaScript.
- Prefer clear, descriptive identifiers in `camelCase` for JS (`routeSteps`, `startNodes`).
- Keep CSS custom properties under `:root` and reuse them before adding new color literals.
- Keep Thai user-facing labels consistent with existing UI text; keep internal keys in English.

For larger changes, avoid adding more inline script complexity; extract modules instead.

## Testing Guidelines
Automated tests are not set up yet. Minimum requirement before merge:

- Manually validate core flows: home, search, detail, navigate, map, and admin tabs.
- Verify responsive behavior on mobile-width and desktop-width viewports.
- Confirm query-param navigation works (example: `/?from=info-counter&to=opd`).

When tests are introduced, place them under `tests/` and use `*.test.js` naming.

## Commit & Pull Request Guidelines
No commit convention is established in history yet (repository has no commits). Start with:

- Commit messages in imperative mood, concise subject line (example: `Add QR param handling for navigation`).
- One logical change per commit.
- PRs should include: summary, user-visible impact, manual test steps, and screenshots/GIFs for UI changes.
- Link related issues/tasks when available.
