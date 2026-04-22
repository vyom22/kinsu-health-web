# Kinsu × Sparrow — Claude Code Handover
### Customer Acquisition & Fundraising Workstream

> **Date:** April 22, 2026
> **Purpose:** This file is the single source of truth for a Claude Code session tasked with building Kinsu Health's customer-facing website and social media content automation pipeline.
> **Two goals drive everything below:** (1) acquire early Android users in India, (2) produce investor-ready materials that demonstrate traction and technical moat.

---

## 0. Files You Need in the Claude Code Session

Place these files in the working directory alongside this handover:

| File | What it is | Why Claude Code needs it |
|---|---|---|
| `SPARROW_FULL_BRIEF.md` | Complete technical brief for Sparrow (the AI engine) | Investor deck content, technical differentiator copy, whitepaper references |
| `KINSU_BRAND_BRIEF.md` | Brand voice, design system, audience personas, content pillars, platform playbook | All copy, design tokens, tone guardrails, compliance checklist |
| App screenshots / mockups (if available) | Kinsu app UI | Hero section mockups, feature demos, social media visuals |
| Logo files (SVG/PNG) | Kinsu Health logo | Website header, social templates, favicon |
| `kinsuhealth.in` domain details | DNS / hosting info | Deployment configuration |

> **If any of the above are missing, ask the user before proceeding.** The two markdown briefs are the minimum — everything else is nice-to-have but the session can scaffold placeholders.

---

## 1. What This Project Is

### Kinsu Health (the product users touch)
A family health vault Android app for the Indian market. It unifies prescriptions, lab reports, vitals, medications, care routines, and emergency contacts into one private, offline-first, DPDP Act 2023–compliant app.

### Sparrow (the AI engine underneath)
A 154M-parameter hybrid language model (Multi-Scale Retention + TTT-Linear + SwiGLU) built from scratch. Its defining property is **O(1) inference memory** — 31.5 MB constant regardless of sequence length. No Transformer attention, no KV cache, no context window.

### The Strategic Link
Sparrow's O(1) memory means medical AI can run **on-device**, on low-end Android hardware, on 4G, without sending Indian health data to foreign cloud endpoints. This is the technical moat that makes Kinsu's "AI insights" possible while being genuinely private and DPDP-compliant.

**For customer-facing copy:** Lead with Kinsu (the product benefit). Sparrow is invisible to users.
**For investor-facing materials:** Lead with Sparrow (the technical moat). Kinsu is the go-to-market.

---

## 2. Target Audiences

### For Customer Acquisition (website + social)

**A. "Sandwich Generation" Caregiver (PRIMARY)**
- Age 32–48, urban / tier-1 and tier-2 India
- Managing parents' chronic conditions while raising kids
- Pain: "My mom's cardiologist asked for her last three ECGs and I spent an hour on WhatsApp"
- Hooks: Family Care, dependent sharing, SOS, remote medication visibility

**B. Chronic-Condition Self-Manager**
- Age 40–65, on 3–6 daily medications, sees 2–3 specialists/year
- Pain: "I have six folders. My endocrinologist never has context from my cardiologist."
- Hooks: Vault, vitals trends, medication reminders, AI summaries

**C. Wellness-Minded Millennial (SECONDARY)**
- Age 24–35, Instagram + TikTok native
- Pain: "I track every workout but have no idea what my last blood panel said."
- Hooks: Routines (hair/skin), vitals logging, sleek UI, privacy-first positioning

### For Fundraising (investor materials)

**D. Investors (Seed / Pre-Series A)**
- Looking for: technical moat, India-specific market fit, team capability, traction metrics
- Key messages: O(1) on-device inference, DPDP compliance as feature, ABDM/ABHA readiness, family-first design (not a Practo clone)
- Assets needed: pitch deck, one-pager, technical whitepaper, demo video script

---

## 3. Brand Voice & Design System

### Voice Rules
- Clear, confident, calm — like a trusted family doctor, not a startup bro
- Concrete examples over adjectives: "Find your 2022 lipid panel in 3 seconds" > "Lightning-fast search"
- Indian English, occasional Hindi where natural (parivaar, seva) — never pander
- Foreground privacy as a feature, not a footnote
- **Never claim:** diagnose, treat, cure, replace doctors, "unhackable", "100% safe"
- **Never use:** "revolutionary", "game-changing", "AI-powered disruptor"

