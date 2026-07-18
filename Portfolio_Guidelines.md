# Implementation Guidelines
**Portfolio Redesign — Senior Designer**

> **Status:** Draft
> **Version:** 0.1
> **Last Updated:** April 2026
> **Author:** [Your Name]
> **Linked PRD:** Portfolio_PRD.md
> **Linked Design Brief:** Portfolio_Design_Brief.md

These guidelines are the technical complement to the Design Brief. Where the brief defines intent, this document defines rules — how tokens are implemented, what patterns to follow, and what to avoid when building.

---

## 1. Stack

| Layer | Choice | Notes |
|---|---|---|
| Framework | Next.js (App Router) | SSG preferred; use `generateStaticParams` for case study routes |
| Styling | Tailwind CSS v3 | Config-driven; no inline styles, no CSS modules |
| Typography | Figtree + JetBrains Mono | Loaded via `next/font/google` — not a `<link>` tag |
| Content | MDX (flat-file) | Case studies authored in `.mdx`; no CMS for v1 |
| Hosting | Vercel | Zero-config deploys from `main` branch |
| Icons | Lucide React | Single library; no mixing icon sets |

---

## 2. Tailwind Configuration

```js
// tailwind.config.ts
import type { Config } from 'tailwindcss'

const config: Config = {
  content: ['./app/**/*.{ts,tsx}', './components/**/*.{ts,tsx}'],
  theme: {
    extend: {
      colors: {

        // ── Backgrounds ──────────────────────────────
        bg: {
          primary:  '#0F0F0F',
          elevated: '#1A1A1A',
          subtle:   '#242424',
        },

        // ── Text ─────────────────────────────────────
        text: {
          primary:   '#F0EFEB',
          secondary: '#9A9994',
          muted:     '#5C5C57',
        },

        // ── Brand Accent ──────────────────────────────
        accent: {
          DEFAULT: '#7D9E85',
          hover:   '#9BB8A3',
          subtle:  '#2A3D2E',
        },

        border: '#2E2E2E',

        // ── Semantic ──────────────────────────────────
        critical: {
          fg:     '#F87171',
          bg:     '#2D1515',
          border: '#5C2626',
        },
        warning: {
          fg:     '#FB923C',
          bg:     '#2D1A0E',
          border: '#5C3518',
        },
        pending: {
          fg:     '#FBBF24',
          bg:     '#2D2208',
          border: '#5C4510',
        },
        info: {
          fg:     '#60A5FA',
          bg:     '#0E1A2D',
          border: '#1A3558',
        },
        success: {
          fg:     '#86EFAC',
          bg:     '#0E2D1A',
          border: '#1A5C35',
        },
        neutral: {
          fg:     '#9A9994',
          bg:     '#1A1A1A',
          border: '#2E2E2E',
        },
      },

      // ── Typography ───────────────────────────────────
      fontFamily: {
        sans: ['var(--font-sans)', 'system-ui', 'sans-serif'],
        mono: ['var(--font-mono)', 'monospace'],
      },

      // ── Layout ───────────────────────────────────────
      maxWidth: {
        content: '1100px',
        prose:   '680px',
      },

      // ── Motion ───────────────────────────────────────
      transitionDuration: {
        fast: '200ms',
      },
    },
  },
}

export default config
```

---

## 3. Typography Setup

Use `next/font/google` — never a `<link>` tag. This handles preloading, eliminates layout shift, and keeps fonts self-hosted via Vercel's CDN.

```ts
// app/layout.tsx
import { Figtree, JetBrains_Mono } from 'next/font/google'

const figtree = Figtree({
  subsets: ['latin'],
  weight: ['300', '400', '500', '600', '700', '800'],
  variable: '--font-sans',
  display: 'swap',
})

const jetbrainsMono = JetBrains_Mono({
  subsets: ['latin'],
  weight: ['400', '500'],
  variable: '--font-mono',
  display: 'swap',
})

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="en" className={`${figtree.variable} ${jetbrainsMono.variable}`}>
      <body className="bg-bg-primary text-text-primary font-sans antialiased">
        {children}
      </body>
    </html>
  )
}
```

---

## 4. Token Usage Reference

### 4.1 Color Classes

