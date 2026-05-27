# Screenshot Recommendations

Recommendations for replacing the four placeholder slots in `soledger-site/index.html`, plus suggested additional shots to strengthen the page. All screenshots should be taken from the iPhone 17 simulator (id: `21340FA1-20C1-474B-9052-3CB4F6E6DBDB`, OS 26.4.1) at native resolution in portrait orientation.

> **Format note:** The CLAUDE.md for this site says 1290×2796 PNG (iPhone 15 Pro Max). Since the available simulator is iPhone 17, capture at that device's native resolution and update the CLAUDE.md reference once confirmed. Export as PNG, no device frame (the site provides its own phone chrome).

---

## Required Placeholders (already in index.html)

### Slot 1 — Hero phone screen
**Location:** `index.html` lines 91–94, inside `.phone` `.phone-screen`  
**Current placeholder label:** "hero screenshot · drop your home screen / shoe list here · 9:19.5 portrait"  
**Destination filename:** `assets/screenshots/home.png`

**Recommended shot:**
Take the **main Shoes tab** with a realistic, populated state:
- Active shoe in the full-bleed hero card at the top (e.g., a named road trainer with ~300 miles on a 500-mile lifespan, showing the tread gauge ring in healthy green).
- 2–3 additional pairs in the rotation list below with varied mileage states — one healthy, ideally one near its nudge threshold (amber "replace soon" banner) so the color system is immediately visible.
- Show the app in **light mode** (matches the site's warm cream palette).
- Make sure the shoe names and brand text look realistic (not "Test Shoe 1").
- The Sync chip should be visible but not foregrounded.

**Why this works:** It's the first thing visitors see. It needs to answer "what does this app actually look like?" in one glance while showcasing the core value prop (gauge ring, replace-soon amber, cost-per-mile chip).

---

### Slot 2 — Gallery shot 01: Shoe list
**Location:** `index.html` lines 212–219, first `.shot` in `.gallery`  
**Current caption:** "01 · Shoe list"  
**Destination filename:** `assets/screenshots/shoe-list.png`

**Recommended shot:**
A **wider / taller crop of the Shoes tab** — similar concept to the hero shot but showing more of the list. Ideally:
- Hero card shows a shoe with ~80–85% life used (warm amber tread gauge, "replace soon" banner active) — this lets visitors see the replace-soon state clearly.
- 2–3 rotation shoes below with healthy green gauges.
- Light mode.

**Why:** The gallery caption says "the home — active pair on top, healthy below, retired stowed away." This shot should tell that story — differentiated states help it read quickly.

---

### Slot 3 — Gallery shot 02: Detail / CPM
**Location:** `index.html` lines 221–228, second `.shot` in `.gallery`  
**Current caption:** "02 · Detail · CPM"  
**Destination filename:** `assets/screenshots/shoe-detail.png`

**Recommended shot:**
The **Shoe Detail view** for a shoe with meaningful mileage and a real purchase price entered:
- Tread gauge ring prominently visible with % used.
- **Cost per mile** stat showing a realistic figure (e.g., `$0.32 / mi`) — this is a key differentiating feature the site calls out in the features section.
- Projected cost per mile also visible.
- "This week's mileage" and run count tiles.
- 3–5 runs in the recent run history list with dates and distances.
- Light mode.

**Why:** The CPM feature is the #2 feature card on the site ("Cost per mile, finally."). This is the screenshot that makes that claim tangible.

---

### Slot 4 — Gallery shot 03: Dark mode
**Location:** `index.html` lines 230–238, third `.shot` in `.gallery`  
**Current caption:** "03 · Dark mode"  
**Destination filename:** `assets/screenshots/dark-mode.png`

**Recommended shot:**
The same **Shoe Detail view** (or the Shoes tab hero card) in **dark mode** — the app's warm dark palette (bone text on near-black background, ember accents).
- Show a shoe at a visually interesting state — either the replace-soon amber state or a nicely-used tread gauge.
- The caption on the site says "reading by candlelight — warm, never corporate gray" — the warm dark tones should be front and center, not a flat gray.

**Why:** Demonstrates the design quality of the dark mode and shows it's not an afterthought. The site copy emphasizes warmth and craft; the screenshot needs to deliver that.

---

## Suggested Additional Screenshots (not currently slotted, but worth considering)

### Suggested A — Sync Review / Run Assignment
**Represents feature:** "Synced from Apple Health" (Feature 01) and the "Pick which pair" step in How It Works.

The **Sync tab** showing a list of unassigned runs from Apple Health:
- A few run rows visible with distance, date, and duration.
- The "Apply All" button visible at the top.
- One run with a shoe picker open (showing the shoe selection dropdown).
- Light mode.

**Why add it:** The "how it works" section explains the assignment step but has no visual. Visitors unfamiliar with HealthKit-based tracking benefit from seeing what that assignment moment looks like — it's not obvious from the shoe list alone.

---

### Suggested B — Replace-soon notification (iOS notification banner)
**Represents feature:** "A nudge before you need it" (Feature 03).

A **system-level notification banner** from Soledger showing a replace-soon alert, captured on the home screen or within the app:
- Example: "Pegasus 41 · Replace soon — 72 mi left" (or similar).
- Can be captured via iOS Simulator's notification simulation.

**Why add it:** The replace-soon alert is Feature 03 and is prominent in the site copy and the bottom floating chip in the hero. Showing the actual notification makes the promise concrete.

---

### Suggested C — History tab (retired pair memorial)
**Represents feature:** The full shoe lifecycle — retire, archive, review history.

The **History tab** showing:
- A lifetime stats card at top (total miles served, avg cost per mile).
- 2–3 retired pairs listed with their final mileage.
- One retired pair tapped to show the memorial detail view (final miles, cost per mile, months served).

**Why add it:** The site doesn't currently surface the lifecycle story — shoes get retired, their history lives on. This would round out the feature story if the gallery is ever expanded beyond 3 shots.

---

## Capture Checklist

- [ ] Set simulator to iPhone 17 (id: `21340FA1-20C1-474B-9052-3CB4F6E6DBDB`)
- [ ] Use realistic shoe names, brands, and prices (no test data)
- [ ] Vary mileage states: at least one healthy, one near threshold
- [ ] Slots 1–3: light mode; Slot 4: dark mode
- [ ] Status bar: set to a clean time (e.g., 9:41 AM), full signal, full battery
- [ ] Export as PNG at native simulator resolution
- [ ] Place in `soledger-site/assets/screenshots/`
- [ ] Replace `.slot` divs in `index.html` per the instructions in `CLAUDE.md`
- [ ] Update CLAUDE.md screenshot resolution note if iPhone 17 resolution differs from 1290×2796
