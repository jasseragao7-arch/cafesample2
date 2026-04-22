# 🎨 Tiny Canvas Cafe — Website Masterprompt

---

## ⚡ BEFORE YOU BEGIN — READ THE WORKSPACE

**This is the mandatory first step. Do not write any code until it is complete.**

You are working inside a VS Code project. Two folders have been added to the workspace root that you must fully internalize before building anything:

### 1. Read the `components/` folder
```
- List every file inside the components/ folder recursively
- Read the full contents of each component file
- Identify: component name, props/API, visual style, and intended use case
- Note which components are best suited for: cards, navbars, tabs, buttons, galleries, menus, modals, or hero sections
```

### 2. Read the `skills/` folder
```
- List every file inside the skills/ folder recursively
- Read the full contents of each skill file
- Identify: what each skill does, what inputs it expects, and what output or behavior it produces
- Note which skills apply to: animations, layout, image handling, interactivity, accessibility, or performance
```

### 3. Build a mental map before coding
After reading both folders, internally map each website section (Hero, About, Activity Guide, Menu, Gallery, Footer) to the most appropriate available components and skills. Prefer project-local components and skills over writing things from scratch. Only write custom code where no suitable component or skill exists.

> **Rule:** If a component or skill exists for something, use it. Do not reinvent what's already in the workspace.

---

## BRAND OVERVIEW

**Tiny Canvas Cafe** is a cozy sip-and-paint café located in the UAE (prices in AED). Its tagline is **"Meet, Sip, and Create!"** — blending specialty coffee, pastries, and creative art activities in one warm, artistic space. The brand aesthetic is **warm, handcrafted, and nostalgic** — think earthy browns, creamy beiges, plaid textures, coffee tones, and whimsical hand-drawn illustrations.

---

## VISUAL IDENTITY

| Element | Detail |
|---|---|
| **Primary colors** | Warm brown `#6B3A1F`, chocolate `#3B1A0A`, cream/latte `#EDE0CC`, sand beige `#F5ECD7` |
| **Accent colors** | Soft taupe `#C4A882`, muted tan `#D6C4A0` |
| **Typography** | Playful rounded display font for headings (e.g. Fredoka One, Nunito Black, or Lilita One); cozy monospace or handwriting font for body (e.g. Courier Prime, Caveat, or Patrick Hand) |
| **Visual motifs** | Plaid/gingham checkerboard backgrounds, coffee beans, paint brushes, canvases, latte art, heart icons, ceramic pots, watercolor washes |
| **Overall tone** | Warm, artisanal, playful, inviting — like a cozy corner café with an art studio inside |

---

## WEBSITE STRUCTURE & PAGES

Build a **single-page scrolling website** with smooth anchor navigation. Include the following sections:

---

### 1. HERO SECTION
- Full-screen header with the **Tiny Canvas Cafe** logo treatment: "sip and paint!" tagline above, large bold arched "TINY CANVAS CAFE" text
- Background: illustrated/watercolor café scene with warm earthy tones; include subtle bokeh or soft grain texture overlay
- Animated floating coffee cup or paint brush element
- CTA buttons: **"Explore Activities"** (scrolls to activities) and **"See the Menu"** (scrolls to menu)
- Tagline: **"Meet, Sip, and Create!"**

---

### 2. ABOUT / INTRO SECTION
Short warm introduction paragraph. Example copy:
> *"Welcome to Tiny Canvas Cafe — Abu Dhabi's coziest sip and paint experience. Whether you're a first-time painter or a seasoned artist, grab a drink, pick up a brush, and let your creativity flow."*

Include 2–3 illustrated icon cards representing: ☕ Coffee & Drinks · 🎨 Art Activities · 🏺 Ceramics

---

### 3. ACTIVITY GUIDE SECTION

Section title: **"Activity Guide"**

Display 3 activity cards with icons, names, and descriptions:

| Activity | Description |
|---|---|
| **The Tiny Starter** | Mini canvas (20×20 cm) + painting palette. Perfect for beginners wanting a taste of creativity. |
| **The Masterpiece Bundle** | Medium canvas (50×50 cm) + painting palette + any drink of your choice! The full creative experience. |
| **Sculpt'nPaint** | Create your own ceramics from scratch, then paint and glaze them. A truly hands-on masterpiece. |