| Token | Tailwind Class | Example Use |
|---|---|---|
| Background — Primary | `bg-bg-primary` | Page root, full-bleed sections |
| Background — Elevated | `bg-bg-elevated` | Cards, nav, code blocks |
| Background — Subtle | `bg-bg-subtle` | Hover states, secondary surfaces |
| Text — Primary | `text-text-primary` | Body copy, headings |
| Text — Secondary | `text-text-secondary` | Metadata, captions, labels |
| Text — Muted | `text-text-muted` | Timestamps, disabled states |
| Accent | `bg-accent`, `text-accent`, `border-accent` | CTAs, links, active nav |
| Accent Hover | `hover:text-accent-hover` | Link hover state |
| Accent Subtle | `bg-accent-subtle` | Tags, badges, chip backgrounds |
| Border | `border-border` | Card borders, dividers, inputs |

### 4.2 Semantic Color Classes

Use semantic colors only in their intended context. The pattern is always `{role}-{scale}`:

```tsx
// Status badge example
<span className="text-critical-fg bg-critical-bg border border-critical-border rounded px-2 py-0.5 text-xs font-mono">
  Critical
</span>

<span className="text-success-fg bg-success-bg border border-success-border rounded px-2 py-0.5 text-xs font-mono">
  Success
</span>
```

### 4.3 Typography Classes

| Use | Classes |
|---|---|
| Display / Hero | `font-sans text-6xl font-extrabold tracking-tight` |
| Heading 1 | `font-sans text-4xl font-bold` |
| Heading 2 | `font-sans text-2xl font-semibold` |
| Heading 3 | `font-sans text-xl font-semibold` |
| Body | `font-sans text-base font-normal leading-relaxed` |
| Small / Meta | `font-sans text-sm text-text-secondary` |
| Monospace label | `font-mono text-xs text-text-muted tracking-wide uppercase` |

### 4.4 Layout Classes

```tsx
// Content container
<div className="max-w-content mx-auto px-6 md:px-12 lg:px-20">

// Prose / reading column (case study body)
<article className="max-w-prose mx-auto">
```

---

## 5. Component Patterns

### 5.1 Primary CTA Button

```tsx
<button className="
  bg-accent hover:bg-accent-hover
  text-bg-primary
  font-sans font-semibold text-sm
  px-5 py-2.5 rounded
  transition-colors duration-fast
">
  Get in touch
</button>
```

### 5.2 Secondary CTA Button

```tsx
<button className="
  bg-transparent
  border border-accent hover:border-accent-hover
  text-accent hover:text-accent-hover
  font-sans font-semibold text-sm
  px-5 py-2.5 rounded
  transition-colors duration-fast
">
  View case study
</button>
```

### 5.3 Ghost / Tertiary Link

```tsx
<a className="
  text-text-secondary hover:text-text-primary
  font-sans text-sm
  inline-flex items-center gap-1
  transition-colors duration-fast
  group
">
  Read more
  <span className="group-hover:translate-x-0.5 transition-transform duration-fast">→</span>
</a>
```

### 5.4 Case Study Card

```tsx
<article className="
  bg-bg-elevated
  border border-border hover:border-neutral-fg
  rounded-md p-6
  hover:-translate-y-0.5
  transition-all duration-200
  cursor-pointer
">
  <p className="font-mono text-xs text-text-muted uppercase tracking-wide mb-3">
    Product · 2024
  </p>
  <h2 className="font-sans text-xl font-semibold text-text-primary mb-2">
    Project Title
  </h2>
  <p className="font-sans text-sm text-text-secondary leading-relaxed">
    One-line descriptor of the project and its scope.
  </p>
</article>
```

### 5.5 Navigation

```tsx
<nav className="
  sticky top-0 z-50
  bg-bg-primary/80 backdrop-blur-sm
  border-b border-border
  transition-all duration-200
">
  <div className="max-w-content mx-auto px-6 md:px-12 lg:px-20 h-14 flex items-center justify-between">
    <a href="/" className="font-sans font-semibold text-text-primary hover:text-accent transition-colors duration-fast">
      [Your Name]
    </a>
    <ul className="flex items-center gap-8 text-sm text-text-secondary">
      <li><a href="/work"    className="hover:text-text-primary transition-colors duration-fast">Work</a></li>
      <li><a href="/about"  className="hover:text-text-primary transition-colors duration-fast">About</a></li>
      <li><a href="/contact" className="hover:text-text-primary transition-colors duration-fast">Contact</a></li>
    </ul>
  </div>
</nav>
```

### 5.6 Status Badge (Semantic)

