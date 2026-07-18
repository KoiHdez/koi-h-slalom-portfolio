# Case Study Template
**Portfolio Redesign — Koi Hernandez**

> **Status:** Draft
> **Version:** 0.1
> **Last Updated:** April 2026
> **Author:** Koi Hernandez
> **Linked PRD:** Portfolio_PRD.md

This template defines the structure, writing guidance, and MDX frontmatter for every case study on the portfolio. Use it as the starting point for each project. The goal is consistency in structure, not uniformity in voice — each case study should feel like it belongs to the same site while telling a distinct story.

---

## How to Use This Template

1. Duplicate this file and rename it to the project slug (e.g. `banking-on-design.mdx`)
2. Fill in the frontmatter fields first — these power the case study index cards
3. Write each section using the guidance notes (delete the notes before publishing)
4. Flag any NDA-restricted content with `[NDA — available on request]` inline
5. Mark the file `status: draft` until it has been reviewed by at least one peer

---

## MDX Frontmatter

```mdx
---
title: ""
slug: ""
summary: ""
role: ""
client: ""
industry: ""
disciplines:
  - ""
year: ""
duration: ""
status: draft # draft | review | published
featured: false # true for P0 case studies shown on home page
nda: false # true if any portion is restricted
---
```

### Frontmatter Field Guide

| Field | Description | Example |
|---|---|---|
| `title` | Full case study title | "Banking on Design: Powering Efficiency Through Comprehensive Design Systems" |
| `slug` | URL-safe identifier | `banking-on-design` |
| `summary` | 1–2 sentence descriptor for index card | "How a 5-library Figma architecture cut design time in half for a global investment bank." |
| `role` | Your role(s) on the project | "Lead Designer, Design Systems" |
| `client` | Client description (not necessarily the name) | "Global investment bank" |
| `industry` | Industry tag | "Financial Services" |
| `disciplines` | Array of discipline tags | `["Design Systems", "UI Design"]` |
| `year` | Year of delivery | "2023" |
| `duration` | Project length | "12 months" |
| `status` | Publishing state | `draft` / `review` / `published` |
| `featured` | Show on home page | `true` / `false` |
| `nda` | Any NDA-restricted content | `true` / `false` |

---

## Case Study Structure

---

### 0. Hero

**What goes here:** A single strong image — a mockup, a design artifact, or a composed screenshot. Full-bleed on desktop. This is the first thing a visitor sees after clicking through from the index.

**Guidance:**
- Use a dark-framed mockup consistent with the site's palette
- Avoid white browser frames or stock device renders
- The image should hint at the scale or complexity of the work — not just a single screen
- If NDA prevents showing the actual work, use an abstracted or anonymized version

```mdx
<CaseStudyHero
  src="/images/work/[slug]/hero.png"
  alt="[Descriptive alt text]"
/>
```

---

### 1. Metadata Strip

**What goes here:** A compact row of project metadata displayed just below the hero. Rendered as a component — no prose needed here.

```mdx
<MetaStrip
  role="[Your role]"
  client="[Client descriptor]"
  industry="[Industry]"
  disciplines={["Tag 1", "Tag 2"]}
  year="[Year]"
  duration="[Duration]"
/>
```

---

### 2. Overview

**Word target:** 80–120 words

**What goes here:** The elevator pitch for the case study. A visitor should be able to read this and immediately understand the scale, context, and stakes of the project — before committing to reading further.

**Guidance:**
- Write this last — it's a distillation of everything below
- Lead with the situation, not your role
- Include one concrete signal of scale (company size, user count, dollar amount, timeline)
- Avoid: "I was tasked with…" / "The goal was to…" openers

**Template:**
```
[Client descriptor] needed to [core problem in one clause]. 
Over [duration], I [your primary contribution] — resulting in [top-line outcome].
```

**Example (CS-01):**
> A global investment bank needed a unified design system to bring consistency across multiple product teams working in silos. Over [X months], I led the creation of a 5-library Figma architecture used by three design pods — cutting time-to-design in half and leaving the client with the tools and governance to continue independently.

---

### 3. Problem

**Word target:** 100–150 words

**What goes here:** The tension. What was broken, missing, or at risk before this project started? Write this from the user or business perspective first — your role comes later.

