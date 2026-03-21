# Gameplay Guide

How SoapsHungerStamina changes survival gameplay.

---

## Stamina Is Your Movement Budget

Think of stamina as fuel. Every action costs fuel.

**Sprinting** costs stamina while you hold the sprint button and move. Stop sprinting, stamina stops draining (but doesn't regen instantly — MMOCore handles regen).

**Jumping** costs stamina per jump. Spam-jumping is limited by the cooldown.

**Swimming** costs stamina while you're in water. Exit water, cost stops.

---

## Hunger Is The Penalty

Stamina runs out? Hunger kicks in.

**Keep sprinting with no stamina?** Your hunger bar drops instead.

**It drains saturation first** (the golden sparkles), then actual hunger.

**Hunger has a floor** (default: 0, meaning it can fully drain). Your server admin can change this so players never starve completely.

---

## What Changes Your Gameflow

### Travel

Running across the map now costs stamina. You can't just run forever. You need to:
- Rest and let stamina regen
- Eat if stamina drains to hunger
- Plan routes to avoid exhaustion

### Combat

Stamina is a combat resource. You can't:
- Sprint endlessly while chasing
- Spam-jump while fighting

You have to manage when you sprint, when you jump, when you rest.

### Food Matters Again

Food isn't just about health. It's about recovering from drained hunger.

Food = stamina tank refiller (kind of).

---

## Action Bar Hints

Watch the action bar at the top of your screen. It shows your stamina in real time.

**Colors change:**
- Green/Blue = plenty of stamina
- Yellow/Orange = getting low
- Red = running out (warning kicks in)

When stamina hits zero, that's when hunger starts draining.

---

## Game Modes

This plugin only affects **Survival** and **Adventure** modes.

**Creative** and **Spectator** don't drain stamina or hunger. Build events? Staff testing? No drain.

---

## Respawning

When you die and respawn, your stamina tracking resets. You start fresh.

Stamina regen is handled by MMOCore, so check your class's stamina regen rate.

---

## Tips for Survival

1. **Don't run out of stamina in dangerous places** — Hunger drains fast without stamina.
2. **Always have food** — It's your backup resource when stamina fails.
3. **Plan sprinting** — Long distances cost a lot. Shorter sprints + walking in between works better.
4. **Jumping is a situational tool** — Use it when you need it, not constantly.
5. **Let stamina regen** — Stop sprinting, let your bar fill back up before the next rush.
