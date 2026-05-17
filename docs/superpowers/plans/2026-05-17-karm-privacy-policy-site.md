# Karm Privacy Policy Site — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Publish a static privacy policy page for the Karm app at `https://woozlyapp.github.io/karm-privacy/`

**Architecture:** Single self-contained `index.html` with inline CSS served directly by GitHub Pages from the `main` branch root. No build step, no dependencies, no JavaScript.

**Tech Stack:** Plain HTML5, CSS, GitHub Pages, GitHub CLI (`gh`)

---

## File Map

| File | Action | Purpose |
|------|--------|---------|
| `index.html` | Create | Privacy policy page — self-contained HTML + CSS |
| `README.md` | Create | Repo description for GitHub |

---

### Task 1: Add contact email and create README

**Files:**
- Create: `README.md`

- [ ] **Step 1: Decide on contact email**

  Choose which email to display for privacy inquiries. Options:
  - A dedicated address like `privacy@woozlyapp.com`
  - Your personal developer contact email

  Note this email — you will use it in Task 2.

- [ ] **Step 2: Create README.md**

  Create `README.md` at the repo root with this content (substitute your actual email):

  ```markdown
  # karm-privacy

  Privacy policy page for the [Karm](https://play.google.com/store/apps/details?id=com.woozlyapp.karm) app, served via GitHub Pages.

  **Live URL:** https://woozlyapp.github.io/karm-privacy/

  ## Updating the Policy

  Edit `index.html` and commit to `main`. GitHub Pages deploys automatically within ~60 seconds.
  ```

- [ ] **Step 3: Commit**

  ```bash
  git add README.md
  git commit -m "Add README"
  ```

---

### Task 2: Create the privacy policy page

**Files:**
- Create: `index.html`

