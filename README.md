# Creaky Cleats

Microsite for the **Creaky Cleats** slowpitch softball team. Plain static HTML — no build step — deployed via GitHub Pages.

## Pages

- `index.html` — landing page
- `roster.html` — team roster
- `handbook.html` — new-member handbook / knowledge base (stubbed with placeholders)
- `style.css` — shared styles
- `.nojekyll` — tells GitHub Pages to serve files as-is (skip Jekyll)

## Editing content

Edit the HTML files directly. The handbook sections are marked with placeholder notes — replace them with real info and delete any that don't apply.

## Local preview

Just open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploying

Pushing to `main` publishes the site. One-time setup: in the repo's
**Settings → Pages**, set the source to **Deploy from a branch**, branch
`main`, folder `/ (root)`. The site will be live at
https://creaky-cleats.github.io/home/
