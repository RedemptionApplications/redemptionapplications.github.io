# Redemption Applications — Website Build Spec
# For use with Claude Code

## Project Overview

Build a complete, static, single-page business website for **Redemption Applications (RA)**, a freelance mobile and software development company based in Utah, run by a husband-and-wife team. The site must be production-ready, SEO-optimized, mobile-first, and deployable to GitHub Pages with zero dependencies on a backend server.

The finished product should feel like a polished agency site — not a generic template. It should inspire trust from potential clients who are individuals with app ideas or small businesses looking to hire a developer. The primary conversion goal is getting visitors to **book a free discovery call** — not to quote a price. Pricing is never mentioned on the site.

---

## Tech Stack

- **Pure HTML5 + CSS3 + Vanilla JavaScript** (no frameworks, no build tools required)
- Single `index.html` file with embedded or linked CSS/JS
- All assets in an `/assets/` folder (images, logo, favicon)
- Deployable as-is to GitHub Pages (just push and go)
- Google Fonts via CDN link in `<head>`
- No npm, no webpack, no React — keep it dependency-free for easy maintenance

---

## Brand Identity

### Colors (match the logo exactly)
```
--color-bg:          #0a1628   /* Deep navy background */
--color-surface:     #0d1f3c   /* Slightly lighter navy for cards/sections */
--color-blue:        #4db8d4   /* Electric teal-blue (bracket/accent color) */
--color-blue-dark:   #2a8fa8   /* Darker blue for hover states */
--color-gold:        #b8962e   /* Warm gold accent lines */
--color-text:        #e8eef4   /* Off-white body text */
--color-text-muted:  #7a9bb5   /* Muted blue-gray for secondary text */
--color-white:       #ffffff   /* Pure white for headings and logo letters */
--color-border:      rgba(77, 184, 212, 0.2)  /* Subtle blue border */
```

### Typography
- **Display/Headings**: `'Exo 2'` from Google Fonts — geometric, tech-forward, matches the logo aesthetic
- **Body**: `'Source Sans 3'` from Google Fonts — clean, professional, highly readable
- **Code/Monospace accents**: `'JetBrains Mono'` from Google Fonts — for any technical decorative text
- Import all three in `<head>`

### Logo
- Use the provided `assets/RA_logo.png` in the nav
- Display at approximately 48px height
- On small screens, scale down proportionally

### Visual Style
- Dark navy base, tech/precision aesthetic — matches the "targeting reticle" design language of the logo
- Subtle grid lines in the background (CSS only, very low opacity)
- Bracket `[ ]` motifs used as decorative elements (mirrors the logo)
- Gold accent lines used sparingly as horizontal dividers or underline accents
- Electric blue used for interactive elements, borders, and highlights
- Animations: smooth, purposeful, not flashy — fade-ins on scroll, subtle hover lifts on cards

---

## Site Architecture

Single-page site with smooth scroll navigation. Sections in order:

1. `#home` — Hero
2. `#services` — Services
3. `#process` — How It Works
4. `#portfolio` — Portfolio / Past Work
5. `#about` — About
6. `#contact` — Contact

---

## Section Specifications

### 1. Navigation (fixed, top)

- Fixed to top, full width
- Background: `--color-bg` with `backdrop-filter: blur(10px)` and slight transparency on scroll
- Left: RA logo image (`assets/RA_logo.png`, ~48px tall)
- Right: Nav links — Services | Process | Portfolio | About | Contact
- Active link highlighted with `--color-blue`
- CTA button: **"Book a Free Discovery Call"** → scrolls to `#contact`
  - Styled with a blue border, transparent fill, hover fills with blue
- Mobile: hamburger menu, full-screen slide-down nav
- On scroll past hero: nav background becomes fully opaque

---

### 2. Hero Section (`#home`)

Full viewport height. This is the most important section — it must be striking.

**Layout**: Centered content, vertical stack

**Headline** (large, white, `'Exo 2'` bold):
> "Your App Idea. Expertly Built."

**Subheadline** (medium, muted blue-gray):
> "Custom mobile and software solutions for individuals and growing businesses. From concept to launch — with a team that cares about your success."

**CTA Buttons** (side by side):
- Primary: "Book Your Free Discovery Call" → scrolls to `#contact`
  - Filled with `--color-blue`, white text
- Secondary: "See Our Work" → scrolls to `#portfolio`
  - Outlined, blue border, transparent fill

