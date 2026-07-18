# Product Requirements Document
**Portfolio Redesign — Senior Designer**

> **Status:** Draft
> **Version:** 0.1
> **Last Updated:** April 2026
> **Author:** Koi Hernandez
> **Timeline:** 1–2 months

---

## 1. Overview

### 1.1 Summary
We are rebuilding a personal design portfolio from the ground up as a React-based web application. The portfolio will serve a senior Product/UX and Design Systems designer who is targeting the next step toward a Principal-level role. The site must simultaneously impress hiring managers at tech companies, attract freelance and consulting clients, and establish a distinctive personal brand — all while authentically reflecting who the designer is today, not who they were when they built their last portfolio.

### 1.2 Problem
The existing portfolio no longer reflects the designer's current skill level, depth of thinking, or career trajectory. Visitors arriving from job applications, referrals, or cold outreach encounter work and framing that undersells seniority and strategic impact. There is no unified signal that communicates "this is a Principal-level designer" — the site lacks the case study depth, systems thinking, and personal voice needed to differentiate at that level.

### 1.3 Opportunity
A designer's portfolio is their highest-leverage career asset. A strong rebuild will: (1) accelerate job search velocity by giving hiring managers and founders immediate confidence in the designer's level, (2) open freelance and consulting pipelines that currently require longer discovery conversations, and (3) create a durable personal brand platform that compounds over time. Without this, the designer continues to be evaluated on outdated evidence that does not match their actual capabilities.

---

## 2. Users & Context

### 2.1 Primary Audiences

| Audience | Context of Use | What They Need to See |
|---|---|---|
| Hiring manager / recruiter (tech company) | Scanning 20+ portfolios; time-limited; looking for level signals | Immediate credibility, strong case study titles, clear seniority indicators |
| Startup founder / small team lead | Evaluating a potential design hire or fractional partner | Problem-solving ability, systems thinking, personality fit, ROI signal |
| Agency / consultancy lead | Vetting a collaborator or specialist for a project | Range of work, craft quality, reliability, communication style |
| Freelance / consulting prospect | Referred or found via search; needs to quickly decide to reach out | Clear services, trust signals, easy contact path |

### 2.2 User Stories

| # | User Story | Priority |
|---|---|---|
| US-01 | As a hiring manager, I want to immediately understand the designer's level and specialty so I can decide if they're worth a call. | P0 |
| US-02 | As a startup founder, I want to see how this designer thinks and solves problems so I can assess fit for my team. | P0 |
| US-03 | As a freelance prospect, I want to understand what services are offered and how to engage so I can reach out quickly. | P0 |
| US-04 | As any visitor, I want to get a sense of who this person is — not just their work — so I can feel confident in the human behind the portfolio. | P1 |
| US-05 | As a returning visitor, I want to see updated work and thinking so I know the portfolio is actively maintained. | P1 |
| US-06 | As a mobile visitor, I want to browse case studies comfortably on my phone so I can review work anywhere. | P1 |

---

## 3. Requirements

### 3.1 Functional Requirements

> P0 = must ship. P1 = should ship. P2 = nice to have.

| ID | Requirement | Priority | Notes |
|---|---|---|---|
| FR-01 | Home page with clear value proposition, specialty (Product/UX + Design Systems), and career level (Senior → Principal) | P0 | Above the fold, no scrolling required |
| FR-02 | Case study pages with problem framing, process, outcomes, and impact metrics | P0 | Minimum 3 deep case studies at launch |
| FR-03 | About page that conveys personality, values, and career narrative | P0 | Differentiate from generic bio copy |
| FR-04 | Contact / engagement path (email, LinkedIn, or inquiry form) | P0 | One clear CTA on every page |
| FR-05 | Design Systems showcase section highlighting systems-level thinking and deliverables | P0 | Can be integrated into case studies or standalone |
| FR-06 | Resume / credentials accessible (PDF download or inline) | P1 | Gated or open — decision TBD |
| FR-07 | Navigation that works for both quick scanners and deep readers | P1 | Consider progressive disclosure |
| FR-08 | Project filtering or tagging by type (Product, Systems, Freelance) | P2 | Only if 6+ projects at launch |

### 3.2 Non-Functional Requirements

