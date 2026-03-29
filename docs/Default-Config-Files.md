# Default Config Files

What each default setting does and what files the plugin creates.

---

## What Gets Created

On first run, the plugin creates three files:

```
plugins/SoapsHungerStamina/
  ├── config.yml     (all settings — actions, effects, biomes, UI, etc.)
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

- **bypass-permission:** Players with this permission skip all stamina/hunger drain
- **stop-sprint-on-empty:** Forces sprinting to stop at 0 stamina
- **debug:** Prints drain info to console (off by default)

### GUI

```yaml
gui:
  enabled: true
```

- **enabled:** The `/shs gui` settings panel is available. Turn off to disable it (commands still work)

### Actions

```yaml
actions:
  sprint:
    enabled: true
    drain-per-second: 2.5
  jump:
    enabled: true
    cost: 4.0
    cooldown: 300
  swim:
    enabled: true
    drain-per-second: 2.0
  block-place:
    enabled: true
    cost: 0.3
  block-break:
    enabled: true
    cost: 0.8
  sneak:
    enabled: true
    regen-per-second: 1.5
  attack:
    enabled: true
    cost: 2.5
  shield-block:
    enabled: true
    initial-cost: 1.5
    drain-per-second: 0.5
```

Quick math on the defaults:
- 100 stamina lasts 40 seconds of sprinting
- 100 stamina = 25 jumps
- 100 stamina = 40 melee hits
- 100 stamina = 333 blocks placed
- Sneaking regens 1.5/sec on top of MMOCore's natural regen

### Hunger Overflow

```yaml
hunger:
  enabled: true
  drain-per-second: 1.0
  min-hunger: 0
  drain-saturation: true
```

- When stamina is empty, food drains at 1 point per second (half a shank)
- Can drain all the way to 0 (full starvation possible)
- Saturation goes first, then the food bar

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

- Checks every 4 ticks (5 times per second) — smooth and efficient
- You need to move at least 0.05 blocks to count as "moving"

### Exhaustion Effects

```yaml
effects:
  enabled: false
  recovery-threshold: 15.0
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
- **Slowness I** while exhausted (amplifier 0)
- **3 water drip particles** per tick around the head
- **Brief darkness flashes** on screen edges
- **3% chance** per tick of a small knockback stumble
- Everything clears once stamina gets above 15%

### Biomes

```yaml
biomes:
  enabled: false
  cold-drain-multiplier: 1.15
  hot-drain-multiplier: 1.10
  freeze:
    enabled: true
    ticks-per-tick: 1
  sweat:
    enabled: true
    count: 4
  encumbrance-biome-bonus: 0.15
```

Off by default. When enabled:
- Cold biomes drain 15% faster and apply freeze ticks
- Hot biomes drain 10% faster and show sweat particles
- Being encumbered in an extreme biome adds another 15% on top
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

- Severely encumbered players lose 8 air ticks per engine tick underwater
- Fall damage can increase up to 75% at max weight

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
- **prefix** — Gradient-colored plugin name added to all messages
- **command.*** — Responses for every command
- **exhaustion.*** — "You are exhausted" / "strength returning" messages
- **encumbrance.*** — Weight warning/recovery messages
- **biome.*** — Climate change messages (entering cold/hot/neutral biomes)
- **ui.format** — Normal stamina display
- **ui.low-stamina-format** — Warning display when low
- **gui.*** — All text in the admin settings GUI (titles, labels, setting names, value names)

---

## weight.yml Defaults

Controls the weight/encumbrance system.

### Armor Weight

Each armor material has a multiplier that affects stamina drain:

| Material | Multiplier | Effect |
|---|---|---|
| Leather | 1.0 | No change |
| Chainmail | 1.05 | 5% faster drain |
| Gold | 1.1 | 10% faster drain |
| Iron | 1.15 | 15% faster drain |
| Diamond | 1.25 | 25% faster drain |
| Netherite | 1.35 | 35% faster drain |

The plugin multiplies all 4 armor slots together. Full netherite = ~1.35⁴ ≈ 3.3x drain.

### Encumbrance Thresholds

- **max-weight:** 100 — above this, you're "encumbered" (message + faster drain)
- **severe-weight:** 150 — above this, you're "severely encumbered" (drowning + fall damage penalties)

### Item Weights

Every item type has a weight. Some examples from the defaults:
- Blocks (stone, dirt, etc.): 1.0–2.0 per stack slot
- Tools (pickaxe, sword): 2.0–4.0
- Armor pieces: 3.0–6.0
- Heavy items (anvil, enchanting table): 10.0–15.0
- Light items (sticks, seeds): 0.1–0.5

The full list is in weight.yml and can be customized per item.
