# Hunger Modes

Set in `config.yml` → `hunger.mode`.

| Mode | Value | Behavior |
|------|-------|----------|
| Overflow | `overflow` | When stamina would drop below 0, excess drains food (and optionally saturation). Default. |
| Bar mirror | `bar` | Vanilla food bar shows stamina percent. Saturation and exhaustion are locked so vanilla hunger does not interfere. |
| Off | `disabled` | No hunger integration. Stamina-only. |

Toggle in-game: `/shs toggle hunger` (overflow) or `/shs toggle hunger-bar` (bar). Only one mode is active at a time.

## Overflow mode

```yaml
hunger:
  mode: overflow
  drain-per-second: 0.5    # unused in overflow; overflow is event-driven
  min-hunger: 0            # food floor when draining
  drain-saturation: true   # drain saturation before food
```

When a drain would take stamina below zero, the overflow amount reduces hunger. Bypass: `soapsstamina.bypass.hunger`.

The engine zeros vanilla exhaustion in overflow mode so vanilla sprint/jump hunger does not stack on top of plugin drain.

## Bar mode

Food level = `(stamina / max_stamina) * 20`. Players see stamina on the vanilla hunger bar. Useful when you hide custom UI (`ui.enabled: false`) but still want a familiar bar.

## Disabled mode

```yaml
hunger:
  mode: disabled
```

No food changes from SHS. Use when another plugin owns hunger or you only want MMOCore stamina UI.

## Related settings

- `ui.format` placeholders include `%hunger%` for overflow status command output.
- Stamina food (`actions.yml` → `stamina-food`) restores stamina directly; it does not require a specific hunger mode.
