# Patterns borrowed from keys-chocolates

Reference: `C:\Users\accc0\Downloads\Builda\keys-chocolates\index.html`

## 1. Mobile drawer (lines 185-254 CSS, 2229-2252 JS)
Right-side slide-in drawer with separate overlay, body scroll lock via `body.style.overflow = 'hidden'`, `body.drawer-open` class hides the bottom hamburger to prevent duplicate close X. Drawer link entrance uses staggered `slideInLeft` keyframes with nth-child animation-delays (lines 219-224).

## 2. Accordion (lines 1114-1145 CSS, 2255-2265 JS)
Single-open behavior: opening one closes others. Pure `max-height: 0` → `max-height: 500px` transition with `overflow: hidden`. Aria-expanded toggled on header. No mixed `display: none` (avoids the Desync Collapse anti-pattern).

## 3. Reviews carousel arrows (lines 2270-2290 JS)
Step calculation reads card width + gap from computed style. Arrow `disabled` state managed by scroll position. Smooth scroll via `scrollBy({behavior: 'smooth'})`. Arrows hide on mobile via media query.

## 4. CSS variable architecture (lines 43-64)
`--nav-h: 84px` custom prop with mobile override `--nav-h: 70px` at 768px. Fed into `scroll-padding-top: calc(var(--nav-h) + 16px)` so anchor links land cleanly. Shadow tokens (`--shadow-soft`, `--shadow-mid`, `--shadow-deep`) for consistent elevation.

## 5. Trust-bar overlap pattern (lines 432-454)
Section sits with `margin-top: -56px` and `position: relative; z-index: 5` to break the hero/section boundary. Stronger than a flat band — creates the section-overlap rule in v5 step 6.

## 6. Form behavior (lines 2114-2144)
`novalidate` on form, `placeholder` text in branded voice not generic. Phone marked optional with inline `(optional)` text — not via missing required attr alone (clearer to user).

## 7. Footer structure (lines 2168-2216)
4-column desktop grid with brand+description+social on left, then 3 link columns (Shop / Visit / Contact). Contact column uses semantic `<address>` with `<strong>` venue label. `footer-bottom` row with copyright on left and a personal "Made with love at..." note on right.

## 8. JSON-LD multi-block pattern (lines 2323-2540)
Separate `Organization` block + per-location `FoodEstablishment` blocks, each with own `address`, `geo`, `openingHoursSpecification`, `aggregateRating`, `paymentAccepted`, `hasMenu`, `knowsAbout`, `areaServed`. For Redline this collapses to single LocalBusiness/SportsActivityLocation but the multi-`@type` array pattern is the takeaway.

## What I did NOT borrow
- Brand colors (chocolate green/pink — completely different brand)
- Fonts (Shrikhand display — wrong tone for athletic premium)
- Headline copy / voice / tone
- Hero composition (interactive map → image swap was specific to keys; my hero is photo-led from the start)
- Signature visual elements (chocolate map, family-shop motifs)
