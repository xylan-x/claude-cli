---
name: claude-cli
description: "Use Claude Code CLI to communicate with Claude Code for any coding task in the current repo: refactor, review, delegate tasks, simplify code, or answer implementation questions. Trigger when the user asks to run Claude/Claude Code/CC."
---

# Claude CLI

## Overview

Run Claude Code CLI in the current repo to communicate with Claude Code for coding tasks. Default to one-time (-p) unless the user asks for an interactive session or yolo mode.

## Quick Start (one-time default)

- Run once and exit:
  - `claude -p "Summarize recent changes in this repo"`
- Pipe input:
  - `git diff | claude -p "Review these changes"`

Login note:
- Assume the user is already logged in.
- If not, run `claude` and use `/login`.

## Yolo mode (skip permission prompts)

Use only when the user explicitly asks to skip permission prompts.

- Example (one-time + yolo):
  - `claude -p "Refactor this module" --dangerously-skip-permissions`
- Warning: this bypasses safety prompts. Confirm the user asked for it.

## Interactive mode (optional)

Use only when the user explicitly asks for an interactive session.

- Start an interactive session in the current repo:
  - `claude`
- Start interactive with an initial prompt:
  - `claude "Refactor this module for clarity"`

## Common options

- Model:
  - Prefer `--model sonnet` unless the user specifies another model.
- Output format:
  - Default text output.
  - Use `--output-format json` or `--output-format stream-json` only if the user asks for machine-readable output.
- Working directory:
  - Run in the current repo. Do not add extra directories unless requested.

## Session controls (optional)

Document these options but do not use them unless the user asks.

- Continue the last session in this directory:
  - `claude -c`
  - Benefit: keep context without restarting.
- Resume a specific session:
  - `claude -r "<session-id-or-name>"`
  - Benefit: return to a named or previous session.
- Fork a session:
  - `claude -r "<session-id-or-name>" --fork-session`
  - Benefit: branch from a previous session without overwriting it.
