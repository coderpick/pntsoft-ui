---
title: PeopleNTech Design System Spec (index.html)
type: design_system
technology:
  - Tailwind CSS v4
  - Swiper JS v11
  - Manrope (Bunny Fonts)
last_updated: 2026-06-07
---

# PeopleNTech Design System Spec (index.html)

This document details the architecture, design tokens, responsive layout grid, interactive components, and scripting specifications that make up the PeopleNTech UI Design System as implemented in [index.html](file:///home/hafizur/www/pntsoft-ui/index.html).

---

## 1. Architectural Foundation & Tech Stack

The design system is constructed as a modern, high-fidelity single-page experience utilizing a lightweight, dynamic compilation pipeline and rich interactive libraries:

- **Tailwind CSS v4 Engine:** Compiled on-the-fly in-browser using `@tailwindcss/browser@4` for instant design flexibility.
- **Typography & Font Delivery:** Integrated via Bunny Fonts to load the *Manrope* typeface family (`300, 400, 500, 600, 700, 800`) cleanly without tracking.
- **Component Slider Suite:** Powered by `Swiper JS (v11)` for touch-responsive, hardware-accelerated carousel elements.
- **Interactivity Engine:** Built with vanilla ES6+ JavaScript using modern browser APIs (`IntersectionObserver`, `requestAnimationFrame`, `matchMedia`, `localStorage`).

---

## 2. Global Styling & Configuration

### Typography
- **Primary Font Family:** `'Manrope', sans-serif`
- **Root Sizing & Sizing Tokens:**
  - Base body: `15px` with a leading of `1.625` (relaxed).
  - Main hero header: Dynamic fluid typography (`text-clamp-xl` / `text-[2.8rem] md:text-[5.2rem]`) with tight line spacing (`leading-[1.04]`) and compressed letter-spacing (`tracking-tight`).
  - Sections/Subheadings: Uppercase labels with wide tracking (`tracking-[0.18em]`, `text-[0.65rem]` to `text-[0.72rem]`).

### Color Palette (Tokens)
The theme implements a rich, technical color palette designed for high contrast and seamless Light-to-Dark transition.

#### 1. Core Palette Tokens

| Token / Role | Light Mode Value | Dark Mode Value | Description / Usage |
| :--- | :--- | :--- | :--- |
| **Primary Background** | `#edeff5` | `#0b0f19` | Global page body backgrounds |
| **Section Card Fill** | `#ffffff` | `#0f172a` / `#1e293b` | Inner grid components and content card bases |
| **Primary Text** | `#0f172a` | `#f8fafc` | Main headings, titles, active navigation links |
| **Secondary Text** | `#475569` | `#94a3b8` | Subtitles, helper text, descriptions, inactive links |
| **Accent Color (Primary)** | `#e8440a` | `#ff5a1f` | Vibrant theme branding, focal highlights, active indicator |
| **Accent Text Color** | `#ffffff` | `#ffffff` | Contrast text color on active buttons and highlights |
| **Grid Lines & Borders** | `#cbd5e1` | `#334155` | Grid boundaries and component borders |
| **Topbar Background** | `#13264d` | `#1e293b`/20 | Top strip accent background |

#### 2. Component & UI Elements Color Rules

- **Interactive Primary Button (`.btn-primary`):**
  - **Light Mode Default:** Background `#0f172a`, Text `#ffffff`.
  - **Light Mode Hover:** Background `#e8440a`, Text `#ffffff`.
  - **Dark Mode Default:** Background `#f8fafc`, Text `#0b0f19`.
  - **Dark Mode Hover:** Background `#ff5a1f`, Text `#ffffff`.
- **Interactive Secondary Button (`.btn-secondary`):**
  - **Light Mode Default:** Border `#cbd5e1`, Background transparent, Text `#0f172a`.
  - **Light Mode Hover:** Border `#0f172a`, Text `#0f172a`.
  - **Dark Mode Default:** Border `#334155`, Background transparent, Text `#f8fafc`.
  - **Dark Mode Hover:** Border `#f8fafc`, Text `#f8fafc`.
- **Partner Marquee Elements:**
  - **Text:** `#475569` (Light) / `#94a3b8` (Dark).
  - **Divider Stars (`✦`):** Accent Color (`#e8440a` / `#ff5a1f`).
- **Swiper Bullet Pagination:**
  - **Default Bullet:** Background `#cbd5e1` (Light) / `#334155` (Dark), opacity `1.0`.
  - **Active Bullet:** Background `#e8440a` (Light) / `#ff5a1f` (Dark).

#### 3. Technology Stack Icon Hover Palette
Interactive grid items in the Expertise section change icon colors or container highlights on focus/hover:

| Technology | Default Color | Light Mode Hover Color | Dark Mode Hover Color |
| :--- | :--- | :--- | :--- |
| **Python** | `#475569` / `#94a3b8` | `#3776ab` (Python Blue) | `#ffd43b` (Python Yellow) |
| **Django** | `#475569` / `#94a3b8` | `#092e20` (Django Forest Green) | `#10b981` (Django Emerald) |
| **React** | `#475569` / `#94a3b8` | `#61dafb` (React Light Blue) | `#61dafb` (React Light Blue) |
| **Next.js** | `#475569` / `#94a3b8` | `#0f172a` (Slate 900) | `#f8fafc` (Slate 50) |
| **Vue** | Grayscale / Opacity `0.7` | Grayscale `0` (Vue Green `#41b883` & `#35495e`) | Grayscale `0` (Vue Green `#41b883` & `#35495e`) |
| **Tailwind CSS** | `#475569` / `#94a3b8` | `#38bdf8` (Tailwind Cyan) | `#38bdf8` (Tailwind Cyan) |
| **Flutter** | `#475569` / `#94a3b8` | `#02569B` (Flutter Blue) | `#40D0FD` (Flutter Sky Blue) |
| **MySQL** | `#475569` / `#94a3b8` | `#00758f` (MySQL Dark Cyan) | `#00758f` (MySQL Dark Cyan) |
| **PostgreSQL** | Grayscale / Opacity `0.7` | `#336791` (Postgres Navy) | `#4169e1` (Royal Blue) |
| **Docker** | `#475569` / `#94a3b8` | `#2496ed` (Docker Blue) | `#2496ed` (Docker Blue) |

---

## 3. Layout Grid & Technical Aesthetics

### Responsive Container
- All main blocks wrap within a centered limit of `max-w-[1340px]` with fluid padding (`px-6 md:px-10`).

### The Blueprint Grid (Retro-Technical Aesthetics)
Rather than typical floating cards, sections use structural grid boundaries (`border-l border-r border-t border-b`) to align content to a unified grid blueprint.
- **Grid Dividers:** Vertical and horizontal dividers use custom border colors (`border-[#cbd5e1]` / `dark:border-[#334155]`) that flow across sections.
- **Corner Decorators:** Content headers and hero panels feature decorative corner-brackets made using absolute pseudo-elements. For example:
  ```html
  <div class="relative before:content-[''] before:absolute before:w-2.5 before:h-2.5 before:top-[-1px] before:left-[-1px] before:border-t-2 before:border-l-2 before:border-[#0f172a] dark:before:border-[#f8fafc]">
      <!-- Content here -->
  </div>
  ```
  This creates a high-fidelity CAD/Blueprint appearance.

---

## 4. Components & Interactive Elements

### 4.1 Buttons (`.btn`)
All buttons share a base class ensuring consistent dimensions and transitions:
- **Base Style (`.btn`):** `inline-flex`, uppercase letter-spaced font (`.75rem`, `tracking-[0.07em]`), extra bold font-weight (`700`), custom spacing (`.82rem 1.75rem`), and default hover transitions.
- **Primary Action (`.btn-primary`):** 
  - *Light Mode:* Dark Slate bg, white text. Hover transitions to Orange `#e8440a`.
  - *Dark Mode:* Slate 50 bg, dark text. Hover transitions to Vibrant Orange `#ff5a1f` with white text.
- **Secondary Action (`.btn-secondary`):**
  - Bordered transparent style (`border-[#cbd5e1]` / `dark:border-[#334155]`). Text color reactive. Hover transitions to full Slate borders.

### 4.2 Interactive Header & Navigation
- **Topbar:** Multi-link information stripe utilizing brand colors with high-contrast social links.
- **Navbar (`id="nav"`):** Sticky positioned wrapper with glassmorphism backdrop (`backdrop-blur-lg`, `bg-[#edeff5]/95` / `dark:bg-[#0b0f19]/95`) and sub-border lines.
- **Hoverable Dropdown Menus:** Desktop nav items (`Services`, `Industries`, `About`) feature CSS-driven hover menus:
  - Transition timings utilize `duration-250` and `opacity` visibility transitions. Chevrons rotate 180 degrees on hover.
  - *Services Dropdown:* Lists core agency solutions (Custom Software, Web Application, eCommerce, Mobile App, MVP Design, IT Consultancy).
  - *Industries Dropdown:* Links to business verticals (Healthcare, Logistics, Retail & eCommerce, Tour & Travel, Education).
  - *About Dropdown:* Navigates to About Us, Our Team, and Portfolio links.
- **Responsive Navigation Actions:**
  - Breakpoint threshold at `768px` controlled dynamically by script.
  - Hamburger trigger (`id="hbg"`) and close button (`id="close-m"`) manage a full-screen overlay menu (`id="mmenu"`) for mobile layouts.

### 4.3 Statistics Counter Panel
- Includes four numerical panels that animate upon visibility.
- Utilizes `data-target` and `data-suffix` attributes to count from 0 to target values.
- Implementation uses an `IntersectionObserver` to trigger a recursive `requestAnimationFrame` counting function, ensuring smooth GPU-friendly scroll timing.

### 4.4 Infinite Partner Marquee
- A horizontally scrolling panel displaying client logos/names.
- Powered by Tailwind custom keyframes:
  ```css
  @keyframes marquee {
    0% { transform: translateX(0%); }
    100% { transform: translateX(-50%); }
  }
  ```
- Implemented with infinite, linear looping (`animate-[marquee_25s_linear_infinite]`).

### 4.5 Hover-Driven Service Cards
- Grid-aligned container elements representing service catalog items.
- On hover, cards trigger simultaneous micro-animations:
  - Transition of svg icon container background (`bg-[#f1f5f9]` -> `#e8440a` / `#ff5a1f`).
  - SVG icon line transitions from orange to white.
  - Title text transition.
  - Arrow slide animation (`group-hover:translate-x-1`).
  - Subtle drop shadow lift (`hover:shadow-2xl hover:shadow-[#0f172a]/5`).

### 4.6 Testimonials Slider (Swiper Integration)
- Integrated using `swiper-bundle.min.js`.
- Custom styled bullets matching the brand theme:
  - Default bullets (`.swiper-pagination-bullet`): Light mode `#cbd5e1`, Dark mode `#334155`.
  - Active bullet (`.swiper-pagination-bullet-active`): Animates to `width: 22px`, changes color to Orange (`#e8440a` / `#ff5a1f`).
- Navigation control handles custom SVG arrows inside circular hover buttons.

### 4.7 Contact Form System (`id="cform"`)
- Handled via event listeners preventing standard page redirects.
- On submission:
  - Submit button changes state (`Sending...`) and is disabled.
  - Form hides with a transition, and a hidden success alert (`id="fsuccess"`) becomes visible.

---

## 5. Theme Variation Selector
A floating quick-select menu (`fixed top-1/2 -translate-y-1/2 right-4`) enables testing other design presets:
- **v1.html:** Classic Blue Theme Palette.
- **v2.html:** Vibrant Coral / Orange Theme Palette (Standard).
- **v3.html:** Soft Emerald Theme Palette (Light-weighted, rounded corners).
- **v4.html:** Royal Purple Theme Palette.

---

## 6. JavaScript State and Logic Specifications

### 6.1 Dark Mode Scripting Flow
Theme toggling uses local storage preservation (`pt-theme`) and media queries:
```javascript
const html = document.documentElement;
const toggle = document.getElementById('theme-toggle');

function applyTheme(dark) {
    if (dark) {
        html.classList.add('dark');
        // Swaps SVG icons
    } else {
        html.classList.remove('dark');
        // Swaps SVG icons
    }
}
// Initialization checks: saved storage -> matches media query
const saved = localStorage.getItem('pt-theme');
const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
applyTheme(saved ? saved === 'dark' : prefersDark);
```

### 6.2 Scroll Animations (Fade Up Observer)
Elements marked with class `.fu` are initially offset and hidden (`opacity-0 translate-y-7`). An `IntersectionObserver` with threshold `0.07` handles revealing elements on scroll:
```javascript
const io = new IntersectionObserver(entries => {
    entries.forEach(e => {
        if (e.isIntersecting) {
            e.target.classList.add('!opacity-100', '!translate-y-0');
        }
    });
}, { threshold: 0.07, rootMargin: '0px 0px -40px 0px' });
```
