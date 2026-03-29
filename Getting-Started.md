# Getting Started

## Installation

1. **Make sure you have MMOCore running**  
   The plugin won't load without MMOCore installed and active.

2. **Drop the jar into your plugins folder**  
   Copy `SoapsHungerStamina-1.0.1.jar` into your server's `plugins/` directory.

3. **Start your server**  
   Restart the server or load the plugin via your plugin manager.

4. **Check the console**  
   Look for: `SoapsHungerStamina enabled — hooked into MMOCore stamina.`  
   If you see errors about MMOCore, stop the server and confirm MMOCore is loaded first.

5. **Config files are auto-generated**  
   The plugin creates three files on first run:
   - `config.yml` — all the settings
   - `messages.yml` — all the text players see
   - `weight.yml` — item weights for the encumbrance system

## Quick Test

1. Join the server in Survival mode
2. Hold `W + Ctrl` to sprint
3. Watch your stamina display — it should drop
4. Stop sprinting — your stamina regens (handled by MMOCore)
5. Keep sprinting after stamina hits zero — your food bar should drop

## Adjusting Settings

**Option A — Edit the config file:**  
Edit `plugins/SoapsHungerStamina/config.yml`, save, then run `/shs reload`.

**Option B — Use the in-game GUI:**  
Run `/shs gui` to open a clickable settings panel. Toggle features on/off, adjust values, all without leaving the game.

## Default Behavior

- **Sprint:** 2.5 stamina per second
- **Jump:** 4 stamina per jump
- **Swim:** 2 stamina per second
- **Attack:** 2.5 stamina per hit
- **Block place:** 0.3 stamina per block
- **Block break:** 0.8 stamina per block
- **Shield block:** 1.5 upfront + 0.5 per second
- **Sneak:** +1.5 stamina regen per second
- **Hunger overflow:** 1 hunger point per second when stamina is empty
- **Exhaustion effects:** Off by default (enable in config)
- **Biome effects:** Off by default (enable in config)
- **Weight/encumbrance:** Uses weight.yml thresholds
- **Display:** Boss Bar showing stamina
- **GUI:** Enabled, accessible with `/shs gui`

Everything works out of the box. Tune it later if needed.
