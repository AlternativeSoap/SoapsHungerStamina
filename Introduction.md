# Introduction

## Why this plugin exists

Vanilla survival hunger and MMOCore stamina don't talk to each other. Players end up managing two separate resources that feel completely disconnected.

SoapsHungerStamina fixes that by making stamina the primary resource for everything physical. When stamina is gone, hunger becomes the cost. Your inventory weight matters. The biome you're in matters. The altitude matters. How hard you push matters.

## How it works

Stamina is your movement currency. Sprinting drains it per second, jumping costs a flat amount per jump, swimming drains it per second, and attacking costs stamina per hit. Placing and breaking blocks cost a small amount each. Raising a shield costs stamina upfront and keeps draining while held. Sneaking and standing still give bonus stamina regen on top of MMOCore's natural regen.

Beyond the basics, the plugin tracks a wide range of physical actions. Gliding with an elytra drains stamina over time. Climbing ladders, vines, or scaffolding costs stamina. Eating food restores a flat amount of stamina. Mace smash attacks cost extra on top of the normal attack drain. Shooting a bow, crossbow, or trident costs stamina (bows can scale with draw charge). Throwing items — snowballs, eggs, ender pearls, potions, wind charges, and more — each have their own stamina cost. Paddling a boat, crawling through 1-block gaps, launching with riptide, and using tools like hoes, shears, and brushes all drain stamina too.

The environment plays a role as well. Walking on soul sand or honey blocks increases drain. Standing in powder snow drains stamina. Bouncing on slime blocks costs a small amount per bounce. Standing in water or lava drains stamina passively. Active potion effects like Speed and Haste can multiply your drain if that feature is enabled.

Taking damage has its own mechanic called "winded." Getting hit drains stamina instantly and applies a lingering drain over several seconds. Critical hits are harsher — they drain more and completely lock out all stamina regen for a configurable duration.

When stamina is empty and you keep doing stuff, two things happen. First, your food bar starts draining instead (overflow mode), or the food bar can be replaced entirely with a stamina display (bar mode). Second, overexertion accumulates — keep pushing past zero and you start taking real damage that scales up the longer you ignore it. There's a grace period before damage starts and a warning message before it gets dangerous.

If exhaustion effects are enabled, hitting zero stamina has physical consequences. Slowness makes you sluggish, sweat particles drip from your character, heavy breathing darkens your vision briefly, and stumble nudges knock you off course. All effects clear once stamina recovers past a configurable threshold.

Biomes add another layer. Cold biomes (snowy plains, frozen ocean, deep dark, etc.) freeze you and drain stamina faster, with freeze particles to show the cold. Hot biomes (desert, jungle, nether) make you sweat and drain faster too. Each biome can have its own custom drain multiplier, and being encumbered in an extreme biome makes it even worse. The nether biomes come preconfigured with higher multipliers.

Altitude matters too. Above a configurable height threshold, thin mountain air increases stamina drain and applies passive drain. Below a configurable depth threshold, stuffy cave air does the same. Between the two thresholds is a comfortable zone with no penalty. The multiplier scales linearly from the threshold edge to the world boundary.

Weight matters. Armor has weight — full netherite adds 37% more stamina drain. Items in your inventory add up based on per-item weights (over 1000 items are preconfigured). Cross the encumbrance threshold and you get slower drain, Slowness, and a warning message. Cross the severe threshold and it gets much worse — sprint is blocked, you drown faster, and fall damage increases. Shulker boxes and bundles weigh their contents. With PlaceholderAPI, max carry weight can scale with level or attributes, and drain can be reduced by stats.

MMOItems integration lets you assign custom weights to specific items by their MMOItems type and ID, or set default weights for entire item types. If a weapon already applied a stamina cost through MythicLib, the plugin's attack drain is automatically skipped to prevent double-charging.

For feedback, you get real-time stamina display through action bar, boss bar, or chat messages. There's an optional text-character stamina bar (`████░░░░░░`), low stamina warnings that change color, and messages when exhaustion kicks in or clears. Biome transition messages tell you when the climate changes. Overexertion warnings tell you when you're pushing too hard.

Admins can open `/shs gui` to toggle features and change values in-game. No config file editing needed, every setting has a clickable item. Left/right click to adjust values, shift-click for bigger jumps. The GUI includes a biome settings page for adding, removing, and editing biomes. Weight and encumbrance settings can be managed with `/shs weight` commands.

## Why it matters

Your server gets a real resource loop:
- Travel costs stamina
- Combat costs stamina
- Projectiles and abilities cost stamina
- Gliding, climbing, and boating cost stamina
- Carrying heavy gear has a downside
- Biomes feel different to be in
- Altitude matters for mountain and cave exploration
- Running out means hunger drain, exhaustion effects, and overexertion damage
- Food becomes valuable again — eating restores stamina
- Resting and recovery feel necessary

Stamina → hunger overflow → exhaustion effects → overexertion damage. That's the loop.
