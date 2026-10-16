# Handoff: NutriLabel Home prototype

Status: **first version done.** A landing page with one tile per app: Workspace, Pantry, Recipe Builder.

## How it runs
Plain HTML/CSS, no build, no npm. Opens from `index.html` (works from disk or GitHub Pages).

Tiles use relative links to sibling folders, so they work when the apps sit next to each other:
- GitHub Pages: `mahindra-nwf.github.io/nutrilabel-home-prototype/` → `../nutrilabel-workspace-prototype/` etc.
- Local preview: `.claude/launch.json` serves the **parent folder** (`E:\`) on port 5181. Open
  `http://localhost:5181/nutrilabel-home-prototype/`. Workspace and Pantry resolve; the Recipe Builder only
  resolves if `nutrilabel-recipe-layout-v3` is also in that parent folder (today it lives on `D:\`).

## Files
| File | What it is |
|---|---|
| `index.html` | Top bar (brand, theme toggle) and the three tiles. Theme toggle script inline. |
| `base.css` | Design tokens + shared components, copied unchanged from the Workspace prototype (NLv4 `src/styles/base.css`). Don't edit; copy again when it changes. |
| `home.css` | Home page styles. Colors only via base.css tokens. Each tile sets `--tile` / `--tile-soft`. |

## Adding an app
Copy a `<a class="tile">` block in `index.html`, change the `href`, icon, text and the two tile color tokens.

## Notes for rebuilding in NLv4
- The theme choice is stored per browser under `nl_home_theme`; the other prototypes keep their own, so it doesn't carry over yet.
- In NLv4 this becomes the app's start route, with the tiles as links to the `workspace`, `pantry` and builder modules.
