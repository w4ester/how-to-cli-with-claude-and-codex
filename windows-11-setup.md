# How to Run Claude Code on Windows 11

A beginner-friendly, step-by-step guide for installing and running Claude Code CLI on Windows 11.

---

## Official Sources

All information in this guide is sourced from:
- **Setup Guide**: https://code.claude.com/docs/en/setup.md
- **Quickstart**: https://code.claude.com/docs/en/quickstart.md

---

## Glossary: Key Terms Explained

Before we start, let's understand what these terms mean:

### CLI (Command Line Interface)
A text-based way to interact with your computer. Instead of clicking buttons and icons, you type commands. On Windows, you use PowerShell or Command Prompt for this.

### Terminal / Console
The window where you type CLI commands. On Windows 11, this is typically:
- **PowerShell** - Microsoft's powerful command shell (blue icon)
- **Command Prompt** - The older Windows command line (black icon)
- **Windows Terminal** - A modern app that can run both (recommended)

### Node.js
A program that lets you run JavaScript code on your computer (not just in a web browser). Many developer tools, including Claude Code, are built with JavaScript and need Node.js to run.

### npm (Node Package Manager)
A tool that comes with Node.js. Think of it like an "app store" for developer tools. You use npm to download and install programs like Claude Code. When you run `npm install`, it downloads the code and sets it up for you.

### WSL (Windows Subsystem for Linux)
A feature in Windows that lets you run Linux (another operating system) inside Windows. Some developer tools work better in Linux, so WSL gives you that option without needing a separate computer.

### Git
A version control system - it tracks changes to your files over time. Think of it like "track changes" in Microsoft Word, but for all your project files. Git for Windows includes "Git Bash", which gives you a Linux-like terminal on Windows.

### Bash
A type of command shell (like PowerShell, but from the Linux/Unix world). Git Bash lets you use Bash commands on Windows.

### API (Application Programming Interface)
A way for programs to talk to each other. Claude Code uses the Anthropic API to communicate with Claude's AI servers over the internet.

### OAuth
A secure way to log in. Instead of giving your password to every app, OAuth lets you log in through a trusted service (like Anthropic) that then tells the app "yes, this person is who they say they are."

---

## System Requirements

> Source: https://code.claude.com/docs/en/setup.md

| Requirement | What it means |
|-------------|---------------|
| Windows 10 or newer | Your Windows version must be 10 or 11 |
| 4GB+ RAM | Your computer needs at least 4 gigabytes of memory |
| Internet connection | Claude Code talks to servers online, so you need internet |
| WSL or Git for Windows | Windows needs one of these to run Claude Code (explained below) |

**Why WSL or Git for Windows?**
Claude Code was designed to work in Unix-like environments (Linux, Mac). Windows works differently, so you need either WSL or Git Bash to give Claude Code an environment it understands.

---

## Choosing Your Installation Method

You have several options. Here's how to decide:

| If you... | Use this method |
|-----------|-----------------|
| Want the simplest setup | **Method 1: PowerShell native install** |
| Already have Git for Windows | **Method 1 or 3** |
| Already have Node.js installed | **Method 3: npm install** |
| Are comfortable with Linux | **Method 2: WSL** |
| Want to learn command line | Any method - they all teach you! |

---

## Method 1: Native PowerShell Install (Recommended for Beginners)

> Source: https://code.claude.com/docs/en/setup.md

This is the easiest method. It uses a script from Anthropic that handles everything for you.

### Step 1.1: Open PowerShell

**How to open PowerShell on Windows 11:**
1. Press the **Windows key** on your keyboard (or click the Start button)
2. Type `PowerShell`
3. Click on "Windows PowerShell" or "PowerShell"

You'll see a blue window with white text. This is PowerShell!

### Step 1.2: Run the Install Command

Copy and paste this command into PowerShell, then press Enter:

```powershell
irm https://claude.ai/install.ps1 | iex
```

**What does this command mean? Let's break it down:**

| Part | What it does |
|------|--------------|
| `irm` | Short for "Invoke-RestMethod" - downloads something from the internet |
| `https://claude.ai/install.ps1` | The web address of Anthropic's official installation script |
| `|` | The "pipe" symbol - sends the output of one command to another |
| `iex` | Short for "Invoke-Expression" - runs the downloaded script |

So this command: downloads the installer script, then runs it.

### Step 1.3: Wait for Installation

The script will:
1. Check your system
2. Download Claude Code
3. Install it in the right location
4. Set up your PATH (so you can run `claude` from anywhere)

---

## Method 2: Using WSL (Windows Subsystem for Linux)

> Source: https://code.claude.com/docs/en/setup.md

This method installs Claude Code inside a Linux environment on your Windows computer.

### Step 2.1: Install WSL (if you don't have it)

Open PowerShell **as Administrator**:
1. Press Windows key
2. Type `PowerShell`
3. Right-click on "Windows PowerShell"
4. Select "Run as administrator"
5. Click "Yes" when asked

Then run:

```powershell
wsl --install
```

This installs WSL with Ubuntu Linux. Restart your computer when prompted.

### Step 2.2: Open WSL

After restarting:
1. Press Windows key
2. Type `Ubuntu` (or `WSL`)
3. Click to open it

You'll see a terminal that looks different - this is Linux running inside Windows!

### Step 2.3: Install Claude Code in WSL

In the WSL/Ubuntu terminal, paste:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

**What does this command mean?**

