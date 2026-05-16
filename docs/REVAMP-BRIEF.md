# Zenith Digital MENA — Revamp Brief

A working document for the full revamp of `zenithdigitalmena.com`. Treat this as version 1.0: locked enough to act on, editable as reality teaches us things.

> **How to use this document.** Read it once end-to-end. Then work through Section 8 (Rollout Plan) one step at a time, pasting the Claude Code prompts into your terminal. Sections 1–7 are reference; Section 8 is the playbook; Section 9 is the warning label.

---

## Table of Contents

1. Strategic Foundation
2. Visual Identity & Design System
3. Information Architecture & Page Choreography
4. Copy Direction & Voice
5. Content Architecture & Authoring
6. Features & Integrations
7. MCP Setup
8. Rollout Plan
9. Honest Risks & Watchpoints
10. The Closing Frame

---

## Section 1 — Strategic Foundation

### 1.1 The brand in one sentence
Zenith is a Dubai-based digital studio engineering brand systems, products, and intelligent automation for the GCC's most ambitious operators.

### 1.2 The job of the new website
Convert warm, sophisticated traffic — primarily referrals, second-order outbound, and search traffic looking for a credible MENA digital partner — into qualified inquiries for $50K+ engagements.

The site must do three things, in priority order:

1. **Reinforce a referral within 60 seconds** so warm traffic doesn't cool.
2. **Validate Zenith for outbound** so cold links sent in LinkedIn / email convert.
3. **Demonstrate a clear point of view** that signals judgment-grade thinking, not commodity execution.

### 1.3 Strategic constraints we accept
- **Brand-led, fully anonymized.** No founder names, no founder photos, no client names, no testimonials, no logo wall.
- **Proof comes from the design itself, the methodology, the writing, and (eventually) 1–2 deeply written anonymized case studies.**
- **The site must read as expensive at first glance and intelligent on the second.**

### 1.4 Audience profile
- **Primary:** CMOs, founders, COOs, family-office MDs at GCC fintechs, real-estate groups, and family-owned conglomerates ($30M+ revenue or Series B+ stage).
- **Secondary:** Senior marketing / product leaders evaluating regional partners on behalf of executive teams.
- **Visual diet:** Linear, Notion, Stripe, Bloomberg, FT, *The Economist*, Apple product pages. They will judge the site against this baseline, not against other agencies.

### 1.5 Success, 90 days post-launch
- Bilingual EN / AR with parity across all pages.
- A measurable lift in form submissions vs. the old `mailto:` link (instrumented via analytics).
- Every referred prospect who lands on the site emails or books a call within 7 days of first visit.
- At least one inquiry per month attributable to the `/thinking` section, signalling the POV is doing its job.

---

## Section 2 — Visual Identity & Design System

### 2.1 Voice & tone
- **Confident, never loud.** Statements, not slogans.
- **Specific over abstract.** "11 weeks to ship a unified KYC system" beats "we transform digital experiences."
- **Plural we, not royal we.** "We engineer," not "we craft beautiful experiences."
- **No agency clichés.** Banned word list lives in §4.2.
- **Sentence case in headlines.** Title Case Reads Like A 2010 Brochure.
- **Numbers as proof.** Whenever a claim can carry a number, it carries a number.

### 2.2 Color system

**Surfaces**
- `--bg-primary: #050507` — deep near-black, hero and dramatic sections
- `--bg-secondary: #0A0A0C` — default page background
- `--bg-tertiary: #111114` — cards, elevated surfaces
- `--bg-inverse: #FAFAFA` — rare; CTAs, full-bleed inverse moments

**Text**
- `--text-primary: #FAFAFA`
- `--text-secondary: rgba(250, 250, 250, 0.72)`
- `--text-tertiary: rgba(250, 250, 250, 0.45)`
- `--text-quaternary: rgba(250, 250, 250, 0.28)` — microcopy, eyebrow labels

**Accent (the only non-monochrome color on the site)**
- `--accent-primary: #6BA0D8` — headline accent words, geometric anchor, key data points
- `--accent-soft: #A8C5E0` — secondary highlights, hover states
- `--accent-deep: #1E4A78` — ambient gradients, behind-the-scenes glow

**Borders**
- `--border-subtle: rgba(250, 250, 250, 0.06)` — default dividers
- `--border-default: rgba(250, 250, 250, 0.12)` — card borders, input borders
- `--border-strong: rgba(250, 250, 250, 0.25)` — hover, focus

> **Rule:** No other colors anywhere on the site. No green, no red, no warning yellow. Status states use accent-primary or text-secondary only.

### 2.3 Typography

**Two faces, no exceptions.**

- **Display sans (EN):** *Geist* — free, modern, designed by Vercel. Reads as engineered without being cold.
- **Display sans (AR):** *IBM Plex Sans Arabic* — free, technical, optically matches Geist when scaled correctly.
- **Mono:** *Geist Mono* — same family harmony.
- **Weights used:** 400 regular, 500 medium. **No 600 or 700.** Heavier weights look amateurish on dark backgrounds at large sizes.
- **Letter-spacing:** -0.045em at 88px+, scaling down to -0.02em at 24px.

