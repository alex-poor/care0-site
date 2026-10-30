# care0. — product site

A single self-contained `index.html` product splash page for **care0.** — the
capability-first primary-care platform. No build step, no dependencies: the whole
page (styles, scripts, the Mapple logo as a data URI) is in one file. Google Fonts
are the only external request.

It lives here, separate from the (private) platform repo, so GitHub Pages can serve
it publicly.

## What's on the page

- Working **omnibox** demo that routes typed queries the way the real console does.
- Interactive **patient-held record** demo (grant a reader → decrypt → revoke → goes dark).
- The **"Take the tour"** flyover — the same 12 steps the console runs, with the *why it wins*.
- An animated **Encounter-spine** lifecycle (planned → arrived → in-progress → finished → auto-invoice).
- **Safety-by-construction** — the type-level guarantee and the Severity-3 `422` hard block.
- Architecture crate table, the "see it in 2 minutes" flow, and a live **skin switcher**
  (Default / Light / Midnight / Game Boy / Kawaii) that re-colours the whole page.

## Deploy to GitHub Pages

```fish
cd care0-site
git init -b main
git add -A
git commit -m "care0 product site"
gh repo create care0-site --public --source=. --remote=origin --push
# then: repo → Settings → Pages → Source: "Deploy from a branch" → main / (root)
```

Served at `https://<user>.github.io/care0-site/`. The empty `.nojekyll` file tells
Pages to serve the files as-is (no Jekyll processing).

Prefer a custom domain? Add a `CNAME` file containing the domain and point a DNS
`CNAME`/`ALIAS` at `<user>.github.io`.

## Editing

Open `index.html` — everything is inline and commented. The content lives in the
`<script>` data arrays (`FEATURES`, `TOUR`, `CRATES`, `SKINS`, …); the look lives in
the `:root` token blocks at the top of `<style>`. To swap the Mapple logo, replace the
`data:image/png;base64,…` URI inside the `.madeby` link.
