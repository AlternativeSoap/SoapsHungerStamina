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
    drain-per-second: 2.0
  jump:
    enabled: true
    cost: 3.0
    cooldown: 300
  swim:
    enabled: true
    drain-per-second: 1.5
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
  message-cooldown: 0
  low-stamina-warning: true
  low-stamina-threshold: 20.0
```

**type** — `ACTION_BAR` (above hotbar), `BOSS_BAR` (top of screen), or `CHAT` (client-sided chat messages).

**update-threshold** — Stamina change needed before the UI refreshes (reduces flicker on tiny drains).

**message-cooldown** — Milliseconds between UI messages. Set to 0 for no cooldown. For `CHAT` mode, recommended 2000-5000 to prevent chat spam.

**low-stamina-warning** — Show a warning message when stamina drops below the threshold.

**low-stamina-threshold** — Percentage (20% = warning at 1/5 stamina remaining).

---

## Exhaustion Effects

Visual and gameplay effects applied when stamina hits zero. Disabled by default.

```yaml
effects:
  enabled: false
  recovery-threshold: 10.0
  slowness:
    enabled: true
    amplifier: 1
  sweat-particles:
    enabled: true
    count: 3
  heavy-breathing:
    enabled: true
  stumble:
    enabled: true
    chance: 0.05
    strength: 0.1
```

**enabled** — Master toggle for the entire effects system.

**recovery-threshold** — Stamina percentage the player must recover to before effects clear. At 10%, effects linger until the player regens past 10% stamina.

**slowness.enabled** — Applies a Slowness potion effect while exhausted.

**slowness.amplifier** — Slowness strength (0 = Slow I, 1 = Slow II, etc.).

**sweat-particles.enabled** — Spawns water drip particles around the player's head.

**sweat-particles.count** — Number of particles per tick. Higher = more visible sweat.

**heavy-breathing.enabled** — Applies brief Darkness pulses (screen edges darken).

**stumble.enabled** — Random small knockback nudges while exhausted.

**stumble.chance** — Chance per engine tick (0.05 = 5% chance each tick).

**stumble.strength** — How hard the stumble pushes (0.1 = very subtle).

---

## Messages

All player-facing text is in `plugins/SoapsHungerStamina/messages.yml`.

Supports MiniMessage formatting (colors, gradients, bold, etc.).

Key sections:
- **prefix** — Colored tag added to every message
- **command.*** — All command response messages
- **exhaustion.enter** — Message when exhaustion effects activate
- **exhaustion.recover** — Message when stamina recovers
- **ui.format** — Stamina display format
- **ui.low-stamina-format** — Warning display when stamina is low

Edit and reload to rebrand for your server.
