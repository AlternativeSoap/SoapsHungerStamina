# SoapsHungerStamina

**Make stamina and hunger work together in survival gameplay.**

SoapsHungerStamina bridges MMOCore stamina and vanilla survival. Sprint, jump, swim, fight, mine, and build — all of it costs stamina. When stamina runs out, hunger drains instead. Carry too much weight and everything gets worse. Cold biomes freeze you, hot biomes make you sweat.

## What It Does

- **8 actions** drain stamina — sprinting, jumping, swimming, attacking, block placing, block breaking, shield blocking, and sneaking restores it
- When stamina hits zero, the cost overflows into your food bar
- Exhaustion effects kick in at zero stamina — slowness, sweat, heavy breathing, stumble
- **Biome system** — cold biomes freeze you and drain faster, hot biomes make you sweat
- **Weight system** — heavy armor and full inventories slow your stamina drain recovery
- **Admin GUI** — change every setting in-game without touching config files
- **Per-player bypass** — 18 granular permissions to exempt specific features per player
- Real-time stamina display via action bar, boss bar, or chat
- PlaceholderAPI support for scoreboards and other plugins

## Quick Links

- [Getting Started](Getting-Started.md) — Install and run it
- [Configuration](Configuration.md) — Tune it for your server
- [Commands & Permissions](Commands-and-Permissions.md) — Admin tools and bypass permissions
- [Gameplay Guide](Gameplay-Guide.md) — How it affects gameplay
- [Default Config](Default-Config-Files.md) — What the defaults do
- [Examples](Examples.md) — Preset configs for different server types

## Requires

- Paper 1.21.x server
- MMOCore plugin
- MythicLib (required by MMOCore)
- PlaceholderAPI (optional — for `%shs_*%` placeholders)

## Version

1.0.1 by AlternativeSoap
