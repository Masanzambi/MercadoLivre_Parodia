# Base44 sandbox notes

## What this project is
A static front-end only site (parody Mercado Livre page). Files that matter:
`index.html`, `styles.css`, `scripts.js`, and the local assets in `imagens/`.
There is **no** backend, package manager, build step or database.

## Running it here
`docker compose -f docker-compose.base44.yml up -d --build`

One service (`web`) runs `live-server` on host port 3000 with the repo root
bind-mounted, so HTML/CSS/JS edits are served live from the checkout — just
refresh (live-server also pushes a reload to the browser). Product images come
from Unsplash and the icon font from a CDN, both loaded by the browser; no
credentials or API keys are needed anywhere.

## Notes
- The `imagens/` filenames contain spaces, non-ASCII characters and a `²`
  (e.g. `agoniado logo².png`). Keep them URL-encoded/verbatim in HTML/CSS.
- `scripts.js` renders the product grid on `DOMContentLoaded`; the search box
  filters the in-memory `products` array by title substring.
- Verification: `curl -s localhost:3000/ | grep -i "Ofertas Imperdíveis"` should
  return the hero heading served from `index.html`.
