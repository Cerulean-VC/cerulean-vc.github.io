# cerulean.vc

The Cerulean Ventures website. It is a Jekyll site that GitHub Pages builds and hosts.

## Where the content lives

| What | File |
| --- | --- |
| Home page copy | `index.html` |
| Thesis | `thesis.md` |
| Sectors (home rows, portfolio pills and filters) | `_data/sectors.yml` |
| Portfolio companies | `_data/companies.yml` |
| Essays on Substack | `_data/writing.yml` |
| Investment notes | `_notes/*.md` |
| Partners and advisors | `_data/team.yml` (photos in `assets/img/team/`) |
| Founder terms | `_data/terms.yml` |
| Legal pages | `important-disclosures.md`, `website-terms-of-use.md` |

The portfolio page lists each company once, with a pill for every sector in its `sectors`. Visitors can filter the list by sector, and `/portfolio/#energy` opens the list filtered to energy. On the home page, a company appears in the row of every sector it lists. The home page also shows the newest essay tagged with each sector. When a sector has no essay, it shows the newest investment note for that sector.

When you change the thesis, update `version`, `version_date` and `revisions` in `thesis.md`. The "see what changed" link opens this file's commit history on GitHub, so the history comes from git.

## Publish on GitHub Pages

1. Create a GitHub repository and push this folder as its root:

   ```
   git init -b main
   git add .
   git commit -m "Cerulean website"
   git remote add origin git@github.com:OWNER/REPO.git
   git push -u origin main
   ```

2. In the repository, open Settings → Pages. Set the source to "Deploy from a branch", branch `main`, folder `/ (root)`.
3. Check the site at `https://OWNER.github.io/REPO/`. If links on that address point to the wrong place, add `baseurl: /REPO` to `_config.yml` for as long as you use that address.
4. Switch the domain last, because cerulean.vc stays on Super until the DNS changes:
   - Settings → Pages → Custom domain: `cerulean.vc`.
   - At your DNS provider, point `cerulean.vc` at GitHub Pages with four A records: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`. Point `www` at `OWNER.github.io` with a CNAME record.
   - Tick "Enforce HTTPS" once GitHub has issued the certificate.

GitHub Pages is free on a public repository. A private repository needs a paid GitHub plan.

## Run it locally

```
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000.

## Still to fill in

- Matthew's bio in `_data/team.yml`.
- A blurb for Jasmine Energy, and a confirmed one for Watt Carbon, in `_data/companies.yml`.
- Company websites, years and stages where they are blank in `_data/companies.yml`.

## What moved from the old site

- `/articles` now redirects to `/writing/`.
- Nine investment notes moved to `/notes/`, and their old addresses redirect there.
- These old notes were not moved, so their addresses will stop working: SBP, Thallo, Neutral Labs, Nibiru, Masa Finance, KYVE Network, Digital Gaia and Covalent. The Silta note already returns "not found" on the old site.
- The Elio note lost one image, because it was hosted on a Google Docs link that expires.
- Fonts are self-hosted (Inter and Libre Baskerville, SIL Open Font License), so the site makes no calls to Google Fonts.
