# Small Things Farm — smallthingsfarm.com

Pre-launch marketing site for **Small Things Farm**, a family market garden near
Columbus, Ohio, breaking ground in 2027. Plain HTML/CSS — no build step, no framework.

## Pages

| File | Page |
|---|---|
| `index.html` | Home — hero, promises, what we'll grow, road to harvest |
| `about.html` | Our story — why we're leaving tech for the farm |
| `contact.html` | Contact — email + Saturday market info |
| `styles.css` | Shared stylesheet (design tokens + all components) |
| `404.html` | Not-found page |

`design_handoff_smallthingsfarm_site/` is the original design handoff (option 1C,
"The Roadside Stand", is the implemented design). It is kept for reference only and
is not part of the deployed site.

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

## Swap in real photos

Two placeholder frames are marked with HTML comments:

- `index.html` — hero frame (portrait, ~340×420): currently shows "Breaking Ground in 2027"
- `about.html` — land photo (~380×300)

Each comment shows the exact `<img>` tag to paste in place of the `<svg>` block.
Put photos in an `images/` folder.
