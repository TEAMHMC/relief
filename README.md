# RELIEF

Standalone site for Health Matters Clinic's disaster relief work.

Live at https://relief.healthmatters.clinic

## Structure

    index.html                         the page
    assets/css/hmc-parallax.css        shared parallax and reveal layer
    assets/js/vendor/                  GSAP, ScrollTrigger, Lenis (vendored, not CDN)
    assets/js/hmc-immersive.js         scroll layer: reveals, count-ups, parallax
    assets/js/hmc-parallax.js          lightweight layer: kinetic marquee
    assets/site/hmc-buttons-1.0.3.*    shared HMC button system

`assets/` is shared byte for byte with the other HMC program sites. Do not fork it
here. If the shared layer changes, copy the whole folder across so every site stays
in step.

## Deploy

GitHub Actions. `.github/workflows/deploy.yml` uploads the repo root as the Pages
artifact on every push to main. Do not switch to "deploy from a branch"; every other
HMC site uses Actions and this matches.

DNS: `relief` CNAME to `teamhmc.github.io`, set to DNS only in Cloudflare (grey
cloud). Proxying through the orange cloud commonly breaks Pages TLS issuance.

## Editing copy

Every figure on this page comes from HMC's published L.A. Wildfire Relief Response
impact report covering the January 18, 2025 distribution day. Nothing is estimated,
extrapolated, or rounded. If you change a number, change it to match the report.

One accuracy note that matters: Health Matters Clinic participated in and attended
the Cal OES Regional Disaster Ready Summit for Los Angeles County in September 2023.
The page must not describe that as training, certification, credentialing, or a
partnership, because it was none of those. The FAQ states this plainly and should
stay.

House style: no em dashes, no emojis, no invented figures, quotes, partner names, or
outcomes. No claim of SOC 2 or HIPAA certification.

## Photography

There is no photography in this repository yet. Two `.photoband.placeholder` bands
are marked with a dashed border and a visible label so they are not mistaken for
finished design, and the hero carousel runs tonal gradient panels rather than images.

Any photograph added here needs a signed media release for anyone identifiable, must
not identify a recipient's household, address, or vehicle plate, and must come from
this program rather than another HMC program.

## Animation hooks

Driven by `hmc-immersive.js`, unmodified:

- `[data-reveal]` scroll reveal
- `.impact-num` count-up. The regex only matches `^\d+%?$`, so anything with a comma
  or a decimal has to be split. `1,540` is marked up as a literal `1,` followed by
  `<span class="impact-num">540</span>` so the count-up fires and the rendered value
  stays exact.
- `.hero-slide` carousel, 4 slides on a 5500ms cycle with Ken Burns
- `.hmc-kinetic-row` marquee

The immersive layer disables itself under `prefers-reduced-motion`, when GSAP is
missing, and when the page is inside an iframe. The ranked bars run on a separate
IntersectionObserver so they still animate in the iframe case.

## Buttons

Use `hmc-btn` plus `hmc-btn-primary` or `hmc-btn-secondary`, and set `data-hmc-label`
to exactly the same text as the label. The 1.0.3 CSS builds the roll-up from that
attribute. Do not load `hmc-buttons-1.0.0.js`: it wraps text nodes for the older CSS
and renders every label twice.