**Locked CSS variables**
```css
--font-display: 'Geist', system-ui, sans-serif;
--font-display-ar: 'IBM Plex Sans Arabic', system-ui, sans-serif;
--font-mono: 'Geist Mono', ui-monospace, monospace;
```

Self-host fonts (woff2 only, subset to needed glyphs) for performance and reliability. Latin subset for Geist; Arabic subset for Plex.

### 2.4 Type scale

| Role | Size | Weight | Line-height | Letter-spacing |
|---|---|---|---|---|
| Hero display | 88–120px (clamp) | 500 | 0.92 | -0.045em |
| Section title | 56–72px | 500 | 1.0 | -0.035em |
| Subtitle | 32–40px | 400 | 1.15 | -0.02em |
| Lead paragraph | 20–22px | 400 | 1.45 | -0.01em |
| Body | 16–17px | 400 | 1.55 | 0 |
| Small | 14px | 400 | 1.5 | 0 |
| Eyebrow (mono) | 10–11px | 500 | 1 | 0.18em uppercase |

### 2.5 Spacing & layout
- **Container:** max-width 1280px, horizontal padding `clamp(20px, 4vw, 56px)`.
- **Vertical rhythm:** 8px base unit. Section padding `clamp(80px, 12vh, 180px)` top and bottom. Cinematic sites need air.
- **Grid:** 12-column desktop, 4-column tablet, 1-column mobile. Most content uses 6–8 columns; the wide grid is for asymmetric moments.

### 2.6 Motion

- **Library:** GSAP 3.12+ with ScrollTrigger plugin, plus Lenis for smooth scroll. Loaded on the homepage and any page with scroll-driven sections; lazy-loaded elsewhere.
- **Easing:** `power3.out` for entrances, `power2.inOut` for transforms, `expo.out` for hero reveals. **No bounces.** No elastic. No `back.ease`. Cinematic = restrained.
- **Duration:** 600–900ms hero reveals; 300–500ms hover; 1.2–2s pinned scroll scenes.
- **Stagger:** 60–80ms between siblings.
- **Scroll choreography pattern:** every page has 3–7 scenes. A scene is a section that pins, transforms, then releases. Use ScrollTrigger's `pin` + `scrub`. Reference: Apple AirPods Pro page, Apple Vision Pro page.
- **Reduced motion:** respect `prefers-reduced-motion: reduce` everywhere. All animations gracefully degrade to instant state transitions.

### 2.7 The geometric language

The hero artifact is a recurring visual motif used across the site, not just on the homepage.

- **Building blocks:** concentric circles, intersecting ellipses, triangular geometry, a glowing core point, sparse satellite points.
- **Style:** thin strokes (0.5–1.5px), low opacity (40–90%), single accent color over deep glow.
- **Variations per page:** homepage (full piece, rotating); services (simplified, one motif per service); case / practice (one geometric anchor per scene); thinking (smaller, top-of-article ornament); contact (a single open ring).
- **Implementation:** SVG with GSAP-driven rotation / morphing. Three.js only if we later want depth, but SVG-first to keep weight down and Arabic-mirroring trivial.

### 2.8 Bilingual & RTL

- **Routing:** locale-prefixed paths. EN at `/`, AR at `/ar/`. Astro i18n handles this natively.
- **Direction:** `<html dir="rtl" lang="ar">` on AR pages. All layout uses CSS logical properties (`margin-inline-start`, etc.) so it mirrors automatically.
- **Component mirroring:** the geometric artifact, navigation, hero alignment, and CTAs all mirror. ScrollTrigger animations work identically regardless of direction.
- **Language switcher:** top-right of the header, simple `EN / ع` toggle. Persists in `localStorage` and cookie.
- **Content authoring:** Astro Content Collections with locale field. Each piece of content has `en` and `ar` versions linked by a shared `linkedSlug`.
- **Fallback:** if AR translation is missing, show EN with a small "الترجمة العربية قيد الإعداد" notice rather than 404.

---

## Section 3 — Information Architecture & Page Choreography

### 3.1 Site map

```
/                              Home (EN)
/ar/                           Home (AR)

/practice                      How an engagement actually runs (formerly /work)
/ar/practice

/services                      How we work + what we offer
/ar/services

/thinking                      POV essays (replaces /blog)
/ar/thinking
/thinking/[slug]               Individual essay
/ar/thinking/[slug]

/about                         The studio (methodology-led)
/ar/about

/contact                       Start a project
/ar/contact

/legal/privacy                 Privacy notice
/legal/terms                   Terms (if relevant)
```

**Renamed from old site:** `/blog` → `/thinking`. 301 redirect required.
**Renamed from old site:** `/work` → `/practice`. 301 redirect required.
**Added:** `/legal/*` for privacy compliance (GDPR + UAE PDPL).

### 3.2 Navigation

**Header (sticky on scroll, always visible)**
```
[Zenith · Digital MENA]   Practice  Services  Thinking  About   [Start a project]   [EN/ع]
```
- Logo left, primary nav center, CTA + language switcher right.
- On scroll past 80px: header shrinks to compact mode (smaller logo, tighter padding).
- Mobile: hamburger opens full-screen nav with same items, plus language switcher and contact link.
- "Start a project" is the **only filled button** anywhere on the site. Every other CTA is text + arrow.

