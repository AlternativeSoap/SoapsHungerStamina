# SoapsHungerStamina

**Make stamina and hunger work together in survival gameplay.**

SoapsHungerStamina ties MMOCore stamina into vanilla survival. Sprinting, jumping, swimming, fighting, mining, building, gliding, climbing, boating, throwing — it all costs stamina. Different weapons drain different amounts. Run out and your food bar starts draining instead. Push too hard and overexertion deals real damage. Carry too much weight and things get worse. Cold biomes drain you with exposure, hot biomes make you sweat. High altitude thins the air, deep caves feel stuffy. Second Wind gives you a last-resort burst when you hit zero. Eat the right foods for a stamina buff. Sleep in a bed to recover. Dodge out of danger or sprint burst past threats.

## What It Does

- 30+ actions and mechanics drain or restore stamina — sprinting, jumping, swimming, attacking, blocking, elytra gliding, climbing, mace smashes, projectiles (bow, crossbow, trident, throwables), boat paddling, crawling, riptide, tool use (including flint & steel), and more
- Weapon-type stamina costs — swords, axes, tridents, and fists each drain a different amount per hit
- Attack and block-place exclusion lists — exempt specific items or blocks from costing stamina
- Shield improvements — shields get forced down when stamina is too low, and blocking costs extra per hit based on incoming damage
- Stamina Food — 13 foods give a "Well Fed" buff that reduces all stamina drain for a set duration
- Second Wind — a last-resort recovery burst when stamina hits zero, with a configurable cooldown
- Dodge — sneak while sprinting to dash out of danger at the cost of stamina
- Sprint Burst — automatically gain a short speed boost when your stamina is near full
- Bed Rest — sleeping in a bed restores stamina and grants a "Well Rested" drain reduction buff
- Environmental systems: biome exposure (cold/hot with grace periods and protection), altitude, powder snow, soul sand, honey blocks, water/lava contact
- When stamina hits zero, the cost overflows into your food bar (or replace the food bar entirely with a stamina display)
- Overexertion system — keep pushing at zero stamina and you take escalating damage
- Winded mechanic — taking hits drains stamina; critical hits lock out all regen
- Exhaustion effects at zero stamina: slowness, sweat particles, heavy breathing, stumble, recovery animation
- Biome exposure system with 38 pre-configured biomes, cold/hot zones, grace periods, and armor/block protection
- Altitude system — high elevations and deep caves increase drain
- Potion modifiers — Speed and Haste can increase stamina drain
- Weight system — armor weight, inventory encumbrance, drowning/fall damage penalties
- MMOItems integration — custom item weights by type and ID
- Scaling systems — PlaceholderAPI max carry weight (`scaling-weight`) and stat vs load stamina drain (`scaling-drain`)
- Sound effects for stamina events — low stamina, exhaustion, Second Wind, dodges, and more
- Per-world drain multipliers and the ability to disable the plugin in specific worlds
- Admin GUI to change every setting in-game without touching config files
- In-game biome management (add, remove, edit biomes from the GUI)
- Weight commands to manage items, armor, and encumbrance settings from chat
- 30+ per-player bypass permissions for exempting specific features
- Real-time stamina display via action bar, boss bar, or chat — players can choose their own display with `/stamina display`
- Session statistics — track distance sprinted, jumps, dodges, and more with `/shs stats`
- PlaceholderAPI support with 19 placeholders for scoreboards and other plugins

## Quick Links

- [Getting Started](Getting-Started.md) — install and run it
- [Introduction](Introduction.md) — how the systems work together
- [Configuration](Configuration.md) — tune it for your server
- [Commands & Permissions](Commands-and-Permissions.md) — admin tools and bypass permissions
- [Default Config Files](Default-Config-Files.md) — what the defaults do
- [Placeholders](Placeholders.md) — PlaceholderAPI placeholders
- [Examples](Examples.md) — preset configs for different server types

## Requires

- Paper 1.21.x server
- MMOCore plugin
- MythicLib (required by MMOCore)
- PlaceholderAPI (optional, for `%shs_*%` placeholders)
- MMOItems (optional, for custom item weights and duplicate drain prevention)

## Compatibility Matrix

| Component | Supported | Notes |
|---|---|---|
| Paper | 1.21.x | Primary target runtime |
| MMOCore | Required | Stamina backend |
| MythicLib | Required by MMOCore | Install with MMOCore |
| PlaceholderAPI | Optional | Needed for `%shs_*%` placeholders |
| MMOItems | Optional | Custom item weight + attack-drain dedupe |

## 5-Minute Quick Start

1. Install Paper, MMOCore, MythicLib, and this plugin.
2. Start server once to generate `config.yml` and `actions.yml`.
3. Run `/shs gui` and keep defaults except:
   - enable `sprint-lock`
   - pick `hunger` mode (`overflow` or `bar`)
4. Test with one player: sprint to zero, verify sprint lock + recovery.
5. Adjust one preset baseline from `Examples.md` for your server type.

## Performance Profile (Operator Guidance)

- Low-load baseline: keep `engine.tick-interval: 4` and default effects off for lightweight servers.
- Medium-load profile: disable non-essential visuals (`effects`, heavy particles), keep biome systems tuned.
- High-load profile: increase `engine.tick-interval`, reduce action complexity, and use per-world disables for lobby worlds.

Use these as starting guidance before production tuning.

## Version

1.0.7 by AlternativeSoap
