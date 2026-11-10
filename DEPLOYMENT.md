# Deploying the ServiceGate marketing site

This folder is the public GitHub Pages site for ServiceGate, served at https://ess2292.github.io/servicegate/. The paid CLI source is not in this repository.

The site stays **noindex**. Every HTML page includes `<meta name="robots" content="noindex">` and `robots.txt` disallows all crawlers. Do not replace `robots.txt` with `robots.launch.txt`, and do not remove `noindex`, until launch is approved.

The buy button stays disabled while `data-checkout-url` is empty. Do not point it at a test-mode checkout on this public site, and do not set a live Lemon Squeezy URL until publish approval.

Support contact on these pages links to GitHub Issues on [ESS2292/servicegate-action](https://github.com/ESS2292/servicegate-action/issues). Do not invent a support email.


## Files

- `index.html`, `privacy.html`, `terms.html`, `styles.css`, `robots.txt`, `.nojekyll`
- `og-image.svg` and `og-image.png` (pages use the PNG for Open Graph and Twitter cards)
- `favicon.svg`, `favicon-32.png`, `apple-touch-icon.png`
- `guides/`
- `sitemap.xml` (prepared for launch; not referenced by the live `robots.txt`)

## When launch is approved

Follow the ordered checklist in `/workspace/envgate-launch/LAUNCH-RUNBOOK.md`. To flip this site locally:

```bash
/workspace/envgate-launch/scripts/go-live.sh --dry-run servicegate 'https://LIVE-CHECKOUT-URL'
# only after approval:
/workspace/envgate-launch/scripts/go-live.sh --apply servicegate 'https://LIVE-CHECKOUT-URL'
```

The script sets `data-checkout-url` on `#buy-btn`, enables the button, replaces `noindex` with `index,follow` on every HTML page, copies `robots.launch.txt` over `robots.txt`, and refreshes sitemap lastmod dates. It does not commit, push, or submit the sitemap. Review the diff, then commit and push this repository so GitHub Pages updates.

Do not point `data-checkout-url` at a test-mode checkout on this public site. A PNG `og:image` is already in place. Replace the GitHub Issues support contact with a real seller support email only when one has been chosen. Do not invent an address.
