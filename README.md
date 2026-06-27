# BI Portfolio

A single static page (`index.html`) that showcases Power BI dashboards via
**Publish-to-web** iframe embeds. No build step, no backend — GitHub Pages serves
the file as-is.

## How to swap in a real embed

1. In **Power BI Service**: open the report → **File → Embed report → Publish to web (public)**.
2. Power BI gives you an `<iframe …>` snippet and a `src` URL.
3. In `index.html`, find the marker inside a dashboard section:

   ```html
   <!-- ▼▼▼  PASTE YOUR PUBLISH-TO-WEB IFRAME HERE  ▼▼▼ -->
   ```

   Either paste Power BI's URL into the existing `src=""`, **or** replace the whole
   `<iframe class="embed__frame" …>` tag with Power BI's snippet — just keep
   `class="embed__frame"`, a descriptive `title=`, `allowfullscreen`, and an
   `https://` source.
4. That's it. A real (opaque) report paints over the "Paste your embed code here"
   empty-state automatically — no other change needed.

## Add another dashboard

Each `<section class="dashboard">` is a self-contained, copy-pasteable unit. Copy the
whole section, paste it below the previous one, and:

- the `01 /` index number **auto-increments** (CSS counter — don't hand-number it),
- rename the `<h2>`,
- edit the four spec rows (Stack / Grain / Pattern / Refresh),
- rewrite the three write-up blocks (business problem / model design / DAX or pipeline pattern).

## ⚠️ Data safety — read before publishing

**Publish-to-web is fully public and exposes the *entire underlying model*** — every
table, column, and measure, not just what's on the visible page. Anyone with the link
(and search engines) can reach it.

→ **Only publish reports built on anonymized / synthetic data.** Handle that in Power BI
(before publishing), not in this repo. This site only embeds whatever the published
report already exposes.

## Deploy (GitHub Pages)

Push to a public repo, then **Settings → Pages → Build from a branch → `main` / root**.
The site goes live at `https://<user>.github.io/<repo>/`.

## Local preview

It's a plain file — open `index.html` in a browser, or serve the folder:

```bash
python -m http.server 8000   # then visit http://localhost:8000
```