### Design Tokens
- Primary: `#309BD3` (Kinsu blue)
- Background: soft off-whites, warm greys
- Accents: muted success-green, alert-red — no neon
- Typography: clean sans-serif (Inter / similar), generous line-height, large numerals for data
- Icons: lucide-react style — thin strokes, rounded, humane
- Motion: subtle, confidence not flash
- Photography direction: real Indian families, multi-generational, diverse skin tones, natural lighting — no stock white-coats

### Compliance Checklist (EVERY piece of copy must pass)
- [ ] Does not claim to diagnose, treat, or cure
- [ ] Does not imply replacing a doctor (use "complements")
- [ ] No absolute security promises (use "encrypted, DPDP-compliant")
- [ ] No real user data shown (sample data only)
- [ ] ABDM/ABHA references verified for current compatibility
- [ ] No minor's face/data without explicit consent (default: avoid)

---

## 4. Product Features (for copy reference)

| Pillar | What it does | Copy hook |
|---|---|---|
| Unified Vault | Upload prescriptions, lab reports, X-rays. Search, filter, preview in-app. | One tap to show any doctor your last 5 reports. |
| Medications | Add meds with dosage, meal-time, frequency. Notification reminders. | Never miss the 8 PM BP tablet again. |
| Vitals Logging | BP, sugar, weight, temperature, SpO₂, pulse — with trends. | Spot the pattern before your doctor asks. |
| Family Care | Add dependents and caregivers. Shared records with consent. | Manage your parents' medications from your phone. |
| SOS | Emergency contacts + Medical ID + Indian helplines (102, 112, 1091, 1066). | Tap-to-call the right person in 3 seconds. |
| Hair & Skin Routines | Scheduled steps with completed/missed/scheduled tracking. | Turn a scattered routine into a streak. |
| AI Insights | Evidence-grounded summaries, trend callouts, wellness tips. | Understand your reports, not just store them. |
| ABHA Ready | ABDM-compatible for future hospital record linking. | National health stack, from day one. |

### USP Ranking (use this order in copy)
1. Built for Indian families, not individuals
2. DPDP Act 2023 compliant — data encrypted, never sold, consent withdrawable
3. Offline-first — works in low-connectivity clinics
4. ABDM/ABHA compatible — no vendor lock-in
5. Evidence-grounded AI, not hallucinated advice
6. One app replaces five half-working apps

---

## 5. Sparrow Technical Claims (for investor materials only)

Use these **only** in investor-facing content. Never expose internal architecture names (TTT-RetNet) externally — use "Sparrow" as the public name.

### Headline Claims (all empirically verified)
- **O(1) inference memory:** 31.5 MB constant, verified to 25,000+ tokens with 0.00% variation
- **No context window:** unlimited sequence length, no KV cache
- **On-device capable:** full model runs in ~330 MB total RSS, fits 64 MB RAM embedded targets (quantised)
- **400× memory advantage** over 7B Transformer at 25K tokens (31.5 MB vs 12.5 GB)
- **Real-time domain adaptation:** TTT layer adapts to medical domain within ~64 tokens, 64% loss reduction measured
- **Two-memory RAG architecture:** exact fact recall at 2,050× improvement over baseline

### Key Numbers for Decks
| Metric | Value |
|---|---|
| Parameters | 154M (151.9M exact) |
| Val loss (best) | 2.9151 @ step 248,750 |
| Tokens trained | ~16.2B |
| Streaming state size | 31.5 MB (constant) |
| Model weights (bf16) | ~22.8 MB |
| Total process RSS | ~330 MB |
| Training hardware | 2× A100 SXM4 (H200 node) |
| RAG recall improvement | 10×–2,050× across fact types |
| Memory invariance | 0.00% variation over 25K tokens |
| Latency per token | ~18–20ms (no trend with length) |

### Comparison Table (for pitch decks)
| Property | Transformer (7B) | Sparrow (154M) |
|---|---|---|
| Memory at 10K tokens | ~5,000 MB | 31.5 MB |
| Memory at 100K tokens | OOM | 31.5 MB |
| Continuous 24/7 operation | No (resets) | Yes |
| Minimum hardware | 16–80 GB VRAM | 64 MB RAM |
| Domain adaptation | Fine-tuning required | In-context (~64 tokens) |
| Exact fact recall | Yes (KV cache) | Via RAG (+3 KB/fact) |

---