Each card should have:
- A playful illustrated icon (brush, canvas, or ceramic pot)
- Activity name in bold display font
- Short description
- Hover animation (lift/glow effect)

---

### 4. DRINK MENU SECTION

Section title: **"Our Menu"**

Divide into 3 subsections displayed as styled menu boards or card columns:

#### ☕ Coffee
| Item | Price |
|---|---|
| Signature Latte | 25 AED |
| Spanish Latte | 22 AED |
| Iced Latte | 20 AED |
| Karak Chai | 8 AED |

#### 🧃 Juices & Smoothies
| Item | Price |
|---|---|
| Fresh Strawberry Juice | 10 AED |
| Fresh Mango Juice | 10 AED |
| Strawberry & Banana Smoothie | 15 AED |
| Mixed Berry Smoothie | 15 AED |

#### 🥐 Pastries
| Item | Price |
|---|---|
| Butter Croissant | 12 AED |
| Pain au Chocolat | 15 AED |

Design tip: Use a warm parchment-style card background with brown serif headings and monospace/handwriting prices. Add small illustrated coffee bean or paint splash decorations between sections.

---

### 5. GALLERY / MOOD SECTION *(optional but recommended)*

A horizontally scrolling or masonry-style image gallery section. Use warm placeholder cards styled as polaroid photos or canvas frames showing:
- Finished paintings
- Coffee cups with latte art
- Ceramic pieces
- Happy customers painting

Title: **"What You'll Create"** or **"From Our Canvas to Yours"**

---

### 6. FOOTER / CONTACT SECTION

- Repeat the Tiny Canvas Cafe logo
- Tagline: **"Meet, Sip, and Create!"**
- Social media icons (Instagram, TikTok)
- Location: Abu Dhabi, UAE *(placeholder — fill in actual address)*
- Simple copyright line

---

## INTERACTIVITY REQUIREMENTS

- **Smooth scroll navigation** between sections on anchor clicks
- **Sticky navbar** (minimal, transparent on hero → solid on scroll) with logo + nav links
- **Hover animations** on activity cards: subtle lift + shadow
- **Menu tab switcher** (Coffee / Juices / Pastries toggle) with animated underline
- **Fade-in-on-scroll** animations for section content using IntersectionObserver
- **Parallax or floating element** on the hero (optional: subtle moving coffee cup or paint drip)
- **Mobile responsive** — single column layout on small screens, plaid background scales gracefully

---

## AESTHETIC DIRECTION

Execute this as **warm maximalist cozy** — not sparse, not clinical. The site should feel like stepping into the café itself:

- Use `@import` from Google Fonts for a playful rounded display font + a cozy handwriting or monospace font
- Background textures: CSS-drawn plaid/gingham pattern using `repeating-linear-gradient` in cream and tan
- Wavy section dividers between sections (SVG wave shapes in cream/brown)
- Generous use of warm brown `#6B3A1F` for headings, cream `#F5ECD7` for backgrounds, chocolate `#3B1A0A` for accents
- Hand-drawn style borders or dashed borders on cards
- Coffee bean and paint brush SVG illustrations as decorative elements inline

---

## TECHNICAL SPEC

- **Single HTML file** (HTML + embedded CSS + vanilla JS — no frameworks needed)
- All fonts via Google Fonts CDN
- No external image dependencies — use CSS illustrations, SVG art, or emoji-based placeholders
- Fully self-contained and mobile responsive
- Smooth and performant — avoid heavy JS libraries
- **Components from `components/`** must be imported or inlined as discovered — do not duplicate their logic
- **Skills from `skills/`** must be applied at every relevant step — treat them as project-level conventions, not optional suggestions

---

## 🔁 COMPONENT & SKILL INTEGRATION CHECKLIST

Before delivering the final output, verify the following:

- [ ] Every file in `components/` has been read and considered
- [ ] Every file in `skills/` has been read and applied where relevant
- [ ] No component has been rebuilt from scratch if an equivalent exists in `components/`
- [ ] No pattern has been manually coded if a skill already defines the approach
- [ ] All components are used with their correct props/API as defined in their source files
- [ ] The final output reflects the project's own conventions, not generic boilerplate

---

*End of masterprompt. Use this document to generate the full Tiny Canvas Cafe website.*