| ID | Requirement | Category | Target |
|---|---|---|---|
| NFR-01 | Page load performance | Performance | < 3s LCP on 4G; Lighthouse score ≥ 90 |
| NFR-02 | Mobile responsiveness | Accessibility | Fully functional at 375px and up |
| NFR-03 | Accessibility compliance | Accessibility | WCAG 2.1 AA minimum |
| NFR-04 | Uptime | Reliability | 99.9% via static hosting (Vercel, Netlify, etc.) |
| NFR-05 | SEO basics | Discoverability | Meta tags, OG images, semantic HTML, sitemap |
| NFR-06 | Privacy | Security | No unnecessary tracking; disclose any analytics |

---

## 4. Design & UX

### 4.1 User Flow

Primary path: Referred visitor or job applicant link → Landing page → Case study → About → Contact

1. Visitor arrives at home page via shared link, job application, or search.
2. Above the fold: they immediately understand who this is, what they do, and at what level.
3. They scroll or navigate to featured case studies — titles and thumbnails signal quality and scope.
4. Inside a case study: they move through problem → process → outcome, with metrics and artifacts visible.
5. They visit About to get a sense of the person behind the work.
6. They hit a clear CTA — email, LinkedIn, or contact form — and reach out.

### 4.2 Key Screens / Components

| Screen / Component | Description | Status |
|---|---|---|
| Home / Landing | Hero with name, title, specialty, and featured work. Fast-loading, strong first impression. | To design |
| Case Study — Index | Grid or list of projects with thumbnail, title, and 1-line descriptor. | To design |
| Case Study — Detail | Full case study page: problem, process, outcome, impact. Long-form scrolling layout. | To design |
| About | Personal narrative, career arc, values, photo, and what the designer is looking for. | To design |
| Design Systems Showcase | Highlights systems work: tokens, component libraries, documentation, governance. | To design |
| Contact / CTA | Persistent CTA element + dedicated contact page or section. | To design |
| Navigation | Minimal, fast, works on mobile. Possibly sticky. | To design |

### 4.3 Edge Cases & Error States

| Scenario | Expected Behavior |
|---|---|
| Visitor with no JavaScript | Core content (text, images, navigation) must still be accessible. No JS-only critical paths. |
| Mobile visitor on slow connection | Images lazy-loaded; critical text and CTAs appear before images fully load. |
| Case study NDA / restricted work | Clear "NDA — available on request" state with a prompt to reach out. |
| 404 / broken link | Custom 404 page that redirects to home and doesn't leave visitor stranded. |
| Contact form failure | Fallback to direct email address displayed inline. |
| Very long case study | Progress indicator or TOC for long-form pages to reduce abandonment. |

---

## 5. Technical Considerations

### 5.1 Approach
React-based SPA or SSG (e.g., Next.js or Vite). Case study content managed via MDX or a lightweight CMS (Contentlayer, Sanity, or flat-file markdown) to make updates easy without redeployment friction. Hosted on a JAMstack platform (Vercel preferred for React). Custom domain with HTTPS.

### 5.2 Affected Systems / Services

| System | Change Type | Notes |
|---|---|---|
| Existing portfolio site | Full replacement | Archive current site before decommissioning |
| Domain / DNS | Modified | Point to new host; ensure zero-downtime cutover |
| Analytics (optional) | New | Privacy-respecting analytics (Plausible, Fathom, or GA4) |
| Image hosting / CDN | New | Optimize all images; use CDN for case study assets |
| Email / contact | New or Modified | Form service (Formspree, Resend) or direct mailto link |

### 5.3 Data Model
Each case study will have: title, slug, tags (discipline), summary, hero image, body content (MDX), outcome metrics, and NDA flag. About page is static. Contact is stateless (form POST or mailto).

### 5.4 Security & Privacy Considerations
- No sensitive user data collected unless a contact form is added — if so, use a trusted third-party form backend.
- NDA-protected work should not be included in the public repo or deployed assets.
- Analytics, if added, should be disclosed and use privacy-respecting tooling.

---

## 6. Launch Plan

