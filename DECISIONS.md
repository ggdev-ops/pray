# DECISIONS.md — Architectural Decisions

## Decision 1: Random Selection Over Sequential

**Date:** Prior to refactor
**Context:** Original `pray.js` showed names in order (1, 2, 3...). User experience felt repetitive — predictable next name killed the sense of discovery.
**Decision:** Use random selection with deduplication. Track shown names in an array. Pick random, skip seen, until all 99 are shown.
**Consequences:**
- Each session feels fresh — user doesn't know what's coming
- `shownPrayers` array prevents duplicates
- Reset clears the array, restarting the cycle
**Alternative rejected:** Sequential with shuffle on page load — rejected because shuffle-on-load still gives a static order for that session. Random-on-click gives unpredictability per tap.

---

## Decision 2: AGENTS.md Visibility Policy

**Date:** 2026-09-15
**Context:** AGENTS.md contains Ahmed's development philosophy, agent roles, and the 100-line boundary rule. Decided whether to commit it to the public GitHub repo or exclude it via .gitignore.
**Decision:** Commit AGENTS.md. It is part of the project identity. The public repo should reflect what this project actually is — not a sanitized version.
**Consequences:**
- Public visitors can read the development philosophy
- Agents cloning the repo get the rules immediately
- No hidden "real" version of the project
**Alternative rejected:** Gitignore AGENTS.md — rejected because it would make the public repo a lie. The project includes this file. Excluding it hides the project's true nature.

---

## Decision 3: Touch-Action Manipulation for Button

**Date:** 2026-09-15
**Context:** Double-tap on mobile triggered unwanted zoom when tapping the prayer button. User reported accidental zoom in.
**Decision:** Add `touch-action: manipulation` CSS property to all buttons. This disables the300ms tap delay and double-tap-to-zoom behavior while preserving pinch-to-zoom.
**Consequences:**
- No more accidental zoom on rapid taps
- Pinch-to-zoom still works for accessibility
- Instant tap response (no 300ms delay)
**Alternative rejected:** JavaScript `touchend` prevention — rejected because CSS solution is simpler, cleaner, and doesn't require JS event handling.

---

## Decision 4: PWA Manifest for Add to Home Screen

**Date:** 2026-09-15
**Context:** User wanted "Add to Home Screen" shortcut like native apps. Browsers require a web app manifest to show the install prompt.
**Decision:** Create `manifest.json` with app metadata (name, icons, theme, display mode). Add `<link rel="manifest">` and `<meta name="theme-color">` to HTML head. Generate 192x192 and 512x512 PNG icons.
**Consequences:**
- Browser shows "Add to Home Screen" banner on mobile
- App appears in home screen with custom icon
- Standalone display mode (no browser chrome)
- Dark theme matches app design
**Alternative rejected:** Skip PWA, just use a bookmark — rejected because the user explicitly asked for install behavior. PWA is the standard approach.

---

## Decision 5: Font Size Toggle for Accessibility

**Date:** 2026-09-15
**Context:** User reported fixed font size with no way to change it. Single size doesn't accommodate all reading preferences.
**Decision:** Add a 3-state font size toggle (أ- / أ / أ+) below the prayer text. Use CSS classes on `<body>` to scale prayer and counter text. Persist choice in `localStorage`.
**Consequences:**
- User controls text size without browser zoom
- Choice persists across sessions via localStorage
- Three sizes: small (16px), medium (20px), large (26px)
- Toggle is minimal UI — doesn't clutter the interface
**Alternative rejected:** Use relative `rem` units and rely on browser zoom — rejected because the user wants explicit in-app control, not browser-level zoom.
