# shipper-help

Help site built with [Docsify](https://docsify.js.org/). Everything in `docs/`
is served as-is: no build step, no Node dependencies.

Site: https://hurkin.github.io/shipper-help/

## Editing

- `docs/instructions/`: guides. Add a page, then list it in `docs/instructions/_sidebar.md`.
- `docs/release-notes/`: one file per release. List it in `docs/release-notes/_sidebar.md` and the table in `README.md`.
- `docs/context/`: context-sensitive help, one file per SHP feature mnemonic (the
  screen's help button passes it). Its sidebar is generated, alphabetical by title. `docs/context/A004.md` opens at
  `https://hurkin.github.io/shipper-help/#/context/A004`. The mnemonic appears only
  in the file name and URL, never in the page text.
- `docs/assets/`: shared images.
- Screenshots still to be captured are marked `Screenshot placeholder` with the
  file name to save them as (`grep -rn "Screenshot placeholder" docs`).

After adding, removing or retitling any page, run `python scripts/build-index.py`. It
rebuilds `docs/context/_sidebar.md` and `docs/search-paths.js`, the list of every page
search indexes (Docsify search otherwise sees only the sidebar on screen). Pages in the
other sections are searchable once they are in their `_sidebar.md`. Rerun it after editing
page text too: it stamps a version that makes browsers rebuild their cached search index
right away (otherwise edits reach search within an hour).

The sidebar is hidden when the site is framed (shipper-ui's help panel) or opened with
`?sidebar=0`, e.g. `#/context/A004?sidebar=0`.

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
