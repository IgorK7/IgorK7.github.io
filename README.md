# Igor Kuznetsov: academic website

Live at <https://igork7.github.io>. One static page on Bootstrap 5.3 (loaded from the jsDelivr CDN),
one stylesheet, no build step: GitHub Pages serves the `main` branch as it is.

```
index.html             the whole site: Home, Research, Teaching, Contact under a fixed top bar
assets/css/style.css   small overrides on Bootstrap (LBS blue #001e62, dark blue #001440)
assets/img/            profile.jpg (450 x 600), favicon.svg
.nojekyll              serve the files as they are (no Jekyll processing)
```

## Updating

1. Edit `index.html` and change the "Last updated" line in the footer.
2. Preview: run `python3 -m http.server` in this folder and open <http://localhost:8000>.
3. Commit and push to `main`. The live site updates within a minute or two; the repository's
   Settings > Pages shows the latest deployment.

## CV and paper PDFs

The PDFs live on Google Drive, each shared as "Anyone with the link" (Viewer).

- The CV links (top bar and home button) use Drive's direct-download address,
  `https://drive.google.com/uc?export=download&id=<file id>`, so a click saves the PDF.
  The saved file takes the Drive file's name.
- Paper links open Drive's viewer: `https://drive.google.com/file/d/<file id>/view`.
- SSRN links open the paper's SSRN page, `https://papers.ssrn.com/sol3/papers.cfm?abstract_id=<id>`.
  A revision uploaded to SSRN keeps that address.
- To update a PDF without changing its link, replace the file in Drive (Manage versions, or
  overwrite it in a synced folder). Uploading a new copy gives it a new id, which then has to
  replace the old one in `index.html`.

## Adding a paper

Copy an `<article class="paper">` block in the Research section of `index.html`, give it a new `id`,
and put its links (SSRN page, PDF) in a `<p class="links mb-0">` line under the abstract.

## Custom domain

1. Register the domain (Cloudflare Registrar, Porkbun or Namecheap; about USD 10 a year).
2. At the registrar's DNS panel:
   - `CNAME` record: host `www` -> `igork7.github.io`
   - `A` records for the bare domain (`@`): `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
3. In this repository's Settings > Pages > Custom domain, enter the domain and save. GitHub commits a
   `CNAME` file to `main`, so pull before the next push. Tick "Enforce HTTPS" once the certificate is
   issued (minutes to a few hours).
