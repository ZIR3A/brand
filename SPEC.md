# SPEC.md - Futuristic 3D Landing Page

## Project Overview

**Project Name:** NEXUS - Futuristic 3D Landing Page
**Type:** Single-page marketing website with 3D WebGL elements
**Core Functionality:** A visually stunning, production-ready landing page featuring an interactive 3D scene with floating geometric structures, particle systems, and smooth scroll-driven animations
**Target Users:** Tech companies, Web3 projects, creative agencies, and futuristic brands

---

## UI/UX Specification

### Layout Structure

**Page Sections:**
1. **Hero Section** - Full viewport 3D canvas with centered typography overlay
2. **Features Section** - 3-column grid showcasing product features
3. **Stats Section** - Animated counters with glowing effects
4. **CTA Section** - Interactive call-to-action with 3D element
5. **Footer** - Minimal footer with social links

**Responsive Breakpoints:**
- Mobile: < 768px (single column, reduced 3D complexity)
- Tablet: 768px - 1024px (2-column grid)
- Desktop: > 1024px (full 3D experience)

### Visual Design

**Color Palette:**
- `--bg-primary`: #030305 (near-black)
- `--bg-secondary`: #0a0a0f (dark surface)
- `--bg-tertiary`: #12121a (elevated surface)
- `--text-primary`: #ffffff (white)
- `--text-secondary`: #a0a0b0 (muted gray)
- `--accent-primary`: #00f0ff (cyan neon)
- `--accent-secondary`: #ff00aa (magenta neon)
- `--accent-tertiary`: #7b2dff (purple neon)
- `--glow-cyan`: rgba(0, 240, 255, 0.4)
- `--glow-magenta`: rgba(255, 0, 170, 0.4)

**Typography:**
- Primary Font: "Orbitron" (Google Fonts) - headings, brand name
- Secondary Font: "Exo 2" (Google Fonts) - body text, UI elements
- Hero Title: 80px desktop / 40px mobile, weight 700
- Section Titles: 48px desktop / 32px mobile, weight 600
- Body Text: 18px, weight 400, line-height 1.6
- Navigation: 14px, weight 500, letter-spacing 2px

**Spacing System:**
- Section padding: 120px vertical desktop, 60px mobile
- Container max-width: 1400px
- Grid gap: 40px
- Card padding: 32px

**Visual Effects:**
- Glassmorphism cards with backdrop-blur(20px)
- Gradient borders using pseudo-element masks
- Glow effects on accent elements
- Scanline overlay effect on hero
- Noise texture overlay for depth

### Components

**Navigation Bar:**
- Fixed position, transparent background with blur on scroll
- Logo left, nav links center, CTA button right
- Hover: cyan underline animation

**Hero 3D Scene:**
- Floating wireframe icosahedron (slow rotation)
- Particle field (stars moving toward camera)
- Grid floor with perspective
- Ambient fog for depth
- Mouse parallax on camera

**Feature Cards:**
- Glassmorphism background
- Icon with glow effect
- Title and description
- Hover: lift + border glow

**Stats Counter:**
- Large number with accent color
- Animated count-up on scroll into view
- Subtle pulse glow

**CTA Button:**
- Gradient border (cyan to magenta)
- Inner dark fill
- Hover: gradient fills, scale 1.05
- Click: ripple effect

---

## Functionality Specification

### Core Features

1. **Three.js 3D Scene**
   - WebGL renderer with antialias
   - Perspective camera with mouse-controlled parallax
   - Wireframe icosahedron with continuous rotation
   - Particle system (500+ particles)
   - Infinite grid floor
   - Post-processing bloom effect (optional, performance permitting)
   - Responsive canvas sizing
   - Cleanup on page unload

2. **GSAP Animations**
   - Hero text entrance: staggered fade-up with blur
   - Navigation fade-in on load
   - Scroll-triggered section reveals
   - Feature cards stagger animation
   - Stats counter animation on scroll
   - Smooth scroll with ScrollTrigger
   - Parallax effects on scroll

3. **Interactive Elements**
   - Mouse move affects 3D camera position
   - CTA button hover effects
   - Navigation links with underline animation
   - Feature cards lift on hover
   - Reduced motion media query support

### User Interactions

- Scroll to navigate through sections
- Mouse movement affects 3D scene perspective
- Hover on cards for lift effect
- Click CTA for ripple feedback
- Click nav links for smooth scroll to section

### Edge Cases

- Fallback for WebGL not supported
- Graceful degradation on low-end devices (reduced particles)
- Handle window resize for 3D scene
- Prevent memory leaks on SPA navigation

---

## Acceptance Criteria

1. Page loads with 3D scene visible and animated
2. Hero text animates in on page load
3. Scrolling reveals sections with smooth animations
4. Feature cards have hover effects
5. Stats animate when scrolled into view
6. Mouse movement affects 3D scene
7. Responsive design works on mobile/tablet/desktop
8. No console errors (except expected warnings)
9. Lighthouse performance score > 80
10. Reduced motion respected when set in OS

---

## Technical Implementation

**File Structure:**
- index.html (single file with embedded CSS and JS)

**External Dependencies (CDN):**
- Three.js r158
- GSAP 3.12 with ScrollTrigger
- Google Fonts: Orbitron, Exo 2

**Browser Support:**
- Chrome 90+
- Firefox 90+
- Safari 15+
- Edge 90+