```tsx
type SemanticRole = 'critical' | 'warning' | 'pending' | 'info' | 'success' | 'neutral'

const badgeClasses: Record<SemanticRole, string> = {
  critical: 'text-critical-fg bg-critical-bg border-critical-border',
  warning:  'text-warning-fg  bg-warning-bg  border-warning-border',
  pending:  'text-pending-fg  bg-pending-bg  border-pending-border',
  info:     'text-info-fg     bg-info-bg     border-info-border',
  success:  'text-success-fg  bg-success-bg  border-success-border',
  neutral:  'text-neutral-fg  bg-neutral-bg  border-neutral-border',
}

function StatusBadge({ role, label }: { role: SemanticRole; label: string }) {
  return (
    <span className={`
      ${badgeClasses[role]}
      border rounded px-2 py-0.5
      font-mono text-xs uppercase tracking-wide
    `}>
      {label}
    </span>
  )
}
```

---

## 6. Motion Rules

```tsx
// ✅ Always wrap animations in reduced-motion check
const prefersReducedMotion =
  typeof window !== 'undefined'
    ? window.matchMedia('(prefers-reduced-motion: reduce)').matches
    : false

// ✅ Tailwind motion utilities
'transition-colors duration-fast'     // color/border changes
'transition-all duration-200'         // multi-property (cards)
'transition-transform duration-fast'  // arrow nudge on hover

// ✅ Page fade (using Framer Motion or CSS)
// opacity: 0 → 1, 300ms, ease
// Never: slide, flip, scale-in

// ❌ Never use
'animate-bounce'
'animate-pulse'   // unless a genuine loading state
'duration-700'    // nothing longer than 400ms
```

---

## 7. File & Folder Conventions

```
app/
├── layout.tsx           # Font setup, global styles, nav + footer
├── page.tsx             # Home
├── work/
│   ├── page.tsx         # Case study index
│   └── [slug]/
│       └── page.tsx     # Case study detail (dynamic route)
├── about/
│   └── page.tsx
└── contact/
    └── page.tsx

components/
├── ui/                  # Primitives: Button, Badge, Card
├── layout/              # Nav, Footer, Container
└── case-study/          # CaseStudyCard, CaseStudyHero, MetaStrip

content/
└── case-studies/
    ├── project-one.mdx
    └── project-two.mdx

public/
└── images/
    └── work/            # Case study assets — organized by slug
```

---

## 8. Rules & Anti-Patterns

### Do
- Use design token classes exclusively — no raw hex values in JSX
- Use `font-sans` and `font-mono` classes — never hardcode font names in JSX
- Use semantic color roles only for status, validation, and metadata — never decoration
- Wrap all transitions in `duration-fast` or `duration-200` — nothing longer
- Use `max-w-prose` for all case study body text
- Use `antialiased` on `<body>` — already set in layout

### Don't
- ❌ Use Tailwind's built-in color palette (`blue-500`, `red-400`, etc.) — use semantic tokens instead
- ❌ Use arbitrary values (`text-[#F87171]`) — if a color isn't in the config, add it to the config
- ❌ Use `style={{}}` inline styles for anything token-related
- ❌ Load fonts via `<link>` — use `next/font/google`
- ❌ Mix icon libraries — Lucide only
- ❌ Use `cursor-pointer` on non-interactive elements
- ❌ Use `!important` overrides — rethink the component instead

---

## 9. Accessibility Checklist

- [ ] All color combinations pass WCAG 2.1 AA (4.5:1 for normal text, 3:1 for large)
- [ ] Focus styles visible on all interactive elements — `focus-visible:ring-2 focus-visible:ring-accent`
- [ ] All images have descriptive `alt` text (empty `alt=""` for decorative images)
- [ ] Touch targets are minimum `44×44px` on mobile
- [ ] `prefers-reduced-motion` respected for all animations
- [ ] Semantic HTML used throughout (`<nav>`, `<main>`, `<article>`, `<section>`)
- [ ] Heading hierarchy is correct and never skipped (h1 → h2 → h3)
- [ ] No content is conveyed by color alone — always paired with text or icon

---

## 10. Handoff Notes for Claude Code

```
Stack: Next.js 14 App Router + Tailwind CSS v3 + TypeScript
Fonts: next/font/google (Figtree + JetBrains Mono) — see app/layout.tsx pattern above
Icons: lucide-react
Content: MDX flat files in /content/case-studies/
Token system: All colors via tailwind.config.ts — no raw hex in JSX, no Tailwind defaults
Do NOT use: inline styles, <link> for fonts, Tailwind default color palette, CSS modules
Key config files: tailwind.config.ts, app/layout.tsx
Acceptance criteria:
  - [ ] All classes resolve to design tokens
  - [ ] No raw color values in component files
  - [ ] Semantic colors only used for status/validation/metadata
  - [ ] Figtree loads via next/font with no layout shift
  - [ ] Reduced motion respected across all animated elements
```
