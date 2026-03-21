# Examples

Real-world configuration tuning for different server styles.

---

## PvP Arena (Short, Intense Fights)

Higher costs to make stamina management matter in fights.

```yaml
actions:
  sprint:
    enabled: true
    drain-per-second: 8.0  # 4x default, drains fast
  jump:
    enabled: true
    cost: 10.0  # Much more expensive
    cooldown: 400  # Slightly longer cooldown
  swim:
    enabled: true
    drain-per-second: 5.0  # 3x+ default

hunger:
  enabled: true
  drain-per-second: 2.0  # Penalty is harsher
  min-hunger: 4  # Can't fully starve

effects:
  enabled: true  # Exhaustion effects active
  recovery-threshold: 15.0
```

Result: Every sprint counts. Stamina management is tight. Hunger is a real risk. Exhaustion effects punish reckless play.

---

## Survival Exploration (Low Stakes)

Lower costs so travel doesn't feel punishing.

```yaml
actions:
  sprint:
    enabled: true
    drain-per-second: 1.0  # Half default
  jump:
    enabled: true
    cost: 1.5  # Half default
    cooldown: 200
  swim:
    enabled: true
    drain-per-second: 0.5  # Gentle

hunger:
  enabled: true
  drain-per-second: 0.5  # Slow penalty
  min-hunger: 3  # Can't starve completely
```

Result: Travel is fun, stamina is a soft constraint, food is backup.

---

## Hardcore Mode (Maximum Impact)

Stamina is a real survival resource.

```yaml
actions:
  sprint:
    enabled: true
    drain-per-second: 6.0  # 3x default
  jump:
    enabled: true
    cost: 8.0  # ~3x default
    cooldown: 350
  swim:
    enabled: true
    drain-per-second: 4.0  # ~3x default

hunger:
  enabled: true
  drain-per-second: 1.5
  min-hunger: 0  # Can fully starve
  drain-saturation: true

general:
  stop-sprint-on-empty: true

effects:
  enabled: true
  recovery-threshold: 15.0
  stumble:
    enabled: true
    chance: 0.10  # Doubles default stumble chance
    strength: 0.15
```

Result: Stamina is critical. Hunger is deadly. Exhaustion effects are brutal. Every action matters.

---

## Jump-Only Server (Parkour)

Only jumping drains stamina; sprint and swim are free.

```yaml
actions:
  sprint:
    enabled: false  # Off
  jump:
    enabled: true
    cost: 2.0  # Lighter than default
    cooldown: 250
  swim:
    enabled: false  # Off

hunger:
  enabled: false  # No overflow

effects:
  enabled: false  # No exhaustion effects

ui:
  type: ACTION_BAR
```

Result: Parkour is the focus. Stamina bar shows jump capacity.

---

## Peaceful Roleplay (Minimal Drain)

Stamina is barely noticeable; emphasis is roleplay.

```yaml
actions:
  sprint:
    enabled: true
    drain-per-second: 0.5  # Barely there
  jump:
    enabled: true
    cost: 1.0  # So cheap
    cooldown: 150
  swim:
    enabled: true
    drain-per-second: 0.3

hunger:
  enabled: true
  drain-per-second: 0.2  # Almost negligible
  min-hunger: 10  # Always clearly alive

effects:
  enabled: false  # Too immersive for RP
```

Result: Stamina bar is present but not dominating gameplay.

---

## How to Apply

1. Edit your `config.yml` with values from an example above
2. Run `/shs reload`
3. Test in-game for 10 minutes
4. Tweak numbers up or down based on feel
5. Reload again and retest

Don't overthink it — start with one of these and adjust.
