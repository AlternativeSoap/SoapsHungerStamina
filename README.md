# SoapsHungerStamina

Stamina and hunger, actually connected. MMOCore handles the bar; this plugin decides what costs stamina in survival.

Sprint, jump, swim, fight, mine, glide, climb, paddle, throw stuff. Run out of stamina and your food bar pays the bill. Keep going at zero and overexertion starts hurting you. Pack too much and movement gets rough. Cold and hot biomes, altitude, weight, beds, dodges, second wind, the works.

## What it does

- Lots of actions drain or restore stamina (sprint, jump, swim, attack, shield, elytra, climbing, mace, bows, tridents, throwables, boats, crawling, riptide, tools, and more)
- Per-weapon costs and exclusion lists for attacks and block place/break
- Shields drop when stamina is too low; blocking costs more on big hits
- Stamina food, second wind, dodge, sprint burst, bed rest buffs
- Biomes, altitude, soul sand, honey, powder snow, water/lava contact
- Hunger overflow or replace the food bar with a stamina bar
- Overexertion damage, winded on hit, exhaustion effects (slowness, sweat, stumble, etc.)
- Weight: armor load, encumbrance, drowning/fall penalties, MMOItems overrides
- PlaceholderAPI scaling for max carry (`scaling-weight`) and stat vs load drain (`scaling-drain`)
- Admin GUI, biome editor, weight commands, per-world toggles
- 30+ bypass permissions, player-chosen UI, session stats, 19 PAPI placeholders

## Docs

- [Getting Started](Getting-Started.md)
- [Introduction](Introduction.md)
- [Configuration](Configuration.md)
- [Commands & Permissions](Commands-and-Permissions.md)
- [Default Config Files](Default-Config-Files.md)
- [Placeholders](Placeholders.md)
- [Examples](Examples.md)

## You need

- Paper 1.21.x
- MMOCore + MythicLib
- PlaceholderAPI (optional, for `%shs_*%`)
- MMOItems (optional, custom weights + no double attack drain)

| | | |
|---|---|---|
| Paper | 1.21.x | Main target |
| MMOCore | Required | Stamina backend |
| MythicLib | Required | Comes with MMOCore |
| PlaceholderAPI | Optional | Placeholders |
| MMOItems | Optional | Custom item weights |

## Quick start

1. Install Paper, MMOCore, MythicLib, drop in this plugin.
2. Start once so `config.yml` and `actions.yml` generate.
3. `/shs gui`: turn on sprint-lock, pick hunger mode (`overflow` or `bar`).
4. Sprint to zero on a test player. Food should drop; sprint should lock if you enabled it.
5. Tweak from a preset in [Examples.md](Examples.md) if you want a baseline.

## Performance tips

- Light server: `engine.tick-interval: 4`, leave heavy effects off.
- Busy server: trim particles/effects, tune biomes, disable stamina in lobby worlds via `disabled-worlds`.
- Really busy: bump tick interval, simplify actions, use per-world disables.

## Version

1.0.7 by AlternativeSoap
