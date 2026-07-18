# Design Brief
**Portfolio Redesign — Senior Designer**

> **Status:** Draft
> **Version:** 0.2
> **Last Updated:** April 2026
> **Author:** [Your Name]
> **Linked PRD:** Portfolio_PRD.md

---

## 1. Design Intent

This portfolio should feel like the designer's best work made physical — not a showcase of every project, but a deliberate, considered artifact that signals depth, craft, and seniority. The aesthetic sits at the intersection of **engineered precision** (Linear, Vercel, Stripe) and **editorial structure** (NYT, long-form publications): dark, minimal, and typographically confident without being cold or inaccessible.

The personality of the designer should come through in restraint — what's *not* there is as important as what is. No filler. No noise. Every element earns its place.

---

## 2. Aesthetic Direction

### 2.1 Mood & Tone

**Keywords:** Considered. Sharp. Quiet confidence. Intentional. Authoritative without being stiff.

The site should feel like a senior designer made it — not because it's overdesigned, but because every decision is clearly reasoned. Visitors should feel they're in capable hands before they've read a single word.

**What to avoid:**
- Overly playful or experimental UI (this is not a motion/brand portfolio)
- Generic "designer portfolio" templates (grid of thumbnails, pastel backgrounds)
- Dark mode as a style choice without purpose — the darkness should feel *earned*, not decorative
- Excessive animation or scroll-jacking

### 2.2 Visual References

| Reference | What to Borrow |
|---|---|
| Linear.app | Tight spacing, monospace details, dark backgrounds with high-contrast type, engineered feel |
| Vercel.com | Confident use of negative space, restrained color, subtle gradients and glows |
| Stripe.com | Information density done right — complex content made scannable and trustworthy |
| NYT / editorial publications | Typographic hierarchy, structured layouts, the weight that good prose-heavy design carries |

---

## 3. Color System

### 3.1 Palette

| Role | Name | Hex | Usage |
|---|---|---|---|
| Background — Primary | Near Black | `#0F0F0F` | Page backgrounds, primary surface |
| Background — Elevated | Dark Gray | `#1A1A1A` | Cards, panels, code blocks |
| Background — Subtle | Dim Gray | `#242424` | Hover states, dividers, secondary surfaces |
| Text — Primary | Off White | `#F0EFEB` | Body copy, headings |
| Text — Secondary | Warm Gray | `#9A9994` | Metadata, captions, subheadings |
| Text — Muted | Dim | `#5C5C57` | Timestamps, disabled states, decorative labels |
| Accent | Sage Green | `#7D9E85` | CTAs, links, active states, highlights |
| Accent — Hover | Sage Light | `#9BB8A3` | Hover variant of accent |
| Accent — Subtle | Sage Dim | `#2A3D2E` | Accent backgrounds, tags, badges |
| Border | Subtle Line | `#2E2E2E` | Dividers, card borders, input outlines |

### 3.2 Semantic Colors

Semantic colors carry meaning and should only be used in their intended context — never decoratively. Each has a foreground (text/icon), a background (badge/callout surface), and a border value tuned for the dark palette.

| Role | Name | Foreground | Background | Border | Usage |
|---|---|---|---|---|---|
| Critical | Red | `#F87171` | `#2D1515` | `#5C2626` | Errors, destructive actions, blockers |
| Warning | Orange | `#FB923C` | `#2D1A0E` | `#5C3518` | Caution states, at-risk items, deprecations |
| Pending | Yellow | `#FBBF24` | `#2D2208` | `#5C4510` | In-progress, awaiting action, draft states |
| Informational | Blue | `#60A5FA` | `#0E1A2D` | `#1A3558` | Neutral info, tips, contextual notes |
| Success | Green | `#86EFAC` | `#0E2D1A` | `#1A5C35` | Completed, confirmed, passing states |
| Neutral | Gray | `#9A9994` | `#1A1A1A` | `#2E2E2E` | Inactive, disabled, secondary metadata |

**Note:** The Success green (`#86EFAC`) is intentionally distinct from the brand accent sage (`#7D9E85`) — one signals system state, the other is aesthetic. Never use them interchangeably.

### 3.3 Color Rules
- The accent (sage green) is used sparingly — links, one key CTA per section, active navigation state. It should feel meaningful when it appears, not decorative.
- Semantic colors appear only in status badges, alert callouts, form validation, and case study metadata tags (e.g. project status). Not in navigation, heroes, or decorative contexts.
- No pure black (`#000000`) or pure white (`#FFFFFF`) — the off-white and near-black keep the contrast from feeling harsh.
- Backgrounds layer: `#0F0F0F` → `#1A1A1A` → `#242424` for visual depth without color.
- Gradients, if used, should be extremely subtle — a faint radial glow behind a hero element at most.

---

## 4. Typography

### 4.1 Typeface

