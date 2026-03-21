# Configuration

All settings are in `plugins/SoapsHungerStamina/config.yml`.

Edit the file and run `/shs reload` to apply changes live.

---

## General

```yaml
general:
  bypass-permission: "soapsstamina.bypass"
  stop-sprint-on-empty: true
  debug: false
```

**bypass-permission** — Permission node that completely skips stamina and hunger drain. Useful for staff ranks or special events.

**stop-sprint-on-empty** — If true, players are forced to stop sprinting when stamina hits zero. Prevents awkward sprinting while hunger is draining.

**debug** — Prints drain amounts to console for every action. Useful when balancing, off by default.

---

## Actions

Three actions drain stamina. You can enable/disable and tune each.

```yaml
actions:
  sprint:
    enabled: true
    drain-per-second: 5.0
  jump:
    enabled: true
    cost: 8.0
    cooldown: 300
  swim:
    enabled: true
    drain-per-second: 3.0
```

**sprint.drain-per-second** — How much stamina drains every second while sprinting and actually moving.

**jump.cost** — Flat stamina cost per jump. Cooldown prevents rapid double-jumps from both counting.

**jump.cooldown** — Milliseconds between countable jumps (300ms = 3 jumps per second max).

**swim.drain-per-second** — How much stamina drains every second while swimming.

---

## Hunger Overflow

When stamina hits zero, hunger starts draining instead.

```yaml
hunger:
  enabled: true
  drain-per-second: 1.0
  min-hunger: 0
  drain-saturation: true
```

**enabled** — Turn overflow to hunger on/off.

**drain-per-second** — Hunger drain rate after stamina is empty (1 point = half a shank).

**min-hunger** — Hunger floor: it won't drain below this. Set to 2 or 3 if you want food to always keep players barely alive.

**drain-saturation** — If true, saturation drains before food level. Matches vanilla hunger behavior.

---

## Hunger Bar Mode

Optional: use vanilla hunger bar to show stamina instead.

```yaml
hunger-bar:
  enabled: false
```

When enabled, the hunger bar visually represents your stamina percentage (0-100% stamina = 0-20 food level). Vanilla hunger mechanics are suppressed. Players can eat to restore stamina.

Only use this if you want a completely different visual approach.

---

## Engine (Performance)

```yaml
engine:
  tick-interval: 4
  movement-threshold: 0.05
```

**tick-interval** — Server ticks between drain checks (20 ticks = 1 second). Lower values = smoother drain and faster UI updates, but more CPU. Default 4 is smooth and efficient.

**movement-threshold** — How many blocks of horizontal movement count as "moving". Prevents drain while standing still. 0.05 is tuned for normal play.

---

## UI Display

```yaml
ui:
  type: ACTION_BAR
  update-threshold: 0.5
  low-stamina-warning: true
  low-stamina-threshold: 20.0
```

**type** — `ACTION_BAR` (above hotbar) or `BOSS_BAR` (top of screen).

**update-threshold** — Stamina change needed before the UI refreshes (reduces flicker on tiny drains).

**low-stamina-warning** — Show a warning message when stamina drops below the threshold.

**low-stamina-threshold** — Percentage (20% = warning at 1/5 stamina remaining).

---

## Messages

All player-facing text is in `plugins/SoapsHungerStamina/messages.yml`.

Supports MiniMessage formatting (colors, gradients, bold, etc.).

Edit and reload to rebrand for your server.