- [ ] **Step 1: Create index.html**

  Create `index.html` at the repo root with the full content below. Replace `YOUR_CONTACT_EMAIL` (appears twice, in the `href` and link text) with the email you chose in Task 1.

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Privacy Policy — Karm</title>
    <style>
      *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
      body {
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
        color: #1a1a1a;
        background: #fff;
        line-height: 1.7;
        padding: 2rem 1.25rem;
      }
      .wrap { max-width: 680px; margin: 0 auto; }
      h1 { font-size: 1.75rem; font-weight: 700; margin-bottom: 0.25rem; }
      .meta { color: #666; font-size: 0.9rem; margin-bottom: 2.5rem; }
      h2 { font-size: 1.1rem; font-weight: 600; margin: 2rem 0 0.5rem; }
      p { margin-bottom: 1rem; }
      ul { margin: 0.5rem 0 1rem 1.5rem; }
      li { margin-bottom: 0.4rem; }
      a { color: #1a73e8; }
      footer {
        margin-top: 3rem;
        padding-top: 1.5rem;
        border-top: 1px solid #eee;
        color: #666;
        font-size: 0.85rem;
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <h1>Privacy Policy</h1>
      <p class="meta">Karm &mdash; Effective date: May 17, 2026</p>

      <p>Karm ("the app") is a minimal offline daily task tracker. This policy explains what data is collected when you use the app and how it is used.</p>

      <h2>Data Stored on Your Device</h2>
      <p>All task data — your tasks, history, and settings — is stored locally on your device. This data never leaves your device and is not transmitted to us or any server.</p>
      <p>Karm has no accounts, no sign-in, and no cloud sync. We never see your tasks.</p>

      <h2>Advertising (Google AdMob)</h2>
      <p>Karm displays ads provided by Google AdMob. To serve and measure ads, AdMob may collect:</p>
      <ul>
        <li>Advertising ID (Google Advertising ID on Android, IDFA on iOS)</li>
        <li>Device information (model, operating system version)</li>
        <li>IP address and approximate location derived from it</li>
        <li>Ad interaction data (impressions and clicks)</li>
      </ul>
      <p>Google controls this data independently under its own privacy policy. We do not receive or store this data ourselves.</p>
      <p>For details, see <a href="https://policies.google.com/privacy" target="_blank" rel="noopener">Google's Privacy Policy</a> and <a href="https://policies.google.com/technologies/partner-sites" target="_blank" rel="noopener">how Google uses data from apps that use its services</a>.</p>

      <h2>Opting Out of Personalized Ads</h2>
      <p>You can opt out of interest-based ads through your device settings:</p>
      <ul>
        <li><strong>Android:</strong> Settings &rarr; Google &rarr; Ads &rarr; Opt out of Ads Personalization</li>
        <li><strong>iOS:</strong> Settings &rarr; Privacy &amp; Security &rarr; Apple Advertising &rarr; turn off Personalized Ads</li>
      </ul>

      <h2>Children's Privacy</h2>
      <p>Karm is not directed at children under 13. We do not knowingly collect personal information from children under 13.</p>

      <h2>Future Updates</h2>
      <p>A future version of the app will introduce optional accounts and subscription features. This privacy policy will be updated before those features are released.</p>

      <h2>Changes to This Policy</h2>
      <p>If we make material changes to this policy, we will update the effective date at the top of this page. Continued use of the app after changes constitutes acceptance of the updated policy.</p>

      <h2>Contact</h2>
      <p>For privacy-related questions, contact us at <a href="mailto:YOUR_CONTACT_EMAIL">YOUR_CONTACT_EMAIL</a>.</p>

      <footer>
        &copy; 2026 WoozlyApp. All rights reserved.
      </footer>
    </div>
  </body>
  </html>
  ```

- [ ] **Step 2: Verify the email substitution**

  ```bash
  grep -n "YOUR_CONTACT_EMAIL" index.html
  ```

  Expected: no output (zero matches). If you see matches, the substitution was missed — fix them before continuing.

- [ ] **Step 3: Commit**

  ```bash
  git add index.html
  git commit -m "Add privacy policy page"
  ```

---

### Task 3: Create GitHub repo and push

**Prereq:** GitHub CLI (`gh`) must be authenticated. Run `gh auth status` to check. If not authenticated, run `gh auth login` first.

- [ ] **Step 1: Verify gh is authenticated**

  ```bash
  gh auth status
  ```

  Expected: shows `Logged in to github.com as ...`

- [ ] **Step 2: Create the remote repo under woozlyApp org**

  ```bash
  gh repo create woozlyApp/karm-privacy \
    --public \
    --description "Privacy policy for the Karm app"
  ```

  Expected: `✓ Created repository woozlyApp/karm-privacy on GitHub`

- [ ] **Step 3: Add remote and push**

  ```bash
  git remote add origin https://github.com/woozlyApp/karm-privacy.git
  git push -u origin main
  ```

  Expected: `Branch 'main' set up to track remote branch 'main' from 'origin'.`

---

### Task 4: Enable GitHub Pages

- [ ] **Step 1: Enable Pages via GitHub API**

  ```bash
  gh api repos/woozlyApp/karm-privacy/pages \
    --method POST \
    --field source='{"branch":"main","path":"/"}'
  ```

  Expected: JSON response containing `"url": "https://woozlyapp.github.io/karm-privacy/"` and `"status": "building"` (or `"built"`).

- [ ] **Step 2: Wait for deployment (~60 seconds) and verify**

  ```bash
  gh api repos/woozlyApp/karm-privacy/pages --jq '.status'
  ```

  Expected: `"built"`. If still `"building"`, wait 30 seconds and retry.

- [ ] **Step 3: Open the live URL**

  ```bash
  open https://woozlyapp.github.io/karm-privacy/
  ```

  Verify the page loads, shows the correct effective date, the AdMob section, opt-out instructions, and the correct contact email.

- [ ] **Step 4: Confirm URL for app store use**

  The privacy policy URL to submit to Google Play and App Store Connect is:

  ```
  https://woozlyapp.github.io/karm-privacy/
  ```