**Primary: Figtree** (Google Fonts)
Figtree is a clean geometric sans-serif with a warmth that sets it apart from more clinical choices like Inter or Geist. It has strong weight range, excellent legibility at small sizes, and a personality that sits comfortably between engineered and editorial — well-suited to this portfolio's dual reference points.

```html
<!-- Load via Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Figtree:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
```

**Monospace: JetBrains Mono** (Google Fonts)
Used for project IDs, code snippets, technical callouts, and small decorative labels. Provides a clear contrast to Figtree without requiring a separate font service.

```html
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### 4.2 Type Scale

**Display / Hero**
- Font: `Figtree`
- Weight: 700–800
- Size: 56–72px (desktop), 36–48px (mobile)
- Usage: Name, hero headline only

**Heading 1**
- Font: `Figtree`
- Weight: 700
- Size: 36–40px (desktop), 28–32px (mobile)
- Usage: Page titles, case study titles

**Heading 2**
- Font: `Figtree`
- Weight: 600
- Size: 24–28px
- Usage: Section headers within case studies

**Heading 3**
- Font: `Figtree`
- Weight: 600
- Size: 18–20px
- Usage: Sub-sections, card titles

**Body**
- Font: `Figtree`
- Weight: 400
- Size: 16px
- Line height: 1.7
- Usage: All prose, case study body copy

**Small / Meta**
- Font: `Figtree`
- Weight: 400–500
- Size: 13–14px
- Color: Text — Secondary (`#9A9994`)
- Usage: Dates, tags, captions, project metadata

**Monospace (accent use)**
- Font: `JetBrains Mono`
- Weight: 400–500
- Usage: Project IDs, code snippets, technical callouts, small decorative labels

### 4.2 Typography Rules
- Line lengths capped at 65–70 characters for body copy — editorial standard for readability.
- Generous leading (1.7) on body; tighter (1.2–1.3) on large display headings.
- Letter-spacing: slightly loose on small uppercase labels (`0.08em`), tight or default on everything else.
- No decorative typefaces — the sans-serif does all the work through weight, size, and spacing.

---

## 5. Spacing & Layout

### 5.1 Grid
- Max content width: **1100px** (prevents over-stretching on wide screens)
- Single-column for case study body (reading-optimized)
- 12-column grid for home and index pages
- Horizontal padding: `24px` mobile, `48px` tablet, `80px` desktop (outside the max-width container)

### 5.2 Spacing Scale
Based on an 8px base unit:

| Token | Value | Usage |
|---|---|---|
| `space-1` | 8px | Inline gaps, icon padding |
| `space-2` | 16px | Component internal padding |
| `space-3` | 24px | Card padding, tight section gaps |
| `space-4` | 32px | Component separation |
| `space-6` | 48px | Section separation (mobile) |
| `space-8` | 64px | Section separation (desktop) |
| `space-12` | 96px | Major section breaks |
| `space-16` | 128px | Hero padding, page-level breathing room |

### 5.3 Layout Principles
- **Negative space is a design element.** Resist the urge to fill gaps.
- Case study pages use a narrow reading column (max 680px) centered within the content area.
- Section breaks rely on spacing and typography hierarchy — not horizontal rules or dividers (except sparingly).

---

## 6. Interaction & Motion

### 6.1 Principles
Motion should be **functional, not decorative**. Every animation should communicate something: state change, hierarchy, or relationship.

### 6.2 Interaction Patterns

| Element | Behavior |
|---|---|
| Links / CTAs | Color shift to accent-hover on hover; `200ms ease` transition |
| Navigation items | Subtle underline or color shift; no dramatic transforms |
| Case study cards | Slight lift (`translateY(-2px)`) + border brightening on hover |
| Page transitions | Fade only — `opacity 0→1`, `300ms`. No slides, no flips. |
| Image reveals | Fade in on scroll-enter (`IntersectionObserver`); no parallax |
| Cursor | Default system cursor — no custom cursors |

### 6.3 Motion Rules
- No scroll-jacking or scroll-hijacking of any kind.
- Respect `prefers-reduced-motion` — all animations wrap in a media query check.
- Duration ceiling: `400ms`. Nothing lingers.

---

## 7. Iconography & Imagery

### 7.1 Icons
- Use a single icon library — `Lucide` or `Phosphor` (both have a clean, minimal weight that fits the aesthetic).
- Icons used sparingly — navigation, external link indicators, and UI affordances only. Not decorative.
- Size: 16px or 20px. Never larger unless a specific UI moment calls for it.

### 7.2 Case Study Imagery
- Screenshots and design artifacts should be presented in **dark-framed mockups** — consistent with the site's dark background, not the default white browser frames.
- No drop shadows on images — use a subtle `1px border` in `#2E2E2E` to separate from background.
- Full-bleed images allowed at the top of case study pages (hero) — cropped and purposeful.
- Avoid stock photography entirely. Real work, real artifacts only.

### 7.3 Portrait / Personal Photo
- One photo, used on the About page.
- Should feel candid and warm — not a corporate headshot, not a posed studio shot.
- Black and white or desaturated is acceptable and may fit the palette better.

