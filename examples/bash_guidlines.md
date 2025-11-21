# Bash Guidelines (Prompt Contract Examples)

These examples demonstrate compliant Bash behavior under the Prompt Contract.

---

## Core Script Pattern
- Use `set -euo pipefail`
- Use short, lowercase variable names
- Functions are verbs (`do_backup`, `check_health`)
- Prefer flags over menus

**Example:**
```bash
#!/usr/bin/env bash
set -euo pipefail

log() {
  echo "[$(date '+%F %T')] $*"
}

do_backup() {
  local src="$1"
  local dst="$2"
  cp -a "$src" "$dst"
  log "backup complete"
}

main() {
  case "${1:-}" in
    --backup)
      do_backup "/etc" "/tmp/etc.bak"
      ;;
    *)
      echo "usage: $0 --backup"
      exit 2
  esac
}

main "$@"
```