# Thrive marketing images

Turns clean app screenshots into branded marketing images (App Store + social)
with consistent typography and differentiator-led copy.

## Why this exists
Hand-scrubbing PII out of real screenshots is slow and error-prone. Thrive
already ships **Privacy Mode**, which swaps every module to a realistic demo
household — no real balances, no names, no account numbers. Screenshot *that*
and there is nothing to redact.

## Workflow

**1. Turn on Privacy Mode**
In Thrive: the privacy toggle in the toolbar (or Settings → Privacy & Security).
Confirm the banner is showing before you capture — that's your guarantee the
numbers on screen are demo data.

**2. Capture the shot list** (iPhone, no notch clutter — clean status bar)
Save each into `raw/` with these exact names:

| File | Screen | Why it sells |
|---|---|---|
| `transactions.png` | Transactions list | No bank linking — the privacy proof |
| `household.png` | Settings → Privacy → Household Sharing | Spouse sharing, our #2 differentiator |
| `dashboard.png` | Dashboard | The "know where you stand" hero |
| `budget.png` | Budget at-a-glance | Zero-based budgeting |
| `giving.png` | Giving goal + graph | Stewardship / tithe |
| `emergency-fund.png` | Emergency Fund | Safety net |

Capture the **screen only** (no device frame, no added captions) — the
generator adds the frame, gradient, and copy.

**3. Generate**
```
swift make_marketing.swift
```
Output in `out/`, three sizes per shot:
- `appstore-6.9` (1320×2868) — primary iPhone size
- `appstore-6.5` (1242×2688) — older device families
- `social-og` (1200×630) — link previews, blog headers, social posts

## Changing the copy
Edit the `shots` array at the top of `make_marketing.swift`. Each entry has a
`badge`, `headline` (use `\n` for line breaks), an `accent` phrase tinted
emerald, and a `subhead`. Layout is handled for you.

## Copy principles
- Lead with the differentiator, not the feature.
- Short declaratives beat descriptions: "No bank linking. Ever."
- Name what competitors can't claim: no bank credentials, no servers, an
  Apple-verified "Data Not Collected" label, spouse sharing without a shared
  login.
- Never name a competitor's trademark.
