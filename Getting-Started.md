# Getting Started

## Installation

1. **Make sure you have MMOCore running.**
   The plugin won't load without it. MythicLib is also required (it's a dependency of MMOCore).

2. **Drop the jar into your plugins folder.**
   Copy `SoapsHungerStamina-1.0.6.jar` into `plugins/`.

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
- Sprint: 0.8 stamina per second
- Jump: 1.0 stamina per jump
- Swim: 0.7 stamina per second
- Water contact: 0.3 stamina per second
- Lava contact: 1.0 stamina per second
- Attack: 0.8 stamina per hit (with optional per-weapon-type costs and exclusion list)
- Block place: 0.15 stamina per block (with exclusion list)
- Block break: 0.2 stamina per block (with exclusion list)
- Shield block: 0.2 upfront + 0.1 per second + 0.5 per hit absorbed (shield forced down at 1.0 stamina)
- Sneak regen: +1.2 stamina per second (after 1.5s cooldown)
- Idle regen: +0.6 stamina per second (after 1.5s cooldown)
- Winded (hit): 0.3 instant + 0.4/s for 3s | Critical: 1.0 instant + 0.8/s for 4s + 2.5s regen lock
- Elytra: 0.5 stamina per second
- Climbing: 0.4 stamina per second
- Mace smash: 2.0 extra stamina (on top of attack cost)
- Boat: 0.1 stamina per second
- Crawling: 0.35 stamina per second
- Riptide: 2.0 stamina per launch
- Tool use: hoe 0.2, shears 0.15, brush 0.1, flint & steel 0.15
- Powder snow: 0.5 stamina per second
- Slime bounce: 0.5 per bounce
- Soul sand: 1.20x drain multiplier
- Honey block: 1.15x drain multiplier
- Potion modifiers: disabled by default (Speed 1.15x, Haste 1.10x)
- Damage intake: 0.3 stamina per heart of damage

**Systems** (configured in `config.yml`):
- Projectiles: enabled (bow 1.5, crossbow 1.8, trident 2.0, 10 throwable types)
- Overexertion: enabled (threshold 25.0, warns at 75%, damage starts at 0.5/tick)
- Second Wind: disabled by default (5s idle at zero → 30% stamina recovery, 90s cooldown)
- Hunger overflow: enabled at 0.5 food points per second
- Exhaustion effects: disabled by default (with recovery animation)
- Sounds: disabled by default (5 configurable event sounds)
- Biomes: disabled by default (38 pre-configured biomes with exposure system)
- Altitude: disabled by default
- Stamina Food: enabled (13 foods configured — golden apple, golden carrot, meats, stews)
- Dodge: disabled by default (sneak while sprinting, 4.0 cost, 1.5s cooldown)
- Sprint Burst: disabled by default (speed boost on sprint start, 6.0 cost, 30s cooldown)
- Bed Rest: enabled (sleeping restores full stamina + Well Rested buff for 120s)
- Per-world settings: disabled-worlds list and optional per-world drain multipliers
- Player display choice: disabled by default (let players pick actionbar/bossbar/off)
- Display: Boss Bar showing stamina
- GUI: enabled, accessible with `/shs gui`

**Weight** (configured in `weight.yml`):
- Armor weight: enabled (leather 5.5% to netherite 37%)
- Encumbrance: enabled at 300/500 thresholds
- Drowning/fall damage: enabled
- 1000+ item weights preconfigured
- MMOItems weights: disabled by default

Everything works out of the box. Tune it later if needed.
