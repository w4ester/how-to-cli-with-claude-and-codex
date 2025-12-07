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

### Create a Default UNIX User Account:

Ubuntu will ask you to create a user account. **This is separate from your Windows account** - it's your identity inside the Linux environment.

**When you see:** `Enter new UNIX username:`
- Type a username (lowercase, no spaces)
- Examples: `will`, `dev`, `coder`
- Press Enter

**When you see:** `New password:`
- Type a password you'll remember
- **IMPORTANT: You will NOT see ANY characters as you type!**
  - No dots (•••)
  - No asterisks (***)
  - The cursor won't move
  - **This is completely normal** - it's a Linux security feature
- Just type your password "blindly" and press Enter

**When you see:** `Retype new password:`
- Type the same password again (still invisible)
- Press Enter

**Success looks like:**
```
username@DESKTOP-XXXXXX:~$
```

This is your Linux command prompt. **You now have Linux running inside Windows!**

---

## Step 1.2: Install Node.js (Required for both tools)

**What is Node.js?** A program that runs JavaScript on your computer. Both Claude Code and Codex are built with JavaScript.

---

### BEFORE YOU START: How to Copy and Paste in Ubuntu Terminal

The Ubuntu terminal works differently than regular Windows apps!

**To copy a command from this guide:**
1. Use your mouse to highlight the command text
2. Hold down the **Ctrl** key on your keyboard and press the **C** key
   (This copies the text - nothing visible happens, that's normal)

**To paste into the Ubuntu terminal (choose one method):**

| Method | How to do it |
|--------|--------------|
| **Easiest** | Move your mouse into the Ubuntu window and **click the RIGHT mouse button** |
| **Keyboard** | Hold **Ctrl** AND **Shift** together, then press **V** |

**Why doesn't the normal paste work?**
In Linux terminals, the normal paste shortcut (Ctrl and V together) does something else. That's why you need to either right-click or add the Shift key.

---

### Run these commands one at a time:

**For each command below, do this:**
1. Highlight the command text with your mouse
2. Press **Ctrl + C** (hold Ctrl, tap C) to copy
3. Click inside your Ubuntu terminal window
4. **Right-click your mouse** to paste the command
5. Press the **Enter** key to run it
6. **Wait** for it to finish (you'll see your prompt come back) before doing the next one

---

### COMMAND 1: Update the package list

**What this does:** Downloads the latest list of available software (like refreshing an app store).

**The command to copy:**
```
sudo apt update
```

**Step-by-step:**
1. Use your mouse to highlight the text `sudo apt update` above
2. Hold the **Ctrl** key and tap the **C** key (this copies it)
3. Click inside your Ubuntu terminal window
4. **Right-click** your mouse (the command appears)
5. Press the **Enter** key

**What you'll see:**
```
[sudo] password for yourname:
```

**What to do:**
- Type your password (remember: NO characters will appear - that's normal!)
- Press **Enter**
- Wait for text to scroll by (this is normal)
- **You're done when you see** your prompt again, like: `yourname@DESKTOP-XXXXX:~$`

---

### COMMAND 2: Install nvm (Node Version Manager)

**What this does:** Installs a tool that helps you install Node.js.

**The command to copy:**
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
```

**Step-by-step:**
1. Highlight the entire command above (it's long - make sure you get all of it)
2. Hold **Ctrl** and tap **C**
3. Click inside your Ubuntu terminal
4. **Right-click** to paste
5. Press **Enter**

**What you'll see:**
- Text downloading and installing
- Eventually a message about "nvm" being installed
- **You're done when you see** your prompt again: `yourname@DESKTOP-XXXXX:~$`

---

### COMMAND 3: Reload your terminal settings

**What this does:** Tells your terminal to recognize the nvm tool you just installed.

**The command to copy:**
```
source ~/.bashrc
```

**Step-by-step:**
1. Highlight `source ~/.bashrc`
2. Hold **Ctrl** and tap **C**
3. Click inside your Ubuntu terminal
4. **Right-click** to paste
5. Press **Enter**

**What you'll see:**
- Probably nothing! That's normal.
- **You're done when you see** your prompt again: `yourname@DESKTOP-XXXXX:~$`

---

### COMMAND 4: Install Node.js

**What this does:** Downloads and installs Node.js version 20 (the stable version).

**The command to copy:**
```
nvm install 20
```

**Step-by-step:**
1. Highlight `nvm install 20`
2. Hold **Ctrl** and tap **C**
3. Click inside your Ubuntu terminal
4. **Right-click** to paste
5. Press **Enter**

**What you'll see:**
```
Downloading and installing node v20.x.x...
Now using node v20.x.x (npm v10.x.x)
```
- **You're done when you see** your prompt again: `yourname@DESKTOP-XXXXX:~$`

---

### COMMAND 5: Verify Node.js is installed

**What this does:** Checks that Node.js installed correctly.

**The command to copy:**
```
node --version
```

**Step-by-step:**
1. Highlight `node --version`
2. Hold **Ctrl** and tap **C**
3. Click inside your Ubuntu terminal
4. **Right-click** to paste
5. Press **Enter**

**What you should see:**
```
v20.x.x
```
(The x's will be numbers, like `v20.10.0`)

**If you see a version number, Node.js is installed!**

---

### COMMAND 6: Verify npm is installed

**What this does:** Checks that npm (Node Package Manager) installed correctly. npm comes bundled with Node.js.

**The command to copy:**
```
npm --version
```

**Step-by-step:**
1. Highlight `npm --version`
2. Hold **Ctrl** and tap **C**
3. Click inside your Ubuntu terminal
4. **Right-click** to paste
5. Press **Enter**

**What you should see:**
```
10.x.x
```
(The x's will be numbers, like `10.2.3`)

**If you see a version number, npm is installed!**

---

## Step 1.3: Install Git (Required for version control)

---

### COMMAND 7: Install Git

**What this does:** Installs Git, a tool for tracking changes to your code.

**The command to copy:**
```
sudo apt install git -y
```

**Step-by-step:**
1. Highlight `sudo apt install git -y`
2. Hold **Ctrl** and tap **C**
3. Click inside your Ubuntu terminal
4. **Right-click** to paste
5. Press **Enter**

**What you'll see:**
- It might ask for your password (type it, press Enter)
- Text will scroll showing the installation
- **You're done when you see** your prompt again: `yourname@DESKTOP-XXXXX:~$`

---

### COMMAND 8: Verify Git is installed

**What this does:** Checks that Git installed correctly.

**The command to copy:**
```
git --version
```

**Step-by-step:**
1. Highlight `git --version`
2. Hold **Ctrl** and tap **C**
3. Click inside your Ubuntu terminal
4. **Right-click** to paste
5. Press **Enter**

**What you should see:**
```
git version 2.x.x
```

**If you see a version number, Git is installed!**

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
