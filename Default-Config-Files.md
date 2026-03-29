# Default Config Files

What each default setting does and what files the plugin creates.

---

## What Gets Created

On first run, the plugin creates three files:

```
plugins/SoapsHungerStamina/
  ├── config.yml     (all settings: actions, effects, biomes, UI, etc.)
  ├── messages.yml   (all player-facing text)
  └── weight.yml     (item weights for the encumbrance system)
```

All are fully editable. Run `/shs reload` to apply changes, or use `/shs gui` to change settings in-game.

---

## config.yml Defaults

### General

```yaml
general:
  bypass-permission: "soapsstamina.bypass"
  stop-sprint-on-empty: true
  debug: false
```

- `bypass-permission`: players with this permission skip all stamina/hunger drain
- `stop-sprint-on-empty`: forces sprinting to stop at 0 stamina
- `debug`: prints drain info to console (off by default)

### GUI

```yaml
gui:
  enabled: true
```

The `/shs gui` settings panel is available. Turn off to disable it (commands still work).

### Actions

```yaml
actions:
  sprint:
    enabled: true
    drain-per-second: 1.2
  jump:
    enabled: true
    cost: 2.0
    cooldown: 300
  swim:
    enabled: true
    drain-per-second: 1.0
  block-place:
    enabled: true
    cost: 0.15
  block-break:
    enabled: true
    cost: 0.4
  sneak:
    enabled: true
    regen-per-second: 0.8
  attack:
    enabled: true
    cost: 1.2
  shield-block:
    enabled: true
    initial-cost: 0.8
    drain-per-second: 0.3
```

Quick math on the defaults:
- 100 stamina lasts ~83 seconds of sprinting
- 100 stamina = 50 jumps
- 100 stamina = ~83 melee hits
- 100 stamina = 666 blocks placed
- Sneaking regens 0.8/sec on top of MMOCore's natural regen

### Hunger Overflow

```yaml
hunger:
  enabled: true
  drain-per-second: 0.5
  min-hunger: 0
  drain-saturation: true
```

When stamina is empty, food drains at 0.5 points per second. Can drain all the way to 0 (full starvation possible). Saturation goes first, then the food bar.

### Hunger Bar

```yaml
hunger-bar:
  enabled: false
```

Off by default. When on, the food bar displays stamina percentage instead.

### Engine

```yaml
engine:
  tick-interval: 4
  movement-threshold: 0.05
```

Checks every 4 ticks (5 times per second), smooth and efficient. You need to move at least 0.05 blocks to count as "moving."

### Exhaustion Effects

```yaml
effects:
  enabled: false
  recovery-threshold: 10.0
  slowness:
    enabled: true
    amplifier: 0
  sweat-particles:
    enabled: true
    count: 3
  heavy-breathing:
    enabled: true
  stumble:
    enabled: true
    chance: 0.03
    strength: 0.1
```

Off by default. When you turn them on:
- Slowness I while exhausted (amplifier 0)
- 3 water drip particles per tick around the head
- Brief darkness flashes on screen edges
- 3% chance per tick of a small knockback stumble
- Everything clears once stamina gets above 10%

### Biomes

```yaml
biomes:
  enabled: false
  cold-drain-multiplier: 1.10
  hot-drain-multiplier: 1.08
  freeze:
    enabled: true
    ticks-per-tick: 1
  sweat:
    enabled: true
    count: 4
  encumbrance-biome-bonus: 0.10
```

Off by default. When enabled:
- Cold biomes drain 10% faster and apply freeze ticks
- Hot biomes drain 8% faster and show sweat particles
- Being encumbered in an extreme biome adds another 10% on top
- 36 biomes are pre-configured (20 cold, 11 hot, 5 nether with custom multipliers)

### Encumbrance

```yaml
encumbrance:
  drowning:
    enabled: true
    air-loss-per-tick: 8
  fall-damage:
    enabled: true
    max-multiplier: 1.75
```

Severely encumbered players lose 8 air ticks per engine tick underwater. Fall damage can increase up to 75% at max weight.

### UI

```yaml
ui:
  type: BOSS_BAR
  update-threshold: 0.5
  message-cooldown: 0
  low-stamina-warning: true
  low-stamina-threshold: 25.0
  bar:
    enabled: false
    length: 10
    filled-char: "█"
    empty-char: "░"
```

- Boss bar display by default (top of screen)
- Updates when stamina changes by 0.5 or more
- Warning format below 25% stamina
- Text bar disabled by default (enable and use `%stamina_bar%` in messages.yml)

---

## messages.yml Defaults

Controls all player-facing text. Everything uses [MiniMessage formatting](https://docs.advntr.dev/minimessage/).

Key sections:
- `prefix` - gradient-colored plugin name added to all messages
- `command.*` - responses for every command
- `exhaustion.*` - "You are exhausted" / "strength returning" messages
- `encumbrance.*` - weight warning/recovery messages
- `biome.*` - climate change messages (entering cold/hot/neutral biomes)
- `ui.format` - normal stamina display
- `ui.low-stamina-format` - warning display when low
- `gui.*` - all text in the admin settings GUI (titles, labels, setting names, value names)

---

## weight.yml Defaults

Controls the weight/encumbrance system.

### Armor Weight

Armor uses a per-piece weight system. The total drain multiplier is `1.0 + sum(equipped piece weights)`. Each piece adds a small amount:

| Material | Helmet | Chestplate | Leggings | Boots | Full Set |
|---|---|---|---|---|---|
| Leather | 0.01 | 0.02 | 0.015 | 0.01 | 1.055 (5.5% more drain) |
| Chainmail | 0.02 | 0.04 | 0.03 | 0.02 | 1.11 (11% more drain) |
| Gold | 0.025 | 0.05 | 0.04 | 0.025 | 1.14 (14% more drain) |
| Iron | 0.04 | 0.08 | 0.06 | 0.04 | 1.22 (22% more drain) |
| Diamond | 0.05 | 0.10 | 0.08 | 0.05 | 1.28 (28% more drain) |
| Netherite | 0.07 | 0.13 | 0.10 | 0.07 | 1.37 (37% more drain) |
| Turtle | 0.035 | — | — | — | (helmet only) |

### Encumbrance Thresholds

- `max-weight`: 300 - above this, you're "encumbered" (message + faster drain)
- `severe-weight`: 500 - above this, you're "severely encumbered" (drowning + fall damage penalties)
- `encumbered-drain-multiplier`: 1.4 (40% faster drain when encumbered)
- `severe-drain-multiplier`: 2.0 (double drain when severely encumbered)
- `default-weight`: 0.25 (weight for any item not explicitly listed)

### Item Weights

The plugin ships with over 1000 item weight entries covering all survival-obtainable items. Some examples:
- Stone/ore blocks: 1.0-1.5
- Dirt/sand: 0.8-0.9
- Wood logs/planks: 0.5-0.8
- Tools (pickaxe, sword): 2.0-4.0
- Heavy blocks (anvil, enchanting table): 10.0-15.0
- Light items (sticks, seeds): 0.1-0.3

Unlisted items use the `default-weight` (0.25). The full list is in weight.yml and can be customized per item or managed with `/shs weight` commands.
