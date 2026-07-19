# Small Things Farm — smallthingsfarm.com

Pre-launch marketing site for **Small Things Farm**, a family market garden near
Columbus, Ohio, breaking ground in 2027. Plain HTML/CSS — no build step, no framework.

## Pages

| File | Page |
|---|---|
| `index.html` | Home — hero, promises, what we'll grow, road to harvest |
| `csa.html` | CSA shares — estimated pricing, how it works, reservations (not yet open) |
| `about.html` | Our story — why we're leaving tech for the farm |
| `contact.html` | Contact — email + Saturday market info |
| `styles.css` | Shared stylesheet (design tokens + all components) |
| `404.html` | Not-found page |

`design_handoff_smallthingsfarm_site/` is the original design handoff (option 1C,
"The Roadside Stand", is the implemented layout). It is kept for reference only and
is not part of the deployed site.

## Brand (July 2026 identity)

The site follows the **Brand & Identity Guide v1.0** (July 2026). Key facts:

- **Palette** — Forest `#2E3C23` (primary ink & ground), Sage `#737C60`,
  Cream `#F3E9D9` (paper), Ochre `#9B6223` (accent/CTAs, never a field color),
  Bark `#4D361D`, Gold `#B0813B` (ochre lifted for dark grounds).
- **Type** — Cormorant Garamond SemiBold for display (always ALL CAPS, tracked);
  Source Serif 4 for body and utility caps (fallback Georgia). Loaded from
  Google Fonts.
- **Tagline** — `THE SMALL THINGS MATTER.` — always caps, always with the period.
  Ochre on light grounds, gold on dark.
- **Logo kit** — `assets/brand/` holds the outlined production SVGs
  (logos, icons, lockups). The site header is the full-width
  `lockups/banner-lockup.svg` (badge + name + tagline, on Forest) with the
  nav menu centered beneath it. `04-horizontal-wordmark-cream.svg` is a
  recolor of the wordmark (forest→cream, ochre→gold) kept for other
  dark-ground uses. The favicon is `icons/icon-sprout.svg` (the circular
  roundel marks are unused on the site by request; the files remain in
  `assets/brand/` for print/packaging).
  Full kit incl. editable text + Cormorant Garamond TTFs lives in the
  downloaded `Small-Things-Farm-Logo-Kit.zip` (not committed).

## Deployment (GitHub Pages + Porkbun)

1. **GitHub Pages** — in the repo: *Settings → Pages → Build and deployment*,
   set Source to "Deploy from a branch", branch `main`, folder `/ (root)`.
   > Note: Pages on a **private** repo requires a paid GitHub plan (Pro or higher).
   > On the free plan the repo must be public.
2. **Custom domain** — the `CNAME` file in this repo already contains
   `smallthingsfarm.com`. In *Settings → Pages*, the custom domain field should
   show `smallthingsfarm.com` once DNS resolves.
3. **Porkbun DNS** (porkbun.com → Domain Management → smallthingsfarm.com → DNS Records).
   Delete Porkbun's default parked-page ALIAS/CNAME records first, then add:

   | Type | Host | Answer |
   |---|---|---|
   | A | *(leave blank — apex)* | `185.199.108.153` |
   | A | *(leave blank — apex)* | `185.199.109.153` |
   | A | *(leave blank — apex)* | `185.199.110.153` |
   | A | *(leave blank — apex)* | `185.199.111.153` |
   | CNAME | `www` | `justaveragematt.github.io` |

4. **HTTPS** — once DNS has propagated and the certificate is issued (minutes to
   a few hours), check **Enforce HTTPS** in *Settings → Pages*.

## Email signup (currently removed)

The email signup forms have been removed until a newsletter service is chosen.
The styles (`.signup-form`, `.signup-band`, `.form-note`) are still in `styles.css`,
and HTML comments mark where the forms belonged (hero on `index.html`, a
`signup-band` section above the footer on `about.html` / `contact.html`).

To restore with Buttondown:

1. Create a free account at [buttondown.com](https://buttondown.com) (free up to 100 subscribers).
2. Re-add the form markup at the commented spots:

   ```html
   <form class="signup-form" action="https://buttondown.com/api/emails/embed-subscribe/USERNAME" method="post">
     <input type="email" name="email" required placeholder="your@email.com" aria-label="Email address">
     <button type="submit">Follow along</button>
   </form>
   ```

3. Replace `USERNAME` with your Buttondown username. On submit, subscribers land on
   Buttondown's "check your email to confirm" page — that's the success state.

(Prefer Formspree? Use your Formspree endpoint as the form `action` instead.)

## CSA reservations (Tally) — not yet open

`csa.html` shows estimated share pricing and states that orders will be accepted
once the farm is running at full capacity. When you're ready to open a **capped**
reservation list:

1. Create a free account at [tally.so](https://tally.so) and make a form with
   fields: name, email, share size (Small / Family).
2. In the form's **Settings → Close form**, set **Submission limit** to the number
   of shares available, and write a custom closed message (e.g. "All shares are
   spoken for this season — email us to join the waitlist."). Tally closes the
   form automatically once the limit is reached.
3. In `csa.html`, find the `TODO` comment in the reservations section and replace
   the paragraph with the `<a class="button-link" href="https://tally.so/r/YOUR_FORM_ID">Reserve a share</a>`
   link (the `.button-link` style is already in `styles.css`).

Estimated pricing context (researched July 2026): nearby NW-Ohio CSAs charge
~$28–35/week for a 6–8 item box (The Farm on Central $27.95, Shared Legacy $33,
Riehm small $35); Columbus-area farms run ~$32–54/week across sizes (eQuality
$585 full season, New Century small→large). The page's $30/wk small and $45/wk
family estimates sit inside both bands.

## Swap in real photos

Two placeholder frames are marked with HTML comments:

- `index.html` — hero frame (portrait, ~340×420): currently shows "Breaking Ground in 2027"
- `about.html` — land photo (~380×300)

Each comment shows the exact `<img>` tag to paste in place of the `<svg>` block.
Put photos in an `images/` folder.