| Part | What it does |
|------|--------------|
| `curl` | A program that downloads files from the internet |
| `-fsSL` | Options: fail silently, show errors, follow redirects, be secure |
| `https://claude.ai/install.sh` | The web address of Anthropic's Linux installation script |
| `|` | Pipe - sends the downloaded script to the next command |
| `bash` | Runs the script using the Bash shell |

---

## Method 3: npm Installation

> Source: https://code.claude.com/docs/en/setup.md

This method requires Node.js to be installed first.

### Step 3.1: Install Node.js

**What is Node.js again?**
Node.js lets your computer run JavaScript programs. Claude Code is written in JavaScript, so it needs Node.js to run.

**How to install Node.js:**

1. Go to https://nodejs.org
2. Click the big green button that says "LTS" (Long Term Support - the stable version)
3. Run the downloaded installer (.msi file)
4. Click "Next" through the wizard, keeping all defaults
5. **Important:** Make sure "Add to PATH" is checked
6. Click "Install"
7. Click "Finish"

### Step 3.2: Verify Node.js Installation

Close and reopen PowerShell (important!), then type:

```powershell
node --version
```

You should see something like `v20.10.0`. If you see an error, restart your computer and try again.

Also check npm:

```powershell
npm --version
```

You should see something like `10.2.3`.

### Step 3.3: Install Claude Code with npm

Now you can install Claude Code:

```powershell
npm install -g @anthropic-ai/claude-code
```

**What does this command mean?**

| Part | What it does |
|------|--------------|
| `npm` | Node Package Manager - the app store for JavaScript programs |
| `install` | Tell npm to download and install something |
| `-g` | "Global" - install it so you can use it from any folder |
| `@anthropic-ai/claude-code` | The name of the package (like an app name in an app store) |

**Note:** The `@anthropic-ai/` part is like a username or organization name. It tells npm this package is made by Anthropic (the company that makes Claude).

---

## After Installation: Verify It Worked

> Source: https://code.claude.com/docs/en/setup.md

Run this command to check your installation:

```bash
claude doctor
```

This runs a diagnostic check. If everything is working, you'll see a success message.

---

## First Time: Logging In

> Source: https://code.claude.com/docs/en/quickstart.md

### Step 1: Navigate to a Project Folder

Open PowerShell (or your terminal of choice) and go to a folder where you want to work:

```powershell
cd C:\Users\YourName\Projects
```

**What is `cd`?**
`cd` stands for "change directory" - it moves you to a different folder. A "directory" is just another word for folder.

### Step 2: Start Claude Code

```bash
claude
```

### Step 3: Follow the Login Prompts

The first time you run Claude Code:
1. It will ask how you want to log in
2. A web browser will open automatically
3. Log in to your Anthropic account (or create one)
4. Click "Authorize" to give Claude Code permission
5. Return to your terminal - you're now logged in!

**Your login is saved,** so you won't need to do this every time.

---

## Authentication Options Explained

> Source: https://code.claude.com/docs/en/setup.md

You can use Claude Code with different types of accounts:

### Option A: Claude Console (API Account)
- **What it is:** A developer account at console.anthropic.com
- **Billing:** Pay based on how much you use the API
- **Best for:** Developers who want usage-based pricing
- **Sign up:** https://console.anthropic.com

### Option B: Claude App Subscription
- **What it is:** A subscription to claude.ai (Pro or Max plan)
- **Billing:** Fixed monthly price
- **Best for:** People who also want to use Claude on the web
- **Sign up:** https://claude.ai (then subscribe to Pro or Max)

### Option C: Enterprise (Advanced)
- Through Amazon Bedrock, Google Vertex AI, or Microsoft Foundry
- **Best for:** Large companies with existing cloud contracts

---

## Using Claude Code: Basic Commands

Once you're logged in, here's what you can do:

| What you type | What happens |
|---------------|--------------|
| `claude` | Starts Claude Code |
| `/help` | Shows all available commands |
| `/clear` | Clears the conversation history |
| `Ctrl+C` | Exits Claude Code |
| `/login` | Logs in (if needed) |

**Inside Claude Code, you just type naturally!** Ask questions, give instructions, and Claude will help you with coding tasks.

---

## Updating Claude Code

> Source: https://code.claude.com/docs/en/setup.md

Claude Code updates itself automatically. But you can manually update:

```bash
claude update
```

---

## Troubleshooting Common Issues

### "claude is not recognized"
**What this means:** Your computer doesn't know where to find Claude Code.

**Solutions:**
1. Close your terminal and open a new one
2. Restart your computer
3. Run `claude doctor` to diagnose

### "Permission denied" errors
**What this means:** You don't have permission to install programs in that location.

**Solution:** Run PowerShell as Administrator (right-click > Run as administrator)

### Nothing happens when I run the install command
**What this means:** The download might be blocked.

**Solutions:**
1. Check your internet connection
2. Try a different network (sometimes work/school networks block downloads)
3. Temporarily disable antivirus and try again

---

## Summary: What We Learned

In this guide, you learned:

1. **CLI** - Typing commands instead of clicking buttons
2. **npm** - An "app store" for developer tools
3. **Node.js** - A program that runs JavaScript on your computer
4. **WSL** - Linux running inside Windows
5. **How to install Claude Code** - Using PowerShell, WSL, or npm
6. **How to log in** - Using OAuth through your browser
7. **Basic commands** - Starting, using, and exiting Claude Code

---

## Document Metadata

| Field | Value |
|-------|-------|
| Created | 2025-12-07 |
| Tool Used | Claude Code `Write` tool |
| Project | how-to-cli-with-claude-and-codex |
| Sources | Official Anthropic docs (cited above) |
| Audience | Complete beginners |
