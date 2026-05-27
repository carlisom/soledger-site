# Go-Live Checklist — Coming Soon → Live App Store

Steps to complete once Soledger is approved and live on the App Store.

---

## 1. Get the real App Store URL

After App Store approval, find the URL in App Store Connect:
- **Apps → Soledger → App Information → View on App Store**
- Format: `https://apps.apple.com/app/soledger/id<YOUR_APP_ID>`

---

## 2. Update `index.html` (2 places)

**Hero badge** (~line 59) and **bottom CTA badge** (~line 354).

For each, replace the `<span class="coming-soon-wrap">...</span>` wrapper with a plain link:

```html
<!-- Before -->
<span class="coming-soon-wrap">
  <a href="#" class="app-store-badge" ...>...</a>
  <span class="coming-soon-badge">Coming Soon</span>
</span>

<!-- After -->
<a href="https://apps.apple.com/app/soledger/id<YOUR_APP_ID>" class="app-store-badge" ...>...</a>
```

---

## 3. Update `support.html` (1 place)

The "Open in App Store →" contact link (~line 62). Replace the muted span with a real link:

```html
<!-- Before -->
<span style="opacity:0.55; cursor:default">Open in App Store →</span>
<span class="coming-soon-badge" style="position:static; margin-left:8px; vertical-align:middle">Coming Soon</span>

<!-- After -->
<a href="https://apps.apple.com/app/soledger/id<YOUR_APP_ID>">Open in App Store →</a>
```

---

## 4. Update the nav "Get the app" button (4 files)

`index.html`, `support.html`, `privacy.html`, `terms.html` — each has a nav button (~line 38–42).

```html
<!-- Before -->
<span class="coming-soon-wrap">
  <a href="#download" class="btn">Get the app</a>
  <span class="coming-soon-badge">Coming Soon</span>
</span>

<!-- After -->
<a href="https://apps.apple.com/app/soledger/id<YOUR_APP_ID>" class="btn">Get the app</a>
```

---

## 5. Clean up now-unused CSS

Once all coming-soon markup is removed, delete these rules from `styles.css`:

```css
/* Coming Soon badge overlay */
.coming-soon-wrap { ... }
.coming-soon-wrap .app-store-badge,
.coming-soon-wrap .btn { ... }
.coming-soon-badge { ... }
```

---

## 6. Verify

- Open all four pages and confirm every badge/button links to the correct App Store URL.
- Test on mobile — the nav badge clips differently at narrow widths.
- Submit the App Store URL as the Marketing URL in App Store Connect if not already set.
