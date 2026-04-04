# Getting Started

## Installation

1. **Make sure you have MMOCore running.**
   The plugin won't load without it. MythicLib is also required (it's a dependency of MMOCore).

2. **Drop the jar into your plugins folder.**
   Copy `SoapsHungerStamina-1.0.4.jar` into `plugins/`.

3. **Optional: Install PlaceholderAPI** for `%shs_*%` placeholders on scoreboards, tab lists, etc.

4. **Optional: Install MMOItems** for custom item weights and automatic duplicate drain prevention on weapon attacks.

5. **Start your server.**
   Restart or load the plugin via your plugin manager.

6. **Check the console.**
   You should see: `SoapsHungerStamina enabled — hooked into MMOCore stamina.`
   If you get errors about MMOCore, stop and make sure MMOCore is loaded first.

7. **Config files are auto-generated.**
   Four files are created on first run:
   - `config.yml` — general settings, engine, projectiles, overexertion, hunger, effects, biomes, altitude, UI, GUI
   - `actions.yml` — all action drain/regen values (sprint, jump, swim, attack, elytra, climbing, etc.)
   - `messages.yml` — all player-facing text (MiniMessage formatted)
   - `weight.yml` — armor weights, encumbrance, scaling, drowning/fall damage, MMOItems weights, item weights

## Quick Test

1. Join the server in Survival mode
2. Hold `W + Ctrl` to sprint
3. Watch your stamina display — it should drop
4. Stop sprinting and your stamina regens (handled by MMOCore)
5. Keep sprinting after stamina hits zero and your food bar should drop

## Adjusting Settings

You can either edit the config files and run `/shs reload`, or use the in-game GUI with `/shs gui` to change things without leaving the game. Commands like `/shs toggle` and `/shs config set` also work from chat.

## Default Behavior

**Actions** (configured in `actions.yml`):
- Sprint: 1.0 stamina per second
- Jump: 1.5 stamina per jump (300ms cooldown)
- Swim: 1.0 stamina per second
- Water contact: 0.5 stamina per second
- Lava contact: 1.5 stamina per second
- Attack: 1.0 stamina per hit
- Block place: 0.15 stamina per block
- Block break: 0.3 stamina per block
- Shield block: 0.6 upfront + 0.3 per second
- Sneak regen: +0.8 stamina per second (after 2s cooldown)
- Idle regen: +0.4 stamina per second (after 2s cooldown)
- Winded (hit): 0.5 instant + 0.6/s for 3.5s | Critical: 1.5 instant + 1.2/s for 5s + 3s regen lock
- Elytra: 0.8 stamina per second
- Climbing: 0.6 stamina per second
- Eating: +3.0 stamina restored per food item
- Mace smash: 2.5 extra stamina (on top of attack cost)
- Boat: 0.3 stamina per second
- Crawling: 0.5 stamina per second
- Riptide: 2.5 stamina per launch
- Tool use: hoe 0.2, shears 0.15, brush 0.1
- Powder snow: 0.7 stamina per second
- Slime bounce: 0.5 per bounce
- Soul sand: 1.20x drain multiplier
- Honey block: 1.15x drain multiplier
- Potion modifiers: disabled by default (Speed 1.15x, Haste 1.10x)
- Damage intake: 0.5 stamina per heart of damage

**Systems** (configured in `config.yml`):
- Projectiles: enabled (bow 1.5, crossbow 1.8, trident 2.0, 10 throwable types)
- Overexertion: enabled (threshold 15.0, warns at 75%, damage starts at 1.0/tick)
- Hunger overflow: enabled at 0.5 food points per second
- Exhaustion effects: disabled by default
- Biomes: disabled by default (36 pre-configured biomes)
- Altitude: disabled by default
- Display: Boss Bar showing stamina
- GUI: enabled, accessible with `/shs gui`

**Weight** (configured in `weight.yml`):
- Armor weight: enabled (leather 5.5% to netherite 37%)
- Encumbrance: enabled at 300/500 thresholds
- Drowning/fall damage: enabled
- 1000+ item weights preconfigured
- MMOItems weights: disabled by default

Everything works out of the box. Tune it later if needed.
