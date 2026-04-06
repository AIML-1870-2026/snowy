# Drug Safety Explorer — Spec

## Overview

A single-page web application for **educational purposes only** that lets users compare prescription and OTC drugs side by side using live data from the [OpenFDA API](https://open.fda.gov/apis/).

---

## Core Features

### 1. Drug Comparison
- User enters 1–3 drug names in search fields
- Each drug gets its own comparison card rendered side by side
- Cards display:
  - Drug name and generic name (if different)
  - Top reported adverse effects (from `drug/event` endpoint)
  - A count badge showing total adverse event reports
  - Color-coded severity indicator (see below)
  - Recall history (from `drug/enforcement` endpoint)
  - Optional expandable sections (see below)

### 2. Adverse Effects Display
- Pull from `drug/event.json` — aggregate `patient.reaction.reactionmeddrapt` terms
- Show top 10 most frequently reported reactions
- Each reaction shown as a tag/pill with frequency count
- Severity color coding:
  - **Red** — serious/life-threatening outcomes reported (outcome code 1, 2, or 5)
  - **Orange** — hospitalization or disability reported (outcome code 3 or 4)
  - **Yellow** — non-serious outcomes only
  - **Gray** — outcome data unavailable

### 3. Market Withdrawal Timeline
- Pull from `drug/enforcement.json` filtered by drug name
- Render a vertical timeline showing:
  - Date of recall/withdrawal
  - Reason (e.g., contamination, labeling error, safety risk)
  - Classification (Class I = most serious → Class III = least serious)
  - Voluntary vs. FDA-mandated
- Timeline entries color-coded by recall class (red/orange/yellow)

### 4. Optional Expandable Sections (per drug card)
Buttons the user can toggle to reveal additional info:
- **Drug Label Info** — from `drug/label` endpoint: indications, warnings, contraindications
- **Full Reaction List** — complete adverse event reaction list beyond the top 10
- **Recall Details** — full enforcement action text and distribution scope

---

## Edge Case Handling

| Scenario | Behavior |
|---|---|
| Drug not found in OpenFDA | Card shows "No data found for [name]" with a note to check spelling or try a brand/generic name |
| Drug exists but has zero adverse event reports | Card shows a neutral "No adverse events on record" message — not treated as safe, just undocumented |
| Drug exists but has no recall history | Timeline section shows "No recalls or market withdrawals found" |
| API rate limit or network error | Card shows an inline error with a retry button |
| Duplicate drug entered | Deduplicate silently; do not show the same card twice |
| Very long drug name / unusual characters | Sanitize input; truncate display names gracefully |

---

## UI / Layout

- Clean, minimal design — dark or light theme (user toggle)
- Responsive: stacks cards vertically on mobile, side-by-side on desktop
- Prominent disclaimer banner: *"For educational purposes only. Not a substitute for professional medical advice."*
- Search bar at top with an "Add Drug" button to add comparison slots (max 3)
- Each card has an "X" to remove it from comparison
- Loading skeleton while API calls are in flight

---

## API Endpoints Used

| Data | Endpoint |
|---|---|
| Adverse events | `GET /drug/event.json?search=patient.drug.medicinalproduct:[name]&count=patient.reaction.reactionmeddrapt.exact` |
| Recall/enforcement | `GET /drug/enforcement.json?search=product_description:[name]&limit=20` |
| Drug label | `GET /drug/label.json?search=openfda.brand_name:[name]` |

All requests use the public OpenFDA API (no API key required for low-volume use).

---

## Out of Scope

- No user accounts or saved comparisons
- No diagnosis or treatment recommendations
- No drug–drug interaction analysis
- No pediatric or pregnancy-specific filtering
