# Coral Olson Photography

A clean, minimal photography portfolio website for Coral Olson, built with static HTML/CSS and hosted at [coralolsonphotography.com](https://www.coralolsonphotography.com).

---

## Site Structure

```
/
├── index.html                ← Home — hero carousel (currently disabled), philosophy, testimonials, Instagram grid
├── projects.html             ← Portfolio — 2-column tile grid linking to each gallery
├── portraits.html            ← Portraits gallery (3-column masonry)
├── engagement.html           ← Engagements gallery (3-column masonry)
├── family.html                ← Family gallery (3 explicit flex columns)
├── about.html                 ← About page — framed photo + bio, "My Hobbies" panel (commented out)
├── contact.html               ← Contact form (Formspree) with hero background
├── PricingGuide.html          ← Investment / pricing page
├── assets/                    ← All images (photos, favicon, decorative frame PNGs)
├── css/
│   └── styles.css             ← Legacy shared styles (still linked by about.html/PricingGuide.html/index.html)
└── js/
    └── scripts.js             ← Legacy shared JS
```

---

## Pages Overview

### Home (`index.html`)
- Static navbar with the site logo pinned to the top-left corner
- Hero image carousel (Bootstrap) — **currently commented out** in the HTML; re-enable by removing the wrapping comment around the "HERO CAROUSEL" section
- Philosophy section with offset stacked photos
- Selected Works 3-column grid
- Testimonials section — swipeable carousel (3 per page on desktop, 1 on mobile) with ← → arrows, page dots / page count, and autoplay (30s desktop, 10s mobile) with a progress bar and pause button
- Instagram grid (6 photos) + social links
- Footer with nav links

### Portfolio (`projects.html`)
- Off-white hero panel with "My Portfolio" heading and description
- 2-column image grid — each tile links to a gallery page with a centered category label
- "You May Be Interested" section with links to Contact, About, Investment
- Third tile (Family) auto-centers below the first two

### Gallery Pages
All three gallery pages share the same design language and are fully static (no external image API):
- Centered nav link list with the logo pinned to the left corner and a decorative seashell pinned to the right
- Off-white hero banner with page title in wide-tracked uppercase
- Photo grid (masonry layout), hardcoded `<img>` tags in `/assets`
- "Book a Session" dark CTA button
- Instagram footer + copyright

| Page | Layout | Notes |
|---|---|---|
| `portraits.html` | CSS `column-count: 3` masonry, 8px gaps | |
| `engagement.html` | CSS `column-count: 3` masonry, 12px gaps | Rounded corners + subtle hover zoom on each photo |
| `family.html` | 3 explicit flex columns (4 / 3 / 3 split), 8px gaps | |

### About (`about.html`)
- Nav + logo, same pattern as the gallery pages
- **Meet Your Photographer section:** a photo of Coral holding her camera (`assets/coralbeach-framed1.png`) sits inside an ornate frame graphic, to the left of her bio text. That image is pre-composited (cropped + overlaid onto the frame PNG using Python/Pillow, not a live CSS layering trick) — see `assets/frame1.png` through `frame8.png` for other available frame styles. Stacks vertically on mobile.
- The section's background is a repeating vertical coral (`#FFB3AE`) / white stripe pattern that runs continuously down to where the Instagram footer begins.
- **"My Hobbies" section is currently commented out** (its text was merged into the Meet Your Photographer panel as a second paragraph instead) — uncomment the `<section class="about-panel waves" ...>` block to bring it back as its own panel.
- Two decorative panel backgrounds, `shell1.jpg` and `beach.jpg`, use `background-size: cover` with a `min-height` set on the panel so the photo isn't cropped down to a thin sliver on wide/short sections — adjust `min-height` first if you swap in a different photo and it looks over-cropped.

### Contact (`contact.html`)
- Full-height hero with background image and overlaid nav
- Off-white form panel floating below the hero
- Fields: Name, Email, Phone, Session Type (dropdown), Date
- Powered by [Formspree](https://formspree.io) — form action: `https://formspree.io/f/mnnzoqjz`
- Client-side validation: requires at least email or phone

---

## Typography & Design

| Element | Font |
|---|---|
| Headings, nav links, brand/logo text | 'Black Mango' (self-hosted, `fonts/Black Mango Regular.ttf`) |
| Body text | Montserrat (weight 300–400), loaded on most pages. `index.html` currently loads Josefin Sans instead — a leftover inconsistency from an earlier pass, not intentional. |

**Colour palette:**

| Use | Value |
|---|---|
| Page background (about/contact-style pages) | `#ffc24b` (mustard/orange) |
| Page background (home/gallery pages) | `#fff` |
| Teal (links, footer bar, accents) | `#1697a6` |
| Coral (hover states, Instagram handle text) | `#F47068` |
| Coral-pink divider lines (nav border, panel dividers) | `#FFB3AE` |
| Cream panels / Instagram footer | `#FFF4F1` |

---

## Design Conventions

- **Nav:** a single centered link list, with the site logo pinned to the navbar's top-left corner and a decorative seashell pinned to the top-right. Mobile collapses to a hamburger dropdown (the seashell hides at that breakpoint so it doesn't collide with the hamburger button; the logo stays visible).
- **Gallery gaps:** 8px between masonry items (12px on `engagement.html`, which also has hover zoom + rounded corners)
- **Image protection:** Right-click disabled, drag disabled, copy/paste disabled, long-press guard on mobile
- **No Bootstrap** on gallery/portfolio/about pages — all custom CSS. Bootstrap is only used on `index.html` for the hero carousel (currently disabled, see above).

---

## Deployment

Hosted on **GitHub Pages** with a custom domain.

1. Push changes to the `main` branch
2. GitHub Pages auto-deploys within ~1 minute
3. Custom domain configured via CNAME → `coralolsonphotography.com`

**Active branch for production:** `main`

---

## Maintenance

| Task | Notes |
|---|---|
| Add/replace photos | Upload the file to `/assets`, then add or update the `<img src="assets/...">` in the relevant page |
| Update contact form | Change Formspree endpoint in `contact.html` |
| Update copyright year | Search for `Coral Olson 2025` across all files |
| Add a new gallery | Create a new HTML page modelled on `family.html`, add a tile to `projects.html` |
| Re-crop the About page's framed photo | Crop/composite with Pillow (PIL) — see conversation history or recreate: crop the source photo, resize to the frame PNG's transparent window, `Image.alpha_composite()` the frame on top |
