# showtimehorses.co.za

Marketing site for **Showtime** — South African equestrian event management app.
Hosted on **GitHub Pages** with the custom domain `showtimehorses.co.za`.

## Structure

- `index.html` — the whole site (self-contained, no build step)
- `privacy.html` — privacy policy (also linked from the App Store listing)
- `CNAME` — tells GitHub Pages which custom domain to serve

## How to update

Edit `index.html`, commit, and push to `main`. GitHub Pages redeploys automatically
within a minute or two.

## Outstanding setup (one-time)

1. ~~Formspree~~ — done: the demo form posts to `https://formspree.io/f/xlgyyjrn`
   (AJAX with inline success, plain-POST fallback). Manage it in the Formspree dashboard.
2. **Email forwarding**: Cloudflare dashboard → Email → Email Routing — confirm
   `info@showtimehorses.co.za` forwards to a real inbox. The site and privacy policy both use it.

## DNS / TLS architecture (done 2026-07-08)

DNS lives at **Cloudflare** (NOT domains.co.za — that's registrar only). The zone has
four apex `A` records (`185.199.108–111.153`) and `CNAME www → james-gooch-git.github.io`,
all **Proxied (orange cloud)**: Cloudflare terminates TLS with its own certificate and
edge-caches (including Johannesburg/Cape Town), with GitHub Pages as origin.

Consequences of the proxied setup:
- Cloudflare SSL mode must stay **Full** (Flexible risks redirect loops; Full (strict)
  breaks — GitHub holds no cert for this domain while proxied).
- **Always Use HTTPS** should be On in Cloudflare; GitHub's "Enforce HTTPS" checkbox
  is irrelevant and its cert provisioning never completes — expected.
- Pushed changes can take up to ~10 min to appear (edge cache, `max-age=600`);
  purge cache in Cloudflare to see them immediately.
