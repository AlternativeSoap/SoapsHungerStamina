# Getting Started

## Install

1. **MMOCore must be running.** MythicLib too (MMOCore depends on it). Without MMOCore the plugin won't load.

2. **Put the jar in `plugins/`.**  
   `SoapsHungerStamina-1.0.7.jar`

3. **PlaceholderAPI** (optional) if you want `%shs_*%` on scoreboards or tab.

4. **MMOItems** (optional) for custom item weights and skipping duplicate attack drain.

5. **Start the server.**

6. **Console should say:**  
   `SoapsHungerStamina enabled — hooked into MMOCore stamina.`  
   If it complains about MMOCore, fix that first.

7. **First run creates four files:**
   - `config.yml` – general stuff, biomes, UI, overexertion, etc.
   - `actions.yml` – what each action costs or regens
   - `messages.yml` – player-facing text
   - `weight.yml` – armor, encumbrance, item weights, scaling

## Quick test

1. Join in Survival.
2. Sprint (`W` + `Ctrl`).
3. Stamina should drop on your display.
4. Stop sprinting; MMOCore regen takes over.
5. Sprint at zero stamina; food bar should start going down (if overflow is on).

## Changing settings

Edit the yml files and `/shs reload`, or open `/shs gui` and click stuff. `/shs toggle` and `/shs config set` work from chat too.

## Defaults (short version)

**actions.yml highlights:** sprint 0.8/s, jump 1.0, swim 0.7/s, attack 0.8, shield 0.2 + 0.1/s + 0.5 per blocked hit, sneak regen +1.2/s, idle +0.6/s. Elytra, climbing, boat, riptide, tools, winded, mace, etc. are all in the file with sane defaults.

**config.yml highlights:** projectiles on, overexertion on, hunger overflow on, biomes/altitude/dodge/sprint-burst off by default, bed rest on, boss bar stamina display, GUI on.

**weight.yml highlights:** armor weight on, encumbrance at 300/500, drowning and fall damage on, 1000+ item weights, scaling-drain off unless you turn it on.

You can run it as-is and tune later.

## RPG servers: strength vs backpack weight

If you have MMOCore stats + PlaceholderAPI:

1. `weight.yml` → `scaling-drain.enabled: true`
2. Point `placeholder` at your stat (default is strength).
3. `/shs reload`

High strength = a full inventory hurts stamina less. Low strength + heavy loot = everything costs more. You still get encumbrance slowness and sprint block; this only changes how stamina scales with weight.

Use `scaling-weight` too if you want level (or another placeholder) to raise max carry.
