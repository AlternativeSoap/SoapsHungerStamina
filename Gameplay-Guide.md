# Gameplay Guide

How SoapsHungerStamina changes survival gameplay.

---

## Stamina Is Your Budget

Think of stamina as fuel. Every physical action costs fuel.

Sprinting costs stamina while you hold the sprint button and move. Stop sprinting, cost stops.

Jumping costs stamina per jump. Spam-jumping is limited by the cooldown.

Swimming costs stamina while you're actively swimming, and even wading through water has a smaller drain. Touching lava drains stamina fast.

Attacking costs stamina per melee hit. Swing more, drain more.

Placing blocks costs a small amount per block placed.

Breaking blocks costs a small amount per block broken.

Raising a shield costs stamina up front, then keeps draining while the shield is up.

Sneaking is the opposite - it gives you bonus stamina regen. Crouch to catch your breath.

Standing still also gives a small passive regen boost on top of MMOCore's natural recovery.

There's a short cooldown after any draining action before sneak and idle regen kick in, so you can't sprint-crouch-sprint to game the system.

---

## Getting Hit Hurts More Than You Think

The winded system makes taking damage a stamina problem.

A normal hit costs stamina immediately and applies a drain-over-time for several seconds. Keep moving and the drain stacks on top of your actions.

A critical hit is worse - bigger instant cost, longer drain-over-time, and a regen lock that completely blocks all stamina recovery for seconds. Getting crit while low on stamina can send you spiraling.

Each hit can refresh the timer, so sustained combat pressure keeps the drain going.

---

## Hunger Is The Safety Net

Run out of stamina? Hunger kicks in.

Keep doing stuff with no stamina and your food bar drops instead. Saturation burns first (the golden sparkles), then actual hunger.

Hunger has a floor that the admin can configure. By default it stops at 6 (3 shanks), so you won't fully starve from stamina drain alone.

---

## Overexertion - Know When To Stop

If you keep pushing with zero stamina, overexertion starts building up.

There's a grace period - small actions won't immediately hurt you. But once you pass the threshold, you start taking real damage that gets worse the longer you push. The damage scales up over time and caps at a maximum per tick.

Stop draining and overexertion recovers on its own. You'll get warning messages before the damage starts, giving you a chance to back off.

This is the plugin's hard limit. Stamina depletion flows into hunger, and hunger depletion flows into overexertion damage. Respect the loop.

---

## Weight Matters

Your inventory has weight.

Armor is heavy. Heavier armor materials (iron, diamond, netherite) make stamina drain faster through a multiplier.

Items stack up too - everything in your inventory contributes to your total weight. Shulker boxes and bundles are weighed with their contents included.

Cross the encumbered threshold and stamina drain gets worse. You get slowness and a warning message.

Cross the severe threshold and it gets bad:
- Sprint is blocked entirely
- You lose air faster underwater (can drown much quicker)
- Fall damage is multiplied (heavier gear, harder hits)
- Extra slowness when you're in water

Drop items or switch to lighter armor to get back under the limit. Check your weight with `/weight` any time.

If PlaceholderAPI is installed, the server can scale your max carry weight based on other stats - like gaining more capacity as you level up.

---

## Biomes Change The Game

If biomes are enabled by the admin:

Cold biomes (snowy plains, frozen ocean, taiga, etc.) start freezing your character. Stamina drains faster, and there's a passive drain just for standing in one. You'll see a message when you enter.

Hot biomes (desert, jungle, savanna, nether, etc.) make your character sweat. Stamina drains faster, passive drain ticks away. Message on entry.

Neutral biomes have no effect. You'll see a "comfortable" message when leaving an extreme biome.

It stacks with weight too. If you're encumbered and in an extreme biome, the drain gets even worse.

---

## What Changes Your Gameflow

### Travel

Running across the map costs stamina. You can't sprint forever. You need to:
- Rest and let stamina regen (sneaking and standing still both help)
- Eat if stamina drains to hunger
- Plan routes to avoid exhaustion
- Watch your weight - traveling heavy is harder

### Combat

Stamina is a combat resource now. Sprinting costs stamina, every swing costs stamina, jumping costs stamina, blocking with a shield costs stamina. Getting hit winds you and drains even more. A critical hit can lock your regen for seconds.

Running out in a fight means exhaustion effects, hunger drain, and eventually overexertion damage if you don't disengage.

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

Creative and Spectator don't drain stamina or hunger. Players in creative flight are also skipped.

---

## Respawning

When you die and respawn, your stamina tracking resets. Winded effects and overexertion clear. You start fresh.

Stamina regen is handled by MMOCore, so check your class's stamina regen rate.

---

## Tips

1. Don't run out of stamina in dangerous places. Hunger drains fast and overexertion damage is real.
2. Always carry food. It's your backup when stamina fails.
3. Sneak to recover faster - crouching gives bonus stamina regen.
4. Standing still also helps. Even a brief pause lets idle regen tick.
5. Watch your weight. Drop what you don't need before a long trip.
6. Use lighter armor for travel, switch to heavy gear for combat.
7. Plan your sprints. Short bursts + walking is more efficient than one long sprint.
8. Don't hold a shield up constantly - it drains stamina the whole time.
9. Avoid getting crit in combat. The regen lock can turn a fight fast.
10. If you get the overexertion warning, stop immediately. The damage that follows scales up quickly.
