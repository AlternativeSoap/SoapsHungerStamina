# Getting Started

## Installation

1. **Make sure you have MMOCore running**  
   The plugin won't load without MMOCore installed and active.

2. **drop jar into plugins folder**  
   Copy `SoapsHungerStamina-1.0.0.jar` into your server's `plugins/` directory.

3. **Start your server**  
   Restart the server or load the plugin via your plugin manager.

4. **Check the console**  
   Look for: `SoapsHungerStamina enabled — hooked into MMOCore stamina.`  
   If you see errors about MMOCore, stop the server and confirm MMOCore is loaded first.

5. **Config is auto-generated**  
   The plugin creates `plugins/SoapsHungerStamina/config.yml` and `messages.yml` on first run.

## Quick Test

1. Join the server in Survival mode
2. Hold `W + Ctrl` to sprint
3. Watch your action bar — stamina should drop
4. Stop sprinting — your stamina should regen (handled by MMOCore)
5. Keep sprinting after stamina hits zero — your hunger bar should drop

## Adjusting Settings

Edit `plugins/SoapsHungerStamina/config.yml` and save.

Run `/shs reload` in-game to apply changes without restarting.

## Default Behavior

- **Sprint:** 5 stamina per second
- **Jump:** 8 stamina per jump
- **Swim:** 3 stamina per second
- **Hunger overflow:** 1 hunger point per second (when stamina is empty)
- **Display:** Action Bar showing Stamina/Max-Stamina

Everything works out of the box. Tune it later if needed.
