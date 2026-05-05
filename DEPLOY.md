# GroundKit — Vercel Deploy Recipe

This `deploy/` folder is everything you need to host **groundkitapp.com**. Drag-and-drop the entire folder into Vercel and you're live.

---

## Step 1 — Sign up at Vercel (free)

1. Go to https://vercel.com/signup
2. Create an account using your email or GitHub
3. Choose the **Hobby (free)** plan — you don't need Pro for this

---

## Step 2 — Deploy the folder

Easiest path: drag-and-drop.

1. Click **Add New… → Project**
2. Click **Deploy** (or look for "drag a folder" — UI changes occasionally)
3. Drag this **entire `deploy` folder** (the one containing `index.html`) into the upload area
4. Vercel detects it as a static site, builds in ~10 seconds
5. You get a temporary URL like `groundkit-xyz.vercel.app` — verify it loads

---

## Step 3 — Connect your custom domain

1. In the Vercel project dashboard, click **Settings → Domains**
2. Add `groundkitapp.com` and `www.groundkitapp.com`
3. Vercel will show you DNS records to configure

You have two routes for DNS:

### Option A — Use your registrar's nameservers (simpler)
- At your domain registrar (Namecheap, GoDaddy, wherever you bought it), add the **A records** and **CNAME records** that Vercel shows you
- Wait 5-30 min for DNS to propagate
- Done

### Option B — Move DNS to Cloudflare (recommended if you also want free email)
- Sign up at cloudflare.com (free)
- Add `groundkitapp.com` as a site
- Cloudflare will give you 2 nameservers (e.g., `bob.ns.cloudflare.com`, `alice.ns.cloudflare.com`)
- At your registrar, change nameservers to those two
- Once Cloudflare confirms ownership, add Vercel's records in Cloudflare's DNS panel
- This setup also enables free email forwarding (see Step 4)

---

## Step 4 — Set up email forwarding (privacy@ and support@)

Your privacy policy and Apple's review process need real email addresses at these:
- `privacy@groundkitapp.com`
- `support@groundkitapp.com`

**Free option: Cloudflare Email Routing** (only works if your DNS is on Cloudflare from Step 3 Option B)

1. In Cloudflare dashboard, go to **Email → Email Routing**
2. Click **Enable Email Routing** (Cloudflare adds the necessary MX records automatically)
3. Add custom addresses:
   - `privacy@groundkitapp.com` → forwards to `joseph.fratter@gmail.com`
   - `support@groundkitapp.com` → forwards to `joseph.fratter@gmail.com`
4. Verify your destination email
5. Test by sending a message to `privacy@groundkitapp.com` from another account

**Paid option: Google Workspace** — $6/mo for a real `support@groundkitapp.com` mailbox you can sign in to. Worth it if you expect significant support volume.

---

## Step 5 — Verify your URLs work

Visit each in a browser:

- ✅ https://groundkitapp.com — main site (your `index.html`)
- ✅ https://groundkitapp.com/privacy — privacy policy
- ✅ https://groundkitapp.com/terms — terms of service
- ✅ https://groundkitapp.com/support — support page

These four URLs are what Apple's App Store reviewer will click. If any 404, your submission gets rejected.

---

## What Vercel handles automatically

You don't have to worry about:
- HTTPS (Vercel issues a free Let's Encrypt cert)
- Renewal (auto-renews forever)
- CDN (Vercel serves from their global edge by default — fast worldwide)
- Compression / caching headers (configured optimally out of the box)

---

## What's in this folder

```
deploy/
├── index.html             ← Your main marketing site
├── support.html           ← Support page (Apple requires this)
├── vercel.json            ← Routing config: /privacy → /legal/privacy-policy.html etc.
├── legal/
│   ├── privacy-policy.html
│   └── terms-of-use.html
└── website/
    └── images/            ← All marketing images + hero videos (155 MB)
```

---

## Updating content later

To make changes after launch:
1. Edit the file in this folder
2. Re-deploy to Vercel (drag-and-drop the updated folder, or use `vercel --prod` if you install the CLI)
3. New version is live in ~30 seconds

---

## If something breaks

- Vercel logs are at the project dashboard → **Deployments → [latest] → Logs**
- DNS troubleshooting: https://www.whatsmydns.net/#A/groundkitapp.com (if A records aren't propagated, the site won't load)
- Vercel docs: https://vercel.com/docs

---

*Setup time end-to-end: ~30 minutes for a first-timer.*
