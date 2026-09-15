# الدُّعَاءُ بِأَسْمَاءِ اللهِ الْحُسْنَى
# Prayer Through the 99 Names of God

A minimal web app that presents the 99 Names of God (Asma ul Husna) one by one, each paired with a corresponding prayer.

## What This Does

Tap the button. See a Name of God. Read the prayer. Tap again. The app tracks your progress through all 99 names, showing a celebration when you complete them all.

- **Randomized order** — fresh experience each session
- **Progress counter** — know where you are (X / 99)
- **Celebration state** — green glow when all 99 are complete
- **Restart option** — start over anytime

## Live Site

**https://ggdev-ops.github.io/pray/**

## How to Use

1. Open the site
2. Tap "الاسم التالي" (Next Name)
3. Read the Name and prayer
4. Continue until you see all 99
5. Celebrate. Restart if you wish.

## Tech

- Pure HTML, CSS, JavaScript — no frameworks, no build step
- Google Fonts (Cairo) for Arabic typography
- Responsive design — mobile, tablet, desktop

## Project Structure

| File | Purpose |
|------|---------|
| `index.html` | Main interface |
| `pray.js` | 99 Names data + selection logic |
| `AGENTS.md` | Project constitution and development philosophy |
| `DECISIONS.md` | Architectural decision records |

## Development

This project follows a strict workflow defined in `AGENTS.md`. The human architect (Ahmed) directs, the agent builds. Plan first, build second.

## Author

Ahmed Sami — [ggdev-ops](https://github.com/ggdev-ops)
