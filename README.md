# RELIEF: Disaster Relief

Standalone site for Health Matters Clinic's disaster relief work, built on the same
design system and animation layer as TEAMHMC/SMO and TEAMHMC/MHO so behaviour is
identical across HMC surfaces.

Live target: https://relief.healthmatters.clinic (GitHub Pages, see CNAME)

## Structure

    index.html                         the page
    assets/css/hmc-parallax.css        shared parallax + reveal layer
    assets/js/vendor/                  GSAP, ScrollTrigger, Lenis (vendored, not CDN)
    assets/js/hmc-immersive.js         scroll layer: reveals, count-ups, parallax
    assets/js/hmc-parallax.js          lightweight layer: kinetic marquee
    assets/site/hmc-buttons-1.0.3.*    shared HMC button system

`assets/` is copied byte for byte from SMO and verified with `diff -r`. Do not fork it
here. If the shared layer changes, copy the whole folder across again so all three
sites stay in step.

There is no `photos/` directory. That is deliberate. See "Photography needed" below.

## Deploy

GitHub Actions, same workflow as SMO, MHO and Unstoppable:
`.github/workflows/deploy.yml` uploads the repo root as the Pages artifact on every
push to main. Do not switch to "deploy from a branch"; every other HMC site uses
Actions and this matches.

DNS: `relief` CNAME to `teamhmc.github.io`, set to **DNS only** in Cloudflare (grey
cloud), matching `smo`, `mho` and `unstoppable`. Cloudflare will warn that this
exposes the origin IP. That IP is GitHub's shared infrastructure, not an HMC server,
so the warning does not apply. Proxying through the orange cloud commonly breaks
Pages TLS issuance.

## The wording rule, read before editing any copy

Health Matters Clinic **participated in** and **attended** the Cal OES Regional
Disaster Ready Summit for Los Angeles County in September 2023, at the Skirball
Cultural Center. That is the entirety of the relationship.

The page must never say, and does not say, that HMC was **trained by Cal OES**,
**certified**, **credentialed**, **partnered with Cal OES**, or that **Cal OES
trained us**. Overstating a relationship with a state agency is the single change
that would discredit this page. The word *prepared* is fine and is used.

The FAQ carries an explicit disclaimer of any Cal OES certification or partnership,
and the summit fact panel repeats it. Keep both.

## Source of every figure

All counts and percentages come from the **L.A. Wildfire Relief Response impact
report** (`LAWR Report.pdf`), published by HMC and covering the January 18, 2025
distribution day. The report was read in full and every figure below was confirmed
against it. Nothing on the page is estimated, extrapolated or rounded up.

The Cal OES summit details (September 2023, Skirball Cultural Center, one of eight
statewide summits, the convened audience, the stated objectives) are **not** in the
impact report. They come from the summit's own materials and were supplied verified.
If that framing is ever challenged, the summit materials are the citation, not the
impact report.

| Figure | Section |
| --- | --- |
| 198 volunteers; 1,540 service hours; 120 individuals and families | Hero stat row |
| September 2023 summit; sixteen month gap; January 18 2025 deployment | We prepared before it happened |
| 120 assisted, 198 volunteers, 1,540 hours, 36 partner organizations, 980 items, 16 deliveries | One day, by the numbers (six `.impact-num` stat cards) |
| Baby wipes 89.66%, disinfectant wipes 86.21%, cleaning supplies 86.21%, bottled water 82.76%, toilet paper 79.31%, feminine hygiene 75.86%, paper towels 72.41%, deodorant 68.97%, pillows 68.97%, toys 65.52%, children's clothing and shoes 65.52%, diapers 65.52% | What people actually asked for, panel 1 |
| Soap/shampoo/toothpaste/toothbrushes 65.52%, luggage or duffel bags 62.07%, blankets 58.62%, towels 58.62%, women's clothing 55.17%, nonperishable food 51.72%, pet food and supplies 44.83%, backpacks 41.38%, school supplies 37.93%, men's clothing 34.48%, baby formula 31.03% | What people actually asked for, panel 2 |
| n = 29 survey participants | Stated in the section lede and in the FAQ |
| 78 households; 36 organizations; 16 deliveries; 8:00 AM to 8:00 PM; in-kind over $200,000 | How it worked |
| Hygiene kits 280+, PPE 285+, clothing and blankets 700+, baby and child essentials 3,000+, hot meal vouchers 25, gift cards 20+ | How it worked, "What was donated" |
| Partner organization names | How it worked, partner panel |

### Figures checked against the source, and the result

Every figure in the brief matched the PDF exactly. Nothing was contradicted.

Three additional ranked items appear in the PDF that were not in the brief, and are
included on the page because they are sourced: **blankets 58.62%**, **towels 58.62%**,
**luggage or duffel bags 62.07%**.

One nuance worth preserving. The PDF's own headline reads "80%+ of respondents
requested" and lists four items: baby wipes, disinfectant wipes, cleaning supplies,
bottled water. Its body text then says "response rates above 80%" while listing seven
items, three of which are below 80 percent (toilet paper 79.31, feminine hygiene
75.86, paper towels 72.41). The page follows the accurate reading: only the top four
are described as above 80 percent, and only those four get the blue bar treatment.

