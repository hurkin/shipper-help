# shipper-help

Help site built with [Docsify](https://docsify.js.org/). Everything in `docs/`
is served as-is: no build step, no Node dependencies.

Site: https://hurkin.github.io/shipper-help/

## Editing

- `docs/instructions/`: guides. Add a page, then list it in `docs/instructions/_sidebar.md`.
- `docs/release-notes/`: one file per release. List it in `docs/release-notes/_sidebar.md` and the table in `README.md`.
- `docs/context/`: context-sensitive help with no sidebar. `docs/context/A001.md` opens at
  `https://hurkin.github.io/shipper-help/#/context/A001`.
- `docs/assets/`: shared images.

Use relative links and image paths only (e.g. `images/foo.png`, `../`), never paths starting with `/`.
Each section's `_sidebar.md` links are relative to that section's folder.

## Local preview

```sh
python -m http.server 3000 --directory docs
```

Then open http://localhost:3000.

## Publishing (one-time setup)

1. Repo Settings > Pages > Source: "Deploy from a branch"
2. Branch: `main`, Folder: `/docs`
3. Site URL: https://hurkin.github.io/shipper-help/

After that, every push to `main` updates the site.
