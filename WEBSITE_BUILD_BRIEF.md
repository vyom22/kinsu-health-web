# Kinsu Health — Website Build Brief (Phase 1)

> **Status:** locked for execution, 2026-04-22
> **Domain:** kinsu.health (existing GitHub Pages deployment)
> **Scope:** rebuild the single-page marketing site + add `/privacy`, `/terms`, `/waitlist-thanks`, `/404`, `robots.txt`, `sitemap.xml`
> **Out of scope (Phase 2+):** blog, comparison pages (`/vs/practo`), caregiver landing, press kit, social content CLI, investor one-pager

This brief is the single source of truth for Phase 1. It integrates:
- **Campaign strategy** (marketing:campaign-plan)
- **Design system** (ui-ux-pro-max recommendations, resolved against brand lock-ins)
- **SEO foundation** (marketing:seo-audit structure, pre-launch mode)
- **Technical spec** for implementation

---

## 0. Locked Decisions

| # | Decision | Value |
|---|---|---|
| 1 | Domain | `kinsu.health` (not kinsuhealth.in). CNAME must contain this. |
| 2 | Hero variant at launch | Variant A only (caregiver pain). No A/B at launch. |
| 3 | Typography | **Lexend** for headings, **Inter** for body. Both self-hosted or Google Fonts with preload. |
| 4 | Sparrow disclosure level | Consumer-facing: "Sparrow, our on-device AI engine, runs on your phone — your data doesn't leave India." No architecture details. |
| 5 | Photography | No real-family photos in Phase 1. CSS phone mockups + SVG illustrations. Placeholders clearly marked in code. |
| 6 | Primary CTA | Waitlist email (primary). APK download (secondary). Play Store swap-in at W3. |
| 7 | Framework | Plain HTML + Tailwind CDN + vanilla JS. No build step. |
| 8 | Waitlist backend | FormSubmit → `Founders@kinsu.health` (already wired in existing repo) |
| 9 | Analytics | Plausible (privacy-first, cookieless). No GA4. |
| 10 | Founder voice | "We" (team). No named founder on the website. |

---

## 1. Strategic Frame

- **Primary goal (6 weeks):** 2,000 waitlist emails + 500 Android installs
- **Secondary goal:** website serves as a credibility artefact for seed investors (Audience D lurks here silently)
- **Core message a visitor should remember 10 minutes later:** *"Finally, an Indian health app that treats my family's data like it's mine."*
- **Audiences served on-page, in priority order:**
  - A: Sandwich-generation caregiver (32–48) — primary copy target
  - B: Chronic self-manager (40–65) — reached via feature pillars
  - C: Wellness millennial (24–35) — reached via aesthetic + Routines feature
  - D: Seed investors — reached via credibility signals (Section 7 Sparrow hint, DPDP depth, site quality)

---

## 2. Information Architecture

Scroll order with cognitive job and single takeaway per section.

| # | Section | Cognitive Job | Dwell | Single Takeaway |
|---|---|---|---|---|
| — | Sticky top nav | Orient, give escape | <1s | "This is Kinsu, CTA is here" |
| 1 | Hero | Hook + value prop + CTA | 4–6s | "This is for me, and my Ma" |
| 2 | Trust bar | Defuse skepticism | 2s | "DPDP · ABDM · On-device AI" |
| 3 | The Problem | Resonate with pain | 6–8s | "They understand my weekend" |
| 4 | Feature Bento (6 pillars) | Show product in one glance | 10–15s | "One app, six jobs" |
| 5 | Family Care deep-dive | Differentiate from Practo/1mg | 8–10s | "Managing parents is first-class" |
| 6 | Privacy / DPDP | Convert skeptics | 10–12s | "Consent is real, erasure is real" |
| 7 | AI disclaimer + Sparrow signal | Neutralise AI fear, quietly signal moat | 5–6s | "AI complements my doctor, runs on my phone" |
| 8 | FAQ | Close objections | 12–15s | "My specific worry is addressed" |
| 9 | Final CTA banner | Convert | 3–4s | "I can join the waitlist right now" |
| 10 | Footer | Compliance + discovery | 2s | "DPO, privacy, socials" |

