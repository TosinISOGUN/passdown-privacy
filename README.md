# passdown.isogunlabs.com

The public marketing/docs/privacy/security site for **Passdown — Automated Shift Handoffs for
JSM**. Plain static HTML/CSS/JS, no build step, deployed to GitHub Pages directly from this
repo's `main` branch — same classic Pages pipeline as `recap-privacy` and
`field-hygiene`'s site.

This is a **separate repo** from the app itself
([`passdown-automated-shift-handoffs-for-JSM`](https://github.com/TosinISOGUN/passdown-automated-shift-handoffs-for-JSM)),
tracked independently so the site can deploy and iterate without touching the Forge app's own
history.

## Layout

| Path | What's there |
| --- | --- |
| `index.html` | Homepage — hero, how it works, real-handoff screenshot collage, one-engine-two-jobs, principles, FAQ, CTA |
| `docs.html` | Full documentation, sidebar-navigated |
| `privacy.html` | Privacy policy |
| `security.html` | Security policy, including why this app does not carry the "Runs on Atlassian" badge |
| `assets/css/site.css` | Shared styles — Passdown's own blue-to-teal palette, distinct from Recap's amber |
| `assets/js/site.js` | Nav scroll/drawer behavior, reveal-on-scroll, docs sidebar highlighting — generic, shared pattern across the Isogun Labs site family |
| `assets/img/` | Logo, favicon, and real product screenshots (on-call schedule, on-demand summary, three live automated shift-handoff comments) |
| `CNAME` | `passdown.isogunlabs.com` — required for GitHub Pages' custom-domain routing |
| `robots.txt`, `sitemap.xml` | Standard crawler/SEO plumbing |

## Deploy

Pages source is **Deploy from a branch** (`main`, root) — plain static files, nothing to
build. Push to `main` and it's live within a minute or two. Custom domain is configured in
this repo's **Settings → Pages**, pointed at `passdown.isogunlabs.com`; DNS is a `CNAME`
record (`passdown` → `tosinisogun.github.io`) set at Porkbun, the same pattern as every other
`*.isogunlabs.com` subdomain.

## Local preview

The site uses root-absolute asset paths (`/assets/...`), which is correct once served from
the domain root but **will not resolve if you open `index.html` directly from disk** (`file://`
resolves `/` to your drive root, not this folder). Serve it locally instead, from this
directory:

```
npx serve .
# or
python3 -m http.server 8000
```

## Notes

- Every product screenshot on the homepage is real and unedited — captured from the actual
  Forge app running in a real Jira Service Management site, not staged mockups. See the
  "Real handoffs, unedited" section in `index.html`.
- The Security page states plainly that Passdown does not currently qualify for the "Runs on
  Atlassian" badge, and why — this is a genuine, disclosed difference from Recap and Field
  Hygiene's own sites, not an oversight.
- Slack/Teams push is documented in `docs.html` as **planned**, not shipped — don't reword
  that section to imply it's currently available.
- No Marketplace link yet — the app hasn't been submitted. CTAs point to a `mailto:` "get
  notified" link instead of a real listing URL until that changes.
