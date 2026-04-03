# Getting Started

## Installation

1. **Make sure you have MMOCore running.**
   The plugin won't load without it.

2. **Drop the jar into your plugins folder.**
   Copy `SoapsHungerStamina-1.0.3.jar` into `plugins/`.

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
3. Watch your stamina display - it should drop
4. Stop sprinting and your stamina regens (handled by MMOCore)
5. Keep sprinting after stamina hits zero and your food bar should drop
6. If overexertion is enabled, keep pushing and you'll start taking damage

## Adjusting Settings

You can either edit `plugins/SoapsHungerStamina/config.yml` and run `/shs reload`, or use the in-game GUI with `/shs gui` to change things without leaving the game.

## Default Behavior

The plugin works out of the box with balanced defaults. Sprinting, jumping, swimming, combat, mining, and building all cost stamina. Getting hit winds you. Running on empty drains your food bar and eventually hurts you through overexertion.

For exact default values, see [Default Config Files](Default-Config-Files.md).