**Page budget:** 60–90s engaged scroll. Sections 1–4 carry the conversion for the ~50% that bounce before Section 5.

---

## 3. Content (final copy, ready to paste)

> Every string passes the brand brief §11 compliance checklist: no diagnose/treat/cure, no "unhackable", no "revolutionary", no medical claims, no real user data.

### Section 1 — Hero (Variant A, launching)

- **Eyebrow:** `For Indian families.`
- **H1 line 1:** Ma's reports. Your dad's meds. Your kids' vaccinations.
- **H1 line 2:** All in one quiet, private app.
- **Sub:** Kinsu is a family health vault for India. Upload once, find anything in three seconds, and share with any doctor — without forwarding another WhatsApp.
- **Primary CTA:** `Join the waitlist`
- **Secondary CTA (text link):** `Download beta APK →`
- **CTA micro:** Android only · free during beta · no spam, ever

**Visual:** CSS-rendered phone frame showing the Vault screen with three anonymised sample reports (Ms. M. Sharma, Mr. R. Sharma, Baby A.). No real data.

### Section 2 — Trust bar

Single row, uppercase, typography only (no emoji, no flags, no lock icons):

```
DPDP ACT 2023 COMPLIANT   |   ABDM / ABHA READY   |   ON-DEVICE AI · DATA NEVER LEAVES INDIA
```

### Section 3 — The Problem

- **Eyebrow:** `Why we built Kinsu.`
- **H2:** Your family's health is scattered across six apps and three folders.

Three vignette cards, each with a lucide icon + H3 + one-line body:

1. **The WhatsApp dig.** *(icon: `search`)* Your mother's cardiologist asks for her last three ECGs. You spend an hour scrolling through a year of family chats.
2. **The forgotten tablet.** *(icon: `clock`)* Your father forgets if he took the 8 PM BP medication. You're in another city. You both guess.
3. **The duplicate test.** *(icon: `file-x`)* A new specialist orders a lipid panel. You had one done four months ago — but the report is in a hospital folder you can't find.

**Closing line under cards:** *This isn't a tech problem. It's a care problem. Kinsu fixes the part software can.*

### Section 4 — Feature Bento

- **H2:** Six things, one app. No toggling between five half-built ones.

Bento grid. Family Care is the large card (spans 2 cols). Others are equal size.

| Card | Lucide icon | Headline | Hook |
|---|---|---|---|
| **Family Care** (large) | `users-round` | Care for the whole family. | Add parents, dependents, caregivers. Share records with real consent. |
| Unified Vault | `folder-lock` | Every report, in three seconds. | Upload prescriptions, lab reports, X-rays. Search, filter, preview. |
| Medications | `pill` | Never miss the 8 PM tablet. | Add meds with dosage and meal-time. Gentle reminders that actually work. |
| Vitals Trends | `activity` | See the pattern before your doctor asks. | BP, sugar, SpO₂, weight — with readable trends. |
| SOS + Medical ID | `shield-alert` | Tap-to-call the right person in three seconds. | Emergency contacts, allergies, blood group, 102 · 112 · 1091 · 1066 built in. |
| Routines | `sparkles` | Turn a scattered routine into a streak. | Hair, skin, wellness steps — tracked without judgement. |

### Section 5 — Family Care deep-dive

- **Eyebrow:** `The feature that makes Kinsu different.`
- **H2:** Built for Indian families, not Silicon Valley individuals.

Two-column on desktop; stacked on mobile.

**Left — copy (bullet list):**
- Add your parents, your kids, and a caregiver (your sibling in another city, your family GP).
- Each person has their own vault — shared only with whoever you explicitly consent.
- Withdraw access any time. See an audit log of who viewed what.
- The first health app where "joint family" is a feature, not a workaround.

**Right — visual:** SVG family-tree illustration. Three profile nodes linked with consent pills. No real faces.

### Section 6 — Privacy & DPDP

- **Eyebrow:** `Privacy that reads like a promise, not a disclaimer.`
- **H2:** Your data lives on your phone. Not on someone else's server.

Four-card grid:

