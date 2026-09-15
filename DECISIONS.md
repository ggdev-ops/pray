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
