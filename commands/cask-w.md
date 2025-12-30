---
description: Forward commands to Codex session and wait for reply via cask-w command (supports tmux / WezTerm).
---

Forward commands to Codex session and wait for reply via `cask-w` command (supports tmux / WezTerm).

## Execution

**⚠️ IMPORTANT: Use heredoc format to avoid quote escaping issues:**

```bash
cask-w "$(cat <<'EOF'
<content>
EOF
)"
```

Or with `run_in_background=true`:
```
Bash(cask-w "$(cat <<'EOF'
<content>
EOF
)", run_in_background=true)
```

## Parameters
- `<content>` required, will be forwarded to Codex session

## Workflow
1. Start cask-w in background -> get task_id
2. Inform user: "Codex processing (task: xxx)"
3. When bash-notification arrives -> show result

## Examples

**Simple message (no special chars):**
```bash
cask-w "analyze code"
```

**Complex message (with quotes, special chars) - USE HEREDOC:**
```bash
cask-w "$(cat <<'EOF'
Analyze the "login" feature.
Check if it's working correctly.
Look for $variables and backticks.
EOF
)"
```

## Hints
- **Always use heredoc format** when message may contain quotes or special characters
- Use `cask` for fire-and-forget (no wait)
- Use `/cpend` to view latest reply anytime
