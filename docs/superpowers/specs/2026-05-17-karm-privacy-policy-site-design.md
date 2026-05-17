# Karm Privacy Policy Site — Design Spec

**Date:** 2026-05-17  
**Status:** Approved

---

## Overview

A static GitHub Pages site that hosts the privacy policy for the Karm mobile app. Required for Google Play and App Store submissions. The site must be publicly accessible at a stable URL.

---

## Architecture

Single-page static site with no build tooling. One `index.html` file contains the full privacy policy with inline CSS. GitHub Pages serves it directly from the `main` branch root.

- **Repo:** `woozlyApp/karm-privacy` on GitHub
- **Local folder:** `/Users/ayushpaudel/Documents/personal/karm-privacy/`
- **Live URL:** `https://woozlyapp.github.io/karm-privacy/`
- **GitHub Pages source:** `main` branch, root `/`

---

## Files

```
karm-privacy/
  index.html     # Privacy policy page (self-contained HTML + CSS)
  README.md      # Brief description of the repo's purpose
```

No dependencies, no build step, no framework.

---

## Privacy Policy Content

The policy covers the current v1 state of the app and must be accurate and complete for app store review.

### What the app does NOT collect
- No account or sign-up
- No name, email, or personal identifiers from the app itself
- All task data (tasks, history, carryover) stored locally on-device via Hive — never transmitted

### What AdMob collects (third-party)
Karm displays ads served by Google AdMob. AdMob may collect:
- Advertising ID (GAID on Android, IDFA on iOS)
- Device information (model, OS version)
- IP address
- Approximate location (derived from IP)
- Ad interaction data (impressions, clicks)

Google acts as an independent data controller for this data. Reference: [Google's Privacy Policy](https://policies.google.com/privacy) and [How Google uses data from apps](https://policies.google.com/technologies/partner-sites).

### User rights
- Users can opt out of personalized ads via device settings (Android: Google Settings → Ads; iOS: Settings → Privacy → Apple Advertising)
- Users in applicable jurisdictions (GDPR, CCPA) have rights to access/delete their data held by Google

### Forward-looking note
A brief statement that the policy will be updated when v2 introduces accounts and subscriptions.

### Contact
A contact email for privacy-related questions. **To confirm during implementation:** which email address to display (e.g., a dedicated `privacy@` address or the developer's contact email).

### Effective date
2026-05-17

---

## Design Decisions

- **No Jekyll/themes:** overkill for a single policy page; plain HTML loads faster and has zero maintenance overhead
- **Inline CSS:** keeps the file self-contained; no external stylesheet requests
- **No JS:** privacy policy pages should be maximally simple and trustworthy
- **Single page:** terms of service and support pages can be added later if needed without restructuring

---

## Out of Scope

- Terms of Service page (not needed for v1 submission)
- Support page
- v2 policy updates (will be a separate edit when auth/subscription ships)