## 6. Deliverable 1 — Kinsu Website (kinsuhealth.in)

### Requirements
- **Mobile-first** (audience is on 4G Android)
- **Lighthouse > 90**
- **No dark patterns** — no email-wall on homepage, privacy policy linked from every footer
- Framework: static site or lightweight framework (Next.js static export, Astro, or plain HTML/CSS/JS)
- Must work well on low-end Android Chrome

### Page Structure (in order)

**Above the fold (Hero)**
- One-sentence value prop (two variants to A/B test: one rational, one emotional)
- Phone mockup showing vault UI (placeholder if no screenshots provided)
- "Download for Android" CTA button (Play Store link — placeholder until live)
- Trust bar: DPDP compliant · ABDM ready · End-to-end encrypted (typography only, no flag/lock emojis)

**Section 1: The Problem**
- 3–4 pain points with concrete Indian scenarios
- Target audience A primarily

**Section 2: Features**
- Feature cards or accordion with the 6 pillars from §4
- GIF/video demo slots (placeholder if assets not provided)
- Each feature: icon + headline + one-line description + micro-demo visual

**Section 3: Family Care Deep-Dive**
- The primary differentiator — expand on caregiver + dependent + consent model
- Visual: family tree or multi-profile UI mockup

**Section 4: Privacy & DPDP**
- What data is stored where (local-first, encrypted)
- Granular consent (5 categories), right to erasure, right to nominee
- Real DPO contact
- **Not a footnote — this is a selling point**

**Section 5: AI Disclaimer**
- "Complements your doctor, doesn't replace them"
- Evidence-grounded, sources cited
- Sparrow mention: "Powered by on-device AI that never sends your data abroad" (no architecture details)

**Section 6: FAQ**
- 10 questions a skeptical Indian user would actually ask
- Include: "Is my data sent to servers?", "Can I delete everything?", "Does it work offline?", "Is this another Practo?"

**Section 7: Footer**
- Download CTA (repeated)
- Privacy Policy link
- Terms of Service link
- Contact / DPO email
- Social links (Instagram, LinkedIn, Twitter/X)

### Taglines to A/B Test (pick 2 for hero variants)
- Your family's health, in one place.
- One vault. Every report. Every family member.
- Finally, a health app built for Indian families.
- Records, reminders, rights — all yours.
- Care for your parents. From anywhere.
- The health app that respects your data.

---

## 7. Deliverable 2 — Social Media Content Automation

### Goal
Create a repeatable pipeline that produces platform-ready social media content with minimal manual effort. This is about **building the system**, not just writing one-off posts.

### Platform Priorities (in order)
1. **Instagram** — carousels + Reels for consumer audience (A, B, C)
2. **LinkedIn** — founder POV + technical credibility for investors/partners (D)
3. **TikTok / Instagram Reels** — short-form video scripts for virality (C)
4. **Twitter/X** — launch threads, build-in-public (B2B + developer audience)

### Content Pillars (40/25/20/10/5 ratio)
1. **40% Utility** — "How to read a lipid panel", micro-demos, feature walkthroughs
2. **25% Education** — health literacy, DPDP rights explainers
3. **20% Family stories** — caregiving moments, relatable scenarios
4. **10% Privacy** — "Where does your data actually live?"
5. **5% Product news** — launches, updates, milestones

### What the Automation Should Produce

**A. 30-Day Content Calendar**
- Platform, format, content pillar, target audience, hook, caption draft, visual direction, CTA
- CSV or structured format that can be imported into scheduling tools

**B. Instagram Carousel Templates**
- 10-slide structure with consistent layout
- Slide 1: hook (must stop the scroll)
- Slides 2–9: content
- Slide 10: CTA + handle
- Write 5 ready-to-post carousels on:
  1. "5 things your lab report is trying to tell you"
  2. "Your DPDP rights as a health app user"
  3. "Ma's medicine chart → one screen" (caregiver story)
  4. "Why your prescriptions shouldn't live in WhatsApp"
  5. "What to ask your doctor about your next blood test"

**C. LinkedIn Post Templates**
- Founder POV launch post (200 words, first-person, no emojis)
- DPDP compliance walkthrough post
- "Why we built Kinsu" narrative post
- Technical moat post (Sparrow — appropriate level for LinkedIn, no architecture internals)

