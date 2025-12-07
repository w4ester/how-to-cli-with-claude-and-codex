# Step-by-Step Directions: Claude Code & Codex CLI on Windows

This guide provides exact, copy-paste commands to install and run both Claude Code (Anthropic) and Codex CLI (OpenAI) on Windows 11.

---

## Official Sources

| Tool | Documentation |
|------|---------------|
| Claude Code | https://code.claude.com/docs/en/setup.md |
| Claude Code Quickstart | https://code.claude.com/docs/en/quickstart.md |
| OpenAI Codex CLI | https://github.com/openai/codex |
| Codex Quickstart | https://developers.openai.com/codex/quickstart/ |

---

## Important: Windows Requirements

Both tools work best with a Unix-like environment. On Windows, you have two options:

| Option | What it is | Recommendation |
|--------|------------|----------------|
| **WSL** | Windows Subsystem for Linux - runs Linux inside Windows | **Recommended** - Best compatibility |
| **Git Bash** | Comes with Git for Windows - provides bash shell | Good alternative if you don't want WSL |

---

# PART 1: INSTALL PREREQUISITES

## Step 1.1: Install WSL (Recommended)

**What is WSL?** Windows Subsystem for Linux lets you run a real Linux environment inside Windows. Both Claude Code and Codex work better in Linux.

### Open PowerShell as Administrator:
1. Press `Windows key`
2. Type `PowerShell`
3. Right-click "Windows PowerShell"
4. Click "Run as administrator"
5. Click "Yes" when prompted

### Run this command:
```powershell
wsl --install
```

**What this does:**
- Downloads and installs WSL 2
- Installs Ubuntu Linux as your default distribution
- Takes 5-10 minutes depending on internet speed

### Restart your computer when prompted.

### After restart, set up Ubuntu:
1. Press `Windows key`
2. Type `Ubuntu`
3. Click to open it
4. Wait for "Installing, this may take a few minutes..."
5. Create a username (lowercase, no spaces)
6. Create a password (you won't see it as you type - that's normal)

**You now have Linux running inside Windows!**

---

## Step 1.2: Install Node.js (Required for both tools)

**What is Node.js?** A program that runs JavaScript on your computer. Both Claude Code and Codex are built with JavaScript.

### In your Ubuntu/WSL terminal, run these commands one at a time:

```bash
# Update package list (like refreshing an app store)
sudo apt update
```

```bash
# Install Node.js version manager (nvm)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
```

```bash
# Reload your shell configuration
source ~/.bashrc
```

```bash
# Install Node.js version 20 (LTS = Long Term Support = stable)
nvm install 20
```

```bash
# Verify Node.js is installed
node --version
```
You should see something like `v20.x.x`

```bash
# Verify npm is installed
npm --version
```
You should see something like `10.x.x`

---

## Step 1.3: Install Git (Required for version control)

```bash
# Install git
sudo apt install git -y
```

```bash
# Verify git is installed
git --version
```

---

# PART 2: INSTALL CLAUDE CODE

## Step 2.1: Install Claude Code

**Source:** https://code.claude.com/docs/en/setup.md

### In your Ubuntu/WSL terminal, run:

```bash
# Install Claude Code globally using npm
npm install -g @anthropic-ai/claude-code
```

**What this command does:**
| Part | Meaning |
|------|---------|
| `npm` | Node Package Manager - downloads and installs packages |
| `install` | The action to perform |
| `-g` | Global - install so you can use it from any folder |
| `@anthropic-ai/claude-code` | The package name (like an app name) |

### Verify installation:

```bash
claude --version
```

You should see a version number.

---

## Step 2.2: Authenticate Claude Code

### Navigate to a project folder:

```bash
# Go to your home directory
cd ~

# Create a projects folder (if you don't have one)
mkdir -p projects

# Go into it
cd projects

# Create a test project
mkdir test-claude
cd test-claude
```

### Start Claude Code:

```bash
claude
```

### Follow the authentication prompts:
1. Claude Code will display a URL
2. A browser may open automatically (or copy the URL)
3. Log in to your Anthropic account at https://console.anthropic.com
4. Click "Authorize"
5. Return to your terminal

**You're now logged in!** Your credentials are saved for future sessions.

---

## Step 2.3: Test Claude Code

In the Claude Code session, try typing:

```
What files are in this directory?
```

Claude will use its tools to check and respond.

### To exit Claude Code:
Press `Ctrl+C` or type `/exit`

---

# PART 3: INSTALL OPENAI CODEX CLI

## Step 3.1: Install Codex CLI

**Source:** https://github.com/openai/codex

**Important Note:** Windows support for Codex is experimental. This is why we installed WSL first - it provides the Linux environment Codex expects.

### In your Ubuntu/WSL terminal, run:

```bash
# Install Codex CLI globally using npm
npm install -g @openai/codex
```

**What this command does:**
| Part | Meaning |
|------|---------|
| `npm` | Node Package Manager |
| `install` | Download and set up the package |
| `-g` | Global installation |
| `@openai/codex` | The OpenAI Codex package |

### Verify installation:

```bash
codex --version
```

---

## Step 3.2: Authenticate Codex CLI

**Source:** https://developers.openai.com/codex/quickstart/

You have two authentication options:

### Option A: ChatGPT Account (Recommended)

