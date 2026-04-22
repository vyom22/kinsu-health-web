# CLAUDE.md — Kinsu Website Deployment

## Project Overview

This is the static marketing website for **Kinsu AI Labs**, hosted at `kinsu.health` via GitHub Pages.
Zero-build static site — HTML + Tailwind (Play CDN) + vanilla JS.

**Repo:** `https://github.com/vyom22/kinsu-health-web` (branch: `main`, private)
**Live domain:** `kinsu.health` (GoDaddy DNS → `vyom22.github.io`)
**Waitlist form:** FormSubmit → `Founders@kinsu.health`
**Data Protection Officer:** `dpo@kinsu.health`

Strategy, content blueprint, aesthetics, and acceptance criteria live in
`WEBSITE_BUILD_BRIEF.md`. Read that before making substantive content changes.

---

## Repository Structure

```
/
├── index.html             # Home (single-page, all sections inline)
├── privacy.html           # DPDP-compliant Privacy Policy
├── terms.html             # Terms of Service
├── waitlist-thanks.html   # Post-FormSubmit confirmation page
├── 404.html               # Branded not-found page
├── sitemap.xml            # /, /privacy, /terms
├── robots.txt             # Allow all; sitemap reference
├── CNAME                  # Must contain exactly: kinsu.health
├── public/
│   └── kinsu_logo.png     # Favicon, apple-touch-icon, OG fallback
├── WEBSITE_BUILD_BRIEF.md # Source-of-truth for content + design
├── HANDOVER_CLAUDE_CODE.md# Phase 1/2 plan (legacy, informational)
└── CLAUDE.md              # This file
```

---

## Taking the Website Live

Follow these steps in order. Do not skip any step.

### Step 1 — Verify repo contents

```bash
ls -la index.html privacy.html terms.html 404.html waitlist-thanks.html CNAME sitemap.xml robots.txt public/kinsu_logo.png
```

- All listed files must exist at repo root (except the logo under `public/`).
- `CNAME` must contain exactly one line: `kinsu.health`.

### Step 2 — Configure GitHub Pages on `vyom22/kinsu-health-web`

Manual, one-time, in the GitHub UI (cannot be done via CLI for a private repo):

> Repo → Settings → Pages → Source: **Deploy from branch** → `main` → `/ (root)` → Save
> Custom domain: `kinsu.health` → Save
> Once DNS propagates, tick **Enforce HTTPS**.

Note: GitHub Pages on a private repo requires a Pro / Team plan.
If the account is Free, either (a) make the repo public, or (b) upgrade.

### Step 3 — DNS (already configured in GoDaddy)

DNS for `kinsu.health` already points to `vyom22.github.io` (CNAME target). Only
touch it if propagation breaks. Canonical records:

| Type  | Name | Value                 | TTL  |
|-------|------|-----------------------|------|
| A     | @    | 185.199.108.153       | 600  |
| A     | @    | 185.199.109.153       | 600  |
| A     | @    | 185.199.110.153       | 600  |
| A     | @    | 185.199.111.153       | 600  |
| CNAME | www  | vyom22.github.io      | 3600 |

Check propagation:
```bash
dig kinsu.health A +short
```

### Step 4 — Release the custom domain from the previous repo

The custom domain `kinsu.health` is currently bound to the prior deploy.
Before Pages can bind it here, remove the custom domain from the old repo:

> Old repo → Settings → Pages → Custom domain: clear → Save.

Then set it on `vyom22/kinsu-health-web` as in Step 2.

### Step 5 — Activate the FormSubmit waitlist

The waitlist form in `index.html` posts to `https://formsubmit.co/Founders@kinsu.health`.

One-time activation:
1. Submit the form once from the live site.
2. FormSubmit emails a confirmation link to `Founders@kinsu.health`.
3. Click it. Future submissions arrive directly.

### Step 6 — Smoke test after deployment

```bash
curl -I https://kinsu.health
curl -I https://www.kinsu.health   # should 301 → https://kinsu.health
```

Manual checks:
- [ ] `https://kinsu.health` loads, no mixed-content warnings.
- [ ] Favicon appears in tab.
- [ ] Anchor nav scrolls to correct sections.
- [ ] Mobile hamburger works at 375px.
- [ ] `/privacy`, `/terms`, `/waitlist-thanks` all render.
- [ ] Typing a random path (e.g. `/nope`) serves the branded 404.
- [ ] Waitlist form submits → redirects to `/waitlist-thanks`.

---

## Making Changes to the Site

Zero build step. Edit → commit → push.

```bash
git add <files>
git commit -m "describe what changed"
git push origin main
```

GitHub Pages rebuilds automatically within ~60 seconds.

### Brand tokens (CSS vars + Tailwind theme)

| Token              | Value     | Used for                       |
|--------------------|-----------|--------------------------------|
| `ink`              | `#0E1F2B` | Primary text                   |
| `ink-soft`         | `#42566A` | Body / muted text              |
| `paper`            | `#FAF7F0` | Page background                |
| `paper-alt`        | `#F1ECE0` | Alternating section background |
| `line`             | `#E4DED0` | Borders / hairlines            |
| `kinsu.DEFAULT`    | `#309BD3` | Primary brand (buttons, links) |
| `kinsu.ink`        | `#1F6FA0` | Hover / link ink               |
| `kinsu.mist`       | `#E6F2FA` | Tints, accent backgrounds      |
| font: heading      | Lexend    | H1–H3                          |
| font: body         | Inter     | Everything else                |

### Home page section IDs

| Section              | HTML id       | Nav link         |
|----------------------|---------------|------------------|
| Hero                 | `#home`       | —                |
| Problem              | `#problem`    | —                |
| Feature bento        | `#features`   | Features         |
| Family Care          | `#family-care`| Family           |
| Privacy / DPDP       | `#privacy`    | Privacy          |
| AI disclaimer        | `#ai`         | —                |
| FAQ                  | `#faq`        | FAQ              |
| Waitlist             | `#waitlist`   | Join waitlist    |

---

## Do Not

- Do not move `index.html` out of root — GitHub Pages requires it there.
- Do not delete `CNAME` — breaks the custom domain.
- Do not add a build system or bundler — this site is intentionally zero-dependency.
- Do not change the favicon path without updating the `<link rel="icon">` tag across every HTML file.
- Do not expose the internal model codename ("TTT-RetNet") anywhere on the site. Public name is **Sparrow**.
- Do not add third-party trackers or cookies. Analytics, if any, must be cookieless (e.g., Plausible).
- Do not embed real patient/family photos in Phase 1. Illustrations and CSS/SVG placeholders only.
- Do not publish claims that imply Kinsu diagnoses, prescribes, or replaces a clinician. AI outputs are informational.

---

## Contacts

| Role              | Contact                              |
|-------------------|--------------------------------------|
| Founders email    | Founders@kinsu.health                |
| DPO               | dpo@kinsu.health                     |
| Phone             | +91 86993 82384                      |
| DNS registrar     | GoDaddy                              |
| Form backend      | formsubmit.co (no account needed)    |
| Host              | GitHub Pages (vyom22.github.io)      |
