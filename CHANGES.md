# Site Redesign — Summary of Changes

## What Changed

The site was completely redesigned from a Jemdoc-generated table-based layout
(circa 2012) to a modern, hand-written HTML5 + CSS site.

### Old Stack → New Stack

| Before | After |
|--------|-------|
| Jemdoc markup → generated HTML | Hand-written semantic HTML5 |
| `jemdoc.css` (table-based layout) | `style.css` (Flexbox, CSS custom properties) |
| Georgia serif font | Inter (Google Fonts) — clean sans-serif |
| Beige background (`#fdf6e3`) | Light gray (`#f8f9fa`) with white cards |
| Left sidebar navigation | Sticky top navigation bar with blur effect |
| No mobile support | Fully responsive (mobile, tablet, desktop) |

### Files Modified

| File | What happened |
|------|---------------|
| `index.html` | Rewritten — hero section with circular profile photo and bio |
| `research.html` | Rewritten — publication cards with hover effects, project cards |
| `contact.html` | Rewritten — contact card with labeled email entries |
| `style.css` | **New file** — all styling lives here |
| `CHANGES.md` | **New file** — this document |

### Files Kept (not modified)

| File | Purpose |
|------|---------|
| `jemdoc.css` | Old stylesheet (no longer used, kept for reference) |
| `jemdoc.py` | Old build tool (no longer needed to regenerate pages) |
| `mysite.conf` | Old Jemdoc config |
| `MENU` | Old Jemdoc menu definition |
| `*.jemdoc` | Original markup source files |
| `assets/profile.JPG` | Profile photo (unchanged) |

---

## Design Decisions

- **No build tools required.** The site is just 3 HTML files + 1 CSS file.
  Edit them directly — no need to run `jemdoc.py` or any build command.
- **Google Fonts (Inter)** is loaded from a CDN. No fonts need to be
  installed or hosted locally.
- **MathJax** is kept on the research page for rendering math if needed.
- **All content** from the original site is preserved exactly.

---

## How to Edit

### Changing content

Open the relevant `.html` file in any text editor and change the text
inside the HTML tags. The structure is readable — look for elements like
`<p>`, `<h2>`, `<div class="pub-card">`, etc.

### Adding a new publication

Copy an existing `<div class="pub-card">…</div>` block in `research.html`
and update the title, URL, authors, and venue.

### Changing colors or fonts

All design tokens are CSS variables at the top of `style.css`:

```css
:root {
  --color-bg: #f8f9fa;        /* page background */
  --color-surface: #ffffff;    /* card background */
  --color-text: #1a1a2e;      /* main text color */
  --color-accent: #2563eb;    /* links, highlights */
  /* ... */
}
```

Change these values and the entire site updates.

### Deploying

Push to GitHub. If GitHub Pages is enabled on the `master` branch, the
site will update automatically. No build step is needed.

---

## Recommended Follow-up

- **Optimize profile image:** `assets/profile.JPG` is 6.8 MB. Resize it
  to ~600px wide and compress it (tools: squoosh.app, TinyPNG) to reduce
  load time dramatically.
- **Add a favicon:** Place a `favicon.ico` or `favicon.png` in the root
  and add `<link rel="icon" href="favicon.png">` to each page's `<head>`.
- **Add Google Scholar / GitHub links:** These could go in the nav or the
  hero section for easy access.
