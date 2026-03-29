# Gameplay Guide

How SoapsHungerStamina changes survival gameplay.

---

## Stamina Is Your Budget

Think of stamina as fuel. Every action costs fuel.

Sprinting costs stamina while you hold the sprint button and move. Stop sprinting, cost stops.

Jumping costs stamina per jump. Spam-jumping is limited by the cooldown.

Swimming costs stamina while you're in water.

Attacking costs stamina per melee hit. Swing more, drain more.

Placing blocks costs a small amount per block placed.

Breaking blocks costs a small amount per block broken.

Raising a shield costs stamina up front, then keeps draining while the shield is up.

Sneaking is the exception - it gives you bonus stamina regen. Crouch to catch your breath.

---

## Hunger Is The Penalty

Run out of stamina? Hunger kicks in.

Keep doing stuff with no stamina and your food bar drops instead.

It drains saturation first (the golden sparkles), then actual hunger.

Hunger has a floor that the admin can configure. It can drain all the way to empty, or stop at a safe minimum.

---

## Weight Matters

Your inventory has weight.

Armor is heavy. Heavier armor materials (iron, diamond, netherite) make stamina drain faster through a multiplier.

Items stack up too, everything in your inventory contributes to your total weight.

Cross the encumbered threshold and stamina drain gets worse. You'll get a warning message.

Cross the severe threshold and bad things happen:
- You lose air faster underwater (can drown much quicker)
- Fall damage is multiplied (heavier hits)

Drop items or switch to lighter armor to get back under the limit.

---

## Biomes Change The Game

If biomes are enabled by the admin:

Cold biomes (snowy plains, frozen ocean, taiga, etc.) start freezing your character. Stamina drains faster. You'll see a message when you enter one.

Hot biomes (desert, jungle, savanna, nether, etc.) make your character sweat. Stamina drains faster. Message on entry.

Neutral biomes have no effect. You'll see a "comfortable" message when leaving an extreme biome.

It stacks with weight too. If you're encumbered and in an extreme biome, the drain gets even worse.

---

## What Changes Your Gameflow

### Travel

Running across the map costs stamina. You can't sprint forever. You need to:
- Rest and let stamina regen (sneaking helps)
- Eat if stamina drains to hunger
- Plan routes to avoid exhaustion
- Watch your weight, traveling heavy is harder

### Combat

Stamina is a combat resource now. Sprinting costs stamina, every swing costs stamina, jumping costs stamina, blocking with a shield costs stamina. Running out in a fight means exhaustion effects and hunger drain.

You have to manage when you attack, when you block, when you disengage.

### Building

Placing and breaking blocks costs a small amount. Big builds add up. Take breaks.

### Exploration

Cold biomes are harder to explore on foot and hot biomes are draining. Carrying a full inventory of loot makes everything harder, and having the right armor matters - lighter gear for long trips.

---

## Exhaustion Effects

When stamina is completely empty, your character shows it physically. These are optional (off by default) but add a lot of immersion when enabled.

Slowness makes you walk slower. Can't run at full speed on empty.

Sweat particles (water drips) come from your character. Other players can see you struggling.

Heavy breathing darkens your screen edges briefly. Short pulses, not blinding.

Stumble gives you small random knockback nudges. Brief loss of control.

All effects clear once your stamina recovers past a threshold. You'll get messages when effects kick in and when they clear.

---

## Game Modes

This plugin only affects Survival and Adventure modes.

Creative and Spectator don't drain stamina or hunger.

---

## Respawning

When you die and respawn, your stamina tracking resets. You start fresh.

Stamina regen is handled by MMOCore, so check your class's stamina regen rate.

---

## Tips

1. Don't run out of stamina in dangerous places. Hunger drains fast without it.
2. Always carry food. It's your backup when stamina fails.
3. Sneak to recover faster, crouching gives bonus stamina regen.
4. Watch your weight. Drop what you don't need before a long trip.
5. Use lighter armor for travel, switch to heavy gear for combat.
6. Plan your sprints. Short bursts + walking is more efficient than one long sprint.
7. Don't hold a shield up constantly, it drains stamina the whole time.
