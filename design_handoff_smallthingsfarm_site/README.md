# Handoff: smallthingsfarm.com — "Roadside Stand" launch site

## Overview
A pre-launch marketing site for **Small Things Farm**, a family market garden near Columbus, Ohio, breaking ground in 2027. The site announces the farm ("Breaking ground in 2027"), tells the family's story of leaving tech behind, previews what they'll grow, shows the roadmap to first harvest, and collects email signups.

**Target: a static site deployed to GitHub Pages** with the custom domain `smallthingsfarm.com` (purchased via Porkbun). No backend, no build framework required — plain HTML/CSS is the preferred implementation. Do NOT introduce React/Next/etc. unless the user asks.

## About the Design Files
`Homepage Options.dc.html` is a **design reference created in HTML** (open it in a browser with `support.js` alongside). It shows three homepage options; **the user chose Option 1C — "The Roadside Stand"** (the third card, `id="1c"`, labeled "1C · THE ROADSIDE STAND"). Ignore options 1A and 1B except as supplementary reference.

Your task: recreate option 1C as a real multi-page static site. All styles in the reference are inline `style="…"` attributes — extract them into a shared stylesheet. The reference is desktop-only (1200px card); you must add responsive behavior (see below).

## Fidelity
**High-fidelity.** Colors, typography, spacing, and copy in option 1C are final unless noted. Recreate pixel-faithfully at desktop width, then adapt responsively.

## Site Structure
Three pages sharing nav + footer:

1. **`index.html` (Home)** — implement option 1C exactly:
   - Dark-green hero band (`#333f2a`): nav, "BREAKING GROUND IN 2027" badge, headline "The small things make a big difference.", intro paragraph, inline email signup, photo placeholder (340×420)
   - Three promise cards: "Small beds, big care" / "Saturday-fresh" / "No hustle here"
   - Two-column band: "What we'll grow" (chip list + honey chip) and "From here to harvest" (4-step timeline)
   - Dark footer (`#23201a`)
2. **`about.html` (About)** — expand the story using the same visual system. Content direction: the family is leaving tech and the always-on "new normal" to focus on the small things that make a big difference; small beds tended by hand; growing only as fast as they can do it well. Reuse the tone/copy in the reference (see also option 1B's "Why we're doing this" prose for voice). Include a photo placeholder for a family/land photo.
3. **`contact.html` (Contact)** — simple page: email `hello@smallthingsfarm.com`, "find us at a Saturday market near Columbus starting summer 2027", and the email signup block again.

Nav links: Home / About / Contact. Active page link is `#f5efe4` weight 600; inactive `#c9cfae`.

## Design Tokens
Colors:
- Ink (text, footer bg): `#23201a`
- Paper (page bg): `#f5efe4`
- Card bg: `#fffdf7`
- Hero / dark green: `#333f2a`; sage green: `#47563a`
- Hero body text: `#dfe3cf`; hero muted: `#9aa384`; nav inactive / accents on green: `#c9cfae`
- Clay (primary CTA): `#a95a37`, hover `#8a4526` (also link color)
- Ochre: `#a9792b`; slate-blue: `#4d6870`
- Body secondary text: `#574f42`; muted: `#8c8274`; hairline borders: `#dccfba`
- Badge bg on green hero: `#e7e7d3`

Typography (Google Fonts):
- **Spectral** (serif) — headlines & display. H1: 88px/1.0, weight 700, letter-spacing -0.02em (scale down responsively). Card titles 21px/600. Section H2: 32px/700.
- **IBM Plex Sans** — UI: nav, buttons, labels, chips. Labels: 10–12px, uppercase, letter-spacing .1–.28em, weight 600.
- **IBM Plex Mono** — eyebrows, badges, timeline dates, form inputs, small annotations. 11–12px.
- Body: Spectral 13.5–18px, line-height 1.6, color `#574f42`.

Other: **no border-radius anywhere** (sharp corners are intentional; only the 34px round "st" logo mark is circular). Buttons/inputs: 1.5px solid borders where bordered. No shadows except the option-card frame (don't reproduce that — it's presentation chrome).

## Interactions & Behavior
- Links/buttons: hover darkens (CTA `#a95a37 → #8a4526`; footer/nav links lighten to `#f5efe4`)
- **Email signup**: static hosting can't process forms. Wire to a free form/newsletter service — Buttondown (`<form action="https://buttondown.com/api/emails/embed-subscribe/USERNAME" method="post">`) or Formspree. Leave a clearly-marked TODO with the placeholder action URL and tell the user how to finish setup. Show a simple success state (redirect or inline message).
- Photo placeholders: keep as styled placeholder blocks (`<img>`-ready) with alt text; user will supply real photos.
- Smooth-scroll not required; no JS needed beyond (optionally) a mobile nav toggle.

## Responsive
Reference is 1200px desktop. Required breakpoints:
- ≤900px: hero grid stacks (text above photo), promise cards stack to 1 column, two-column band stacks, H1 down to ~48–56px
- ≤600px: paddings 60px → 24px, nav can collapse to a simple stacked/inline list (a hamburger is optional)

## Deployment (include as README in the repo)
1. Repo with `index.html` at root (or `/docs`), GitHub Pages enabled
2. Add `CNAME` file containing `smallthingsfarm.com`
3. Porkbun DNS: A records for apex → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`; CNAME `www` → `USERNAME.github.io`
4. Enable "Enforce HTTPS" in Pages settings once the cert issues

## Assets
- Google Fonts: Spectral (300–800 + italics), IBM Plex Sans (400–700), IBM Plex Mono (400–600)
- No images yet — placeholders only. Two slots: hero photo (~340×420, "the two of us, boots on, on the land") and an About-page land photo.

## Files in this bundle
- `Homepage Options.dc.html` — design reference (option **1C** is the chosen design)
- `support.js` — runtime needed to open the reference file in a browser (keep next to the HTML)
