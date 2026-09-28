# Office Ideas & Feedback

## API Key UX Issue
It's not obvious to users that a development key is necessary (people often have
regular subscriptions without API usage).

Therefore we need to:
- Make Deskburg credit the main/primary option in the UI.
- Make API keys a secondary option.
- Add explanatory copy clarifying that these are **development keys**, not the
  usual consumer AI/LLM subscription most people are used to (e.g. not the same
  as a ChatGPT Plus / regular AI app login).

## Office Spice-Up
- **Toilets**: Add toilets to the office. Idle agents should occasionally "visit"
  them as a small ambient/flavor animation.
- **Janitor**: Add a janitor NPC. No gameplay function — just wanders around
  the office cleaning, for ambience/life.

## Achievements & Gamification

### Concept
Unlocking achievements grants points. Points are spent in the office builder to
visually upgrade items (furniture/decor) through tiers. Example: a sofa has
tiers 1/2/3; everyone starts at tier 1 and can upgrade to tier 2/3 by spending
points earned from achievements. Each upgradeable item needs 3 distinct visual
looks (tier 1/2/3 art assets).

### Suggested achievement ideas
- Onboarding: complete first task, invite a colleague, customize your desk.
- Productivity: complete N tasks, complete tasks X days in a row (streak),
  finish a task before a deadline.
- Collaboration: hand off a task to a colleague, get a task handed to you and
  complete it, work with every colleague at least once.
- Exploration: visit every room/area in the office, use every menu item once.
- Mastery: use each colleague/agent type once, publish to the pinboard N times,
  create N files.
- Fun/hidden: find the janitor, use the toilet easter egg, be idle for a long
  time (rewards low-effort days too, keeps it light-hearted).

### Suggested implementation approach
1. **Achievement definitions**: central config (id, name, description, trigger
   condition, point reward, icon). Keep data-driven so new achievements can be
   added without code changes to the engine.
2. **Event tracking**: emit lightweight events from existing actions (task
   completed, handoff made, file created, pin posted, login streak) into an
   achievement-tracking service that checks conditions and unlocks/rewards.
3. **Points/currency store**: per-user point balance, ledger of
   earned/spent points for auditability.
4. **Builder integration**: each upgradable office item has tiers with an
   associated point cost and a set of visual assets (tier 1/2/3). Builder UI
   shows current tier, next tier cost, and a preview before confirming upgrade.
5. **Notifications**: toast/banner when an achievement unlocks, showing points
   earned and a link to the builder.
6. **Extensibility**: design tiers generically (any item can have N tiers, not
   hardcoded to 3) so we can expand later.

### More gamification ideas
- Daily/weekly login streaks with small point bonuses.
- Leaderboard (optional, opt-in) for teams that like competition.
- Seasonal/limited-time cosmetic items tied to real-world events.
- "Office level" that unlocks new rooms/areas as the whole team collectively
  earns points.
- Random flavor events (janitor waves, colleague brings coffee) with no
  mechanical effect, just charm.

## First-Time Walkthrough / Setup
- On first launch, show a **get started guide** that highlights different
  parts of the UI (menu items, builder, pinboard, colleagues, etc.) with short
  explanations and examples of what each does.
- Make the walkthrough **skippable** at any step for users who want to jump
  straight into using Deskburg.
