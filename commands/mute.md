---
name: mute
description: Toggle notification sounds on/off
user_invocable: true
---

Toggle the mute state for bells-and-whistles notifications.

Check if the mute file exists at `${CLAUDE_PLUGIN_ROOT}/.mute`:

- If it **exists**: delete it and tell the user "Notifications unmuted."
- If it **does not exist**: create it (empty file) and tell the user "Notifications muted."

Use the Bash tool to check and toggle:

```bash
MUTE_FILE="${CLAUDE_PLUGIN_ROOT}/.mute"
if [ -f "$MUTE_FILE" ]; then
    rm "$MUTE_FILE"
    echo "unmuted"
else
    touch "$MUTE_FILE"
    echo "muted"
fi
```

Report the result to the user in one line.
