# Commands & Permissions

## Player Commands

### `/stamina`
Shows your current stamina, max stamina, stamina percentage, and hunger level.

**Permission:** `soapsstamina.use` (default: everyone)

**Example output:**  
`Stamina: 42/100 (42%) | Hunger: 19/20`

**Alias:** `/shs stamina`

---

## Admin Commands

### `/shs reload`
Reloads configuration and message files from disk without restarting the server.

**Permission:** `soapsstamina.admin` (default: op)

Use this after editing the config to apply changes live.

---

### `/shs stamina give <player> <amount>`
Gives stamina to a player (won't exceed their max).

**Permission:** `soapsstamina.admin`

**Example:**  
`/shs stamina give PlayerName 50`

Gives 50 stamina to PlayerName (capped at their max stamina).

---

### `/shs stamina reset <player>`
Resets a player's stamina to maximum.

**Permission:** `soapsstamina.admin`

**Example:**  
`/shs stamina reset PlayerName`

---

### `/shs help`
Shows all available commands.

**Permission:** None required

---

### `/shs`
Shows plugin version and basic usage.

---

## Permissions

### `soapsstamina.admin`
Access to all admin commands: reload, give, reset.

Default: op-only

If you use a permission plugin, grant this to staff ranks that manage server settings.

---

### `soapsstamina.use`
Permission to check own stamina with `/stamina`.

Default: everyone (true)

---

### `soapsstamina.bypass`
Bypasses all stamina and hunger drain.

Default: no one

Useful for:
- Creative/build events (bypass so staff can test without draining)
- Special ranks that shouldn't consume stamina
- PvP events where stamina shouldn't matter

**To use it:**
- Set in config: `bypass-permission: "soapsstamina.bypass"`
- Grant `soapsstamina.bypass` to the ranks you want to exempt
- They will perform all actions (sprint, jump, swim) without any drain

---

## Tab Completion

All admin commands support tab completion for player names and suggestion values.

Example: `/shs stamina give [tab]` shows online player names.

---

## Command Help

Run `/shs help` in-game for a quick reference of all commands.
