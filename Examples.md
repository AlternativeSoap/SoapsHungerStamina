# Examples

Preset configs for different server styles. Copy the values you want into your config.yml and run `/shs reload`.

---

## PvP Arena (Short, Intense Fights)

High costs so stamina management matters in combat. Attacking and shielding are expensive. Getting hit hurts even more.

```yaml
actions:
  regen-action-cooldown: 2500
  sprint:
    enabled: true
    drain-per-second: 6.0
  jump:
    enabled: true
    cost: 8.0
    cooldown: 400
  swim:
    enabled: true
    drain-per-second: 4.0
  water-contact:
    enabled: false
  lava-contact:
    enabled: true
    drain-per-second: 3.0
  attack:
    enabled: true
    cost: 4.0
  shield-block:
    enabled: true
    initial-cost: 3.0
    drain-per-second: 1.5
  block-place:
    enabled: false
  block-break:
    enabled: false
  sneak:
    enabled: true
    regen-per-second: 2.5
  idle:
    enabled: true
    regen-per-second: 1.0
  winded:
    enabled: true
    refresh-on-hit: true
    normal:
      instant-cost: 3.0
      drain-per-second: 1.5
      duration: 4.0
    critical:
      instant-cost: 6.0
      drain-per-second: 3.0
      duration: 6.0
      regen-lock-duration: 5.0

overexertion:
  enabled: true
  threshold: 10.0
  base-damage: 2.0
  scaling-enabled: true
  scaling-divisor: 8.0
  max-damage: 10.0
  recovery-rate: 2.0

hunger:
  enabled: true
  drain-per-second: 1.5
  min-hunger: 4

effects:
  enabled: true
  recovery-threshold: 15.0
  stumble:
    enabled: true
    chance: 0.06
    strength: 0.12
```

Every swing counts. Blocking drains hard. Getting crit locks your regen for 5 seconds. Building is free because it's a PvP arena. Overexertion punishes players who refuse to disengage.

---

## Survival Exploration (Chill Travel)

Low costs so travel doesn't feel punishing. Biomes add flavor. Winded and overexertion are gentle.

```yaml
actions:
  regen-action-cooldown: 1000
  sprint:
    enabled: true
    drain-per-second: 0.8
  jump:
    enabled: true
    cost: 0.8
    cooldown: 200
  swim:
    enabled: true
    drain-per-second: 0.4
  water-contact:
    enabled: true
    drain-per-second: 0.2
  lava-contact:
    enabled: true
    drain-per-second: 1.0
  block-place:
    enabled: true
    cost: 0.05
  block-break:
    enabled: true
    cost: 0.15
  sneak:
    enabled: true
    regen-per-second: 2.0
  idle:
    enabled: true
    regen-per-second: 0.5
  attack:
    enabled: true
    cost: 0.6
  shield-block:
    enabled: true
    initial-cost: 0.3
    drain-per-second: 0.15
  winded:
    enabled: true
    refresh-on-hit: true
    normal:
      instant-cost: 1.0
      drain-per-second: 0.5
      duration: 3.0
    critical:
      instant-cost: 2.0
      drain-per-second: 1.0
      duration: 5.0
      regen-lock-duration: 2.0

overexertion:
  enabled: true
  threshold: 25.0
  base-damage: 0.5
  max-damage: 4.0
  recovery-rate: 5.0

hunger:
  enabled: true
  drain-per-second: 0.3
  min-hunger: 6

biomes:
  enabled: true
  cold-drain-multiplier: 1.05
  hot-drain-multiplier: 1.04
  cold-passive-drain: 0.3
  hot-passive-drain: 0.2

effects:
  enabled: false
```

Travel is fun, stamina is a soft constraint, food is backup. Biomes add atmosphere without being brutal. Overexertion has a generous grace period.

---

## Hardcore (Everything Hurts)

Stamina is a real survival resource. Weight matters. Biomes are dangerous. Getting hit can end a fight.

```yaml
actions:
  regen-action-cooldown: 3000
  sprint:
    enabled: true
    drain-per-second: 4.0
  jump:
    enabled: true
    cost: 5.0
    cooldown: 350
  swim:
    enabled: true
    drain-per-second: 3.0
  water-contact:
    enabled: true
    drain-per-second: 1.0
  lava-contact:
    enabled: true
    drain-per-second: 3.0
  block-place:
    enabled: true
    cost: 0.5
  block-break:
    enabled: true
    cost: 1.0
  sneak:
    enabled: true
    regen-per-second: 1.0
  idle:
    enabled: true
    regen-per-second: 0.2
  attack:
    enabled: true
    cost: 3.0
  shield-block:
    enabled: true
    initial-cost: 2.0
    drain-per-second: 1.0
  winded:
    enabled: true
    refresh-on-hit: true
    normal:
      instant-cost: 3.0
      drain-per-second: 1.5
      duration: 6.0
    critical:
      instant-cost: 5.0
      drain-per-second: 3.0
      duration: 10.0
      regen-lock-duration: 6.0

overexertion:
  enabled: true
  threshold: 8.0
  base-damage: 2.0
  scaling-enabled: true
  scaling-divisor: 5.0
  max-damage: 12.0
  recovery-rate: 1.5
  warning-threshold: 0.6

hunger:
  enabled: true
  drain-per-second: 1.0
  min-hunger: 0
  drain-saturation: true

effects:
  enabled: true
  recovery-threshold: 25.0
  stumble:
    enabled: true
    chance: 0.08
    strength: 0.12

biomes:
  enabled: true
  cold-drain-multiplier: 1.25
  hot-drain-multiplier: 1.20
  cold-passive-drain: 1.0
  hot-passive-drain: 0.8
  encumbrance-biome-bonus: 0.20
```

Stamina is critical. Hunger is deadly - no floor. A critical hit locks out regen for 6 seconds. Overexertion kicks in fast (threshold 8) with aggressive scaling. Biomes punish you hard. Carrying too much gear near water can kill you. Every action matters.

---

## Parkour (Jump Only)

Only jumping costs stamina. Everything else is free.

```yaml
actions:
  regen-action-cooldown: 500
  sprint:
    enabled: false
  jump:
    enabled: true
    cost: 2.0
    cooldown: 250
  swim:
    enabled: false
  water-contact:
    enabled: false
  lava-contact:
    enabled: false
  block-place:
    enabled: false
  block-break:
    enabled: false
  sneak:
    enabled: false
  idle:
    enabled: true
    regen-per-second: 1.0
  attack:
    enabled: false
  shield-block:
    enabled: false
  winded:
    enabled: false

overexertion:
  enabled: false

hunger:
  enabled: false
```

Just jumping. Stand still to recover. Clean and simple for parkour maps.
