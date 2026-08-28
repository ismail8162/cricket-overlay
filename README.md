# CricCast Live

A production-style, dependency-free cricket scoring control panel and OBS browser-source overlay.

## Run

Serve this folder from any static server (or open `index.html` for local scoring). For the overlay, add one of these as an OBS Browser Source:

- `overlay.html?layout=bar`
- `overlay.html?layout=compact`
- `overlay.html?layout=card`
- `overlay.html?layout=squads` (full Playing XI graphic)

Both pages must be served from the same origin. State is saved in the browser and synchronized live with `BroadcastChannel`.

## Deploying for multi-device scoring

Deploy the files to a static host and replace the `LocalMatchStore` adapter in `js/store.js` with a Firebase/Supabase realtime adapter. The state contract is documented in `docs/state-schema.md`; UI code consumes only `store.get()` and `store.save()`.

## Project map

```
index.html                 Admin scoring panel
overlay.html               OBS overlay renderer
css/app.css                Admin and overlay styles
js/store.js                Persistent realtime state adapter
js/scoring.js              Cricket scoring domain logic
js/admin.js                Admin panel rendering and controls
js/overlay.js              Overlay rendering and URL layouts
docs/state-schema.md       State/database contract
```

## Squad workflow

Add players individually under **Team Squads**, then mark one captain and wicket-keeper per side. The striker, non-striker and bowler controls use these squad lists automatically. A wicket opens a next-batter chooser, and the sixth legal ball opens a next-bowler chooser.
