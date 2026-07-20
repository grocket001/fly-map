# The Living Fly Map

An interactive, seasonal fly fishing map. Hover a pin for the quick read (species, season, top fly). Click a pin for the full playbook: all 5 flies, material recipes, colorways, and source links.

Built with plain HTML/JS + [Leaflet](https://leafletjs.com) — no build tools, no API keys, no hosting costs. The entire site is **one file** (`index.html`): open it anywhere and it works.

## Try it locally

Double-click `index.html`. It opens in any browser (map tiles need internet).

## Deploy to GitHub Pages (free, ~10 minutes)

1. **Create a GitHub account** at [github.com](https://github.com) if you don't have one.
2. **Create a new repository**: click the **+** (top right) → *New repository*. Name it something like `fly-map`. Keep it **Public**. Click *Create repository*.
3. **Upload the files**: on the new repo page, click *uploading an existing file*, drag in `index.html` and `README.md`, click *Commit changes*.
4. **Turn on Pages**: repo → *Settings* → *Pages* (left sidebar). Under **Branch**, choose `main` and `/ (root)`, then *Save*.
5. Wait 1–2 minutes. Your site is live at:
   `https://YOUR-USERNAME.github.io/fly-map/`

### Adding your custom domain later

1. Buy the domain anywhere (Namecheap, Cloudflare, Porkbun...).
2. Repo → *Settings* → *Pages* → *Custom domain* → enter it and save.
3. At your domain registrar, add a **CNAME** record pointing `www` to `YOUR-USERNAME.github.io`.
4. Check *Enforce HTTPS* once it verifies. Done — no code changes needed.

## Adding a new location

All fishing data lives in one clearly marked block near the bottom of `index.html` — look for:

```
/* ============================================================
   FLY FISHING MAP — DATA FILE
```

Copy an existing location object (from `{` to `},`), paste it into the `locations` array, and edit:

- `coords`: `[latitude, longitude]` — grab from Google Maps (right-click → copy coordinates)
- `months`: 12 values Jan→Dec, each `"peak"`, `"good"`, `"fair"`, or `"off"`
- `flies`: 5 fly objects with recipe lines, a link, a top colorway, and 2 alternates

No other changes needed — the map, hover cards, season filter, and detail panel all render from that block. International spots work too; the map isn't limited to the US.

## Roadmap ideas

- Photos per fly pattern (add an `img` field and an `<img>` tag in the fly card)
- Marker clustering once you pass ~50 spots (Leaflet.markercluster plugin)
- Split the data block back into a separate JSON file once the site is hosted (fetch works over http; it was inlined so the file also works when opened directly)
- Hatch charts, river flow links (USGS gauges), tide charts 