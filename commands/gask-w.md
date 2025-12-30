---
description: Forward commands to Gemini session and wait for reply via gask-w command (supports tmux / WezTerm).
---

Forward commands to Gemini session and wait for reply via `gask-w` command (supports tmux / WezTerm).

## Execution

**⚠️ IMPORTANT: Use heredoc format to avoid quote escaping issues:**

```bash
gask-w "$(cat <<'EOF'
<content>
EOF
)"
```

Or with `run_in_background=true`:
```
Bash(gask-w "$(cat <<'EOF'
<content>
EOF
)", run_in_background=true)
```

## Parameters
- `<content>` required, will be forwarded to Gemini session

## Workflow
1. Start gask-w in background -> get task_id
2. Inform user: "Gemini processing (task: xxx)"
3. When bash-notification arrives -> show result

## Examples

**Simple message (no special chars):**
```bash
gask-w "explain this"
```

**Complex message (with quotes, special chars) - USE HEREDOC:**
```bash
gask-w "$(cat <<'EOF'
Review the "login" UI component.
Check if it's styled correctly.
Look for $variables and backticks.
EOF
)"
```

## Hints
- **Always use heredoc format** when message may contain quotes or special characters
- Use `gask` for fire-and-forget (no wait)
- Use `/gpend` to view latest reply anytime
