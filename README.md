# American Higher Education Barometer website

Source for [edbarometer.org](https://edbarometer.org), a single static page served by GitHub Pages. There is no build step: what is in this folder is what gets published.

## Files

- `index.html` is the whole page.
- `assets/css/style.css` holds all styles. Colors and fonts are set as variables at the top.
- `assets/img/` holds the hero illustration (`cover.jpg`), the report thumbnail, the social-media preview image, and the favicon.
- `assets/reports/` holds the report PDFs that the Download buttons link to.
- `CNAME` tells GitHub Pages to serve the site at `edbarometer.org`.
- `.nojekyll` turns off GitHub's Jekyll processing, which this site does not need.

## Adding a new report

1. Put the PDF in `assets/reports/`, using a name without spaces.
2. Save a thumbnail of its first page in `assets/img/` (about 560 px wide).
3. In `index.html`, update the "Latest Report" section and the hero's Download Report link. To keep older reports listed, copy the `.report` block and place the older one below it.

## Publishing on GitHub Pages

1. Push this folder's contents to the root of a GitHub repository's `main` branch.
2. In the repository, open Settings, then Pages. Under "Build and deployment", choose "Deploy from a branch", branch `main`, folder `/ (root)`.
3. In the same Pages settings, enter `edbarometer.org` as the custom domain and, once the certificate is issued, tick "Enforce HTTPS".

## Pointing the domain at GitHub

At the domain registrar's DNS settings for `edbarometer.org`:

| Type | Host | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | `<github-username>.github.io` |

Remove any existing A records, forwarding, or website-builder records for `@` and `www` first. DNS changes can take up to a day to spread. GitHub's own instructions are at <https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site>.

Because of the `CNAME` file, the `github.io` address redirects to `edbarometer.org`. Until the DNS change above is made, that means the GitHub address shows whatever the domain currently points to. To preview the site on GitHub before switching the domain, leave the `CNAME` file out of the first push and add it when the DNS is ready.
