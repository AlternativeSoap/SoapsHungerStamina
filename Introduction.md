# Introduction

## Why it exists

Vanilla hunger and MMOCore stamina usually ignore each other. Players juggle two bars that don't feel related.

This plugin makes stamina the main cost for physical stuff. Empty stamina spills into hunger (or replaces the food bar). Weight, biome, altitude, and how hard you push all matter.

## How it works

**Movement and combat.** Sprinting drains per second. Jumps cost a flat amount. Swimming, attacking, placing/breaking blocks, shields (upfront + per second + per blocked hit; shield drops if stamina is too low). Sneak and standing still add bonus regen on top of MMOCore.

**More actions.** Elytra, ladders, mace smash, bows/crossbows/tridents (bow can scale with draw), throwables, boats, crawling, riptide, hoes/shears/brushes/flint & steel. Weapon types can each have their own swing cost. Exclude specific weapons or blocks if you want.

**World stuff.** Soul sand and honey slow you down in stamina terms. Powder snow, water, lava, slime bounces. Speed/Haste can raise drain if you enable that.

**Winded.** Hits drain stamina now and for a few seconds after. Crits hit harder and can lock regen completely for a bit.

**At zero stamina.** Food bar drains (overflow) or becomes a stamina bar (bar mode). Keep acting and overexertion builds until you take real damage. Stand still long enough and Second Wind can pop you back up (cooldown applies).

**Exhaustion effects** (optional): slowness, sweat, heavy breathing, stumble. Clear when stamina recovers past a threshold; recovery particles if you want them.

**Biomes.** Cold/hot exposure timers (defaults: 60s cold, 45s hot grace). Freeze or sweat when exposed. Armor and water matter in heat. Over-encumbered in a hot biome skips the grace period. 38 biomes preconfigured; nether ones are harsher.

**Altitude.** High up = thinner air, more drain. Deep down = stuffy caves, same idea. Middle band is fine.

**Weight.** Armor adds drain (full netherite is roughly +37%). Items have weight; 1000+ defaults. Over 300 weight (default): slower, more drain unless scaling-drain handles it. Over 500: worse slowness, sprint can lock, faster drowning, harder falls. Shulkers and bundles count contents.

**PlaceholderAPI:** `scaling-weight` bumps max carry (often level). `scaling-drain` lets a stat like strength cancel part of your load before stamina drain ramps up.

**MMOItems.** Custom weights per item/type. MythicLib attack costs skip the plugin's attack drain so you don't charge twice.

**Food and rest.** Some foods restore stamina + Well Fed buff. Beds restore stamina + optional Well Rested drain reduction.

**Dodge / sprint burst.** Optional active tricks with cooldowns.

**UI.** Action bar, boss bar, or chat. Players can pick with `/stamina display` if you allow it. Sounds, low stamina warnings, `/shs stats` for session totals.

**Worlds.** Disable stamina entirely in some worlds, or set a drain multiplier per world.

**Admins.** `/shs gui` toggles and sliders. `/shs weight` for encumbrance and items. No file editing required if you don't want it.

## The loop in one line

Spend stamina → hunger pays when it's gone → effects and overexertion if you don't stop → second wind or food/bed to recover.
