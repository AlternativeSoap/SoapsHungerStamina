# Introduction

## Why This Plugin Exists

Vanilla survival hunger and MMOCore stamina don't talk to each other. Players end up managing two separate resources that feel completely disconnected.

SoapsHungerStamina fixes that by making stamina the primary resource for everything physical. When stamina is gone, hunger becomes the cost. Your inventory weight matters. The biome you're in matters. Push too far past empty and your body starts breaking down.

## Core Features

Stamina drains in real time while sprinting, jumping, swimming, attacking, placing blocks, breaking blocks, and shield blocking. Wading through water or touching lava costs stamina too. Sneaking gives bonus stamina regen instead of draining, and standing still provides a small passive recovery on top of MMOCore's natural regen.

When stamina runs out, extra cost spills over into hunger - saturation burns first, then actual food. There's a configurable hunger floor so it never drops below a set minimum, and the drain is smooth and fractional with no sudden chunk loss.

Getting hit drains stamina through the winded system. Normal hits cost stamina and apply a drain-over-time effect. Critical hits are harsher - bigger cost, longer drain, and a regen lock that completely blocks all stamina recovery for several seconds.

If you keep pushing with empty stamina, overexertion kicks in. There's a grace period before anything happens, but once you pass the threshold you start taking real damage that scales the longer you push. Stop and rest to recover.

Toggle each drain type on or off individually. Every action, every effect, every system can be enabled or disabled separately.

### Optional Systems

- **Exhaustion effects** at zero stamina: slowness, sweat particles, heavy breathing, and stumbling - all individually toggleable
- **Sprint lock** when stamina hits zero
- **Hunger bar mode** that syncs the food bar directly with stamina - eating restores stamina instead of food

### Biome System (off by default)

Cold and hot biomes increase stamina drain with custom multipliers. Each biome has its own passive drain on top of that. Cold biomes gradually freeze your character, hot biomes cause sweat particles. Per-biome configuration lets you add, remove, or edit biomes and set custom multipliers. Transition messages fire when entering or leaving extreme biomes. The biome effect stacks with encumbrance for even harsher drain in the worst conditions.

### Weight & Encumbrance

Armor weight and inventory weight affect stamina drain. Two thresholds - encumbered (faster drain, slowness) and severe (even worse drain, sprint blocked, extra slowness in water). Severely encumbered players drown faster and take more fall damage. Per-item weights are configurable in weight.yml, and the system can weigh shulker box and bundle contents. Per-player max weight can be set with permissions.

With PlaceholderAPI installed, max carry weight and drain reduction can scale from other plugins - tie it to MMOCore level, strength attributes, or anything that exposes a placeholder.

### Player Experience

Stamina display via Action Bar, Boss Bar, or Chat with an optional text-based stamina bar. Customizable warnings for low stamina and exhaustion. Adjustable message cooldown so the UI doesn't spam. Lightweight updates avoid flickering. Works properly across death, respawn, world changes, teleports, joining, and leaving.

### Admin Controls

In-game GUI to toggle features and change values without editing config files. Weight commands to manage item weights and encumbrance settings in-game. Toggle and config set commands for quick adjustments. Full tab completion on all commands. Reload configs, messages, and weight files without restarting. Give stamina to players or reset them to full. Per-feature bypass permissions for granular control. Optional debug logging.

### Performance & Stability

Tick-based system with adjustable speed. Won't drain stamina if the player is standing still (unless in an extreme biome with passive drain). Suppresses vanilla exhaustion to avoid conflicts. Handles lag spikes gracefully by capping time between ticks. Only active in Survival and Adventure modes. PlaceholderAPI support if installed.

## The Gameplay Loop

Your server gets a real resource loop:
- Travel costs stamina
- Combat costs stamina - and getting hit makes it worse
- Carrying heavy gear has a real downside
- Biomes feel different to be in
- Running out means hunger drain and exhaustion effects
- Pushing past empty means overexertion damage
- Food becomes valuable again
- Resting and recovery feel necessary

Stamina → hunger overflow → exhaustion effects → overexertion. That's the loop.
