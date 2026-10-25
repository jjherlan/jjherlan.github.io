# James J. Herlan, academic website

This is a Quarto website hosted free on GitHub Pages. It will live at **https://jjherlan.github.io**, and you can add a custom domain later.

## What's in this folder

| File / folder | What it is |
|---|---|
| `_quarto.yml` | Site settings: title, menu, footer links, theme |
| `index.qmd` | Home page (hero photo, about, research themes, news, contact) |
| `research.qmd` | Research themes, future direction, earlier work, field photos, support |
| `publications.qmd` | Papers with DOIs, manuscripts, chapters, proceedings, talks |
| `teaching.qmd` | Courses, mentoring, workshops and outreach |
| `code.qmd` | Interactive apps, GitHub repositories, tools |
| `media.qmd` | YouTube videos and photo gallery |
| `cv.qmd` + `files/Herlan_CV.pdf` | CV page with embedded PDF |
| `images/` | Photos (resized for the web) and the favicon |
| `styles/` | Colors and fonts (`light.scss`, `dark.scss`) and layout (`site.css`) |
| `.github/workflows/publish.yml` | Publishes the site automatically on every push |

## One-time setup (about 15 minutes)

1. **Install Quarto** from https://quarto.org/docs/get-started/ (macOS installer). Check it works in Terminal:
   ```bash
   quarto --version
   ```
2. **Preview the site on your Mac.** In Terminal:
   ```bash
   cd ~/Postdoctoral/Website/herlan-site
   quarto preview
   ```
   A browser window opens and reloads every time you save a file.
3. **Create the GitHub repository.** On GitHub, signed in as `jjherlan`, create a new **public** repository named exactly **`jjherlan.github.io`**. Don't add a README.
4. **Push this folder to it.**
   ```bash
   cd ~/Postdoctoral/Website/herlan-site
   git init -b main
   git add .
   git commit -m "First version of website"
   git remote add origin https://github.com/jjherlan/jjherlan.github.io.git
   git push -u origin main
   ```
5. **Publish once from your Mac.** This creates the `gh-pages` branch that GitHub serves the site from:
   ```bash
   quarto publish gh-pages
   ```
   Answer **Y** when asked. Then on GitHub, open **Settings → Pages** and check that *Source* is **Deploy from a branch**, with branch **`gh-pages`** and folder **`/ (root)`**.
   After this first time, every `git push` to `main` republishes the site automatically through the workflow in `.github/workflows/publish.yml`.
6. Visit **https://jjherlan.github.io**. Your existing project sites (e.g., `jjherlan.github.io/rpn-spatial/`) keep working unchanged.

## Updating the site

Edit any `.qmd` file, check it with `quarto preview`, then:
```bash
git add .
git commit -m "Update publications"
git push
```
GitHub rebuilds and republishes the site in about a minute. Also update the "Last updated" date in the footer (`_quarto.yml`).

**To swap in a new CV:** replace `files/Herlan_CV.pdf` with the new file, keeping the same name, then commit and push.

## Optional: custom domain (e.g., jamesherlan.com)

1. Buy the domain (Cloudflare Registrar or Namecheap, about $10–15 a year).
2. At the registrar, add DNS records for GitHub Pages: four `A` records for `@` pointing to `185.199.108.153`, `185.199.109.153`, `185.199.110.153` and `185.199.111.153`, and a `CNAME` record for `www` pointing to `jjherlan.github.io`. Check GitHub's current docs ("Managing a custom domain for your GitHub Pages site") before you do this.
3. Create a file named `CNAME` in this folder containing just the domain (e.g., `jamesherlan.com`). Add `- CNAME` under `resources:` in `_quarto.yml`, and change `site-url` to match. Commit and push.
4. In **Settings → Pages**, enter the domain and tick **Enforce HTTPS**.

## To do

- [ ] Add **Google Scholar** and **ORCID** links: uncomment the lines in `_quarto.yml` (footer) and the comment at the top of `publications.qmd`.
- [ ] Replace `files/Herlan_CV.pdf` with a corrected CV (see the notes below).
- [ ] Check the photo captions in `research.qmd` and `media.qmd`. Some locations were inferred.
- [ ] Once it's live, redirect or retire the Google Site, and update the website line in your email signature, CV and application materials.

## Notes on the CV currently included (Oct 2026)

- The MEPS paper is now published online (25 Aug 2026, doi:10.3354/meps15300). The CV still lists it as *in press*.
- The *Journal of Fish Biology* (2022) entry on the CV has a different title and species from the published paper. The published title is: *"Now you see me: 'first' records of the greater amberjack* Seriola dumerili *at Rapa Nui range extension or increased scientific effort?"*, J. Fish Biol. 100(3): 835–842, doi:10.1111/jfb.14983.
- The References section lists your referees' email addresses. Consider removing them from the public copy.
