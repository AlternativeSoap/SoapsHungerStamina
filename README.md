# SoapsHungerStamina

**Make stamina and hunger work together in survival gameplay.**

SoapsHungerStamina ties MMOCore stamina into vanilla survival. Sprinting, jumping, swimming, fighting, mining, building - it all costs stamina. Run out and your food bar starts draining instead. Keep pushing and overexertion will hurt you. Carry too much weight and things get worse. Cold biomes freeze you, hot biomes make you sweat. Getting hit in combat winds you and locks out recovery.

## What It Does

- **Action-based stamina** - sprinting, jumping, swimming, water contact, lava contact, attacking, block placing, block breaking, and shield blocking all cost stamina. Sneaking and standing still restore it.
- **Hunger overflow** - when stamina hits zero, extra cost spills into your food bar. Saturation drains first, then actual hunger, with a configurable floor.
- **Winded system** - taking damage drains stamina and applies a drain-over-time. Critical hits are harsher and lock out all regen for seconds.
- **Overexertion** - keep pushing at zero stamina and you start taking scaling damage. A grace period gives you a chance to stop before it hurts.
- **Exhaustion effects** - slowness, sweat particles, heavy breathing, and stumble at zero stamina. All individually toggleable.
- **Biome system** - cold and hot biomes increase drain with custom multipliers and passive drain. Freeze ticks and sweat particles add atmosphere.
- **Weight & encumbrance** - armor weight and inventory weight affect drain. Two thresholds with escalating penalties including drowning, fall damage, and swim slowness.
- **Scaling** - max carry weight and drain reduction can scale from PlaceholderAPI values like MMOCore level or attributes.
- **Admin GUI** - toggle features and change values in-game without touching config files. Includes biome management.
- **Weight commands** - manage item weights and encumbrance settings from chat.
- **20+ bypass permissions** - per-feature exemptions for granular control.
- **Real-time display** - stamina via Action Bar, Boss Bar, or Chat with an optional text bar.
- **PlaceholderAPI support** - 8 placeholders for scoreboards, tab lists, and other plugins.

## Quick Links

- [Introduction](Introduction.md) - what the plugin does and why
- [Getting Started](Getting-Started.md) - install and run it
- [Configuration](Configuration.md) - tune it for your server
- [Commands & Permissions](Commands-and-Permissions.md) - admin tools and bypass permissions
- [Gameplay Guide](Gameplay-Guide.md) - how it affects gameplay
- [Default Config](Default-Config-Files.md) - what the defaults do
- [Examples](Examples.md) - preset configs for different server types
- [Placeholders](Placeholders.md) - PlaceholderAPI integration

## Requires

- Paper 1.21.x server
- MMOCore plugin
- MythicLib (required by MMOCore)
- PlaceholderAPI (optional, for `%shs_*%` placeholders and scaling features)
- MMOItems (optional, prevents double-drain on weapon stamina costs)

## Version

1.0.3 by AlternativeSoap
