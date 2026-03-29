# Examples

Preset configs for different server styles. Copy the values you want into your config.yml and run `/shs reload`.

---

## PvP Arena (Short, Intense Fights)

High costs so stamina management matters in combat. Attacking and shielding are expensive.

```yaml
actions:
  sprint:
    enabled: true
    drain-per-second: 8.0
  jump:
    enabled: true
    cost: 10.0
    cooldown: 400
  swim:
    enabled: true
    drain-per-second: 5.0
  attack:
    enabled: true
    cost: 5.0
  shield-block:
    enabled: true
    initial-cost: 4.0
    drain-per-second: 2.0
  block-place:
    enabled: false
  block-break:
    enabled: false
  sneak:
    enabled: true
    regen-per-second: 3.0

hunger:
  enabled: true
  drain-per-second: 2.0
  min-hunger: 4

effects:
  enabled: true
  recovery-threshold: 15.0
  stumble:
    enabled: true
    chance: 0.08
    strength: 0.15
```

Every swing counts. Blocking drains hard. Sneaking between fights is the only way to recover. Building is free because it's a PvP arena.

---

## Survival Exploration (Chill Travel)

Low costs so travel doesn't feel punishing. Biomes add flavor.

```yaml
actions:
  sprint:
    enabled: true
    drain-per-second: 1.0
  jump:
    enabled: true
    cost: 1.5
    cooldown: 200
  swim:
    enabled: true
    drain-per-second: 0.5
  block-place:
    enabled: true
    cost: 0.1
  block-break:
    enabled: true
    cost: 0.3
  sneak:
    enabled: true
    regen-per-second: 2.0
  attack:
    enabled: true
    cost: 1.0
  shield-block:
    enabled: true
    initial-cost: 0.5
    drain-per-second: 0.2

hunger:
  enabled: true
  drain-per-second: 0.5
  min-hunger: 3

biomes:
  enabled: true
  cold-drain-multiplier: 1.10
  hot-drain-multiplier: 1.05

effects:
  enabled: false
```

Travel is fun, stamina is a soft constraint, food is backup. Biomes add atmosphere without being brutal.

---

## Hardcore (Everything Hurts)

Stamina is a real survival resource. Weight matters. Biomes are dangerous.

```yaml
actions:
  sprint:
    enabled: true
    drain-per-second: 6.0
  jump:
    enabled: true
    cost: 8.0
    cooldown: 350
  swim:
    enabled: true
    drain-per-second: 4.0
  block-place:
    enabled: true
    cost: 1.0
  block-break:
    enabled: true
    cost: 2.0
  sneak:
    enabled: true
    regen-per-second: 1.0
  attack:
    enabled: true
    cost: 4.0
  shield-block:
    enabled: true
    initial-cost: 3.0
    drain-per-second: 1.5

hunger:
  enabled: true
  drain-per-second: 1.5
  min-hunger: 0
  drain-saturation: true

effects:
  enabled: true
  recovery-threshold: 20.0
  stumble:
    enabled: true
    chance: 0.10
    strength: 0.15

biomes:
  enabled: true
  cold-drain-multiplier: 1.30
  hot-drain-multiplier: 1.25
  encumbrance-biome-bonus: 0.25

encumbrance:
  drowning:
    enabled: true
    air-loss-per-tick: 12
  fall-damage:
    enabled: true
    max-multiplier: 2.5
```

Stamina is critical. Hunger is deadly. Biomes punish you. Carrying too much gear near water can kill you. Every action matters.

---

## Parkour (Jump Only)

Only jumping costs stamina. Everything else is free.

```yaml
actions:
  sprint:
    enabled: false
  jump:
    enabled: true
    cost: 2.0
    cooldown: 250
  swim:
    enabled: false
  block-place:
    enabled: false
  block-break:
    enabled: false
  sneak:
    enabled: false
  attack:
    enabled: false
  shield-block:
    enabled: false

hunger:
  enabled: false
```

Pure jump management. Run freely, but time your jumps.
