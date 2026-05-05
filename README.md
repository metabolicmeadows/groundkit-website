# GroundKit Website

Marketing site for **GroundKit** — the soil-smart gardening companion for home gardeners. Lives at [groundkitapp.com](https://groundkitapp.com).

## Deployed via Vercel

This repo auto-deploys to Vercel on every push to `main`. Domain `groundkitapp.com` is connected via custom domain in the Vercel dashboard.

## What's in here

```
.
├── index.html              ← marketing site
├── support.html            ← Apple-required support page
├── vercel.json             ← clean URL routing config
├── legal/
│   ├── privacy-policy.html
│   └── terms-of-use.html
└── website/
    └── images/             ← marketing assets + hero videos
```

## URL routing

Configured in `vercel.json`:

| URL | Serves |
|---|---|
| `/` | `index.html` |
| `/privacy` | `legal/privacy-policy.html` |
| `/terms` | `legal/terms-of-use.html` |
| `/support` | `support.html` |

## Local preview

Open `index.html` directly in a browser, or run a static server:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

Note: clean URLs like `/privacy` only work behind Vercel's routing layer. For local preview, use the full path `legal/privacy-policy.html`.

## Updating content

1. Edit any HTML file
2. Commit and push to `main`
3. Vercel deploys automatically (~30 seconds)

---

© 2026 Metabolic Meadows LLC
