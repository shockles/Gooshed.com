# gooshed.com — deploy

Static link hub. The page lives in `public/` (`index.html` + `assets/`, brand files copied from `nade-pipeline/brand/`).
`wrangler.jsonc` tells Cloudflare Workers to serve `public/`.
Preview locally: the `site` entry in `.claude/launch.json` (http://localhost:8090).

Repo: https://github.com/shockles/Gooshed.com — every push to `main` redeploys.

## Cloudflare Workers (current setup)
1. Workers & Pages → Create → Import a repository → `shockles/Gooshed.com`.
2. Project name `gooshed-com`, build command empty, deploy command `npx wrangler deploy` (defaults). Deploy.
3. Test address: `gooshed-com.<account>.workers.dev`.
4. Custom domain: the Worker → Settings → Domains & Routes → Add → Custom domain → `gooshed.com`, then `www.gooshed.com`.
   The domain has to be added to the Cloudflare account first (home → Add a domain → Free plan, then set the
   two Cloudflare nameservers at the registrar).

## hello@gooshed.com
The page's Business button mails `hello@gooshed.com`. Make it real before sharing the link:
Cloudflare → gooshed.com → Email → Email Routing → add `hello@` → forward to your Gmail (free).

## Later
- Lineup pack card is greyed out with a SOON chip. When the pack and the Beehiiv/Kit signup exist,
  swap the `<div class="link soon">` for an `<a class="link" href="...">` to the signup page.
- Add a gear page once affiliate links are approved.
- Keep sales off the page itself; link out to Gumroad/Lemon Squeezy.
- `public/CNAME` is only for GitHub Pages, if the site ever moves there.
