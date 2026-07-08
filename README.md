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

1. **Formspree** (Book a Demo form): create a free account at [formspree.io](https://formspree.io),
   create a form pointed at `info@showtimehorses.co.za`, and replace `YOUR_FORM_ID`
   in `index.html` with the real form ID.
2. **Email forwarding**: at domains.co.za, forward `info@showtimehorses.co.za`
   to a real inbox — the site and privacy policy both use it.
3. **DNS at domains.co.za** (Manage Domain → DNS):
   - Four `A` records on the apex (`@`): `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153`, `185.199.111.153`
   - `CNAME` record: `www` → `james-gooch-git.github.io`
4. In the GitHub repo: Settings → Pages → confirm custom domain `showtimehorses.co.za`
   and tick **Enforce HTTPS** once the DNS check passes.
