# Build Plan - How to CLI with Claude and Codex

This document tracks our git history with detailed comments about what was built and which tools were used.

---

## Git Commit History

| Hash | Date | Description | Tools Used |
|------|------|-------------|------------|
| `cb0f36e` | 2025-12-07 | Initial commit: Project setup with features.json, build-plan.md, and Windows 11 setup guide | `git init` (Bash tool), `Write` tool for file creation |

---

## Detailed Commit Log

### Commit 1: Initial Project Setup
- **Hash:** `cb0f36e`
- **Date:** 2025-12-07
- **Author:** Claude Code (Opus 4.5) + User

**What was done:**
1. Initialized git repository using `Bash` tool with `git init` command
2. Created `features.json` using `Write` tool - contains all features to test with `tested: false` flags
3. Created `build-plan.md` using `Write` tool - this file for tracking git history
4. Created `windows-11-setup.md` using `Write` tool - instructions for running Claude Code on Windows 11

**Tools Used by Claude Code:**
- `TodoWrite` - To plan and track tasks
- `Bash` - To run `git init` and `git commit` commands
- `Write` - To create new files (features.json, build-plan.md, windows-11-setup.md)

---

## How to Update This Document

After each significant change:
1. Make your changes
2. Create a git commit with detailed message
3. Run `git log --oneline -1` to get the hash
4. Add a new row to the table above
5. Add detailed notes in a new section below

---

## Feature Verification Commits

*As features from features.json are tested and verified, their commits will be logged here:*

| Feature ID | Hash | Date | Verification Notes |
|------------|------|------|-------------------|
| - | - | - | *No features verified yet* |

---

## Claude Code Tools Explained

This section provides detailed explanations of the tools Claude Code uses to help you with tasks. Understanding these tools helps you understand what Claude Code is doing and why.

### Quick Reference Table

| Tool | What it does | When to use it |
|------|--------------|----------------|
| `Bash` | Runs terminal commands | Git operations, scripts, installs |
| `Write` | Creates/overwrites files | New files from scratch |
| `Edit` | Surgical find-and-replace | Modifying existing files |
| `Read` | Shows file contents | Before editing, understanding code |
| `TodoWrite` | Tracks task progress | Multi-step tasks |
| `Task` | Spawns specialist agents | Research, exploration, documentation |

---

### Bash Tool

**What it does:** The Bash tool lets Claude Code execute shell commands on your computer. Claude types a command (like `git init`) and your computer runs it, then shows the output. It's like Claude typing directly into your terminal.

**Common uses:**
- Git operations (`git init`, `git add`, `git commit`, `git push`)
- Running scripts (`npm install`, `python script.py`)
- Checking system info (`node --version`, `pwd`)
- Creating directories (`mkdir`)

**Parameters Claude can set:**
| Parameter | Required | Description |
|-----------|----------|-------------|
| `command` | Yes | The command to run |
| `timeout` | No | How long to wait (max 10 minutes) |
| `run_in_background` | No | For long-running tasks |
| `description` | No | Short description of what the command does |

**Limitations:** Claude should NOT use Bash for reading/editing files - there are dedicated tools (`Read`, `Edit`, `Write`) that work better and safer for file operations.

**Example usage in this project:**
```
Tool: Bash
Command: git init
Description: Initialize git repository
Result: Initialized empty Git repository in /Users/willf/how-to-cli-with-claude-and-codex/.git/
```

---

### Write Tool

**What it does:** The Write tool creates a brand new file or completely overwrites an existing one. Claude provides two things: the full file path and the entire content for the file.

**Important behavior:** This tool OVERWRITES everything - it doesn't append or merge. If the file exists, the old content is completely replaced. That's why Claude should use `Read` first on existing files to see what's there before deciding to use Write.

**Parameters:**
| Parameter | Required | Description |
|-----------|----------|-------------|
| `file_path` | Yes | Absolute path to the file (e.g., `/Users/name/project/file.txt`) |
| `content` | Yes | The entire content to write to the file |

**Best for:**
- Creating new files from scratch
- Generating configuration files
- Writing new documentation

**Example usage in this project:**
```
Tool: Write
File: /Users/willf/how-to-cli-with-claude-and-codex/features.json
Content: [entire JSON content]
Result: File created successfully
```

---

### Edit Tool

**What it does:** The Edit tool does surgical find-and-replace operations in files. Claude provides the exact text to find (`old_string`) and what to replace it with (`new_string`).

**Critical rule:** The `old_string` must be UNIQUE in the file, or the edit fails. If there are multiple matches, Claude either needs to include more surrounding context to make it unique, or use `replace_all: true` to change all occurrences.