**Guidance:**
- Start with the pain, not the project
- Be specific — name the friction, the inefficiency, or the missed opportunity
- If there's a dollar figure, a metric, or a user quote that captures the problem, lead with it
- One paragraph is usually enough — resist the urge to over-explain

**Prompts to get started:**
- What was failing before you arrived?
- What would have happened if this project hadn't happened?
- What did users or stakeholders complain about?

---

### 4. My Role

**Word target:** 60–100 words

**What goes here:** A clear, honest statement of what you personally owned. This is where seniority shows — not through titles, but through scope of responsibility.

**Guidance:**
- Distinguish between what you led vs. what you contributed to
- If you were one of multiple designers, say so — and clarify your lane
- Mention stakeholder relationships only if you owned them (not just attended meetings)
- Avoid: "I was responsible for…" — use active verbs instead

**Format:** Short prose or a tight 3–5 item list. Not both.

**Example (CS-02):**
> I spearheaded the core Marketplace design — from product browsing through cart and order management. I led the pre-launch user interviews, partnered directly with the Product Owner on requirements, and worked alongside developers to close the gap between design intent and implementation. I also contributed to team-wide design process improvements and strengthened the Design QA workflow.

---

### 5. Process

**Word target:** 300–600 words across all process sections

**What goes here:** How you worked. This is the longest section and the one that most clearly signals seniority. Show your thinking, not just your output.

**Guidance:**
- Break into 2–4 named sub-sections (e.g. Discovery, Define, Design, Iterate)
- Each sub-section: 1–2 paragraphs + 1 artifact image
- Emphasize decisions — what did you choose to do, and why?
- Include moments of ambiguity or constraint — how you handled them is more interesting than a clean process
- Avoid: a linear "first I did X, then Y, then Z" narrative — that's a timeline, not a story

**Sub-section structure:**
```mdx
### [Phase name]

[1–2 paragraphs of prose]

<CaseStudyImage
  src="/images/work/[slug]/[artifact].png"
  alt="[Description]"
  caption="[Optional caption]"
/>
```

**Suggested phases by discipline:**

*For Product / UX projects:*
- Discovery & Research
- Define & Prioritize
- Design & Iterate
- Validation & Testing

*For Design Systems projects:*
- Audit & Alignment
- Architecture & Foundations
- Component Build & Documentation
- Governance & Handoff

---

### 6. Outcome

**Word target:** 80–120 words

**What goes here:** What changed because of this project. Lead with metrics where they exist — then contextualize.

**Guidance:**
- Put the hardest number first
- If there are no quantitative metrics, use qualitative signals (longevity, adoption, stakeholder feedback)
- Be honest about constraints — "within a 6-week timeline" is an outcome modifier, not an excuse
- End with a forward-looking statement if relevant (what did this enable next?)

```mdx
<OutcomeCallout
  metrics={[
    { label: "Libraries delivered", value: "5" },
    { label: "Time-to-design reduction", value: "50%" },
    { label: "Teams served", value: "3" },
  ]}
/>

[1–2 paragraphs of prose contextualizing the metrics]
```

---

### 7. Reflection *(optional but recommended for P0 case studies)*

**Word target:** 60–100 words

**What goes here:** One honest, considered thought about what you learned or would do differently. This is the section that most clearly separates senior designers from junior ones — it requires self-awareness.

**Guidance:**
- One paragraph only
- Don't be falsely modest ("I should have done everything differently")
- Don't be defensive ("Given the constraints, this was the best possible outcome")
- The best reflections name a specific tension: speed vs. depth, stakeholder alignment vs. design quality, scope vs. craft

---

### 8. Next Project

**What goes here:** A link to the next case study. Rendered as a component — keeps visitors moving through your work.

```mdx
<NextProject slug="[next-case-study-slug]" />
```

---

## Full MDX Example (Skeleton)

