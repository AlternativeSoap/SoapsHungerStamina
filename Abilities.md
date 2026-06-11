# Abilities

Optional player mechanics in `actions.yml`. All are **disabled by default** except bed rest and stamina food.

## Dodge

```yaml
dodge:
  enabled: false
  cost: 4.0
  cooldown-ms: 1500
  velocity: 1.2
  invulnerable-ticks: 12
```

**Activation:** Sneak while sprinting (sneak key down, must already be sprinting).

**Checks:** Enough stamina, cooldown clear, not bypassing. Rate limit: `context.rate-limits.dodge` (default 3 per 4s).

**Combat:** Dodge is blocked while in combat unless `context.in-combat.allow-dodge: true` (default false). In-combat window: `context.in-combat.duration-ms` (default 6000) after taking damage.

Bypass: `soapsstamina.bypass.dodge`

## Sprint burst

```yaml
sprint-burst:
  enabled: false
  min-stamina-percent: 80.0
  cost: 6.0
  speed-amplifier: 1
  duration-ticks: 60
  cooldown-ms: 30000
  activation-window-ms: 400
```

**Activation:** Double-tap sprint within `activation-window-ms` (stop sprint, then start again quickly).

**Checks:** Stamina at or above `min-stamina-percent`, enough stamina for `cost`, cooldown clear.

Applies Speed for `duration-ticks`. Cooldown messages are silent on failed re-trigger to avoid spam.

Bypass: `soapsstamina.bypass.sprint-burst`

## Bed rest

```yaml
bed-rest:
  enabled: true
  restore-percent: 1.0
  cooldown-seconds: 300
  minimum-sleep-ms: 1000
  buff-enabled: true
  buff-duration-seconds: 120
  buff-drain-reduction: 0.65
```

**Activation:** Sleep through the night (vanilla sleep success).

Restores `restore-percent` of max stamina. Optional **Well Rested** buff reduces all stamina drain by `buff-drain-reduction` for `buff-duration-seconds`.

Bypass: `soapsstamina.bypass.bed-rest`

## Stamina food

```yaml
stamina-food:
  enabled: true
  items:
    GOLDEN_APPLE:
      instant-stamina: 10.0
      buff-duration: 30
      buff-regen-bonus: 0.5
```

**Activation:** Eat configured food items.

`instant-stamina` restores immediately. Optional buff adds bonus regen per second for `buff-duration` (**Well Fed**). Placeholders: `%shs_well_fed%`, `%shs_well_rested%` for buff timers.

Bypass: `soapsstamina.bypass.stamina-food`

## Second wind

Under `winded.second-wind` (default off). If enabled, standing idle at 0 stamina for `idle-seconds` triggers a percent recovery burst with a cooldown. Not a keybind; automatic when conditions match.

Bypass: `soapsstamina.bypass.second-wind`

## Sprint lock

Not a separate ability but affects sprinting:

```yaml
sprint:
  lock:
    enabled: true
    unlock-mode: above-zero   # or threshold-percent
    unlock-threshold-percent: 0.0
```

When stamina is too low, sprint is cancelled. Tune unlock mode so players cannot re-sprint until they recover.