### 6.1 Rollout Strategy
- [ ] Week 1–2: Design system, component library, and home page in Figma + React.
- [ ] Week 3–4: Build and write 3 core case studies.
- [ ] Week 5–6: About page, contact, polish, accessibility audit, performance pass.
- [ ] Week 7: Soft launch — share URL with 3–5 trusted peers for feedback.
- [ ] Week 8: Hard launch — update LinkedIn, resume, and job applications to point to new URL.

### 6.2 Rollback Plan
Keep the existing portfolio live on a staging URL or archived branch until the new site has been validated by at least 5 external viewers. DNS cutover is the point of no return — delay it until confident.

### 6.3 Monitoring & Alerts
- Uptime monitoring via UptimeRobot (free tier sufficient).
- Weekly analytics check for top-visited pages and bounce rate on case studies.
- Track inbound contact rate as a proxy for conversion quality.

---

## 7. Success Metrics

| Metric | Baseline | Target | Timeframe |
|---|---|---|---|
| Inbound recruiter / founder contacts via portfolio | Current baseline (TBD) | +50% vs. old site | Within 60 days of launch |
| Case study avg. time on page | Unknown | > 3 min (signals engagement) | 30 days post-launch |
| Positive unsolicited feedback from peers / reviewers | 0 | ≥ 5 in first week of soft launch | Soft launch week |
| Lighthouse performance score | Unknown (old site) | ≥ 90 across all pages | At launch |
| Mobile usability | Unknown | 0 critical issues in Chrome DevTools audit | At launch |

### 7.1 Leading Indicators
- Positive peer feedback during soft launch.
- Strong Lighthouse scores across Performance, Accessibility, and SEO.
- All 3 core case studies completed and reviewed by a trusted designer peer.

### 7.2 Lagging Indicators
- Increased inbound contact rate within 60 days.
- Portfolio cited as a reason for interview or project offer.
- LinkedIn profile views increase after hard launch announcement.

---

## 8. Open Questions

| # | Question | Owner | Resolved? |
|---|---|---|---|
| 1 | Which case studies to feature? Need to select 3 P0 projects that best demonstrate seniority and range. | Designer | No |
| 2 | NDA work — what can be shown? What requires a password gate or "available on request" state? | Designer | No |
| 3 | Contact form or mailto? Form adds friction but enables better lead capture. | Designer | No |
| 4 | Analytics: include or not? Plausible/Fathom vs. GA4 vs. none. | Designer | No |
| 5 | Resume: public PDF download, or gated behind contact interaction? | Designer | No |
| 6 | Domain: use current domain, or new domain as part of rebrand? | Designer | No |

---

## 9. Out of Scope
- Blog or long-form writing section (can be added post-launch).
- Custom CMS with an admin UI — flat-file MDX is sufficient for v1.
- Dark mode (can be added post-launch).
- Animations or motion design beyond subtle transitions.
- Multilingual support.
- E-commerce or paid gating for any content.

---

## 10. Appendix

### Decisions Log

| Date | Decision | Rationale | Made By |
|---|---|---|---|
| April 2026 | React (custom code) over Framer / Webflow | Full creative control; no platform lock-in; demonstrates technical fluency | Designer |
| April 2026 | 1–2 month timeline | Balances speed to launch with depth of case study writing | Designer |
| April 2026 | Serve all audiences (hiring + freelance + brand) | Designer's goals span job search and consulting pipeline simultaneously | Designer |

### References
- [Add links to inspiration sites, design references, or relevant articles here]

---

## Claude Context Notes
> For AI-assisted implementation. Fill this out when handing to Claude Code.

```
Feature scope for this session: Portfolio site — home, case study index, case study detail, about, contact
Likely stack: Next.js (App Router) + Tailwind + MDX for case study content
Entry point files: app/page.tsx (home), app/work/[slug]/page.tsx (case study), app/about/page.tsx
Patterns to follow: Component-driven; mobile-first Tailwind; semantic HTML; no JS-only critical paths
Do NOT change: Domain / DNS until soft launch is validated by peers
Key acceptance criteria:
  - [ ] Lighthouse ≥ 90 across all pages
  - [ ] WCAG 2.1 AA compliance
  - [ ] 3 case studies live at launch
  - [ ] Contact CTA present on every page
  - [ ] Zero critical mobile usability issues
```
