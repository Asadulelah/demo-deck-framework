# The Demo Deck Framework

**Stop explaining your product. Show it.**

This is the complete framework we use to build sales decks that look and feel like a live product demo instead of a slideshow. It came out of a real client deck that got rejected five times in a row. Every version failed for the same reason: it *explained* the offer. The version that finally closed didn't explain anything. It put the product on the screen.

> The deck is not a document about the product. **The deck IS the product, walked page by page.**

## The core idea

When you sell software or systems, prospects don't buy explanations. They buy the thing they can already see themselves using.

So instead of 20 slides of concepts, metaphors, and feature lists, you build:

- **One consistent application shell across the whole deck.** A real SaaS frame: left sidebar with the product's navigation (one item per module), a top bar (page title, search, user), and a main content area. The shell is identical on every slide; only the active page changes. This is what makes it feel like ONE real product instead of a pile of mockups.
- **A screen for each module.** Every area the system covers gets its own slide showing that page filled with realistic data: tables, KPI cards, charts, status pills, a chat panel, a phone view for customer-facing parts.
- **One line of caption per slide.** A module tag plus a one-line benefit. The screen does the talking. You narrate the rest live. Never paragraphs.
- **Show HOW and HOW EASY, not just what.** The screen shows the mechanism working inside the app. Where useful, a "You / The system" split makes the tiny human action vs the system's work obvious.

## The shape

```
Cover
→ The cost of the problem (ONE slide, tight, not a lecture)
→ "Everything in one place" reveal (hub view of all modules)
→ One app-screen slide per module (dashboard first as the hero)
→ The AI / assistant page
→ Security (light, human language)
→ Migration
→ Close
```

Slide count = whatever the modules need. No filler. Every slide has exactly one intention.

**Slides that are banned:** timeline, before/after, generic CTA, pricing (pricing is a conversation, not a slide), and any slide that is a paragraph wearing a background.

## Quick start

Open [`demo/index.html`](demo/index.html) in a browser. That's the whole skeleton: an app-shell deck for a fictional logistics company, keyboard navigable (← → or 1-9), one screen per module, captions included. It's a single self-contained file. Fork it, swap the sidebar modules and screens for your product, recolor to your brand, done.

## The craft rules

The difference between "obviously a mockup" and "wait, is this live?" is craft. The two docs in [`docs/`](docs/) carry everything we learned the expensive way:

- [**SLIDE-GRAMMAR.md**](docs/SLIDE-GRAMMAR.md) — the per-slide playbook: what each slide type must contain, the caption formula, and the walkthrough order that sells.
- [**CRAFT-RULES.md**](docs/CRAFT-RULES.md) — the engineering: resolution-perfect canvas scaling, grid arithmetic that never orphans a card, per-slide color identity, animation reliability, and how to make fake data feel lived-in.

The three rules people break first:

1. **Anonymous data only.** Every name, handle, and number in the mockup is fictional. Real names from your CRM in a demo deck is how trust dies in one glance.
2. **Lived-in numbers.** `₹86,400` reads real. `₹100,000` reads fake. Mixed deltas, imperfect percentages, one alert that implies real operations.
3. **One accent color per slide, rotating.** A deck where every slide is the same dark-grid-plus-mint reads as AI slop. Color rhythm is what makes it read as designed.

## Why give this away

Because the deck format is not the moat. Knowing what to build for a specific business, building it fast, and making a team actually adopt it is the moat. The framework is free. Use it, close with it, tell me how it went.

## License

MIT. Do whatever you want with it.

---

Built by [Asadulelah](https://www.linkedin.com/in/asadulelah/) — I build AI systems and the operating layer under businesses, and I document the whole climb.
