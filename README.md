# Coral Olson Photography

A clean, minimal photography portfolio website for Coral Olson, built with static HTML/CSS and hosted at [coralolsonphotography.com](https://www.coralolsonphotography.com).

---

## Site Structure

```
/
├── index.html                ← Home — hero carousel, philosophy, testimonials, Instagram grid
├── projects.html             ← Portfolio — 2-column tile grid linking to each gallery
├── marinashoot.html          ← Portraits gallery (3-column masonry)
├── vincentengagment.html     ← Engagements gallery (3-column masonry)
├── family.html               ← Family gallery (3 explicit flex columns)
├── resume.html               ← About page
├── contact.html              ← Contact form (Formspree) with hero background
├── PricingGuide.html         ← Investment / pricing page
├── admin.html                ← Password-protected photo upload admin page
├── assets/                   ← All images (photos, favicon)
├── css/
│   └── styles.css            ← Legacy shared styles (used by some older pages)
└── js/
    └── scripts.js            ← Legacy shared JS
```

---

## Pages Overview

### Home (`index.html`)
- Full-screen hero image carousel (Bootstrap) with overlaid split nav and brand name
- Philosophy section with offset stacked photos
- Selected Works 3-column grid
- Testimonials section — 4 reviews displayed 3 at a time with ← → arrow navigation
- Instagram grid (6 photos) + social links
- Footer with nav links

### Portfolio (`projects.html`)
- Off-white hero panel with "My Portfolio" heading and description
- 2-column image grid — each tile links to a gallery page with a centered category label
- "You May Be Interested" section with links to Contact, About, Investment
- Third tile (Family) auto-centers below the first two

### Gallery Pages
All three gallery pages share the same design language:
- Split nav: links left | "Coral Olson" brand centered | links right
- Off-white hero banner with page title in wide-tracked uppercase
- Photo grid (masonry layout)
- "Book a Session" dark CTA button
- Instagram footer + copyright

| Page | Layout | Cloudinary Tag |
|---|---|---|
| `marinashoot.html` | CSS `column-count: 3` masonry | `portraits` |
| `vincentengagment.html` | CSS `column-count: 3` masonry | `engagements` |
| `family.html` | 3 explicit flex columns (4 / 3 / 3 split) | `family` |

### Contact (`contact.html`)
- Full-height hero with background image and overlaid nav
- Off-white form panel floating below the hero
- Fields: Name, Email, Phone, Session Type (dropdown), Date
- Powered by [Formspree](https://formspree.io) — form action: `https://formspree.io/f/mnnzoqjz`
- Client-side validation: requires at least email or phone

### Admin (`admin.html`)
Password-protected upload page for managing gallery photos.
- Password: stored client-side (change in `admin.html` → `var PASSWORD`)
- Select a gallery (Portraits / Engagements / Family)
- Choose photos from your computer — they are automatically compressed to under 9MB at 90% quality before uploading
- Photos upload directly to Cloudinary tagged with the selected gallery name
- Live per-file status: Compressing → Uploading → Done

---

## Cloudinary Integration

Gallery pages dynamically load photos from Cloudinary at page load.

| Setting | Value |
|---|---|
| Cloud name | `dgqsc76ni` |
| Upload preset | `coral_gallery` (unsigned) |
| Tag list API | `https://res.cloudinary.com/dgqsc76ni/image/list/{tag}.json` |
| Image URL | `https://res.cloudinary.com/dgqsc76ni/image/upload/q_auto,f_auto/{public_id}` |

**How it works:**
- Each gallery page fetches its tag list on load
- If Cloudinary returns images, they replace the static fallback images in the HTML
- If Cloudinary returns empty or errors, the hardcoded static images show instead
- Compression library used: [browser-image-compression](https://github.com/Donaldcwl/browser-image-compression) v2.0.2

**To add photos to a gallery:**
1. Go to `yoursite.com/admin.html`
2. Enter the admin password
3. Select the gallery, choose photos, upload
4. Photos appear on the live site immediately

**To delete photos:**
Log in at [cloudinary.com](https://cloudinary.com) → Media Library → select and delete. Deletion requires the API secret and cannot be done safely from a static page.

---

## Typography & Design

| Element | Font |
|---|---|
| Brand name, headings, hero titles | Cormorant Garamond (weight 300) |
| Nav links, body text, buttons, labels | Montserrat (weight 300–400) |

**Colour palette:**

| Use | Value |
|---|---|
| Page background | `#f9f8f4` (warm off-white) |
| Hero / section panels | `#f2f1ec` |
| Dark buttons / footer | `#1c1c1e` |
| Footer bar | `#111` |

---

## Design Conventions

- **Nav:** Split layout — 3 links left, brand centered, 2 links right. Mobile collapses to hamburger.
- **Gallery gaps:** 8px between masonry items
- **Image protection:** Right-click disabled, drag disabled, copy/paste disabled, long-press guard on mobile
- **No Bootstrap** on gallery/portfolio pages — all custom CSS. Bootstrap only used on `index.html` for the hero carousel.

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
| Add photos to a gallery | Use `admin.html` — select gallery, upload |
| Delete photos | Log into cloudinary.com → Media Library |
| Update contact form | Change Formspree endpoint in `contact.html` |
| Change admin password | Edit `var PASSWORD` in `admin.html` |
| Update copyright year | Search for `Coral Olson 2025` across all files |
| Add a new gallery | Create a new HTML page modelled on `family.html`, add a tile to `projects.html`, use a new Cloudinary tag |
