# REKO'S UPLOADER — Remote Config (Vercel)

Static JSON endpoints for the browser extension. No framework, no build.

## Deploy

```bash
# Option A — CLI
npm i -g vercel
cd REKOS-UPDATE-CONFIG
vercel --prod
```

Or push this folder to a GitHub repo and import it at [vercel.com/new](https://vercel.com/new).

## Endpoints (after deploy)

Replace `<project>` with your Vercel project name:

| File | URL |
|------|-----|
| Announcement | `https://<project>.vercel.app/announcement.json` |
| Version | `https://<project>.vercel.app/version.json` |
| Config | `https://<project>.vercel.app/config.json` |
| Changelog | `https://<project>.vercel.app/changelog.json` |

`vercel.json` enables CORS (`*`) and edge cache 60s so edits go live quickly.

## Edit announcement

Edit `announcement.json` then redeploy (or push to GitHub if linked):

```json
{
  "id": "unique-id-change-each-time",
  "enabled": true,
  "type": "info",
  "badge": "Announcement",
  "headline": "Your title",
  "subtext": "Your message",
  "cta": { "label": "Open", "url": "https://..." },
  "footnote": "REKO'S • @rekos12fps",
  "dismissible": true
}
```

Set `"enabled": false` to hide. Change `"id"` so dismissed users see a new banner again.

Types: `info` | `update` | `update_required` | `warning`

## Point the extension at your URL

In the extension, set host permission + base URL (see extension `popup.js` / `manifest.json`):

```
https://YOUR-PROJECT.vercel.app
```

Default placeholder in the extension is `https://rekos-uploader.vercel.app` — rename after first deploy.