**Footer (consistent across all pages)**
- Wordmark + tagline.
- Three column links: navigation, contact, legal.
- Single email: `contact@zenithdigital.me` (NOT `mailto:`, copy-to-clipboard with "copied" confirmation).
- Studio LinkedIn (not founders').
- Copyright + `Made in Dubai`.

### 3.3 Home (`/`)

**Scene 1 — Hero**
- Full viewport. Headline staggers in over 800ms with mask reveal.
- Geometric artifact rotates slowly (one full rotation per ~60s).
- Bottom strip fades in last. "Scroll to enter" pulses softly.

**Scene 2 — Statement of intent (pinned)**
- Background: pure black.
- One sentence in 72px type, fades in word-by-word as you scroll: *"We work with founders and operators who treat digital craft as a competitive advantage, not a cost center."*
- Geometric anchor (small) sits to the side.

**Scene 3 — What we do (services preview)**
- Four service blocks revealed in sequence: 01 Brand Systems / 02 Product Engineering / 03 Digital Strategy / 04 Intelligent Automation.
- Each block: number, name, one-line description, small geometric variant.
- On hover: subtle scale + geometric rotation.

**Scene 4 — Statement scene (POV anchor)**
- Pinned. Massive headline scales in: *"Most digital work in the GCC is shipped before it's designed."*
- Subhead: *"We're a small studio building the alternative."*
- CTA: *Read our thinking →*

**Scene 5 — Thinking preview**
- 2–3 most recent essays from `/thinking` as cards.
- Each card: eyebrow (date + read time), title, 1-line excerpt.
- "Read all thinking →" link.

**Scene 6 — Closing CTA**
- Black background. Single line *"What are you building next?"* in 88px.
- "Start a project →" CTA centred below. Footer follows.

**Total scroll length:** ~5.5 viewports.

### 3.4 Practice (`/practice`)

Reframed from "Work" to a deep, methodology-led page on how an engagement actually runs at Zenith. No case studies; structured process content.

**Scene 1 — Page hero**
- Eyebrow: `OUR PRACTICE`
- Headline: *"How an engagement actually runs."*
- Subhead: *"Most agencies hide their process behind a sales call. We publish ours."*

**Scene 2 — The four phases (one pinned scene each)**
- **Discover (1–2 weeks):** what we read, who we talk to, what we look for, what the deliverable is.
- **Define (1 week):** the signed decisions document. What's in it. Why ten pages or fewer.
- **Build (4–12 weeks):** two-week increments, end-of-week demos, how we ship, what your team sees and when.
- **Compound (ongoing or hand-off):** retainer vs. clean exit, how we decide which.

Each phase: a geometric anchor, 2–3 paragraphs, a representative artifact (e.g. a redacted decisions doc page, a sample sprint structure), and 1 quote-style operating principle.

**Scene 3 — What we don't do**
- A short, specific list of refusals. *"We don't do trapped retainers. We don't sell juniors at senior rates. We don't write decks."*

**Scene 4 — Closing CTA**

### 3.5 Services (`/services`)

**Scene 1 — Page hero**
- Eyebrow: `HOW WE WORK`
- Headline: *"Four disciplines, one operating principle."*
- Subhead: *"We engineer brand, product, strategy, and automation as a single integrated practice. Specialized, not siloed."*

**Scene 2 — The operating principle (pinned)**
- *"We start with the smallest version of the problem that's worth solving, then build outward."*
- Three principles follow: refuse scope inflation; refuse projects that won't compound; senior practitioners on every meeting.

**Scene 3 — Four disciplines (one scene each)**
For each discipline: geometric variant, 2–3 paragraphs of *how we approach it*, a list of typical deliverables, and an industry-grounded observation (see §4.3 for exact copy).

- **Brand Systems** — identity, naming, voice, design systems
- **Product Engineering** — web, mobile, internal tools, technical architecture
- **Digital Strategy** — positioning, market entry, growth strategy
- **Intelligent Automation** — AI workflows, data systems, internal tooling

**Scene 4 — How an engagement runs**
- The 4-step process from /practice, abbreviated.
- Link: *See how we run an engagement → /practice*

**Scene 5 — Closing CTA**

> **Removed from old site:** Photography & Videography, Digital Marketing & Growth. They diluted the premium positioning. Can be reintroduced as add-ons later if needed.

### 3.6 Thinking (`/thinking`)

**Scene 1 — Page hero**
- Eyebrow: `THINKING`
- Headline: *"How we see digital work in the GCC."*
- Subhead: *"Notes on craft, market, and the gap between what's built and what should be."*

**Scene 2 — Featured essay**
- Newest or strongest essay, full-width card. Eyebrow (date · read time · category), 40px title, 2-line excerpt, *Read →*.

**Scene 3 — Essay grid**
- Remaining essays, 2-column desktop / 1-column mobile, newest first.
- Optional category filter: `All · Strategy · Craft · Market · Practice`.

**Individual essay (`/thinking/[slug]`):**
- Hero: eyebrow, title, date, read time.
- Body: narrow column (640px max), 18–19px body, line-height 1.7, generous spacing, subtle geometric ornaments at section breaks.
- Byline: `Zenith Digital` (no individual name).
- Footer: *"If this resonates, we'd like to hear what you're building."* + contact link, plus optional email signup.
- Reading progress bar at top.

**Empty state (pre-launch):**
> *We're publishing here in Q3 2026. If you'd like to be notified when we do, leave your email below.*

**Launch content target:** 4–6 essays (1,200–2,000 words each) before public launch. See §5.3.

### 3.7 About (`/about`)

**Scene 1 — Page hero**
- Eyebrow: `ABOUT THE STUDIO`
- Headline: *"A small, deliberate practice."*
- Subhead: *"Founded in 2022. Based in Dubai. Working across the GCC and Egypt."*

**Scene 2 — What we believe (pinned)**
- 5 short statements of operating belief, written as principles. Full copy in §4.3.

**Scene 3 — How we work**
- Plain-English description of an engagement, reusing the 4-phase process. 2–3 paragraphs.

**Scene 4 — The studio**
- One paragraph: small studio of senior practitioners, deliberately small, location, reach.
- No photos, no names, no count. Geometric ornament.

**Scene 5 — Closing CTA**

### 3.8 Contact (`/contact`)

**Scene 1 — Page hero**
- Eyebrow: `START A PROJECT`
- Headline: *"Tell us what you're building."*
- Subhead: *"We respond to every serious inquiry within two business days."*

**Scene 2 — The form**
- Single column, generous spacing. Fields:
  - Name (required)
  - Email (required)
  - Company (required)
  - Role (optional)
  - Project type — *Brand · Product · Strategy · Automation · Not sure yet*
  - **Project scale** — *Small (focused, single-discipline) · Mid (multi-discipline, 2–3 months) · Large (strategic or retainer, 3+ months)*
  - Tell us about it (textarea, required, with placeholder: *"Where you are, where you're trying to go, and what's getting in the way."*)
  - Where did you hear about us? (optional)
- Submit: *Send →*
- On success: confirmation message + next-steps + email link.

**Scene 3 — Direct line**
- *"If you'd rather skip the form, write to us at contact@zenithdigital.me. We read every email."*

**Scene 4 — What happens next**
- Three steps: We read it. We reply within 2 business days. We schedule a 30-minute call to see if there's a fit.

---

## Section 4 — Copy Direction & Voice

### 4.1 Voice principles

1. **Statements, not slogans.** A statement is a claim about the world.
2. **Numbers do the heavy lifting.** Whenever a claim can carry a number, it carries a number.
3. **Specificity is the only premium signal we have.** Sectors, timeframes, technologies, methodology — all named.
4. **Sentence-level discipline.** Active voice. One idea per sentence. Em-dashes are allowed.
5. **Reading level: smart, not academic.** *Economist*, not *HBR*.
6. **Arabic is a parallel rewrite, not a translation.** Native review required for headlines and key copy.

### 4.2 Banned-words list

Do not use anywhere on the site, in any locale:

> transform, leverage, synergy, journey, ecosystem, holistic, partner with, unleash, empower, bespoke, tailored, world-class, cutting-edge, passionate, dedicated, drive results, take to the next level, push boundaries, reimagine, reinvent, robust, seamless, end-to-end, future-proof, dynamic, innovative, solutions

Use plain alternatives: *build, work on, design, engineer, ship, deliver, run, help, lead, refuse, choose, decide.*

### 4.3 Locked copy, by page

#### Home

**Hero**
- Eyebrow: `NOW BOOKING — Q3 2026`
- Headline: *Built for what's next.*
- Subhead: *A digital studio engineering brand systems, products, and intelligent automation for the GCC's most ambitious operators.*
- Primary CTA: *Start a project →*
- Secondary CTA: *See how we work →*
- Bottom strip: `EST. 2022 · DUBAI` · `SECTORS: FINTECH · REAL ESTATE · FAMILY OFFICES` · `LANGUAGES: EN · العربية`

**Scene 2 — Statement**
> *"We work with founders and operators who treat digital craft as a competitive advantage, not a cost center."*

**Scene 3 — Services preview**

| 01 | Brand Systems | Identity, voice, and design systems built to scale across products, languages, and channels. |
| 02 | Product Engineering | Web, mobile, and internal tools, engineered for performance, accessibility, and the long term. |
| 03 | Digital Strategy | Positioning, market entry, and growth strategy for teams operating in the GCC and Egypt. |
| 04 | Intelligent Automation | AI workflows and data systems that move work off your team and onto infrastructure. |

**Scene 4 — POV anchor**
- Headline (massive): *"Most digital work in the GCC is shipped before it's designed."*
- Subhead: *"We're a small studio building the alternative."*
- CTA: *Read our thinking →*

**Scene 5 — Thinking preview**
- Section eyebrow: `THINKING`
- Section title: *How we see digital work in the GCC.*
- (Content from Content Collections.)

**Scene 6 — Closing**
- Headline: *What are you building next?*
- CTA: *Start a project →*

#### Practice

**Hero**
- Eyebrow: `OUR PRACTICE`
- Headline: *How an engagement actually runs.*
- Subhead: *Most agencies hide their process behind a sales call. We publish ours.*

**Phase content (you to write in Phase 1):** detailed 2–3 paragraph descriptions of Discover, Define, Build, Compound, with representative artifacts where possible.

**What we don't do:**
> We don't do trapped retainers. We don't sell juniors at senior rates. We don't write decks. We don't take projects we don't believe will compound.

**Closing:** *Start a project →*

#### Services

**Hero**
- Eyebrow: `HOW WE WORK`
- Headline: *Four disciplines, one operating principle.*
- Subhead: *We engineer brand, product, strategy, and automation as a single integrated practice. Specialized, not siloed.*

**Operating principle:**
> *"We start with the smallest version of the problem that's worth solving, then build outward."*
>
> Three things follow:
> 01. **We refuse scope inflation.** A 12-week project that ships beats a 12-month project that doesn't.
> 02. **We refuse projects we don't believe will compound.** Polish for its own sake isn't craft.
> 03. **We refuse to sell juniors at senior rates.** The person who sold you the work is on the work.

**Brand Systems**
- *What it is.* Identity, naming, voice, design systems, and the rules that hold them together over time.
- *How we approach it.* We build brand as a system, not a logo. We design for Arabic at the same moment we design for English, because retrofitting a Latin-first system into Arabic is how brands break.
- *What you'll get.* A defined identity, a working design system (Figma library + Tailwind / Tokens implementation), and documentation a future team can use without us.
- *What we see in the work.* *Most regional brands we encounter were built English-first and bolted Arabic on later. The system breaks within a year. We treat Arabic and English as one design problem from day one — which is roughly how the best Gulf brands of the next decade will be built.*

**Product Engineering**
- *What it is.* Web, mobile, and internal tools, engineered for performance, accessibility, and the long term.
- *How we approach it.* We pick the smallest stack that does the job. Astro and Next.js for marketing and content surfaces. TypeScript everywhere. Core Web Vitals, accessibility, and conversion are tracked from day one.
- *What you'll get.* Production code we maintain or hand off. Documentation, performance budgets, and a system your team can extend.
- *What we see in the work.* *Onboarding flows in regulated MENA fintech routinely lose 30–60% of users between sign-up and verified account. The variance is almost entirely about how the work is run, not which framework is chosen. We run it carefully.*

**Digital Strategy**
- *What it is.* Positioning, market entry, and growth strategy for teams operating in the GCC and Egypt.
- *How we approach it.* Strategy is decisions, not decks. We work in writing. Every engagement ends with a short, signed document of decisions made — ten pages or fewer — that the executive team can act on the next morning.
- *What you'll get.* A defensible position, a market-entry plan or growth thesis, and the operating decisions needed to execute it.
- *What we see in the work.* *Most market-entry plans for the GCC fail at the same point: founders treat Arabic-language product as a translation step at month nine, instead of a design constraint at month one. The strategy work has to be done before the engineering, or it isn't strategy.*

**Intelligent Automation**
- *What it is.* AI workflows, data systems, and internal tooling that move work off your team and onto infrastructure.
- *How we approach it.* We're skeptical of AI theater. We build automation where the math works: where the work is repeatable, the cost of error is bounded, and the team has capacity to maintain what we ship. Small models, narrow workflows, obvious wins first.
- *What you'll get.* Working systems your team owns. Documentation. A clear handoff. We tell you when automation is the wrong answer.
- *What we see in the work.* *AI is currently being sold into the GCC at the abstraction level of "transformation." Most of it will not ship. The work that does ship will look like document routing, queue management, and triage — narrow, boring, and quietly compounding. That's the work we like.*

**How an engagement runs (abbreviated):**
> 01. **Discover** (1–2 weeks). We learn your business, your team, and the actual problem.
> 02. **Define** (1 week). We write down what we're doing, why, and what success looks like. Both sides sign.
> 03. **Build** (4–12 weeks). Two-week increments, end-of-week demos. You see the work as it's made.
> 04. **Compound** (ongoing or hand-off). Retainer or clean exit. Both fine. Trapped retainers aren't.

#### Thinking

**Hero**
- Eyebrow: `THINKING`
- Headline: *How we see digital work in the GCC.*
- Subhead: *Notes on craft, market, and the gap between what's built and what should be.*

**Empty state:**
> *We're publishing here in Q3 2026. If you'd like to be notified when we do, leave your email below.*

#### About

**Hero**
- Eyebrow: `ABOUT THE STUDIO`
- Headline: *A small, deliberate practice.*
- Subhead: *Founded in 2022. Based in Dubai. Working across the GCC and Egypt.*

**What we believe**
> 01. **We work with fewer clients, more deeply.** A handful of engagements at a time, not a roster.
> 02. **We refuse projects we don't believe will compound.** Polish for its own sake is not craft.
> 03. **We bring senior practitioners to every meeting.** The people who sold the work are the people doing it.
> 04. **We treat language as part of the work.** In a region where half the audience reads right-to-left, that's not a translation problem — it's a design and engineering one.
> 05. **We measure what we ship.** Performance, accessibility, conversion, and outcome — named in advance, tracked after.

**How we work**
> Engagements run in four phases — Discover, Define, Build, Compound. We work in two-week increments with end-of-week demos, in writing, never in slideware. Most projects ship in 6–14 weeks. We're not a fit for projects shorter than that, or longer than six months without a clear compounding plan.

**The studio**
> *Zenith is a small studio of senior practitioners across strategy, design, and engineering. We deliberately keep the team small enough that everyone stays close to the work. Based in Dubai, working across the GCC, with current and recent engagements in the UAE, Saudi Arabia, and Egypt.*

#### Contact

**Hero**
- Eyebrow: `START A PROJECT`
- Headline: *Tell us what you're building.*
- Subhead: *We respond to every serious inquiry within two business days.*

**Form labels**
- Your name
- Email
- Company
- Your role (optional)
- What kind of project? *Brand · Product · Strategy · Automation · Not sure yet*
- Project scale? *Small (focused, single-discipline) · Mid (multi-discipline, 2–3 months) · Large (strategic or retainer, 3+ months)*
- Tell us about it. *Where you are, where you're trying to go, and what's getting in the way.*
- Where did you hear about us? (optional)
- Submit: *Send →*

**On success**
> *Thanks. We've received it. We read every inquiry personally and reply within two business days. If your project is time-sensitive, you can also email us directly at contact@zenithdigital.me.*

**Direct line:**
> *If you'd rather skip the form, write to us at contact@zenithdigital.me. We read every email.*

**What happens next**
> 01. **We read it.** Personally, not through a triage tool.
> 02. **We reply within two business days.** Either with questions, a calendar link, or an honest "we're not the right fit, here's who might be."
> 03. **We schedule a 30-minute call.** No pitch. We listen, ask questions, and decide together if there's a fit.

---

## Section 5 — Content Architecture & Authoring

### 5.1 Astro Content Collections

```
src/content/
├── thinking/
│   ├── en/
│   └── ar/
├── services/        (4 disciplines, EN + AR)
│   ├── en/
│   └── ar/
└── pages/           (long-form blocks reused across pages)
    ├── en/
    └── ar/
```

### 5.2 Frontmatter schema (`thinking`)

```yaml
---
title: "Designing for Arabic isn't translating"
slug: "designing-for-arabic"
locale: "en"
linkedSlug: "designing-for-arabic"   # links EN/AR versions
publishedDate: 2026-09-12
readTimeMinutes: 8
category: "Craft"   # Craft | Strategy | Market | Practice
excerpt: "One paragraph, used in cards and meta description."
ogImage: "/og/thinking-designing-for-arabic.png"
draft: false
---
```

### 5.3 Founder homework

**Phase 1 (before launch):**
- Final approval / edit pass on §4.3 copy.
- 4–6 thinking essays in EN, 1,200–2,000 words each. (Heaviest lift; most important.)
- The 5 *what we believe* statements on /about (already drafted; review).
- The /practice deep content — 2–3 paragraphs per phase + representative artifacts.

**Phase 2:**
- AR translations / rewrites of UI strings and at least 2 essays.
- Additional thinking essays (target: 1–2 new per quarter).

**Phase 3:**
- First real anonymized case study, when an engagement is complete and clients permit.

### 5.4 Possible essay topics to consider

1. *"Why most MENA fintech onboarding still loses 40% of users — and why it's not the UI."*
2. *"The case against 'transformation' as a service category."*
3. *"What family offices actually want from a digital partner (and almost never get)."*
4. *"AI automation in the GCC: where it works, where it's theater."*
5. *"Designing for Arabic isn't translating — three years of mistakes."*
6. *"A note on craft: how we decide what's good enough to ship."*

### 5.5 Bilingual workflow

- Phase 1 launch: all UI copy bilingual; thinking essays EN-only.
- Missing AR translations gracefully degrade to EN with a small "translation in progress" notice.
- All UI strings live in `src/i18n/strings.json`, EN and AR keys side by side.

---

## Section 6 — Features & Integrations

### 6.1 Contact form

- **Implementation:** Astro form → Cloudflare Pages Function (`functions/contact.ts`).
- **Email delivery:** Resend API (free tier covers low volume).
- **Anti-spam:** honeypot + server-side rate limit (5/hour per IP via Cloudflare KV). No reCAPTCHA.

### 6.2 Analytics

- **Recommended:** Plausible or Cloudflare Web Analytics — privacy-friendly, no cookie banner needed, lightweight.
- **Events:** `form_submit` (with project type + scale, anonymized), `cta_click_start_project`, `cta_click_email_copy`, `essay_read_complete` (>80% scroll), `language_switch_en_ar` and reverse.

### 6.3 SEO infrastructure

- Per-page meta via Layout props: `title`, `description`, `ogImage`, `canonical`, `locale`, `alternateLocale`.
- Astro Sitemap integration → `/sitemap-index.xml` covering both locales.
- Explicit `robots.txt`.
- OG images dynamically generated per page (`@vercel/og` or similar): 1200x630 PNG, page title in site typography over dark background.
- Structured data: `Organization` schema in Layout, `Article` schema on thinking essays.
- `hreflang` tags pairing EN / AR versions.

### 6.4 Performance budgets

- Lighthouse: ≥90 mobile, ≥95 desktop.
- LCP < 2.5s, FID < 100ms, CLS < 0.1.
- Initial homepage JS: < 80KB gzipped (GSAP + ScrollTrigger + Lenis fits with care).
- Fonts: self-hosted, preloaded, woff2, subset.
- Images: WebP / AVIF with fallbacks, lazy-loaded below the fold.

### 6.5 Accessibility

- WCAG 2.2 AA target.
- Keyboard-only navigation on every page.
- Visible focus rings in accent colour.
- `prefers-reduced-motion` respected for all GSAP animation.
- Text contrast ≥4.5:1.
- `lang` attributes correctly set on EN and AR pages.

### 6.6 Privacy

- Plausible / Cloudflare Web Analytics use no cookies → no consent banner legally required.
- `/legal/privacy` page covers GDPR + UAE PDPL basics.

---

## Section 7 — MCP Setup

### 7.1 Recommended servers, in priority order

**Phase 1 priority**

1. **GitHub MCP** (`@modelcontextprotocol/server-github`) — read repo state, create branches, open PRs, read / comment / merge issues. Essential for the branch workflow.
2. **Filesystem MCP** — built-in, already on.

**Phase 2 priority**

3. **Cloudflare MCP** (`@cloudflare/mcp-server-cloudflare`) — Pages deployments, preview URLs, build logs, KV, DNS.

**Optional**

4. **Resend MCP** — verify Resend setup, view sent emails, debug delivery.
5. **Plausible MCP** — pull analytics into the conversation.
6. **Linear / Notion MCP** — only if you use them for project management.

### 7.2 Not recommended

- Browser-automation MCPs (slow, unreliable for this work).
- CMS MCPs (Sanity, Contentful, etc. — Content Collections is simpler).
- Database MCPs (no database).

### 7.3 Configuration

MCP servers configured in `~/.claude/mcp.json` or project-level `.mcp.json`. Claude Code will help set them up on first launch in the project. Use GitHub fine-grained Personal Access Tokens scoped to the `zenithdigitalmena` repo only.

---

## Section 8 — Rollout Plan

### 8.1 Branch strategy

- `main` — production. Deploys to `zenithdigitalmena.com`. Touched only via merged PRs.
- `revamp` — integration branch (already created, already pushed). Cloudflare auto-builds previews.
- Feature branches off `revamp`: `revamp/foundation`, `revamp/homepage`, `revamp/services`, etc. Merged into `revamp` via PR.
- When `revamp` is fully ready: a single PR merges it into `main`. The whole site changes in one moment.

### 8.2 Phase 1 — Foundation + Homepage (~3 weeks)

#### Step 1 — Bug fixes & infrastructure (1 evening)

> Working on a new branch `revamp/foundation` off `revamp`. Fix the following from the audit, one at a time, and verify `npm run build` succeeds after each:
>
> 1. The blog post `src/pages/blog/practical-ai-for-smes-mena.md` has no `layout` frontmatter. Add `layout: ../../layouts/Layout.astro`.
> 2. `src/components/Header.astro` line 3 has nested `<a>` tags. Fix the markup.
> 3. `src/styles/global.css` has both v3 Tailwind directives (`@tailwind base; @tailwind components; @tailwind utilities;`) and the v4 import (`@import "tailwindcss";`). Remove the v3 directives.
> 4. `src/pages/services.astro` is missing closing tags. Add the missing `</section>` and `</Layout>`.
>
> Don't change anything else.

#### Step 2 — Per-page SEO (1 evening)

> On `revamp/foundation`, refactor `Layout.astro` to accept props: `title`, `description`, `ogImage`, `canonical`, `locale`. Update every existing page to pass its own props. Add the Astro Sitemap integration (`@astrojs/sitemap`) and configure it in `astro.config.mjs`. Add a `public/robots.txt` allowing all and pointing to the sitemap. Don't change visual design.

#### Step 3 — i18n routing scaffolding (1–2 evenings)

> Set up Astro i18n with `en` (default, no prefix) and `ar` (prefix `/ar/`). Configure in `astro.config.mjs`. Create the AR page directory mirroring EN (stub pages saying "Translation coming soon — switch to English →"). Build a `<LanguageSwitcher>` component. Add `hreflang` tags to Layout. Test that `/about` and `/ar/about` both load with correct `<html lang>` and `dir`.

#### Step 4 — Design system foundation (2–3 evenings)

> Implement the design system from the brief. Create `src/styles/tokens.css` with all CSS custom properties from §2.2 (colors), §2.4 (type scale), and §2.5 (spacing). Update Tailwind config to expose these tokens. Self-host Geist, Geist Mono, and IBM Plex Sans Arabic, woff2 only, subsetted, preloaded in Layout. Add `prefers-reduced-motion` CSS. Don't change existing visuals — just add the capability.

#### Step 5 — Motion infrastructure (1 evening)

> Add GSAP 3.12+ with ScrollTrigger plugin and Lenis to dependencies. Create a `<MotionProvider>` Astro island that initializes Lenis and exposes a `useGSAP` pattern. Respect `prefers-reduced-motion`. Lazy-load motion code so it doesn't ship to pages that don't use it.

#### Step 6 — Header + Footer rebuild (1–2 evenings)

> Rebuild `Header.astro` per §3.2: logo + nav + Start a project CTA + EN/AR switcher. Sticky with a compact-on-scroll variant. Mobile hamburger opens a full-screen overlay. Rebuild `Footer.astro`: 3-column layout with nav, contact, legal, plus a copy-to-clipboard email widget. Both bilingual via the i18n strings file. Test on mobile and AR.

#### Step 7 — Homepage (3–5 evenings)

> Rebuild `src/pages/index.astro` as the cinematic 6-scene homepage from §3.3:
> - Scene 1 hero with the geometric artifact and pinned animations.
> - Scene 2 statement of intent with word-by-word reveal.
> - Scene 3 four-services preview.
> - Scene 4 the "Most digital work in the GCC is shipped before it's designed" pinned scene.
> - Scene 5 thinking preview cards (from Content Collections, even if empty initially).
> - Scene 6 closing CTA.
>
> Use the design tokens, type scale, motion tokens. Build the SVG geometric artifact as a reusable `<GeometricArtifact>` component with a slow rotation animation. Use copy from §4.3. Mirror correctly in AR. Test on mobile and check Lighthouse.

#### Step 8 — Phase 1 QA + merge

> Run Lighthouse on the new homepage (mobile + desktop). Verify accessibility with axe DevTools. Test in Safari, Chrome, mobile Safari, and on a real iPhone. Visually test AR. Verify no console errors. Once clean, open a PR from `revamp/foundation` → `revamp`, then `revamp` → `main`. Merge.

### 8.3 Phase 2 — Services / About / Thinking (~3 weeks)

- Build `/services` from §3.5 + §4.3.
- Build `/about` from §3.7 + §4.3.
- Build `/thinking` index + essay template from §3.6.
- Set up Content Collections schemas from §5.
- Founder writes 4–6 essays.
- Translate UI strings to AR; translate ≥2 essays for parity.
- Merge to main.

### 8.4 Phase 3 — Practice / Contact / Polish (~2–3 weeks)

- Build `/practice` from §3.4.
- Build `/contact` with the form + Cloudflare Pages Function + Resend (§6.1).
- Add `/legal/privacy`.
- Plausible / Cloudflare Web Analytics + event instrumentation (§6.2).
- OG image generation for all pages (§6.3).
- Final performance, accessibility, SEO pass.
- Set up 301 redirects: `/blog/*` → `/thinking/*`, `/work` → `/practice`.
- Merge to main. Launch.

### 8.5 Today's first move

1. Save this brief somewhere durable.
2. In Claude Code, open a new branch `revamp/foundation` off `revamp` and paste the Step 1 prompt.
3. Don't try to do Steps 2–8 in one session. One step at a time.
4. After every step: push, get a Cloudflare preview URL, look at it, make sure it's still good before moving on.

---

## Section 9 — Honest Risks & Watchpoints

1. **Claude Code produces a lot of code fast. Most good. Some wrong.** Always read the diff. Especially watch motion code (easy to over-animate), CSS that overrides tokens, and copy (Claude Code may "improve" locked copy — tell it not to).
2. **The thinking essays are the load-bearing wall.** If they're not real, the site fails its primary job. Block real time for writing. If stuck, do a separate planning session.
3. **Bilingual sites take ~1.6× longer than monolingual.** Budget accordingly.
4. **Cinematic motion is tempting to over-do.** Brief says 3–7 scenes per page. Resist 10. Restraint is the entire reason it works.
5. **Mobile performance with GSAP + Lenis + heavy SVG can degrade on older Android.** Test on a real $150 Android device before launch — not just an iPhone.
6. **SEO will dip during migration.** Renaming `/blog` → `/thinking` and `/work` → `/practice` loses some indexed equity. Set up 301s in `_redirects` so it doesn't break.

---

## Section 10 — The Closing Frame

You came in saying *"complete revamp using Claude Code, MCP, and design."*

You're leaving with:
- A clear strategic foundation — anonymized, brand-led, POV-driven, bilingual.
- A locked visual direction — cinematic minimalism, monochrome + cool blue, Geist + Plex Arabic, GSAP-driven scroll choreography.
- A locked information architecture — 6 routes per locale, scene-by-scene choreography per page.
- Real, ready-to-use copy for every page.
- A workflow — `revamp` branch + feature branches, Cloudflare previews, phased merges to main.
- An MCP setup plan.
- Step-by-step prompts to feed Claude Code, in the right order.
- Honest acknowledgment of what's hard, what's risky, and what depends on real work from you.

Build it carefully. Ship it phase by phase. Edit it once it's live. Good luck.

---

*End of brief — version 1.0*