**Decorative elements**:
- Faint CSS grid overlay across the full section (use `background-image: linear-gradient` to make subtle grid lines, ~5% opacity)
- Two corner bracket elements (top-left and bottom-right of the content area) — CSS-drawn, using `--color-blue`, like the logo's targeting reticle corners
- A horizontal gold line above the headline (20% width, centered)
- Three dots (like the logo's dot indicator) below the buttons

**Animation**: Headline and subhead fade in from below on page load (CSS keyframes, staggered with `animation-delay`)

---

### 3. Services Section (`#services`)

**Section title**: "What We Build"
**Section subtitle**: "End-to-end development for the platforms your customers use"

**Service Cards** (3-column grid on desktop, 1-column on mobile):

Display as dark cards with a subtle blue border. On hover: card lifts slightly (`transform: translateY(-4px)`), border brightens.

Card structure: icon (CSS/SVG or Unicode) + title + description

Cards:
1. **Mobile Apps** — `📱` or phone icon
   > "Native-quality Android and iOS apps using Flutter. Smooth, fast, and beautiful — shipped to the Google Play Store and Apple App Store."

2. **Custom Software** — `⚙️` or gears icon
   > "Business tools, internal dashboards, IoT integrations, and workflow automation. Built to your exact specifications."

3. **App Modernization** — `🔄` or refresh icon
   > "Have an existing app that needs updates, redesign, or new features? We take over messy codebases and make them shine."

4. **MVP Development** — `🚀` or rocket icon
   > "Got an idea but need to prove it fast? We scope, build, and ship minimum viable products that are actually viable."

5. **Play Store Deployment** — `▶` or play icon
   > "Full Google Play Store setup, submission, and compliance — including app signing, store listing, and launch support."

6. **Ongoing Support & Maintenance** — `🛡️` or shield icon
   > "Post-launch bug fixes, updates, and feature additions. Never be left stranded after your project ships."

Cards animate in on scroll (fade + slight slide up, staggered).

---

### 4. How It Works Section (`#process`)

**Section title**: "How It Works"
**Section subtitle**: "A clear, simple process — no surprises, no pressure"

Display as a horizontal timeline on desktop, vertical on mobile.

Steps:
1. **Book a Discovery Call** — "Schedule a free 30-minute call. We'll listen to your idea, ask the right questions, and learn what you need — no obligation."
2. **Receive Your Proposal** — "You'll get a clear written proposal with scope, timeline, and cost. No vague estimates — just honest, detailed numbers."
3. **Build & Review Together** — "We build in phases. You review and give feedback at every milestone, so there are never any surprises."
4. **Launch Day** — "Your app goes live. We handle deployment, store submission, and support you through every step of launch."
5. **Ongoing Partnership** — "We don't disappear after launch. Maintenance, updates, and new features are always available as your business grows."

Each step: number in a circle (blue border, `--color-blue` text), step title, step description.

Connecting line between steps (horizontal on desktop, vertical on mobile) using a gold `--color-gold` thin line.

---

### 5. Portfolio Section (`#portfolio`)

**Section title**: "Our Work"
**Section subtitle**: "Real projects. Real results."

Display 3 placeholder project cards (these will be updated with real projects later).

Card structure:
- Image area (use a styled placeholder — dark gradient rectangle with bracket decoration, labeled "Project Image")
- Project name
- Short description
- Tags (tech used): styled as small pill badges in `--color-blue` with low opacity background
- "View Details" link (disabled/placeholder for now)

Placeholder projects:
1. **SenMatrix IoT Dashboard** — "Real-time IoT device monitoring and management platform. Built with Flutter and integrated with hardware sensors."
   Tags: Flutter, IoT, Android, Google Play

2. **Client Project** — "Mobile app for a small business client. Full lifecycle from discovery to Play Store launch."
   Tags: Flutter, Mobile, Android

3. **Your Project Here** — "We're building our portfolio every day. Reach out to discuss your project."
   Tags: Mobile, Web, Custom

---

### 6. About Section (`#about`)

**Section title**: "About Redemption Applications"

Two-column layout on desktop (text left, visual accent right). Single column on mobile.

**Left column — text**:

Heading: "A Team You Can Trust"

Body paragraphs:
> "Redemption Applications is a Utah-based software development studio run by a husband-and-wife team with six years of professional engineering experience. We've built real software for real businesses — and we bring that same expertise and care to every client project."

> "We specialize in mobile app development using Flutter — delivering smooth, cross-platform apps to Android and iOS. Whether you're an entrepreneur with your first app idea or a growing business that needs custom software, we're with you from the first conversation to launch day and beyond."

> "We believe technology should serve your goals — not the other way around. That means clear communication, honest timelines, and code that's built to last."

**Bullet points** (with `--color-blue` checkmark accent):
- ✓ 6 years of professional software engineering experience
- ✓ Husband-and-wife team — reliability and continuity you can count on
- ✓ Flutter specialist — Android & iOS from one codebase
- ✓ Google Play Store deployment experience
- ✓ IoT and hardware integration experience
- ✓ Utah-based, available for remote clients nationwide
- ✓ Fully licensed LLC

**Right column — visual**:
A stylized decorative element: large `[ RA ]` bracket letterform in CSS, or the logo displayed large, centered in a subtle glowing box with the blue/gold color treatment. Not a photo — keep it abstract/brand-consistent.

---

### 7. Contact Section (`#contact`)

**Section title**: "Let's Talk About Your Project"
**Section subtitle**: "Book a free 30-minute discovery call. No pressure, no commitment — just a conversation about what you want to build."

**Introductory note** (small text, muted, above the form):
> "Every project is unique. We don't do one-size-fits-all pricing — we learn about your project first, then give you an honest, detailed proposal. The discovery call is always free."

**Form fields**:
- Name (text input, required)
- Email (email input, required)
- Phone (tel input, optional) — label: "Phone (optional)"
- Project Type (select dropdown):
  - Options: Mobile App | Custom Software | App Modernization | MVP / Proof of Concept | Ongoing Maintenance | Not Sure Yet | Other
- Tell Us About Your Project (textarea, required, ~6 rows)
  - Placeholder text: "Describe your idea, what problem it solves, who your users are, and anything else that feels relevant. Don't worry about having all the answers — that's what the discovery call is for!"
- Submit button: "Request My Free Discovery Call"
  - Full width, filled with `--color-blue`, white text, bold

**Form behavior**:
- Client-side validation (required fields, email format)
- On submit: POST to Formspree endpoint
  - Use placeholder action URL: `https://formspree.io/f/REPLACE_WITH_YOUR_ID`
  - Add a comment in the HTML: `<!-- Replace REPLACE_WITH_YOUR_ID with your actual Formspree form ID after signing up at formspree.io -->`
- On success: hide form, show a success message:
  > "✓ Thank you! We'll reach out within one business day to schedule your free discovery call."
- Style: inputs have dark background, blue border on focus, white text

**Below the form** — contact alternatives (side by side on desktop, stacked on mobile):

- 📞 Phone: `REPLACE_WITH_GOOGLE_VOICE_NUMBER`
  - HTML comment: `<!-- Replace with your Google Voice number -->`
  - Label below number: "Call or text — we respond fast"
- 📧 Email: `hello@redemptionapplications.com`
  - HTML comment: `<!-- Replace with your real business email once set up -->`
  - Label below email: "Prefer email? We check it daily"
- 📍 Location: "Utah, USA — Remote-friendly nationwide"

---

## Footer

Full-width dark footer.

**Left**: RA logo (small) + "© 2025 Redemption Applications LLC. All rights reserved."
**Center**: Quick nav links (Home | Services | Process | Portfolio | About | Contact)
**Right**: "Built with care in Utah 🏔️"

Thin gold horizontal line at the very top of the footer.

---

## SEO Requirements

All of these must be implemented:

### Meta tags in `<head>`:
```html
<title>Redemption Applications | Mobile App Development Utah</title>
<meta name="description" content="Redemption Applications is a Utah-based mobile app development studio. We build Flutter apps for Android and iOS — from idea to launch. Book a free discovery call today.">
<meta name="keywords" content="mobile app development, Flutter developer, Android app, iOS app, freelance app developer Utah, custom software development, app development small business, hire app developer Utah">
<meta name="author" content="Redemption Applications">
<meta name="robots" content="index, follow">
<link rel="canonical" href="https://www.redemptionapplications.com/">
```

### Open Graph tags (for link previews):
```html
<meta property="og:title" content="Redemption Applications | Mobile App Development">
<meta property="og:description" content="Custom mobile apps for individuals and small businesses. Flutter specialist. Utah-based, remote-friendly. Book a free discovery call.">
<meta property="og:image" content="assets/og-image.png">
<meta property="og:url" content="https://www.redemptionapplications.com/">
<meta property="og:type" content="website">
```

### JSON-LD Structured Data (paste inside a `<script type="application/ld+json">` tag):
```json
{
  "@context": "https://schema.org",
  "@type": "ProfessionalService",
  "name": "Redemption Applications",
  "description": "Husband-and-wife mobile app and software development studio based in Utah. Flutter specialist for Android and iOS.",
  "url": "https://www.redemptionapplications.com",
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "Utah",
    "addressRegion": "UT",
    "addressCountry": "US"
  },
  "serviceArea": {
    "@type": "Country",
    "name": "United States"
  },
  "hasOfferCatalog": {
    "@type": "OfferCatalog",
    "name": "App Development Services",
    "itemListElement": [
      {"@type": "Offer", "itemOffered": {"@type": "Service", "name": "Mobile App Development"}},
      {"@type": "Offer", "itemOffered": {"@type": "Service", "name": "Flutter Development"}},
      {"@type": "Offer", "itemOffered": {"@type": "Service", "name": "Custom Software Development"}},
      {"@type": "Offer", "itemOffered": {"@type": "Service", "name": "MVP Development"}},
      {"@type": "Offer", "itemOffered": {"@type": "Service", "name": "Google Play Store Deployment"}}
    ]
  }
}
```

### Additional SEO:
- All images have descriptive `alt` attributes
- Headings use proper hierarchy: one `<h1>` (hero headline), `<h2>` for section titles, `<h3>` for cards
- Each section has an `id` attribute for anchor linking
- Page loads fast — no large images, no blocking scripts
- Include a `robots.txt` file:
  ```
  User-agent: *
  Allow: /
  Sitemap: https://www.redemptionapplications.com/sitemap.xml
  ```
- Include a basic `sitemap.xml` file pointing to the homepage

---

## Accessibility Requirements

- All interactive elements are keyboard-navigable
- Focus states are visible (styled with `--color-blue` outline)
- Color contrast ratios meet WCAG AA minimum
- Form inputs have associated `<label>` elements
- Hamburger menu has `aria-label` and `aria-expanded` attributes
- Images have `alt` text

---

## File Structure to Generate

```
redemption-apps-website/
├── index.html
├── assets/
│   ├── RA_logo.png          ← (copy from provided logo)
│   ├── RA_logo.jpg          ← (copy from provided logo)
│   └── og-image.png         ← (generate: dark navy 1200x630 with RA logo centered)
├── robots.txt
├── sitemap.xml
└── CLAUDE.md                ← (permanent project context, see below)
```

---

## CLAUDE.md Content (permanent project context file)

Generate a `CLAUDE.md` in the project root with this content:

```markdown
# Redemption Applications Website — Project Context

## What This Is
Static business website for Redemption Applications LLC, a freelance mobile/software development studio run by a husband-and-wife team based in Utah.

## Business Model
- Primary conversion goal: get visitors to book a free discovery call
- Pricing is NEVER shown on the site — all pricing comes from the discovery call process
- Target clients: individuals with app ideas, small businesses needing custom software

## Tech Stack
- Pure HTML5 / CSS3 / Vanilla JS — no build tools
- Hosted on GitHub Pages
- Contact form via Formspree

## Brand Colors
- Background: #0a1628
- Surface: #0d1f3c
- Blue accent: #4db8d4
- Gold accent: #b8962e
- Text: #e8eef4
- Muted text: #7a9bb5

## Fonts
- Headings: 'Exo 2' (Google Fonts)
- Body: 'Source Sans 3' (Google Fonts)
- Mono accents: 'JetBrains Mono' (Google Fonts)

## Key Files
- index.html — entire site
- assets/RA_logo.png — primary logo
- robots.txt — SEO crawl permissions
- sitemap.xml — SEO sitemap

## Placeholders to Update Before Launch
- Formspree ID: find REPLACE_WITH_YOUR_ID in index.html
- Google Voice number: find REPLACE_WITH_GOOGLE_VOICE_NUMBER in index.html
- Business email: hello@redemptionapplications.com (update if different)

## Owner
Redemption Applications LLC — Utah, USA
```

---

## Final Notes for Claude Code

- Prioritize mobile-first responsive design
- The site should look polished and professional without requiring any real content beyond what's specified here
- All placeholder text is intentionally written as real marketing copy — use it as-is
- The tone throughout should be warm and approachable, not cold/corporate — this is a small team that genuinely cares about their clients
- Animations should be CSS-only, no JavaScript animation libraries
- JavaScript is only needed for: scroll-based nav styling, hamburger menu, form submission/validation, scroll-triggered fade-ins (use IntersectionObserver)
- Test that the contact form gracefully handles no-JS environments (degrade to plain form submission)
- Comments in the HTML should explain where to update all placeholder values
- Never mention pricing anywhere on the site
- Every CTA (call to action) should point toward booking a discovery call, not requesting a quote
