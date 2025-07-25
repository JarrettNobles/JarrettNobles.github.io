# This is a website for my girlfriends photography booking 
https://www.coralolsonphotography.com/index.html

# Coral Olson Photography 🌟

A clean, modern portfolio website showcasing Coral Olson’s photography, built as static HTML/CSS (Bootstrap-based), hosted at [coralolsonphotography.com](https://www.coralolsonphotography.com).

---

## 🧱 Site Structure

```
/
├── index.html              ← Home / hero landing page
├── projects.html           ← Portfolio overview (grid or vertical layout)
├── marinashoot.html        ← Portrait session gallery
├── vincentengagment.html   ← Wedding & Engagement gallery
├── resume.html             ← About Me / bio section (image-led layout)
├── contact.html            ← Contact form (SB Forms)
├── assets/                 ← Images (hero, sessions, icons, etc.)
├── css/
│   └── styles.css          ← Shared global styles and Bootstrap overrides
└── js/
    └── scripts.js          ← Shared JavaScript (carousel autoplay, page enhancements)
```

---

## 🎯 Features & Highlights

- **Homepage**: Full-screen hero carousel with overlay text and “Book” and “Portfolio” calls to action.
- **Font styling**: ‘Playfair Display’ used for headings and navigation; ‘Plus Jakarta Sans’ for body text.
- **Portfolio layout**: Mix of horizontal grid and vertical card layouts for portfolio sections.
- **About page**: Displays a single full-width image of your biography without any grid cards.
- **Image galleries**: Clean display of images in vertical flows with a “Back to Portfolio” button.
- **Footer**: Consistent Instagram call-to-action banner and copyright text.
- **Form page**: Contact form built with Bootstrap and integrated via SB Forms (inactive until configured).

---

## 🛠 Common Enhancements

### 1. Consistent Navbar Font & Branding  
Ensure that all pages use the same navbar font (`Playfair Display`) and link styles—this helps maintain cohesive branding.

### 2. Disable Cut/Copy/Paste for Images  
To restrict users from downloading or copying images, include the following snippet at the end of every page (before closing `</body>`):
```html
<script>
  document.addEventListener('DOMContentLoaded', () => {
    document.body.addEventListener('cut', e => e.preventDefault());
    document.body.addEventListener('copy', e => e.preventDefault());
    document.body.addEventListener('paste', e => e.preventDefault());
    document.querySelectorAll('img').forEach(img => {
      img.addEventListener('contextmenu', e => e.preventDefault());
      img.setAttribute('draggable', 'false');
    });
  });
</script>
```

### 3. Mobile Optimization
- Use CSS media queries to adjust font sizes, padding, and image widths.
- Ensure navigation collapse works smoothly on small screens.
- The layout should adapt vertically for narrow viewports.

---

## 🚀 Deployment Setup

Sites appear on `GitHub Pages` (e.g., `JarrettNobles.github.io`) or custom domain `coralolsonphotography.com`. Steps:

1. Push updated HTML, CSS, JS, and assets to GitHub repo's `main` branch.
2. Ensure correct domain is set under repo settings (CNAME for custom domain).
3. Verify SSL certificate and redirects are active.
4. Test all pages via real device and browser dev tools in mobile mode.

---

## ✅ Maintenance Checklist

| Task                      | Recommended Frequency |
|---------------------------|-----------------------|
| Add new images/sessions   | As needed             |
| Validate contact form API | Quarterly             |
| Update copyright year     | Annually              |
| Optimize image size/etc.  | Bi-annually           |
| Test mobile responsiveness| After major layout changes |

---

### 💡 Tips

- Keep font imports consistent and remove redundant `link` tags if fonts repeat.
- Use semantic HTML like `<h1 class="page-heading">` to maintain structure.
- Leverage shared styles in `styles.css` and minimize inline overrides.
- Use common footer/Instagram section as a reusable `<footer>` template—or better still, switch to a templating engine if maintaining many pages.

