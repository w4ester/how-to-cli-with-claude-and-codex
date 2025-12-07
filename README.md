# How to CLI with Claude Code & OpenAI Codex

A beginner-friendly guide to installing and using AI coding assistants (Claude Code and OpenAI Codex CLI) on Windows 11.

## What's This Project?

This is a learning resource created **with** Claude Code to teach you **how to use** Claude Code (and Codex). Meta, right?

Every step is documented, including:
- Which tools Claude Code used
- What each command means
- Common errors and how to fix them

## Quick Start

**Want to install Claude Code or Codex on Windows?** Start here:

| Guide | Description |
|-------|-------------|
| [directions.md](directions.md) | Step-by-step commands for both tools |
| [windows-11-setup.md](windows-11-setup.md) | Detailed Windows 11 setup with explanations |

## What's In This Repo?

| File | What it contains |
|------|------------------|
| `README.md` | You're reading it |
| `directions.md` | Copy-paste installation commands for Windows |
| `windows-11-setup.md` | Beginner-friendly guide explaining every term |
| `build-plan.md` | Git history + Claude Code tools documentation |
| `features.json` | Feature checklist for testing |

## Prerequisites

- Windows 10 or 11
- Internet connection
- One of these accounts:
  - **For Claude Code:** [Anthropic Console](https://console.anthropic.com) or [Claude Pro/Max](https://claude.ai)
  - **For Codex:** [ChatGPT Plus/Pro](https://chat.openai.com) or [OpenAI API](https://platform.openai.com)

## Installation Summary

### Claude Code
```bash
# In WSL/Ubuntu terminal
npm install -g @anthropic-ai/claude-code
claude
```

### OpenAI Codex
```bash
# In WSL/Ubuntu terminal
npm install -g @openai/codex
codex
```

**Note:** Both tools require WSL (Windows Subsystem for Linux) on Windows. See [directions.md](directions.md) for full setup.

## Learn How Claude Code Works

Check out [build-plan.md](build-plan.md) for detailed documentation on:
- Every tool Claude Code can use (Bash, Read, Write, Edit, etc.)
- What each tool does and when to use it
- Real examples from building this repo

## Troubleshooting

### WSL "Catastrophic failure"
This is a known Windows bug. Try these fixes:

1. Enable Windows features first:
   - Press `Win`, search "Turn Windows features on or off"
   - Enable: Virtual Machine Platform, Windows Hypervisor Platform, Windows Subsystem for Linux
   - Restart and try again

2. Use winget: `winget install --id Microsoft.WSL -e`

3. Install from Microsoft Store instead

See [directions.md](directions.md) for more troubleshooting tips.

## How This Repo Was Built

This entire repo was created using Claude Code. Every commit message documents:
- What was done
- Which tools were used
- Sources consulted

Run `git log` to see the full history with detailed comments.

## Contributing

Found an error? Have a better explanation? PRs welcome!

## Sources

- [Claude Code Official Docs](https://code.claude.com/docs/en/setup.md)
- [OpenAI Codex GitHub](https://github.com/openai/codex)
- [Codex Quickstart](https://developers.openai.com/codex/quickstart/)

---

*Built with Claude Code (Opus 4.5) - December 2025*