```mdx
---
title: "Banking on Design: Powering Efficiency Through Comprehensive Design Systems"
slug: "banking-on-design"
summary: "How a 5-library Figma architecture cut design time in half for a global investment bank."
role: "Lead Designer, Design Systems"
client: "Global investment bank"
industry: "Financial Services"
disciplines: ["Design Systems", "UI Design"]
year: "2024"
duration: "X months"
status: draft
featured: true
nda: true
---

<CaseStudyHero
  src="/images/work/banking-on-design/hero.png"
  alt="Design system component library overview"
/>

<MetaStrip
  role="Lead Designer, Design Systems"
  client="Global investment bank"
  industry="Financial Services"
  disciplines={["Design Systems", "UI Design"]}
  year="2024"
  duration="X months"
/>

## Overview

A global investment bank needed a unified design system to bring consistency
across multiple product teams working in silos. Over X months, I led the creation
of a 5-library Figma architecture used by three design pods — cutting time-to-design
in half and leaving the client with the tools and governance to continue independently.

## Problem

Designers across multiple teams lacked a centralized, reliable resource for building
new experiences. The fragmentation led to inconsistencies across products, duplicated
effort, and slow delivery. Without a shared foundation, every new feature required
starting from scratch — and no one could agree on what "current state" even looked like.

## My Role

As Lead Designer for the Design Systems Pod, I owned the architecture, component
build, and governance documentation. I coordinated across three design pods to
maintain coherence, partnered with the client's development teams on timely delivery,
and acted as the design system SME throughout the engagement.

## Process

### Audit & Alignment

[How you assessed the current state and aligned stakeholders on the approach]

<CaseStudyImage
  src="/images/work/banking-on-design/audit.png"
  alt="Component audit spreadsheet"
  caption="Existing component audit across three product lines"
/>

### Architecture & Foundations

[How you structured the library system and made key architectural decisions]

<CaseStudyImage
  src="/images/work/banking-on-design/architecture.png"
  alt="5-library architecture diagram"
/>

### Component Build & Documentation

[How you built and documented the components, including any novel solutions]

<CaseStudyImage
  src="/images/work/banking-on-design/form-builder.png"
  alt="Form Builder component"
  caption="Form Builder — reduced time to create complex flows by 50%"
/>

### Governance & Handoff

[How you ensured the system could live on without you]

## Outcome

<OutcomeCallout
  metrics={[
    { label: "Libraries delivered", value: "5" },
    { label: "Time-to-design reduction", value: "50%" },
    { label: "Teams served", value: "3" },
  ]}
/>

The result was a mature, independently operable design system with content and
governance guidelines built in. Post-engagement, the client had everything needed
to maintain and evolve the system — a rarity in consulting work. The system
strengthened cross-team collaboration, optimized asset organization, and enabled
a cohesive digital experience across the bank's products.

## Reflection

[What you learned or would do differently — one honest paragraph]

<NextProject slug="life-sciences-marketplace" />
```

---

## Writing Checklist

Before marking a case study `status: review`, confirm:

- [ ] Frontmatter is complete and accurate
- [ ] Hero image is high-res, dark-framed, and has alt text
- [ ] Overview can be read in under 30 seconds and communicates scale
- [ ] Problem section starts with the user/business pain — not your role
- [ ] At least one concrete metric or measurable outcome is present
- [ ] Process section includes at least 2 artifact images
- [ ] Reflection is honest and specific — not generic
- [ ] NDA-restricted content is flagged or removed
- [ ] A peer has reviewed for clarity and voice consistency
- [ ] Next project link is set to the correct slug

---

## NDA Handling Guidance

When content is restricted, use one of these approaches consistently across all case studies:

**Option A — Available on request (recommended)**
```mdx
> 🔒 Detailed designs for this project are available on request due to NDA.
> [Get in touch →](mailto:koi.hdez@gmail.com)
```

**Option B — Abstracted artifact**
Show a real artifact with identifying details removed or blurred. Describe what it is in the caption.

**Option C — Process only**
Show your process artifacts (Miro boards, wireframe sketches, flow diagrams) without final UI screens. Process work is rarely restricted.

Never omit the outcome section because of NDA — results are almost always discussable even when designs aren't.

---

## Voice Reminders

- Write in first person, past tense: "I led…" not "Koi led…" or "The designer…"
- Start sentences with verbs: "Led the creation of…" not "I was responsible for the creation of…"
- Problem sections: present tense for the state before the project ("Designers lack…")
- Outcome sections: past tense ("The system reduced…") or present for ongoing impact ("The designs are still in use today.")
- No filler phrases: "leveraged," "robust," "seamless," "innovative," "passionate"
