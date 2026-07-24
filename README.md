# Arizona Marshallese Community — Website

The official site for the **Arizona Marshallese Community**, a 501(c)(3) nonprofit
supporting Marshallese families across Arizona.

**Live:** https://azmarshallese.github.io/community_site/

---

## Folder structure

```
AMC_website/
├── index.html      ← the entire site (markup + content + logic)
├── support.js      ← runtime bundle — DO NOT EDIT (generated dc-runtime)
├── assets/         ← images
│   ├── billma-peter.png          (used — President's portrait)
│   ├── chuuk-relief-flyer.png    (available — not yet placed)
│   └── marshall-islands-flag.png (available — not yet placed)
├── README.md
└── .gitignore
```

That's the whole project — a single self-contained page. No build step, no
dependencies to install.

## How it works

The page is one HTML file that renders through a small client-side runtime
(`support.js`). All content and behavior live in **`index.html`**, in two places:

1. **The markup** — the `<x-dc>…</x-dc>` body, with inline styles and `{{ }}`
   placeholders that the runtime fills in.
2. **The component logic** — the `<script type="text/x-dc">` block near the bottom.
   This is where the real content lives: leaders, news updates, scholarships,
   tournament schedules, and donation amounts are all data arrays inside
   `renderVals()`.

> To change text, links, people, or events, edit **`index.html`** only.
> Never edit `support.js` — it's a generated runtime and gets overwritten.

## Run it locally

Any static file server works. From this folder:

```bash
python3 -m http.server 8912
# then open http://localhost:8912/
```

(Opening `index.html` directly with `file://` will not work — the runtime needs
to be served over http.)

## Deploy

The site is published with **GitHub Pages** from two repos that hold the same files:

- `azmarshallese/community_site` → the live site
- `YashuLanki/community_site` → your personal copy

Push changes to `main` and GitHub Pages rebuilds automatically.

## Design system

| | |
|---|---|
| **Fonts** | Fraunces (serif headings) · Figtree (body) |
| **Navy** | `#0B2942` |
| **Cream** | `#F5F0E6` |
| **Gold** | `#E8A94D` |
| **Orange** | `#C4622D` |
| **Green** | `#3A5F4F` |
| **Deep red** | `#8C3B2E` |

Motif: 24-point compass star + Marshallese stick-chart lines (navigation/wayfinding).

## Content owners can edit

- **Facebook link / donation info** — search `fbUrl` in `index.html`.
- **Leaders** — the `leaders` array in `renderVals()`.
- **News / updates** — the `news` array.
- **Scholarships & resources** — the `scholarships` array.
- **Tournaments** — the `tournaments()` method and `sportCards` array.
- **Donation amounts** — the `amtVals` array.

## Known TODOs

- [ ] Add the real donation link (Zelle / PayPal / GoFundMe) — currently points to Facebook.
- [ ] Wire in `chuuk-relief-flyer.png` on the relief-drive callout.
- [ ] Add real photos for the other leaders (currently initials avatars).
- [ ] Add page `<title>`, meta description, favicon, and social-share tags.
