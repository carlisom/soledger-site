# Soledger Site Accuracy Plan

Corrections needed in `soledger-site` based on comparison against the app as built (`FUNCTIONALITY.md` + source code, May 2026). Items are grouped by severity.

---

## Priority 1 — Factually Wrong (fix before launch)

### 1. Subscription model claim — `index.html` FAQ
**Current text (FAQ "Is there a subscription?"):**
> No. Soledger is a one-time purchase on the App Store. No subscriptions, no tiers, no premium analytics behind a paywall. If we add features later, they go to everyone.

**Problem:** The app has a Soledger Pro placeholder in Settings wired to an annual subscription (StoreKit 2 integration pending). The pricing direction is a subscription, not a one-time purchase. This answer is false if the app launches with any paid tier.

**Action required:** Rewrite this answer to reflect the actual model once the pricing decision is finalized. If the freemium model ships (free tier + Pro subscription), a truthful answer might read something like:
> Soledger is free to download. Core tracking is free — no time limits, no nags. Soledger Pro adds [feature list] for $X/year. [Or: We're still nailing down the pricing — check back closer to launch.]

If the app ships without any Pro tier active, this answer is fine as-is but will need updating the moment Pro goes live.

---

### 2. iPad support claim — `index.html` FAQ
**Current text (FAQ "Does it work on iPad or Apple Watch?"):**
> iPad — yes, with a side-by-side list and detail layout.

**Problem:** iPad is explicitly listed as "Post-launch" in FUNCTIONALITY.md. The app is iPhone-only at v1. This claim is incorrect and would mislead buyers expecting iPad support.

**Action required:** Remove the iPad claim. Replace with:
> Not in v1. Soledger is iPhone-only at launch. iPad and Apple Watch are on the roadmap.

Or simply:
> iPhone only for now. Apple Watch and iPad support are planned for a future version.

---

## Priority 2 — Inaccurate Descriptions (fix before launch)

### 3. Replace-soon logic described as percentage-based — `index.html` FAQ
**Current text (FAQ "How do you decide a shoe needs replacement?"):**
> Soledger shows healthy green until 70%, ages it through 85%, and turns amber for *replace soon* after that.

**Problem:** The app's replace-soon nudge is triggered by a configurable **miles-remaining** threshold (default: 75 miles remaining), not by a percentage. The tread gauge ring shows percentage visually, but the nudge fires at a mileage threshold the user sets per-shoe (options: 50, 75, 100, 150 mi). For a 300-mile shoe, 75 mi remaining = 75% used, not 85%. For a 400-mile shoe it's ~81%. The 85% figure is only approximately correct for a 500-mile shoe.

**Action required:** Rewrite to describe how the nudge actually works:
> You set it. When you add a pair you choose the expected lifetime (300–800 miles) and a nudge threshold — the number of miles remaining when Soledger turns amber and sends a *replace soon* alert. The default is 75 miles out, but you can set it higher or lower. You can also retire a pair at any time — Soledger never forces it.

---

### 4. Sync tab described as pull-to-refresh — `support.html` troubleshooting
**Current text:**
> Check that … (3) you've pulled to refresh the Sync tab.

**Problem:** The app does not use pull-to-refresh on the Sync tab. Sync is triggered by tapping the **Sync chip** on the Shoes tab (or fires automatically in the background). There is no pull-to-refresh gesture.

**Action required:** Change to:
> … (3) you've tapped the **Sync** chip at the top of the Shoes tab to run a fresh sync.

---

### 5. Bulk assignment described as "swipe-select" — `support.html` getting started
**Current text:**
> To bulk-assign, swipe-select multiple runs and pick one shoe.

**Problem:** The app has an **Apply All** button that assigns all unassigned runs to the active shoe. There is no swipe-select gesture for multi-run selection in the current implementation.

**Action required:** Replace with:
> To assign all unassigned runs to your active shoe at once, tap **Apply All** at the top of the Sync tab.

---

### 6. Historical Probe location wrong — `support.html` troubleshooting
**Current text:**
> If you're looking for older runs that pre-date when you installed Soledger, use the *Historical Probe* in Settings to pick a date range and search.

**Problem:** The Historical Probe is not in Settings. It is accessible from the **Shoe Detail view** (via a button on that screen) and from the **Sync tab empty state** (when all runs are assigned). It is not in Settings.

**Action required:** Change to:
> If you're looking for older runs, tap **Search older runs** on any shoe's detail screen to open the Historical Probe. Pick a date range and Soledger will search Apple Health for runs you haven't imported yet.

---

### 7. "Un-retire" flow described incorrectly — `support.html` troubleshooting
**Current text (I retired a shoe by accident):**
> Open the shoe, tap the menu, and choose **Un-retire**. The pair returns to your active list with its full history intact.

**Problem:** The app does not have an "Un-retire" menu option on the shoe detail. Restoration happens via (a) **swipe left on the shoe in the History tab** → Restore, or (b) opening the shoe's memorial detail view and tapping **Restore to rotation**. There is no menu → Un-retire path.

**Action required:** Change to:
> Open the **History** tab. Swipe left on the retired shoe and tap **Restore** — or tap the shoe to open its memorial and tap **Restore to rotation**. The pair comes back with its full mileage history intact. Retiring a shoe never deletes data.

---

### 8. Privacy policy lists features that don't exist — `privacy.html`
**Current text (What Soledger collects, bullet list):**
> Shoes you've added — brand, model, purchase price, expected lifetime, **color**, retire status, **photos you choose to attach**.

**Problem:** The current app has no "color" field and no photo attachment feature for shoes. Neither is in FUNCTIONALITY.md or the source. These appear to have been written anticipating future features. Listing non-existent data types in a privacy policy creates false expectations and potential compliance issues.

**Action required:** Remove "color" and "photos you choose to attach" from the bullet. The corrected line:
> Shoes you've added — brand, model, purchase price, expected lifetime, and retire status.

If color or photos are added in a future version, update the privacy policy at that time.

---

## Priority 3 — Nuance / Future Risk (address when relevant)

### 9. Feature card says "No cloud sync" — `index.html` feature 04
**Current text:**
> No accounts. No analytics. No cloud sync, no leaderboards.

**Status:** Accurate for v1. However, iCloud sync is specifically planned as a Soledger Pro feature and the CloudKit architecture is already baked into the data model. When Pro ships with iCloud sync, this feature card will need to be updated. Flag this for the Pro launch checklist rather than changing it now.

---

### 10. Lifespan examples in "How it works" — `index.html` Step 01
**Current text:**
> Set the expected lifetime — 300, 500, 800 miles, whatever your legs and the rubber agree on.

**Status:** These are illustrative examples, not an exhaustive list, so the copy isn't "wrong." However, the app's default lifespan is **400 miles** and the picker includes 300, 400, 500, 600, and 800 mi. Consider adding 400 to the examples ("300, 400, 500…") so it reflects the default and the most common pick for road trainers. Low priority — fix opportunistically.

---

### 11. Milestone alerts — internal discrepancy to resolve
**Not a site error, but flagged here for awareness:** FUNCTIONALITY.md lists milestone alerts at **100 mi, 250 mi, and 500 mi**. The source code (per code analysis) fires at **50, 100, 200, 300, 400, and 500 mi**. The site does not mention specific milestone values anywhere, so no site copy needs changing. But FUNCTIONALITY.md should be updated to match the actual thresholds before it's used as a reference again.

---

## Non-Issues (confirmed correct)

- **Privacy claims** ("no servers, no accounts, no analytics, no third-party SDKs") — accurate.
- **HealthKit read-only access description** — accurate.
- **CSV export** — accurate (`Settings → Export Data`).
- **"No accounts"** claim throughout — accurate.
- **iOS 17+ requirement** — accurate per build settings.
- **Footer "v1.0 · iPhone · iOS 17+"** — accurate.
- **Apple Watch not in v1** — accurately stated in FAQ.
- **Weekly summary day/time** (Sunday 7 PM) — not stated on site, no correction needed.
- **Undo toast times** (5 s retire, 10 s delete) — not stated on site.
