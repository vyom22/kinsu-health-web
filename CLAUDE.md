# CLAUDE.md — Kinsu Website Deployment

## Project Overview

This is the static marketing website for **Kinsu AI Labs**, hosted at `kinsu.health` via GitHub Pages.
Single-file site: `index.html` + `public/kinsu_logo.png`.

**Repo:** `https://github.com/Vaibhav-nn/kinsu-health-website` (branch: `modified-design`)
**Live domain:** `kinsu.health` (GoDaddy DNS → GitHub Pages)
**Contact form:** FormSubmit → `Founders@kinsu.health`

---

## Repository Structure

```
/
├── index.html          # Entire site — HTML + CSS + JS in one file
├── CNAME               # Must contain exactly: kinsu.health
├── public/
│   └── kinsu_logo.png  # Favicon and logo asset
└── CLAUDE.md           # This file
```

---

## Task: Take the Website Live

Follow these steps in order. Do not skip any step.

### Step 1 — Verify repo contents

```bash
# Confirm these files exist at repo root
ls -la index.html CNAME public/kinsu_logo.png
```

- `index.html` must be present at root (not in a subfolder)
- `CNAME` file must exist and contain exactly one line: `kinsu.health`
- `public/kinsu_logo.png` must exist (referenced by favicon in index.html)

If `CNAME` is missing, create it:

```bash
echo "kinsu.health" > CNAME
git add CNAME
git commit -m "Add CNAME for custom domain"
git push origin modified-design
```

### Step 2 — Confirm the correct branch is set for GitHub Pages

GitHub Pages must be configured to deploy from branch `modified-design`, directory `/ (root)`.

This is done manually in the GitHub UI (Claude Code cannot do this via CLI):
> Repo → Settings → Pages → Source: Deploy from branch → `modified-design` → `/ (root)` → Save
> Custom domain: `kinsu.health` → Save
> Once DNS propagates, enable "Enforce HTTPS"

### Step 3 — Verify DNS records in GoDaddy

These A records and CNAME must be set in GoDaddy DNS for `kinsu.health`:

| Type  | Name | Value                  | TTL  |
|-------|------|------------------------|------|
| A     | @    | 185.199.108.153        | 600  |
| A     | @    | 185.199.109.153        | 600  |
| A     | @    | 185.199.110.153        | 600  |
| A     | @    | 185.199.111.153        | 600  |
| CNAME | www  | vaibhav-nn.github.io   | 3600 |

Remove any pre-existing A records pointing elsewhere before adding these.

Check propagation:
```bash
dig kinsu.health A +short
# Should return all four 185.199.x.x IPs once propagated
```

Or use: https://dnschecker.org/#A/kinsu.health

### Step 4 — Activate the contact form

The form in `index.html` posts to `https://formsubmit.co/Founders@kinsu.health`.

FormSubmit requires a one-time activation:
1. Submit the contact form once after the site is live
2. FormSubmit will send a confirmation email to `Founders@kinsu.health`
3. Click the confirmation link in that email
4. All future submissions will arrive directly — no further action needed

### Step 5 — Smoke test after deployment

```bash
# Check the site is reachable
curl -I https://kinsu.health

# Expected: HTTP/2 200, served by GitHub Pages
# Check for: content-type: text/html

# Check www redirect works
curl -I https://www.kinsu.health
# Expected: redirect to https://kinsu.health
```

Also verify manually in browser:
- [ ] `https://kinsu.health` loads with no mixed-content warnings
- [ ] Favicon (Kinsu logo) appears in browser tab
- [ ] Nav links scroll to correct sections
- [ ] Contact form renders correctly
- [ ] Mobile hamburger menu works (test at 375px width)

---

## Making Changes to the Site

All site content and styles live in `index.html`. There is no build step.

```bash
# Edit the file
# Then deploy:
git add index.html
git commit -m "describe what changed"
git push origin modified-design
```

GitHub Pages deploys automatically within ~60 seconds of a push.

### Key design tokens (in `:root` CSS vars)

| Token          | Value                        | Used for              |
|----------------|------------------------------|-----------------------|
| `--teal`       | `#0F9A96`                    | Primary brand colour  |
| `--teal-mid`   | `#0A7C78`                    | Hover states          |
| `--yellow`     | `#F5DF40`                    | Accent / gradient end |
| `--bg-0`       | `#04080F`                    | Main background       |
| `--bg-1`       | `#050B14`                    | Alternate sections    |
| `--cream`      | `#FAF6EE`                    | App mockup screen     |

### Sections and their IDs

| Section            | HTML id      | Nav link         |
|--------------------|--------------|------------------|
| Hero               | `#home`      | —                |
| Health App         | `#app`       | Health App       |
| Sparrow AI         | `#sparrow`   | Sparrow AI       |
| Research Journey   | `#research`  | Research         |
| Why Now            | _(no id)_    | —                |
| Team               | `#team`      | Team             |
| Market Opportunity | _(no id)_    | —                |
| Contact            | `#contact`   | Partner with us  |

---

## Do Not

- Do not move `index.html` into a subfolder — GitHub Pages requires it at root
- Do not delete or modify the `CNAME` file — it will break the custom domain
- Do not add a build system or bundler — the site is intentionally zero-dependency
- Do not change the favicon path (`/public/kinsu_logo.png`) without updating the `<link rel="icon">` tag in `index.html`
- Do not expose internal architecture naming ("TTT-RetNet") anywhere on the site — use "our architecture" or "Hybrid"

---

## Contacts

| Role              | Contact                      |
|-------------------|------------------------------|
| Founders email    | Founders@kinsu.health        |
| Phone             | +91 86993 82384              |
| DNS registrar     | GoDaddy                      |
| Form backend      | formsubmit.co (no account needed) |
