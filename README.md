# SoapsHungerStamina

**Make stamina and hunger work together in survival gameplay.**

SoapsHungerStamina ties MMOCore stamina into vanilla survival. Sprinting, jumping, swimming, fighting, mining, building, gliding, climbing, boating, throwing — it all costs stamina. Run out and your food bar starts draining instead. Push too hard and overexertion deals real damage. Carry too much weight and things get worse. Cold biomes freeze you, hot biomes make you sweat. High altitude thins the air, deep caves feel stuffy.

## What It Does

- 30+ actions and mechanics drain or restore stamina — sprinting, jumping, swimming, attacking, blocking, elytra gliding, climbing, eating, mace smashes, projectiles (bow, crossbow, trident, throwables), boat paddling, crawling, riptide, tool use, and more
- Environmental systems: biome temperature, altitude, powder snow, soul sand, honey blocks, water/lava contact
- When stamina hits zero, the cost overflows into your food bar (or replace the food bar entirely with a stamina display)
- Overexertion system — keep pushing at zero stamina and you take escalating damage
- Winded mechanic — taking hits drains stamina; critical hits lock out all regen
- Exhaustion effects at zero stamina: slowness, sweat particles, heavy breathing, stumble
- Biome system with cold/hot zones, freeze ticks, sweat particles, freeze particles, and passive drain
- Altitude system — high elevations and deep caves increase drain
- Potion modifiers — Speed and Haste can increase stamina drain
- Weight system — armor weight, inventory encumbrance, drowning/fall damage penalties
- MMOItems integration — custom item weights by type and ID
- Scaling systems — PlaceholderAPI-driven max weight and drain reduction
- Admin GUI to change every setting in-game without touching config files
- In-game biome management (add, remove, edit biomes from the GUI)
- Weight commands to manage items, armor, and encumbrance settings from chat
- 30+ per-player bypass permissions for exempting specific features
- Real-time stamina display via action bar, boss bar, or chat with a text stamina bar option
- PlaceholderAPI support with 8 placeholders for scoreboards and other plugins

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

## Version

1.0.4 by AlternativeSoap
