# Claude CLI Skill for Codex

Use this skill to have Codex call the Claude Code CLI (`claude`) from your current repo for refactors, reviews, delegation, and other coding tasks.

## Requirements

- Codex CLI installed and logged in. See the Codex CLI docs.
- Claude Code CLI installed and logged in so `claude` is available on your PATH.

## Install

### Option A: Install with the built-in skill installer (recommended)

From inside Codex (CLI or IDE), run the skill installer and ask it to install from this GitHub repo:

```
$skill-installer
install the claude-cli skill from the xylan-x/claude-cli repo, path ".", ref "master"
```

Restart Codex after installation so it can pick up the new skill.

### Option B: Manual install (per-user or per-repo)

1) Clone this repo.
2) Copy the skill folder to a valid Codex skills directory:
   - Per-user: `~/.codex/skills/claude-cli/`
   - Per-repo: `<repo>/.codex/skills/claude-cli/`
3) Restart Codex.

Codex discovers skills based on standard locations; per-repo skills take precedence over per-user skills.

## Usage

Trigger examples:

- "Run Claude Code to refactor this module."
- "Invoke Claude for a code review of my current changes."
- "Use Claude in one-time (print) mode to complete this task."
- "Delegate this task to Claude in yolo mode (skip permission prompts)."

### Interactive mode (default)

```
claude
```

### One-time mode (print)

Runs once and exits:

```
claude -p "Summarize recent changes in this repo"
```

### Yolo mode (skip permission prompts)

Use only when explicitly requested:

```
claude -p "Refactor this module" --dangerously-skip-permissions
```

### Session controls (optional)

Documented for convenience; use only when the user asks.

```
claude -c
claude -r "<session-id-or-name>"
claude -r "<session-id-or-name>" --fork-session
```

## Notes

- Default model preference is `sonnet`, but it is configurable via `--model`.
- Output format defaults to text; `--output-format json` is available for scripting.

## References

- Codex CLI: https://developers.openai.com/codex/cli
- Codex skills: https://developers.openai.com/codex/skills
- Codex team config (skill locations): https://developers.openai.com/codex/team-config
- Claude Code CLI: https://code.claude.com/docs/en/cli-reference
