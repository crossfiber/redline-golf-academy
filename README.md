# Redline Golf Academy v3

Single-file rebuild of redlinegolfacademy.com. Lives in this repo so the production Netlify site (served from `crossfiber/hogan-elite-golf`) stays untouched until Ryan approves.

## Live preview
- GitHub Pages: https://crossfiber.github.io/redline-golf-academy/ (enable in repo settings → Pages → main branch)
- Production (untouched): https://redlinegolfacademy.com (still served from `hogan-elite-golf` repo via Netlify)

## What's different from v2.29

Built against the v5 master prompt with the audit findings from May 4 baked in:

- Solid navy nav from page load, no transparent-then-solid
- Real photos of Ryan throughout (5 from the Bold Vision Productions gallery): hero, coach portrait, methodology, science, FAQ
- Hero is photo-led with `+8 mph by session 3` floating badge over the photo, not a 4-card SaaS feature grid
- Single-sentence woven trust strip, not 3-stat metric cards
- Real street address visible: footer, contact section, JSON-LD
- Google Maps embed in contact section
- og:image meta tags (placeholder pointing to `/assets/og-share.jpg` — needs the actual share card design)
- All description fields synced (meta, og, twitter, JSON-LD)
- Hours match between visible site and JSON-LD (Mon-Fri 6am-7pm, Sat 7am-5pm)
- novalidate form with branded inline error messages
- Featured pricing card uses badge only, NO scale-transform / orphan-card layout
- Section rhythm varies: hero (asymmetric) → trust band → coach (image-left split) → methodology (full-bleed dark) → pricing (3-card grid) → science (image-left split, inverted) → testimonials (horizontal scroll) → FAQ (asymmetric split with side image) → service area band → contact (form left)
- Zero em-dashes anywhere in the file
- Big Shoulders Display + Hanken Grotesk via Google Fonts (no Fontshare)
- Logo never CSS-inverted

## Fonts
- Headlines: Big Shoulders Display (700, 800)
- Body: Hanken Grotesk (400, 500, 600, 700)
- Both loaded from Google Fonts CDN with display=swap

## Color palette (brand-derived, not invented)
- `--navy`: #0B2545 (matches existing brand)
- `--navy-deep`: #061327 (footer, very dark sections)
- `--teal`: #0EA5E9 (CTA accent only - matches existing brand)
- `--cream`: #F7F4EC (warm page background)
- `--cream-mint`: #ECF0E8 (alt section background)
- `--moss`: #2F5135 (limited golf-context accent for coach title)
- `--gold`: #C8A560 (testimonial stars only)

## Tracking carried over from production
- GA4 Measurement ID: G-HWPYKFK6JV (in head)
- Calendly funnel events: `book_session_click` (on CTA click) and `book_session_complete` (on `calendly.event_scheduled` postMessage)
- Google Search Console: was never explicitly verified via meta tag in the production code; if Ryan has GSC verified via DNS or HTML file it will keep working when this is deployed to the same domain

## Calendly integration
Ported 1:1 from production v2.29: persistent iframe, hover-intent prefetch, idle warm-up, branded shell with palette refit. Same event slugs (`single-session-solo`, `single-session-pair`, `three-session-solo`, `three-session-pair`, `monthly-coaching-solo`, `monthly-coaching-pair`).

## Form
Wired to Netlify Forms (form name: `contact`). Will only work once this code is deployed to a Netlify site. Standalone GitHub Pages preview will show form-submit error states. When you cut over to Netlify, point the same site to this repo.

## Placeholders that still need real content
- `[OG SHARE CARD NEEDED]` — `/assets/og-share.jpg` doesn't exist yet. Build a 1200x630 designed share card (logo + "Fort Myers Golf Lessons | +5 to 10 mph in 3 sessions" + photo of Ryan)
- Testimonials are reused from production (kept fabricated set per Ryan's direction). Replace with real Google reviews when available
- Phone number for additional credibility lines (optional)

## Deploy

```bash
git clone https://x-access-token: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@github.com/crossfiber/redline-golf-academy.git
cd redline-golf-academy
# (drop in updated index.html / assets / etc)
git add .
git commit -m "v3 rebuild"
git push origin main
```

Then in GitHub: Settings → Pages → Source: Deploy from a branch → Branch: main / root → Save. Live at `https://crossfiber.github.io/redline-golf-academy/` within ~60 seconds.

## When Ryan approves the rebuild

To cut over so redlinegolfacademy.com serves this build:

1. Either: copy `index.html`, `robots.txt`, `sitemap.xml`, `assets/` into `crossfiber/hogan-elite-golf` and push to main (Netlify auto-deploys to redlinegolfacademy.com).
2. Or: re-point Netlify build settings to this repo (`crossfiber/redline-golf-academy`) instead of `hogan-elite-golf`.