**Requirements:** ChatGPT Plus, Pro, Team, Business, Edu, or Enterprise subscription

```bash
# Start Codex
codex
```

1. Select "Sign in with ChatGPT" when prompted
2. A browser will open
3. Log in to your ChatGPT account
4. Authorize the CLI
5. Return to terminal

### Option B: API Key

**Requirements:** OpenAI API account with credits at https://platform.openai.com

```bash
# Set your API key (replace with your actual key)
export OPENAI_API_KEY="sk-your-api-key-here"
```

```bash
# Configure Codex to use API key
codex --config preferred_auth_method="apikey"
```

To make the API key permanent, add it to your shell profile:

```bash
# Open your bash profile
nano ~/.bashrc
```

Add this line at the bottom:
```bash
export OPENAI_API_KEY="sk-your-api-key-here"
```

Save: Press `Ctrl+X`, then `Y`, then `Enter`

```bash
# Reload your profile
source ~/.bashrc
```

---

## Step 3.3: Test Codex CLI

```bash
# Start Codex
codex
```

Try asking it to do something:
```
List the files in this directory
```

### To exit Codex:
Press `Ctrl+C` or type `exit`

---

# PART 4: QUICK REFERENCE CARD

## Starting the Tools

| Tool | Command | What it does |
|------|---------|--------------|
| Claude Code | `claude` | Starts Claude Code CLI |
| Codex | `codex` | Starts OpenAI Codex CLI |

## Common Commands Inside Claude Code

| Command | What it does |
|---------|--------------|
| `/help` | Shows all available commands |
| `/clear` | Clears conversation history |
| `/login` | Re-authenticate if needed |
| `Ctrl+C` | Exit Claude Code |

## Common Commands Inside Codex

| Command | What it does |
|---------|--------------|
| `exit` | Exit Codex |
| `Ctrl+C` | Force exit |

## Useful Terminal Commands

| Command | What it does | Example |
|---------|--------------|---------|
| `cd` | Change directory | `cd ~/projects` |
| `ls` | List files | `ls -la` |
| `pwd` | Print working directory | `pwd` |
| `mkdir` | Make directory | `mkdir my-project` |

---

# PART 5: WORKFLOW - USING BOTH TOOLS

## Typical Workflow

1. **Open WSL/Ubuntu terminal**
   - Press `Windows key`, type `Ubuntu`, press `Enter`

2. **Navigate to your project**
   ```bash
   cd ~/projects/my-project
   ```

3. **Initialize git (if new project)**
   ```bash
   git init
   ```

4. **Start your preferred CLI**
   ```bash
   # For Claude Code
   claude

   # OR for Codex
   codex
   ```

5. **Work on your code**
   - Ask questions
   - Request file edits
   - Run commands
   - Review changes

6. **Commit your changes**
   ```bash
   git add .
   git commit -m "Description of changes"
   ```

---

# PART 6: TROUBLESHOOTING

## "Command not found" after installation

**Cause:** Terminal doesn't know where the program is installed.

**Solution:** Reload your shell:
```bash
source ~/.bashrc
```

Or close and reopen your terminal.

---

## WSL won't start

**Solution 1:** Enable virtualization in BIOS
- Restart computer
- Enter BIOS (usually F2, F12, or Del during startup)
- Find "Virtualization" or "VT-x" and enable it

**Solution 2:** Enable Windows features
```powershell
# Run in PowerShell as Administrator
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```
Then restart.

---

## Authentication fails

**For Claude Code:**
```bash
# Log out and try again
claude logout
claude
```

**For Codex:**
```bash
# Reset to ChatGPT auth
codex --config preferred_auth_method="chatgpt"
codex
```

---

## npm install fails with permission errors

**Never use `sudo npm install -g`** - this causes more problems.

**Solution:** Reinstall with nvm (which handles permissions correctly):
```bash
# Uninstall current Node
nvm uninstall node

# Reinstall
nvm install 20
nvm use 20
```

---

## Can't paste in Ubuntu/WSL terminal

**Solution:** Right-click to paste (instead of Ctrl+V)

Or enable Ctrl+V:
1. Right-click the terminal title bar
2. Click "Properties"
3. Check "Use Ctrl+Shift+C/V as Copy/Paste"

---

# PART 7: COMPARISON - CLAUDE CODE vs CODEX

| Feature | Claude Code | Codex |
|---------|-------------|-------|
| **Company** | Anthropic | OpenAI |
| **AI Model** | Claude (Opus, Sonnet) | GPT-4 |
| **Install Command** | `npm install -g @anthropic-ai/claude-code` | `npm install -g @openai/codex` |
| **Start Command** | `claude` | `codex` |
| **Auth Method** | Anthropic Console or API key | ChatGPT account or API key |
| **Windows Support** | WSL or Git Bash required | WSL recommended (experimental) |
| **Subscription** | Console billing or Claude Pro/Max | ChatGPT Plus/Pro or API credits |

---

## Document Metadata

| Field | Value |
|-------|-------|
| Created | 2025-12-07 |
| Tools Used | `WebSearch` tool, `WebFetch` tool, `Write` tool |
| Sources | Official Anthropic and OpenAI documentation |
| Verified | Yes - against official docs |

---

*This guide was created using Claude Code to research official documentation and compile step-by-step instructions.*
