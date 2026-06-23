# bumbl

Human-centered AI, automation, and systems design.

This repository hosts the public Bumbl landing page.

## Live site

- Canonical domain: `https://bumbl.net`
- GitHub Pages project URL: `https://mediumbumble.github.io/bumbl/`
- Repository: `mediumbumble/bumbl`
- Publishing source: `main` branch, `/ (root)` folder
- Custom domain file: `CNAME` containing only `bumbl.net`

## Deployment model

The production site is served by GitHub Pages from the root `index.html` file.

Current model:

- `index.html` at repo root is the live page
- no build step
- no framework
- no package manager
- no deploy command
- fonts load from Google Fonts CDN
- favicon is embedded in `index.html`
- brand assets are stored in the repo for reference and future swaps

When editing the live site, update lowercase `index.html`. GitHub Pages is case-sensitive; do not create or ship `Index.html`.

## GitHub Pages configuration

GitHub UI path:

`Settings -> Pages`

Configuration:

- Source: `Deploy from a branch`
- Branch: `main`
- Folder: `/ (root)`
- Custom domain: `bumbl.net`
- HTTPS: enable `Enforce HTTPS` after GitHub issues the certificate

Known launch behavior:

- GitHub may show `DNS check unsuccessful` while DNS propagation is still catching up.
- If `bumbl.net` loads but GitHub still warns, wait and click `Check again`.
- `Enforce HTTPS` remains unavailable until GitHub provisions the certificate.

## DNS management

The domain `bumbl.net` is managed in Squarespace Domains.

Squarespace path:

`Domains -> bumbl.net -> DNS Settings`

Important: only website records should point to GitHub Pages. Do not remove email records.

### Website records for GitHub Pages

Apex/root records:

```txt
A     @     185.199.108.153
A     @     185.199.109.153
A     @     185.199.110.153
A     @     185.199.111.153
```

WWW record:

```txt
CNAME     www     mediumbumble.github.io
```

Optional IPv6 records, if desired:

```txt
AAAA     @     2606:50c0:8000::153
AAAA     @     2606:50c0:8001::153
AAAA     @     2606:50c0:8002::153
AAAA     @     2606:50c0:8003::153
```

### Records removed during launch

The default Squarespace website records were removed or replaced:

```txt
A      @      198.49.23.144
A      @      198.185.159.145
A      @      198.185.159.144
A      @      198.49.23.145
CNAME  www    ext-sq.squarespace.com
HTTPS  @      Squarespace HTTPS/SVCB-style record
```

### Email records to preserve

Zoho email is configured through DNS and should be left intact:

```txt
MX     @                  mx.zoho.com       priority 10
MX     @                  mx2.zoho.com      priority 20
MX     @                  mx3.zoho.com      priority 50
TXT    @                  zoho-verification...
TXT    zmail._domainkey   v=DKIM1; k=rsa; p=...
TXT    @                  v=spf1 include:zohomail.com ~all
```

Squarespace Domain Connect should also be left alone unless intentionally changing registrar/domain-management behavior:

```txt
CNAME  _domainconnect     _domainconnect.domains.squarespace.com
```

## Launch validation checklist

- [x] Public repo exists: `mediumbumble/bumbl`
- [x] `index.html` exists at repo root
- [x] `CNAME` contains `bumbl.net`
- [x] GitHub Pages source set to `main` / root
- [x] DNS check successful in GitHub Pages
- [x] `http://bumbl.net` loads the site
- [ ] GitHub certificate issued
- [ ] Enforce HTTPS enabled
- [ ] `https://bumbl.net` loads with a padlock
- [ ] `https://www.bumbl.net` redirects correctly
- [ ] Favicon shows in browser tab
- [ ] `Start a conversation` opens a draft to `scott@bumbl.net`
- [ ] Mobile layout checked
- [ ] No console errors

## Maintenance notes

Future content swaps:

- replace temporary/inline wordmark treatment with the official wordmark artwork when ready
- add Megan's finalized bio lines
- add a founder photo if desired
- replace placeholder proof/work examples with true figures only
- add the LinkedIn URL in the footer

Operational rule: once `index.html` is in the repo, the repo is canonical. Do not edit the same site file in multiple places without reconciling back to this repository.
