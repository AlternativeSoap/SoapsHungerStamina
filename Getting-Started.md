# Getting Started

## Installation

1. **Make sure you have MMOCore running.**
   The plugin won't load without it.

2. **Drop the jar into your plugins folder.**
   Copy `SoapsHungerStamina-1.0.1.jar` into `plugins/`.

3. **Start your server.**
   Restart or load the plugin via your plugin manager.

4. **Check the console.**
   You should see: `SoapsHungerStamina enabled - hooked into MMOCore stamina.`
   If you get errors about MMOCore, stop and make sure MMOCore is loaded first.

5. **Config files are auto-generated.**
   Three files are created on first run:
   - `config.yml` - all the settings
   - `messages.yml` - all the text players see
   - `weight.yml` - item weights for encumbrance

## Quick Test

1. Join the server in Survival mode
2. Hold `W + Ctrl` to sprint
3. Watch your stamina display, it should drop
4. Stop sprinting and your stamina regens (handled by MMOCore)
5. Keep sprinting after stamina hits zero and your food bar should drop

## Adjusting Settings

You can either edit `plugins/SoapsHungerStamina/config.yml` and run `/shs reload`, or use the in-game GUI with `/shs gui` to change things without leaving the game.

## Default Behavior

- Sprint: 1.2 stamina per second
- Jump: 2.0 stamina per jump
- Swim: 1.0 stamina per second
- Attack: 1.2 stamina per hit
- Block place: 0.15 stamina per block
- Block break: 0.4 stamina per block
- Shield block: 0.8 upfront + 0.3 per second
- Sneak: +0.8 stamina regen per second
- Hunger overflow: 0.5 hunger points per second when stamina is empty
- Exhaustion effects: off by default (enable in config)
- Biome effects: off by default (enable in config)
- Weight/encumbrance: uses weight.yml thresholds
- Display: Boss Bar showing stamina
- GUI: enabled, accessible with `/shs gui`

Everything works out of the box. Tune it later if needed.
