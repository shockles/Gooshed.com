# gooshed.com — deploy

Static link hub: `index.html` + `assets/` (brand files copied from `nade-pipeline/brand/`).
Preview locally: the `site` entry in `.claude/launch.json` (http://localhost:8090).

## 1. Put it on GitHub
1. Create a new repo on github.com, e.g. `gooshed-site` (public or private both work with Cloudflare).
2. Upload the contents of this `site/` folder to it (drag and drop on github.com works, or `git init` + push).

## 2. Host on Cloudflare Pages (recommended, free, commercial use OK)
1. Cloudflare dashboard → Workers & Pages → Create → Pages → Connect to Git → pick `gooshed-site`.
2. Build settings: framework **None**, build command **empty**, output directory **/** .
3. After the first deploy: the project → Custom domains → add `gooshed.com`, then `www.gooshed.com`.
   If the domain is registered at Cloudflare, DNS is set up automatically. If it is at another registrar,
   either move the nameservers to Cloudflare (Cloudflare walks you through it) or add the CNAME it shows.
4. Every push to the repo redeploys the site.

`CNAME` in this folder is only used by GitHub Pages; Cloudflare ignores it.

### Alternative: GitHub Pages
Repo → Settings → Pages → deploy from branch `main`, folder `/`. Custom domain `gooshed.com`, tick Enforce HTTPS.
At the registrar add A records for `@` → 185.199.108.153, .109.153, .110.153, .111.153 and CNAME `www` → `<github-user>.github.io`.
Keep sales off the page itself (link out to Gumroad/Lemon Squeezy); Pages' terms don't allow running a store on it.

## 3. hello@gooshed.com
The page's Business button mails `hello@gooshed.com`. Make it real before sharing the link:
Cloudflare → gooshed.com → Email → Email Routing → add `hello@` → forward to your Gmail (free).

## Later
- Lineup pack card is greyed out with a SOON chip. When the pack and the Beehiiv/Kit signup exist,
  swap the `<div class="link soon">` for an `<a class="link" href="...">` to the signup page.
- Add a gear page once affiliate links are approved.