**D. TikTok/Reels Script Templates**
- 5 scripts under 30 seconds each
- Hook must land in 2 seconds
- Captions always on (audio-off friendly)
- POV caregiving skits, screen-recorded micro-demos

**E. Twitter/X Launch Thread**
- 8–10 tweets, threaded
- Tweet 1: hook + problem
- Tweets 2–7: feature reveals with visuals
- Tweet 8: privacy angle
- Tweet 9: CTA (download link)
- Tweet 10: ask for RT / feedback

### Automation Architecture (suggested)
Build scripts or templates that:
1. Take a **content brief** (topic, audience, platform, pillar, format) as input
2. Generate **copy + visual direction** per the brand voice rules
3. Output in **platform-ready format** (correct character limits, hashtag sets, image specs)
4. Include a **review checklist** (compliance guardrails from §3 auto-applied)

This could be:
- A Python script that generates batches of content briefs → copy
- A set of prompt templates for different formats
- A CLI tool that takes `--platform instagram --format carousel --topic "lab reports"` and outputs structured content
- Integration with Canva API for visual generation (user has Canva connected)

The user has **Canva, Figma, Gamma, Gmail, Google Calendar, and Google Drive** connected as MCP integrations in claude.ai — these can be used for design generation and scheduling workflows if building artifacts there, but in Claude Code focus on the **content generation pipeline and website code**.

---

## 8. Investor Materials Checklist

While the primary deliverables are website + social automation, keep these on the radar as follow-up tasks:

- [ ] One-pager (Sparrow technical moat + Kinsu market fit)
- [ ] Pitch deck (10–12 slides, Gamma or PPTX)
- [ ] Demo script for investor meetings (3-act structure from SPARROW_FULL_BRIEF.md §14)
- [ ] Technical whitepaper (public version — Sparrow name, no TTT-RetNet internals)
- [ ] Traction dashboard mockup (once early users exist)

---

## 9. Key Constraints & Gotchas

1. **Never expose "TTT-RetNet" publicly.** External name is "Sparrow." Architecture internals (retention math, TTT inner update, gamma values) stay in investor-only materials under NDA.

2. **Sparrow is invisible to consumers.** Users see "AI insights" in Kinsu. They don't need to know about 154M parameters or O(1) memory. The only consumer-facing Sparrow reference: "Powered by on-device AI."

3. **India-specific everything.** Currency in ₹, helplines are Indian (102, 112), DPDP not GDPR, ABDM not HL7 FHIR (though compatible). App is Android-only for now.

4. **Offline-first is real.** Don't write copy that assumes cloud connectivity. The vault works without internet.

5. **No medical claims.** The app complements doctors. It doesn't diagnose, treat, or cure. AI insights cite sources. This is a legal requirement, not just brand preference.

6. **The app is Android-only at launch.** No iOS yet. Don't show iPhone mockups. Play Store only.

7. **DPDP compliance is a feature, not a checkbox.** 5 consent categories, right to erasure, right to nominee, real DPO contact. Treat this as a first-class selling point.

8. **Photography direction matters.** Real Indian families. Multi-generational. No stock-photo white coats. If using placeholder images, note the direction for eventual replacement.

---

## 10. Success Metrics

### Customer Acquisition
- Website live at kinsuhealth.in with Play Store CTA
- 30-day content calendar fully drafted and ready to schedule
- 5 Instagram carousels, 3 LinkedIn posts, 5 Reel scripts, 1 Twitter thread — all ready to publish
- Email waitlist functional (if app not yet on Play Store)

### Fundraising Readiness
- Website serves as a credibility signal (investors will check it)
- LinkedIn presence establishes founder thought leadership
- Technical content (without internals) demonstrates depth
- One-pager and deck drafts ready for refinement

---

## 11. Prioritisation

**Do first:**
1. Website — hero section + features + privacy + FAQ + footer (functional MVP)
2. Instagram carousel #1 ("Why your prescriptions shouldn't live in WhatsApp")
3. LinkedIn founder launch post
4. 30-day content calendar structure

**Do next:**
5. Remaining 4 carousels
6. TikTok/Reel scripts
7. Twitter launch thread
8. Content generation automation scripts

**Do later:**
9. Investor one-pager
10. Pitch deck
11. Demo script
12. Advanced automation (Canva API integration, scheduling)

---

*This handover is complete. Claude Code should have everything needed to begin work. If screenshots, logos, or Play Store links are not yet available, scaffold with clearly marked placeholders and move forward.*
