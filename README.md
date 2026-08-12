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

Two accuracy notes that matter.

Cal OES is the California Governor's Office of Emergency Services, a state agency. It
invited Health Matters Clinic to participate in its Regional Disaster Ready Summit for
Los Angeles County on September 27, 2023, at the Skirball Cultural Center, one of eight
summits held statewide that month. Source: https://news.caloes.ca.gov/ready-summits/
The page may say invited, attended, and participated. It must not describe that as
training, certification, credentialing, or a partnership, because it was none of those.
The FAQ states this plainly and should stay.

HMC was founded in 2020 and its earliest community work was disaster response in
substance: COVID-19 testing, vaccinations, health screenings, mental health support, and
access to digital devices. Do not upgrade that into a claim that HMC was a designated or
official disaster responder in 2020. It was not.

House style: no em dashes, no emojis, no invented figures, quotes, partner names, or
outcomes. No claim of SOC 2 or HIPAA certification.

## Photography

`photos/` holds seven frames from the January 18, 2025 distribution day. All are phone
portrait 3:4 at 1500x2000, each under 400KB. The hero carousel uses four of them as
`background-size:cover` slides; all seven run as `.pfig` figures in two `.photogrid`
blocks.

Cover-cropping a 3:4 frame into a wide band shows only the middle band of the image and
has already cost us the tops of people's heads once. So the hero slides are limited to
frames whose subject is staged supply, with `background-position` set below the point
where anyone appears, and every frame containing volunteers runs uncropped as a figure at
its natural aspect ratio. If you add a photograph with a person near an edge, it goes in
a `.photogrid`, never in the hero.

Any photograph added here needs a signed media release for anyone identifiable, must
not identify a recipient's household, address, or vehicle plate, and must come from
this program rather than another HMC program. Write the caption from what is actually in
the frame. Do not guess.

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
