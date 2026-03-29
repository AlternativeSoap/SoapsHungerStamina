# Introduction

## Why this plugin exists

Vanilla survival hunger and MMOCore stamina don't talk to each other. Players end up managing two separate resources that feel completely disconnected.

SoapsHungerStamina fixes that by making stamina the primary resource for everything physical. When stamina is gone, hunger becomes the cost. Your inventory weight matters. The biome you're in matters.

## How it works

Stamina is your movement currency. Sprinting drains it per second, jumping costs a flat amount per jump, swimming drains it per second, and attacking costs stamina per hit. Placing and breaking blocks cost a small amount each. Raising a shield costs stamina upfront and keeps draining while held. Sneaking is the one exception - it gives bonus stamina regen on top of MMOCore's natural regen.

When stamina is empty and you keep doing stuff, your food bar starts draining instead. Saturation goes first, then actual hunger. There's a configurable minimum so hunger can stop at a floor you set instead of going all the way to zero.

If exhaustion effects are enabled, hitting zero stamina has physical consequences. Slowness makes you sluggish, sweat particles drip from your character, heavy breathing darkens your vision briefly, and stumble nudges knock you off course. All effects clear once stamina recovers past a configurable threshold.

Biomes add another layer. Cold biomes (snowy plains, frozen ocean, etc.) freeze you and drain stamina faster. Hot biomes (desert, jungle, nether) make you sweat and drain faster too. Each biome can have its own custom drain multiplier, and being encumbered in an extreme biome makes it even worse.

Weight matters too. Armor has weight, and heavier armor means faster stamina drain. Items in your inventory add up. Cross a threshold and you're encumbered with faster drain. Cross the severe threshold and it gets really bad - you drown faster and take more fall damage.

For feedback, you get real-time stamina display through action bar, boss bar, or chat messages. There's an optional text-character stamina bar (`████░░░░░░`), low stamina warnings that change color, and messages when exhaustion kicks in or clears. Biome transition messages tell you when the climate changes.

Admins can open `/shs gui` to toggle features and change values in-game. No config file editing needed, every setting has a clickable item. Left/right click to adjust values, shift-click for bigger jumps. The GUI includes a biome settings page for adding, removing, and editing biomes. Weight and encumbrance settings can be managed with `/shs weight` commands.

## Why it matters

Your server gets a real resource loop:
- Travel costs stamina
- Combat costs stamina
- Carrying heavy gear has a downside
- Biomes feel different to be in
- Running out means hunger drain and exhaustion effects
- Food becomes valuable again
- Resting and recovery feel necessary

Stamina -> hunger overflow -> exhaustion effects. That's the loop.
