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

## Finish the email signup (TODO)

The signup forms post to Buttondown but need your account name:

1. Create a free account at [buttondown.com](https://buttondown.com) (free up to 100 subscribers).
2. Your username appears in your Buttondown profile/settings.
3. In `index.html`, `about.html`, and `contact.html`, replace `USERNAME` in
   `action="https://buttondown.com/api/emails/embed-subscribe/USERNAME"`
   with your Buttondown username.
4. On submit, subscribers land on Buttondown's "check your email to confirm" page —
   that's the success state. You can customize it in Buttondown's settings.

(Prefer Formspree? Swap the form `action` for your Formspree endpoint instead —
the markup needs no other changes.)

## Swap in real photos

Two placeholder frames are marked with HTML comments:

- `index.html` — hero frame (portrait, ~340×420): currently shows "Breaking Ground in 2027"
- `about.html` — land photo (~380×300)

Each comment shows the exact `<img>` tag to paste in place of the `<svg>` block.
Put photos in an `images/` folder.