**Parameters:**
| Parameter | Required | Description |
|-----------|----------|-------------|
| `file_path` | Yes | Absolute path to the file |
| `old_string` | Yes | Exact text to find (must be unique unless using replace_all) |
| `new_string` | Yes | Text to replace it with |
| `replace_all` | No | Set to `true` to replace ALL occurrences |

**Why it's better than Write for existing files:** Claude only changes what needs changing - the rest of the file stays exactly the same. This is much safer for existing code and prevents accidental data loss.

**Example usage in this project:**
```
Tool: Edit
File: /Users/willf/how-to-cli-with-claude-and-codex/build-plan.md
Old string: "- **Hash:** *will be updated after commit*"
New string: "- **Hash:** `cb0f36e`"
Result: File updated successfully
```

---

### Read Tool

**What it does:** The Read tool shows Claude what's inside a file. Claude gives it a file path, and it returns the content with line numbers (similar to `cat -n` in terminal).

**Parameters:**
| Parameter | Required | Description |
|-----------|----------|-------------|
| `file_path` | Yes | Absolute path to the file |
| `offset` | No | Skip first N lines (for huge files) |
| `limit` | No | Only read N lines (for huge files) |

**What it can read:**
- Code files (any programming language)
- Text files (markdown, JSON, config files)
- Images (Claude is multimodal and can see images!)
- PDFs (extracts text and visual content)
- Jupyter notebooks (shows all cells with outputs)

**Important rule:** Claude MUST read a file before editing it - the Edit tool will fail if Claude hasn't read the file first in the conversation. This prevents Claude from blindly modifying files without understanding them.

**Example usage in this project:**
```
Tool: Read
File: /Users/willf/how-to-cli-with-claude-and-codex/build-plan.md
Result: [file content with line numbers]
```

---

### TodoWrite Tool

**What it does:** The TodoWrite tool creates and updates a visible task list that both Claude and the user can see. It helps track progress on multi-step tasks.

**Each todo item has:**
| Field | Description | Example |
|-------|-------------|---------|
| `content` | What needs to be done (imperative) | "Create features.json file" |
| `activeForm` | Present tense description | "Creating features.json file" |
| `status` | Current state | `pending`, `in_progress`, or `completed` |

**Why Claude uses it:**
1. Shows YOU progress in real-time
2. Helps Claude remember all steps in complex tasks
3. Prevents forgetting tasks
4. Demonstrates thoroughness

**Rules Claude follows:**
- Only ONE task should be `in_progress` at a time
- Mark tasks `completed` IMMEDIATELY when done (not in batches)
- Create specific, actionable items
- Break complex tasks into smaller steps

**Example usage in this project:**
```
Tool: TodoWrite
Todos:
1. [completed] Initialize git repository
2. [completed] Create initial commit with project description
3. [completed] Create features.json file with feature tracking
4. [completed] Create build-plan.md for git hash tracking
5. [completed] Create Windows 11 Claude Code setup instructions
```

---

### Task Tool

**What it does:** The Task tool launches a separate AI "agent" to handle specific jobs. It's like Claude delegating work to a specialist who can focus deeply on one thing.

**Available agent types:**
| Agent Type | What it does | When to use |
|------------|--------------|-------------|
| `Explore` | Searches and explores codebases | Finding files, understanding structure |
| `Plan` | Designs implementation strategies | Complex features needing architecture |
| `claude-code-guide` | Looks up Claude Code documentation | Questions about Claude Code features |
| `general-purpose` | Complex multi-step research | Open-ended investigation |

**How it works:**
1. Claude gives the agent a detailed prompt describing the task
2. The agent works autonomously (searching, reading, analyzing)
3. The agent reports back with findings
4. Claude uses those findings to help you

**Parameters:**
| Parameter | Required | Description |
|-----------|----------|-------------|
| `prompt` | Yes | Detailed task description for the agent |
| `subagent_type` | Yes | Which type of agent to use |
| `description` | Yes | Short (3-5 word) description |
| `run_in_background` | No | Run while Claude does other work |

**Example usage in this project:**
```
Tool: Task
Subagent type: claude-code-guide
Description: Get Claude Code docs
Prompt: "I need to find the official documentation for installing Claude Code CLI..."
Result: [Official documentation with source URLs]
```

---

## Other Tools Available (Not Used Yet in This Project)

These tools exist but weren't needed for our initial setup:

| Tool | What it does |
|------|--------------|
| `Glob` | Find files by pattern (e.g., `**/*.js` finds all JavaScript files) |
| `Grep` | Search for text patterns across files |
| `WebFetch` | Fetch and analyze content from a URL |
| `WebSearch` | Search the web for current information |
| `AskUserQuestion` | Ask the user for clarification or choices |
| `NotebookEdit` | Edit Jupyter notebook cells |

---

*This tools reference was added to help future sessions understand what Claude Code can do and how it works.*

