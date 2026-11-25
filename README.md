# Security Tools

A small static site with two free, browser-based security self-assessment tools,
linked from [pro-tech-716.com](https://pro-tech-716.com). No build step, no backend —
just static files, so it hosts anywhere (GitHub Pages, Netlify, Cloudflare Pages, or
any web root).

| Tool | What it does | Runs |
|---|---|---|
| [Firmware Secret Looter](firmware-secret-looter/) | Extracts hardcoded credentials (AWS/Google/Stripe keys, PEM private keys, passwords, JWTs, high-entropy tokens) from a firmware or app binary you upload | 100% in the browser — no network calls at all |
| [Doppelganger](doppelganger/) | Generates lookalike domains (homoglyphs, typos, TLD swaps) for your brand and checks which resolve in DNS and can send email | In the browser; DNS-over-HTTPS to `dns.google` from the visitor's own browser |

Both are **client-side only**, so the visitor's files and domain never reach a server of
yours — which is also why they're safe to host as public, open tools.

## Layout

```
index.html                      landing page linking the two tools
firmware-secret-looter/index.html
doppelganger/index.html
.nojekyll                       tells GitHub Pages to serve files as-is
```

## Deploy on GitHub Pages

```bash
# from this folder, after creating the repo (see below)
git push -u origin main
```

Then in the repo: **Settings → Pages → Build and deployment → Deploy from a branch →
`main` / root**. Your site appears at `https://<user>.github.io/<repo>/`.

To use a subdomain of your site instead (e.g. `tools.pro-tech-716.com`), add a `CNAME`
file containing that hostname and point a DNS CNAME record at `<user>.github.io`.

## Link from pro-tech-716.com

Point your "free tests" links at:
- `…/firmware-secret-looter/`
- `…/doppelganger/`

## Scope

Both tools are for assessing assets you own or are authorised to test, and say so on
screen. They show only real results and never fabricate findings.