| Claim | Proof |
|---|---|
| **Local-first storage.** | Records are stored on your device. Cloud sync is opt-in, per category. |
| **Five granular consents.** | Medical records, vitals, medications, family sharing, AI insights — each separate. Change any, any time. |
| **Right to erasure. Right to nominee.** | Delete everything in one tap. Nominate a family member to inherit access. Both are built in — not buried in policy. |
| **A real DPO. A real email.** | `dpo@kinsu.health` goes to a human. Response within 7 days, by law. |

**Footer link:** *Read the full privacy policy →* → `/privacy`

### Section 7 — AI disclaimer + quiet Sparrow signal

- **Eyebrow:** `About the AI.`
- **H2:** It complements your doctor. It doesn't replace them.

Two short paragraphs:

> Kinsu's AI reads your reports and surfaces patterns — a trending blood pressure, a due vaccination, a medication that clashes with another. Every suggestion cites a source. No diagnoses. No cures. No "ask the AI" trying to be a doctor.
>
> Our AI engine, Sparrow, runs on your phone. It doesn't send your health data to servers abroad. That's not a feature we bolted on for India — it's the reason the architecture exists.

### Section 8 — FAQ

Native `<details>` / `<summary>` accordion (keyboard-friendly, zero JS).

1. **Is this another Practo or 1mg?**
   No. Practo and 1mg are for booking doctors and buying medicine. Kinsu is your family's health memory — the reports, meds, vitals, and routines you manage between those appointments.

2. **Is my data sent to servers?**
   Only what you explicitly sync. Records are stored on your device by default. AI runs on your phone, not in the cloud.

3. **Can I delete everything?**
   Yes. One tap, permanent, no retention. It's called the Right to Erasure and the DPDP Act 2023 makes it a legal requirement — we just don't hide the button.

4. **Does it work offline?**
   Yes. The vault, meds, vitals, and SOS all work without internet. Cloud sync resumes when you reconnect.

5. **What is DPDP and why does it matter?**
   India's Digital Personal Data Protection Act 2023 is the country's privacy law. It requires consent to be granular, withdrawable, and real. Most apps treat it as paperwork. We treat it as a product spec.

6. **Is Kinsu ABHA-compatible?**
   We're ABDM-ready. You'll be able to link your ABHA wallet and pull records from partner hospitals in a coming release.

7. **Can I add my elderly parents if they're not tech-savvy?**
   Yes. Caregiver mode is built for this. You manage their records from your phone; they see a simplified view on theirs.

8. **Why Android only?**
   India is 95% Android. We're focusing effort where the users are. iOS is on the roadmap.

9. **What does it cost?**
   Free during beta. The core vault, meds, vitals, and family care will stay free. Some advanced AI insights may be paid later — we'll tell you before that changes.

10. **Who are you?**
    Kinsu AI Labs. A small team that watched family members dig through WhatsApp for the third year in a row and decided that was enough.

### Section 9 — Final CTA banner

Full-width, `--kinsu-blue` background, reversed text.

- **H2:** One vault. One family. One tap away.
- **Body:** Join the waitlist and we'll tell you the day we launch on Play Store — and nothing else.
- **Inline form:** email field + `Join waitlist` button
- **Micro:** By joining, you agree to our [Privacy Policy](/privacy). We use your email to email you about Kinsu. Nothing more.

### Section 10 — Footer

Three columns on desktop, stacked on mobile.

| Column 1: About | Column 2: Privacy | Column 3: Contact |
|---|---|---|
| Kinsu AI Labs | Privacy Policy (`/privacy`) | Founders@kinsu.health |
| Why Kinsu (anchor) | Terms of Service (`/terms`) | DPO: dpo@kinsu.health |
| Press / Press kit (placeholder) | DPDP Commitments (anchor) | LinkedIn · Instagram · X |

**Bottom line:** `© 2026 Kinsu AI Labs · Made in India · Android app, built for Indian families.`

### Microcopy (form states, errors, edge cases)

- Form error: `That email looks off — mind checking?`
- Form success: `You're on the list. We'll write exactly once, the day we launch.`
- Network error: `Something went wrong. Try again in a moment?`
- 404 page headline: `This page isn't in the vault yet.` · subline: `Let's get you back →` · link to `/`
- Skip-to-content link: `Skip to main content`