### Deliberately not on the page

The PDF contains a named individual's personal hardship account (a mother in Malibu)
and a survivor quotation. The hardship account is not reproduced, because a named
family's financial circumstances do not belong on a public marketing page. Two
anonymous quotations are used, both verbatim from the PDF and both attributed only by
role: "Community partner organization" and "Volunteer".

No participation counts appear in the Recovery continues section. None are published
for that work, so the section describes what is on offer and nothing more.

## Photography needed

**There is no wildfire response photography in this repository.** SMO's Skid Row
photography and MHO's event photography were deliberately not reused: presenting a
street medicine run or a park health fair as a disaster response would misrepresent
both programs and the event itself. Text-only and clearly-marked empty bands are the
correct interim state.

Two `.photoband.placeholder` bands are in place, styled like SMO's photo bands but
with a dashed border, a hatched fill and a "Photography needed" label so nobody
mistakes them for finished design.

The hero carousel runs four `.hero-slide` panels filled with dark tonal gradients
(`.hs-1` to `.hs-4`) rather than images, so the 5500ms cycle, the Ken Burns keyframe
and the grain overlay all behave exactly as on SMO and MHO. They are abstract on
purpose; they do not imitate photographs.

### Shot list, in priority order

1. **Hero, four frames.** Landscape, at least 2000px wide, with room at the bottom
   for the headline scrim. Wide establishing shots of the distribution day: the site
   as a whole, the supply staging area, a delivery vehicle being loaded, the
   volunteer line. Replace the four `.hs-*` gradient classes with
   `background-image:url('./photos/relief-hero-1.jpg')` and so on.
2. **Distribution day, wide establishing shot.** Fills the first placeholder band,
   directly after the preparedness section. This is the single most valuable image
   on the page because it is the proof of the whole argument.
3. **Sorting and staging, volunteers at work.** Fills the second placeholder band,
   after the operations section. Hands, boxes, pallets, clipboards. A working shot,
   not a posed group shot.
4. **A delivery in progress.** Sixteen deliveries were the part of the operation that
   reached homebound residents, and there is currently no image of it at all.
5. **The hygiene and cleaning supply tables.** The page argues that hygiene outranked
   food. A photograph of what that actually looked like on the tables would do real
   work for that argument.

### Constraints on any photograph added here

- Anyone identifiable needs a signed media release on file before publication.
- Do not photograph or publish images that identify a relief recipient's household,
  address, or vehicle plate.
- No image from any other HMC program may be used on this page, even temporarily.
- No stock wildfire imagery. A generic burning-hillside stock photo would imply HMC
  documented the fire itself, which it did not.

## Animation hooks

Driven by `hmc-immersive.js`, unmodified:

- `[data-reveal]` scroll reveal
- `.impact-num` count-up. The regex only matches `^\d+%?$`, so anything with a comma
  or a decimal is split. `1,540` is marked up as a literal `1,` followed by
  `<span class="impact-num">540</span>`, so the count-up fires and the final rendered
  value is exact. The other five headline figures are plain integers and animate whole.
- `.hero-slide` hero carousel, 4 slides on a 5500ms cycle with Ken Burns
- `.hero-grain` SVG turbulence overlay at .055 opacity
- `.hmc-kinetic-row` marquee
- Hero is `min-height:100vh; height:100svh`

The immersive layer disables itself under `prefers-reduced-motion`, when GSAP is
missing, and when the page is inside an iframe. That last case matters: if this page
is ever embedded in Webflow the animations will not run, exactly as with SMO and MHO.
The ranked bars are driven by a separate IntersectionObserver so they still animate in
the iframe case.

`blockquote` margin is reset to 0 because the two quote cards are `<blockquote>`
elements inside the stat grid.

## Buttons

Use `hmc-btn` plus `hmc-btn-primary` or `hmc-btn-secondary`, and set `data-hmc-label`
to exactly the same text as the label. The 1.0.3 CSS builds the roll-up from that
attribute. `hmc-buttons-1.0.3.js` is loaded, matching SMO and MHO. Do **not** load
`hmc-buttons-1.0.0.js`: it wraps text nodes for the older 1.0.0 CSS and renders every
label twice.

## Copy rules

No em dashes. No emojis. No generic AI phrasing. No invented figure, quote, partner
name or outcome. No claim of SOC 2 or HIPAA certification. Partner organizations are
named only because the impact report names them.

## Open items

- The impact report is not linked for download from the page. If a public-facing
  version is cleared for publication, add a `reports/` directory and a card in the
  same style as SMO's reports grid.
- No video exists for this program. SMO carries a testimony video; if relief footage
  is ever cut, the `.testimony` block from SMO can be lifted directly.
- The Cal OES summit has no citable public URL captured in this repo. Adding one to
  the summit fact panel would strengthen the page's central claim.
