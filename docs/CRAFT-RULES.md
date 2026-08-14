# Craft Rules — the engineering that makes it feel real

Everything here was learned on real client decks that failed review before these rules existed.

## 1. Resolution-perfect canvas (the auto-fit rule)

Design every slide at a fixed 1920×1080 canvas, then transform-scale the whole canvas to fit the viewport. Never lay out slides in `vw`/`vh` units — they look right on the build machine and break on every other screen.

```js
const DESIGN_W = 1920, DESIGN_H = 1080;
function fit() {
  const s = Math.min(innerWidth / DESIGN_W, innerHeight / DESIGN_H);
  canvas.style.transform = `scale(${s})`;
}
new ResizeObserver(fit).observe(document.body);
window.addEventListener('resize', fit); // catches DPI changes ResizeObserver misses
```

- All inner content in `px`/`rem`. The transform does all responsive math.
- The wrapper background must equal the slide background so letterbox bars blend invisibly.
- `transform-origin: center center` keeps the letterbox symmetric.

## 2. Grid arithmetic (the orphan-card rule)

For any dashboard grid: **the sum of every child's `col-span × row-span` must equal `grid-cols × grid-rows` exactly.** If it doesn't, CSS auto-placement orphans a card into its own row, usually flush against the screen edge, and the screen instantly reads as broken.

Procedure:
1. Pick `grid-rows-N` where N = the tallest child's row-span.
2. Sum all cells used.
3. If the sum ≠ cols × rows, adjust spans until it does.

## 3. Per-slide color identity (the soul rule)

Every slide owns ONE dominant accent color, and the accent rotates through the deck. No two consecutive slides share a dominant accent; no accent appears more than about twice across eight slides.

- The problem slide gets the aggressive color (red family). Pain feels red.
- Within a mostly-monochrome screen, break one card into a contrasting accent. The chromatic break is what makes a screen feel composed instead of generated.
- If the deck is in the client's brand, pull their palette but still enforce rotation.

## 4. Lived-in data (the realism rule)

Sterile data breaks the spell instantly. Fake data must feel like a business that was alive yesterday:

- Round-ish but imperfect totals: `86,400` not `100,000`; `146 days` not `150`.
- Mixed deltas in any leaderboard or list: `+3, -2, 0, +1` — never all positive.
- Sparklines that go down sometimes.
- KPI bars at 72%, 91%, 68% — never a row of 100%s.
- One or two alerts that imply real operations: `9 DAYS QUIET`, `7 ITEMS · 2H AVG`.
- **Every person, company, and handle is fictional.** Letter-coded staff (`Setter A`), topic-led handles (`@signal.daily`), initials for message senders (`J. M.`). Grep your deck for every real name in your CRM before it ships. Zero matches or it doesn't ship.

## 5. Animation reliability

Entrance animations must be explicit per element (`initial` + `animate` + its own `delay`), never parent-staggered variants. Parent-stagger silently fails under reduced-motion settings, backgrounded tabs, and some mobile browsers — and a deck that opens on a blank screen in the room is a disaster you don't get a second take on. Every element must reach its final visible state even if animation never fires.

## 6. The audit loop (before it ships)

Screenshot every slide at its own URL/hash, then check the images, not the code:

1. Each slide's index label matches its actual position.
2. Color rotation holds — no two consecutive screenshots share a dominant accent.
3. No card sits flush against the viewport edge.
4. No real person, price, or internal tool name is visible anywhere.
5. Composition holds at three sizes: 1920×1080, 1366×768, 768×432 — identical layout, just scaled.

A deck that hasn't been screenshot-audited per slide is not done, no matter how it looks in the editor.

## Anti-patterns

- ❌ `100vh` slides without the auto-fit canvas
- ❌ Parent-staggered entrance animations
- ❌ Grid spans that don't sum to the grid size
- ❌ The same accent on two consecutive slides
- ❌ Minimalism that strips all color — it reads as soulless, not premium
- ❌ Real names or handles in mockup data
- ❌ A pricing slide (pricing is a conversation)
- ❌ Shipping without the per-slide screenshot audit