---

## 4. Aesthetics

### 4.1 Style family

- **Name:** *Editorial Minimalism* (soft relative of ui-ux-pro-max's "Exaggerated Minimalism")
- **Pattern:** *App Store Style Landing* with *Minimal Single Column* narrative flow
- **Principles:**
  - One hero statement dominates first viewport
  - Sections separated by whitespace, not dividers
  - Kinsu blue used precisely — CTAs, one underline per section, dividers. Not painted everywhere.
  - Product screenshots float on warm off-white in thin device bezels
  - Zero emoji anywhere. Icons are lucide, 24×24 viewBox, stroke-width 1.5
- **Anti-patterns (rejected):** playful, glassmorphism, gradient-heavy, AI purple-pink, parallax, scale-on-hover, looping lottie

### 4.2 Colour tokens

```css
:root {
  --ink:             #0E1F2B; /* body text, headings */
  --ink-soft:        #42566A; /* secondary text */
  --muted:           #7A8A99; /* tertiary, placeholder */
  --paper:           #FAF7F0; /* page background, warm off-white */
  --paper-alt:       #F1ECE0; /* alternate section bg */
  --surface:         #FFFFFF; /* cards, device screens */
  --line:            #E4DED0; /* hairlines, dividers */
  --kinsu-blue:      #309BD3; /* primary brand, CTA */
  --kinsu-blue-ink:  #1F6FA0; /* hover, deep accent */
  --kinsu-blue-mist: #E6F2FA; /* soft bg for emphasis */
  --ok:              #3E8E6E; /* muted success */
  --warn:            #C25B47; /* warm alert, not neon */
}
```

**Contrast verified:**
- `--ink` on `--paper` = 13.8:1 ✓ AAA
- `--ink-soft` on `--paper` = 6.2:1 ✓ AA
- `--kinsu-blue` button text (#FFF) on `--kinsu-blue` bg = 3.4:1 ⚠ passes AA Large only — CTA text must be **≥16px bold**

### 4.3 Typography

- **Headings:** Lexend (designed for readability, better for 40–65 audience)
- **Body:** Inter (brand-locked)
- **Google Fonts import:**
  ```css
  @import url('https://fonts.googleapis.com/css2?family=Lexend:wght@400;500;600;700&family=Inter:wght@400;500;600;700&display=swap');
  ```
- **Self-host both** if Phase 1 budget allows — saves one external round-trip on low-end Android.
- **Preload** the two most-used weights in `<head>`.

**Type scale (mobile → desktop):**

| Token | Mobile (px/lh) | Desktop (px/lh) | Weight | Tracking | Font |
|---|---|---|---|---|---|
| display | 40/44 | 72/76 | 700 | -0.025em | Lexend |
| h1 (section) | 32/38 | 48/54 | 700 | -0.02em | Lexend |
| h2 | 24/30 | 32/40 | 600 | -0.01em | Lexend |
| h3 (card title) | 18/26 | 20/28 | 600 | 0 | Lexend |
| lead | 18/28 | 20/32 | 400 | 0 | Inter |
| body | 16/26 | 17/28 | 400 | 0 | Inter |
| small | 14/22 | 14/22 | 400 | 0 | Inter |
| eyebrow | 12/16 | 13/18 | 600, uppercase | 0.08em | Inter |

- Line length: `max-width: 65ch` on prose blocks. Never wider.

### 4.4 Layout & spacing

- Mobile: single column, 16px gutters, 20px block padding, 24px between cards
- Tablet (≥768px): 24px gutters, 2-col where useful
- Desktop (≥1024px): 12-col grid, 24–32px gutters, container `max-width: 1120px`
- Section vertical rhythm: 64px mobile, 96–120px desktop
- Card radius: 16px. Button radius: 12px. Input radius: 10px.

### 4.5 Motion

**Principles:** animate ≤2 elements per view, ease-out, honour `prefers-reduced-motion`.

| Motion | Trigger | Duration | Easing |
|---|---|---|---|
| Hero fade-up | Load | 500ms | cubic-bezier(0.2, 0.8, 0.2, 1) |
| Section fade-in | IntersectionObserver @ 20% | 400ms | ease-out |
| Button hover | hover/focus | 150ms | ease-out |
| Accordion open | click | 200ms | ease-out |

No parallax, no marquee, no scale-on-hover (layout shift), no looping lottie. Under `@media (prefers-reduced-motion: reduce)` → `transition: none; animation: none`.

### 4.6 Component inventory

Build once, reuse:

1. `.btn--primary` — Kinsu blue bg, white text, 44px min-height, 16px bold, 12px radius, 150ms hover to `--kinsu-blue-ink`
2. `.btn--ghost` — transparent bg, Kinsu blue text, 1.5px Kinsu blue border
3. `.chip` — small-caps eyebrow pill, mist bg, ink text, pill-shaped
4. `.card` — surface bg, 16px radius, 1px `--line` border, 24px padding, no shadow
5. `.device-frame` — CSS-only thin phone bezel, 360×720 mobile, 300×620 desktop
6. `.faq-item` — native `<details>` / `<summary>`, chevron rotates, 1px bottom border
7. `.trust-bar` — flex row, uppercase, border-left dividers
8. `.input--email` — 44px height, 1.5px border, focus-visible ring Kinsu blue

### 4.7 Placeholders

All placeholder images marked inline with a comment:

```html
<!-- PLACEHOLDER: real family photo, see KINSU_BRAND_BRIEF §7. Replace in Phase 2. -->
```

Phase 1 uses:
- CSS device frame + flat SVG UI mockups (Vault, Medications, Family tree)
- Section 5 family-tree illustration — SVG, flat geometric, `--kinsu-blue` + `--ink`
- No raster photos except `og.png` (which can be a typographic composition if no family shoot is scheduled)

---

## 5. SEO Foundation

### 5.1 Keyword–intent map

**Primary (commercial intent, placed on homepage):**

| Keyword | Difficulty | Where it lives |
|---|---|---|
| family health record app India | Moderate | H1 (Variant A), meta description, SoftwareApplication schema description |
| health vault app Android | Easy–Moderate | H2 on Vault feature card, future `/vault` |
| DPDP compliant health app | Easy | Section 6 H2, schema |
| ABHA wallet app / ABDM app India | Moderate | Trust bar, FAQ #6 |
| medication reminder app for parents | Moderate | Medications card, future blog |
| upload prescription app India | Easy–Moderate | Vault card, future blog |

**Secondary (informational, blog cluster candidates — Phase 3):**

- how to read a lipid panel India
- HbA1c meaning diabetes
- DPDP Act 2023 rights for users
- ABHA number how to create India
- caregiver app for elderly parents India
- family vs individual health app

**Brand (defensive):**

- Kinsu Health, Kinsu app, kinsuhealth, Kinsu review, Kinsu vs Practo, Kinsu DPDP

### 5.2 Meta tags per page

**Homepage `/`:**

```html
<title>Kinsu Health — Family health records, medications & vitals for Indian families</title>
<meta name="description" content="Kinsu is a family health vault for India. Upload prescriptions, track meds and vitals, share with any doctor in seconds. DPDP-compliant, ABDM-ready, on-device AI. Android beta — join the waitlist.">
<link rel="canonical" href="https://kinsu.health/">
<meta name="robots" content="index,follow">

<!-- Open Graph -->
<meta property="og:title" content="Kinsu Health — One vault for your family's health">
<meta property="og:description" content="Prescriptions, meds, vitals, routines — all in one private Android app. DPDP-compliant. On-device AI. Made in India.">
<meta property="og:image" content="https://kinsu.health/public/og.png">
<meta property="og:url" content="https://kinsu.health/">
<meta property="og:type" content="website">
<meta property="og:locale" content="en_IN">

<!-- Twitter -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@kinsuhealth">
<meta name="twitter:title" content="Kinsu Health — One vault for your family's health">
<meta name="twitter:description" content="Prescriptions, meds, vitals, routines — all in one private Android app. DPDP-compliant. On-device AI.">
<meta name="twitter:image" content="https://kinsu.health/public/og.png">
```

**Privacy `/privacy`:** title + description specific to DPDP, canonical, `index,follow`.
**Terms `/terms`:** similar.
**Waitlist thanks `/waitlist-thanks`:** `noindex,nofollow`.

### 5.3 Structured data (JSON-LD, inline at end of `<body>`)

Three blocks:

1. **Organization** — Kinsu AI Labs with logo, URL, sameAs socials, contactPoint
2. **MobileApplication** — Kinsu Health, operatingSystem=Android, applicationCategory=HealthApplication, inLanguage=en-IN, offers price=0 INR
3. **FAQPage** — generated from the same Section 8 data (exact string match — Google penalises mismatch)

Full JSON bodies are in the implementation (§6.2 file structure).

### 5.4 URL structure

```
/                    Homepage
/privacy             Full privacy policy + DPDP commitments
/terms               Terms of service
/waitlist-thanks     Post-signup confirmation (noindex)
/404                 Branded 404 (noindex)

Reserved (Phase 3):
/blog                Blog index
/blog/<slug>         Posts
/vs/practo           Comparison
/caregivers          Audience landing
/press               Press kit
```

No trailing slashes. Lowercase, hyphen-separated.

### 5.5 Internal linking (Phase 1)

Page anchors: `#problem`, `#features`, `#family-care`, `#privacy`, `#ai`, `#faq`, `#waitlist`.

- Desktop top nav → anchor links
- Mobile → collapsed; single sticky-bottom "Join waitlist" button
- Footer → `/privacy`, `/terms` (only non-anchor links)
- `rel="noopener"` on outbound; `mailto:` for DPO

### 5.6 Technical SEO checklist

| Check | Target | Implementation |
|---|---|---|
| HTTPS | ✓ | GitHub Pages / Let's Encrypt (already active) |
| Mobile-friendly | ✓ | viewport meta, 16px base, 44px taps |
| LCP | <2.5s on 4G slow | Inline critical CSS, eager hero |
| CLS | <0.1 | Reserve image dims, font-display: swap + preload |
| INP | <200ms | No blocking JS |
| `robots.txt` | Allow all, disallow `/waitlist-thanks` | ship at root |
| `sitemap.xml` | / + /privacy + /terms | ship at root, referenced in robots |
| Canonical URLs | Set per page | `<link rel="canonical">` |
| Favicon | 32 + apple-touch 180 | generate from kinsu_logo.png |
| 404 page | Branded, links home | `/404.html` |

---

## 6. Technical Specification

### 6.1 Stack

- **Markup:** HTML5, semantic (`<main>`, `<section>`, `<nav>`, `<article>`, `<details>`)
- **CSS:** Tailwind via Play CDN for rapid iteration. Custom tokens in inline `<style>` at top.
- **JS:** Vanilla, <5KB total. Used only for mobile nav, sticky CTA, IntersectionObserver fade-ins, form validation progressive enhancement.
- **No bundler. No Node. No build step.** Matches repo CLAUDE.md zero-dependency constraint.
- **Form:** FormSubmit → `Founders@kinsu.health` (existing integration).
- **Analytics:** Plausible single-line script.
- **Hosting:** GitHub Pages, branch `modified-design`, custom domain via CNAME.

### 6.2 File structure (what Phase 1 ships)

```
/
├── index.html                Single-page marketing site (rewritten)
├── privacy.html              Privacy policy (new)
├── terms.html                Terms of service (new)
├── waitlist-thanks.html      Form submit confirmation (new)
├── 404.html                  Branded 404 (new)
├── robots.txt                Crawl directives (new)
├── sitemap.xml               Sitemap (new)
├── CNAME                     Contains: kinsu.health (new — was missing)
└── public/
    ├── kinsu_logo.png        Existing
    ├── favicon-32.png        New, from logo
    ├── apple-touch-icon.png  New, 180×180 from logo
    └── og.png                New, 1200×630 typographic composition
```

**Non-shipping files:**
- Existing `index.html` in repo (82KB, prior session) — will be replaced
- `WhatsApp Image 2026-04-21 at 00.33.33.jpeg` — unused, can be deleted or left
- `HANDOVER_CLAUDE_CODE.md`, `WEBSITE_BUILD_BRIEF.md`, `CLAUDE.md` — docs, not served (GitHub Pages serves them but they aren't linked)

### 6.3 Performance budget

| Metric | Budget |
|---|---|
| LCP on 4G slow (Moto G4 profile) | <2.5s |
| CLS | <0.1 |
| Total JS (gzipped) | <10KB |
| Total CSS (gzipped) | <40KB (Tailwind CDN is ~30KB) |
| HTML (gzipped) | <60KB |
| Fonts | 2 families × 4 weights, preloaded, `font-display: swap` |
| Hero visual | SVG, <30KB |
| Full page weight first load | <400KB |

### 6.4 Accessibility — WCAG 2.1 AA

- All contrast ratios pass AA (verified §4.2)
- All interactive elements keyboard navigable
- `focus-visible:ring-2 ring-[--kinsu-blue] ring-offset-2`
- Skip-to-content link at top
- `aria-label` on every icon-only button
- `<nav aria-label="Primary">`
- Form: `<label for>` + `aria-describedby` for errors
- FAQ uses native `<details>` (ARIA states built in)
- `prefers-reduced-motion` honoured
- VoiceOver pass before ship

### 6.5 Browser support

- Chrome, Safari, Firefox, Edge (latest 2 versions)
- Chrome/WebView 100+ on Android
- Samsung Internet 18+
- No IE, no pre-2020 Safari

### 6.6 Deploy

1. Ensure CNAME file contains `kinsu.health`
2. Commit to branch `modified-design`
3. GitHub Pages auto-deploys in ~60s
4. Smoke test: `curl -I https://kinsu.health` → 200; Lighthouse mobile run; real device test on ₹10–15K Android
5. Re-confirm FormSubmit by submitting once from live site and clicking the confirmation email

---

## 7. Acceptance Criteria (Phase 1 "done")

- [ ] All 10 sections present with final copy (not lorem, not TODO)
- [ ] Lighthouse mobile: Performance ≥90, Accessibility ≥95, SEO ≥95, Best Practices ≥95
- [ ] Real-device 4G test on low-end Android
- [ ] Contrast audit clean (AA everywhere, AAA for body)
- [ ] Form submits to FormSubmit; confirmation email flow active
- [ ] `/privacy` is a real, readable page; DPO email goes to a human mailbox
- [ ] All meta/OG/schema validate (Schema.org validator + Google Rich Results Test)
- [ ] `sitemap.xml` and `robots.txt` live, referenced from homepage
- [ ] Brand brief §11 compliance checklist passed on every visible string
- [ ] No real user data shown; no white-coat stock; the string "TTT-RetNet" does not appear anywhere
- [ ] Works with JS disabled (content readable, form degrades to standard POST)
- [ ] `prefers-reduced-motion` honoured
- [ ] CNAME contains `kinsu.health`; site resolves at that domain over HTTPS

---

## 8. Build Order

1. **Skeleton + tokens** — HTML scaffold, Tailwind config, CSS variables, typography, spacing
2. **Hero + trust bar + final CTA** — conversion path end-to-end; verify form submits
3. **Problem + Feature Bento + Family Care** — emotional + product
4. **Privacy + AI disclaimer + FAQ** — trust
5. **Footer + `/privacy` + `/terms` + `/404` + robots + sitemap** — compliance and housekeeping
6. **Meta / OG / Schema + Plausible** — SEO layer
7. **Polish** — motion, focus states, copy tightening, SVG mockups
8. **QA** — Lighthouse, device test, a11y sweep, compliance sweep → ship

**Estimated effort:** ~1 focused day for steps 1–6, half day for 7–8.

---

## 9. Open Items (for later phases, not Phase 1)

- Real family photography shoot (Phase 2)
- Social content generation CLI (Phase 2)
- Investor one-pager (Phase 2)
- Blog cluster pages (Phase 3)
- Comparison pages (`/vs/practo`, `/vs/1mg`) (Phase 3)
- Caregiver audience landing (`/caregivers`) (Phase 3)
- ABHA integration announcement page (post-launch)

---

*End of brief. Execute against this document. Any deviation from locked decisions (§0) requires a note in the next session.*
