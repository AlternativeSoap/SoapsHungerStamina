# Default Config Files

This page explains what each default setting does.

---

## config.yml Defaults

The plugin creates this file automatically. Here's what each section does.

### General Settings

```yaml
general:
  bypass-permission: "soapsstamina.bypass"
  stop-sprint-on-empty: true
  debug: false
```

- **bypass-permission:** Staff with this permission don't drain stamina/hunger
- **stop-sprint-on-empty:** Force-stop sprinting when stamina hits 0 (feels better than drifting while hunger drains)
- **debug:** Print detailed drain logs to console (off by default, turn on to troubleshoot)

### Sprint

```yaml
actions:
  sprint:
    enabled: true
    drain-per-second: 5.0
```

Sprinting drains 5 stamina per second. If you're bad at stamina math: 20 stamina lasts 4 seconds of sprinting.

### Jump

```yaml
  jump:
    enabled: true
    cost: 8.0
    cooldown: 300
```

Each jump costs 8 stamina. You can jump at most once every 300ms (about 3 jumps per second). This prevents spam-jump exploitation.

### Swim

```yaml
  swim:
    enabled: true
    drain-per-second: 3.0
```

Swimming drains 3 stamina per second (slower than sprinting).

### Hunger Overflow

```yaml
hunger:
  enabled: true
  drain-per-second: 1.0
  min-hunger: 0
  drain-saturation: true
```

- **enabled:** Overflow draining is on
- **drain-per-second:** When stamina is empty, hunger drains at 1 point/sec (half a shank)
- **min-hunger:** Hunger won't go below 0 (players can fully starve)
- **drain-saturation:** Saturation (sparkles) drains before visible hunger (vanilla behavior)

### Hunger Bar Mode

```yaml
hunger-bar:
  enabled: false
```

Off by default. Turn on if you want the vanilla hunger bar to show stamina percentage instead.

### Engine

```yaml
engine:
  tick-interval: 4
  movement-threshold: 0.05
```

- **tick-interval:** Drain checks every 4 ticks (smooth, efficient). Lowering this = more checks = smoother drain but more CPU.
- **movement-threshold:** You need to move 0.05 blocks for it to count as "moving" (prevents stationary drain).

### UI

```yaml
ui:
  type: ACTION_BAR
  update-threshold: 0.5
  low-stamina-warning: true
  low-stamina-threshold: 20.0
```

- **type:** Shows stamina on the action bar (above hotbar)
- **update-threshold:** UI only updates when stamina changes by 0.5 or more (reduces flicker)
- **low-stamina-warning:** Show a special Warning message when stamina is low
- **low-stamina-threshold:** "Low" means below 20% stamina

---

## messages.yml Defaults

The plugin creates this file automatically. It controls all player-facing text.

**Everything supports MiniMessage formatting** — colors, gradients, bold, etc.

Key sections:

- **prefix** — Added to every message (colored gradient by default)
- **ui.format** — Stamina display on action bar
- **ui.low-stamina-format** — Warning display when stamina is low
- **command.*** — All command response messages

You can edit any of these to match your server's style or language.

---

## What Gets Created

On first run, the plugin creates:

```
plugins/SoapsHungerStamina/
  ├── config.yml          (action costs, overflow, engine settings)
  └── messages.yml        (all player-facing text)
```

Both are fully editable. Reload with `/shs reload` to apply changes.
