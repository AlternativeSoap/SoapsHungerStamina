# SoapsHungerStamina

**Make stamina and hunger work together in survival gameplay.**

SoapsHungerStamina ties MMOCore stamina into vanilla survival. Sprinting, jumping, swimming, fighting, mining, building - it all costs stamina. Run out and your food bar starts draining instead. Carry too much weight and things get worse. Cold biomes freeze you, hot biomes make you sweat.

## What It Does

- 8 actions drain stamina (sprinting, jumping, swimming, attacking, block placing, block breaking, shield blocking) and sneaking restores it
- When stamina hits zero, the cost overflows into your food bar
- Exhaustion effects at zero stamina: slowness, sweat, heavy breathing, stumble
- Biome system with cold/hot zones that affect drain speed
- Weight system where heavy armor and full inventories hurt your recovery
- Admin GUI to change every setting in-game without touching config files
- In-game biome management (add, remove, edit biomes from the GUI)
- Weight commands to manage items and encumbrance settings from chat
- 18 per-player bypass permissions for exempting specific features
- Real-time stamina display via action bar, boss bar, or chat
- PlaceholderAPI support for scoreboards and other plugins

## Quick Links

- [Getting Started](Getting-Started.md) - install and run it
- [Configuration](Configuration.md) - tune it for your server
- [Commands & Permissions](Commands-and-Permissions.md) - admin tools and bypass permissions
- [Gameplay Guide](Gameplay-Guide.md) - how it affects gameplay
- [Default Config](Default-Config-Files.md) - what the defaults do
- [Examples](Examples.md) - preset configs for different server types

## Requires

- Paper 1.21.x server
- MMOCore plugin
- MythicLib (required by MMOCore)
- PlaceholderAPI (optional, for `%shs_*%` placeholders)

## Version

1.0.1 by AlternativeSoap