---

## 8. Voice & Tone

The writing on this site is part of the design. It should sound like a senior designer talking to a peer — not a job applicant addressing a panel.

| Context | Tone |
|---|---|
| Hero / headline | Confident, direct. No qualifiers. "I design systems that scale." not "I'm passionate about..." |
| Case study intro | Problem-first. Start with the tension, not the solution. |
| Case study body | Clear, precise, outcome-oriented. Show thinking without over-explaining. |
| About page | Human, considered, slightly personal. The one place to let personality fully show. |
| CTAs | Direct and low-pressure. "Get in touch" not "Let's connect and build something amazing!" |

**Words to avoid:** passionate, excited, leverage (verb), synergy, storytelling (as a noun-brand), "I help [x] achieve [y]" opener formulas.

---

## 9. Component Patterns

### 9.1 Navigation
- Minimal top nav: Name/logo left, 3–4 links right (Work, About, Contact + optional Resume)
- Sticky on scroll; slight background blur (`backdrop-filter`) as it sticks
- Mobile: hamburger or slide-in drawer — nothing elaborate

### 9.2 Case Study Cards (Index)
- Dark card, subtle border, project title + 1-line descriptor + discipline tag
- No hover image previews — let the title and descriptor do the work
- Optional: project year and a very small role label

### 9.3 Case Study Detail Page Structure
```
Hero image (full-bleed or contained)
↓
Project metadata strip (year, role, company, discipline tags)
↓
Overview / problem statement (1–2 paragraphs)
↓
Process sections (as many as needed, with artifact images)
↓
Outcome + metrics callout (visually distinct block)
↓
Next project link
```

### 9.4 CTAs
- Primary CTA: Sage green background, near-black text, `border-radius: 4px` — sharp, not pill-shaped
- Secondary CTA: Transparent background, sage green border + text
- Ghost / tertiary: Text-only with arrow `→`

---

## 10. Open Design Decisions

| # | Decision | Options | Status |
|---|---|---|---|
| 1 | Logo usage | Use existing logo / wordmark only / no logo — name in type | Unresolved |
| 2 | Font selection | **Resolved — Figtree (Google Fonts)** | Resolved |
| 3 | Home page hero format | Name + title + tagline / full-bleed featured project / split layout | Unresolved |
| 4 | Case study card style | Image thumbnail / text-only / minimal abstract graphic | Unresolved |
| 5 | About page photo | Color vs. desaturated / candid vs. environmental | Unresolved |
| 6 | Accent color final value | `#7D9E85` as specified — verify contrast ratios against all bg values | To verify |

---

## 11. Accessibility Notes
- All text must meet WCAG 2.1 AA contrast ratios — verify accent color (`#7D9E85`) on all background values before finalizing.
- Focus states must be clearly visible — use a `2px solid` accent-colored outline, not browser default.
- All images require descriptive alt text, including case study artifacts.
- Interactive elements must have a minimum touch target of `44x44px` on mobile.

---

## Appendix: Quick Reference Tokens

```css
/* Colors — Brand */
--color-bg-primary:     #0F0F0F;
--color-bg-elevated:    #1A1A1A;
--color-bg-subtle:      #242424;
--color-text-primary:   #F0EFEB;
--color-text-secondary: #9A9994;
--color-text-muted:     #5C5C57;
--color-accent:         #7D9E85;
--color-accent-hover:   #9BB8A3;
--color-accent-subtle:  #2A3D2E;
--color-border:         #2E2E2E;

/* Colors — Semantic */
--color-critical-fg:    #F87171;
--color-critical-bg:    #2D1515;
--color-critical-border:#5C2626;

--color-warning-fg:     #FB923C;
--color-warning-bg:     #2D1A0E;
--color-warning-border: #5C3518;

--color-pending-fg:     #FBBF24;
--color-pending-bg:     #2D2208;
--color-pending-border: #5C4510;

--color-info-fg:        #60A5FA;
--color-info-bg:        #0E1A2D;
--color-info-border:    #1A3558;

--color-success-fg:     #86EFAC;
--color-success-bg:     #0E2D1A;
--color-success-border: #1A5C35;

--color-neutral-fg:     #9A9994;
--color-neutral-bg:     #1A1A1A;
--color-neutral-border: #2E2E2E;

/* Typography */
--font-sans:  'Figtree', system-ui, sans-serif;
--font-mono:  'JetBrains Mono', monospace;

/* Spacing */
--space-1:  8px;
--space-2:  16px;
--space-3:  24px;
--space-4:  32px;
--space-6:  48px;
--space-8:  64px;
--space-12: 96px;
--space-16: 128px;

/* Layout */
--max-width-content:    1100px;
--max-width-prose:      680px;

/* Motion */
--duration-fast:    200ms;
--duration-default: 300ms;
--ease-default:     ease;
```
