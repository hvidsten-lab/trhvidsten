# Hvidsten research group website

Static website for the Hvidsten research group (NMBU), hosted on **GitHub Pages**
at <https://trhvidsten.com>. Plain HTML + CSS — no build step, no framework.

## Structure

```
index.html               Home
people.html              People (team grid + "my journey")
research.html            Research — current projects
research-background.html   Methods & background (local descriptors, gene regulation)
research-collaborators.html
publications.html        Peer-reviewed articles + preprints
publications-other.html / -posters.html / -presentations.html / -press.html
tools.html               Software & code
teaching.html            Master-thesis topics, courses, supervised theses, links
news.html                News timeline
fun.html                 Cartoons, links, classic papers
stuff-that-matters.html  Personal page
404.html                 Not-found page

assets/css/style.css     The single stylesheet (all styling lives here)
onewebmedia/  image/     Images (people photos, logos, tool icons, figures)
docs/                    Linked PDFs (theses, slides, classic papers under docs/classics)
binding_sites/ bioinf_cho/ fibroblast/   Supplementary-data pages for older papers

CNAME                    Custom domain (trhvidsten.com) — do not delete
.nojekyll                Tells GitHub Pages to serve files as-is
people/ research/ ...    Small redirect stubs that preserve the OLD one.com URLs
```

## Editing content

Everything is hand-editable HTML.

- **Add a publication:** open `publications.html`, copy an existing `<li>…</li>`
  in the `<ol class="pub-list">`, and edit the text/links. Wrap your own name in
  `<strong>T. R. Hvidsten</strong>` to keep it bold.
- **Add a person:** in `people.html`, copy a `<figure class="person">…</figure>`
  block, drop the new photo into `onewebmedia/`, and update the `src`, name and role.
- **Add news:** in `news.html`, add an `<li>` under the relevant year.
- **Colours / fonts / spacing:** all in `assets/css/style.css` (see the `:root`
  variables at the top — change `--green-700` etc. to re-theme the whole site).

The top navigation is repeated in each file's `<header>`. If you change a nav link,
update it in each page (or ask Claude to regenerate them).

## Deploying (one-time GitHub Pages setup)

1. Create a GitHub repo and push the contents of this folder to the `main` branch.
2. Repo **Settings → Pages** → Source: *Deploy from a branch* → `main` / `/ (root)`.
3. Under **Custom domain**, enter `trhvidsten.com` and Save (this uses the `CNAME` file).
4. At one.com DNS, point the domain at GitHub Pages:
   - `A` records for `@` → `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153`, `185.199.111.153`
   - `CNAME` record for `www` → `<your-github-username>.github.io`
5. Back in Settings → Pages, tick **Enforce HTTPS** once the certificate is issued.

After the first deploy, every `git push` to `main` republishes the site.
