---
name: setup
description: Run this skill once to set up the full Roll the Code bizdev toolkit. Installs all plugins, Firecrawl, and verifies the environment. Invoke with /setup
---

You are the Roll the Code BizDev Toolkit setup agent. Your job is to install everything Anti needs in one go — minimal manual steps.

## OS Detection

Before running any step, detect the operating system by running:

```bash
uname -s 2>/dev/null || echo "Windows"
```

- If output contains `Darwin` → **macOS path**
- If output contains `Linux` → **Linux path** (follow macOS steps, substituting `~/.bashrc` for `~/.zshrc`)
- If command fails or output is `Windows` → **Windows path**

Print at the top: `🖥️ Detected OS: [macOS / Windows / Linux]`

**If you just cloned this repo:** Copy `.env.example` to `.env` and fill in `CLOUDFLARE_API_TOKEN` and `PRODUCT_HUNT_TOKEN`. `.env` is in `.gitignore` — never commit it.

---

## Setup sequence

Run each step in order. Print a clear status line after each step: ✅ Done or ❌ Failed.

---

### Step 1: Verify Claude Code version

```bash
claude --version
```

Print the version. If it fails, tell the user to restart the terminal.

---

### Step 2: Install plugins

Since you cannot run slash commands directly, instruct the user to run them manually inside Claude Code. Print all commands clearly for copy-paste:

```
/plugin marketplace add nextlevelbuilder/ui-ux-pro-max-skill
/plugin install ui-ux-pro-max@ui-ux-pro-max-skill

/plugin marketplace add alirezarezvani/claude-skills
/plugin install marketing-skills@claude-code-skills
/plugin install c-level-skills@claude-code-skills
/plugin install business-growth-skills@claude-code-skills

/plugin marketplace add coreyhaines31/marketingskills
/plugin install marketing-skills@marketingskills

/reload-plugins
```

Print: "Copy-paste these commands into Claude Code one by one. Come back when done."

---

### Step 3: Install system dependencies

#### 3a. Node.js

Check if Node is available:
```bash
node --version
```

**If missing:**

- **macOS:** Run `brew install node`
  - If Homebrew itself is missing: `command -v brew` returns nothing → tell user to install from https://brew.sh then re-run `/setup`
- **Windows:** Tell user to install from https://nodejs.org (LTS version), then re-run `/setup`. Stop here.
  > ⚠️ After install, close and reopen PowerShell. If still not found: `$env:PATH += ";C:\Program Files\nodejs"`

#### 3b. Puppeteer CLI

```bash
npm install -g puppeteer-cli
puppeteer --version
```

- **macOS/Linux:** If `puppeteer` not found after install: `export PATH="$(npm config get prefix)/bin:$PATH"`
- **Windows:** Close and reopen PowerShell. If still not found: `$env:PATH += ";$env:APPDATA\npm"`

#### 3c. uv (Python package runner, required for MCPs)

**macOS/Linux:**
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
source ~/.zshrc   # or ~/.bashrc on Linux
uv --version
```

**Windows (PowerShell):**
```powershell
irm https://astral.sh/uv/install.ps1 | iex
```
After install, either close/reopen PowerShell or run:
```powershell
$env:PATH += ";C:\Users\$env:USERNAME\.local\bin"
```
Verify: `uv --version`

> ⚠️ **Windows Cursor PATH note:** After installing uv, `uvx` is NOT available in Cursor's integrated terminal. Always use full path: `C:\Users\[username]\.local\bin\uvx.exe`

---

### Step 4: Install Firecrawl

```bash
npm --version
```

If npm is not available: "⚠️ npm not found. Install Node.js first, then re-run /setup." Stop here.

```bash
npm install -g firecrawl-cli
```

Prompt the user: "Please paste your Firecrawl API key (get it free at https://firecrawl.dev):"

Wait for input, then:
```bash
firecrawl auth <API_KEY>
firecrawl --version
```

---

### Step 5: Install MCP servers

#### 5a. Reddit MCP

**macOS/Linux:**
```bash
claude mcp remove reddit 2>/dev/null || true
claude mcp add reddit -- uvx mcp-reddit
```

**Windows (PowerShell):**
```powershell
claude mcp remove reddit
claude mcp add reddit -- C:\Users\$env:USERNAME\.local\bin\uvx.exe mcp-reddit
```

Verify in Claude Code (`/mcp`): `reddit · ✔ connected`

---

#### 5b. LinkedIn MCP — Login

⚠️ **This step CANNOT run inside Cursor's integrated terminal.** It opens an interactive browser login.

**macOS:** Open a separate Terminal window — press `Cmd + Space`, type Terminal, press Enter. Run:
```bash
uvx linkedin-scraper-mcp --login
```

**Windows:** Open a separate PowerShell window — press `Win+X → Terminal`. Run:
```powershell
C:\Users\$env:USERNAME\.local\bin\uvx.exe linkedin-scraper-mcp --login
```

A browser window opens. Log into LinkedIn and wait for the profile save confirmation. Then come back.

---

#### 5c. LinkedIn MCP — Register

**macOS/Linux:**
```bash
claude mcp remove linkedin 2>/dev/null || true
claude mcp add linkedin -- uvx linkedin-scraper-mcp
```

**Windows:**
```powershell
claude mcp remove linkedin
claude mcp add linkedin -- C:\Users\$env:USERNAME\.local\bin\uvx.exe linkedin-scraper-mcp
```

Verify: `linkedin · ✔ connected`

---

#### 5d. Product Hunt MCP

Requirements:
- `PRODUCT_HUNT_TOKEN` must be set in `.env` — contact Réka for the real value

**macOS/Linux:**
Copy `.env.example` to `.env` if not done:
```bash
cp .env.example .env
```

**Windows:**
```powershell
Copy-Item .env.example .env
```

Then open `.env` and replace `REPLACE_WITH_YOUR_DEVELOPER_TOKEN`.

Add the MCP — instruct the user to run kakukk, then paste:

> Edit `~/.claude.json` (macOS/Linux) or `C:\Users\[USERNAME]\.claude.json` (Windows).
> Find the "projects" entry for this repo and add to "mcpServers":
> ```json
> "producthunt": {
>   "type": "stdio",
>   "command": "uvx",
>   "args": ["--from", "product-hunt-mcp", "product-hunt-mcp"],
>   "env": {
>     "PRODUCT_HUNT_TOKEN": "PASTE_YOUR_TOKEN_HERE"
>   }
> }
> ```
> On Windows, replace `"command": "uvx"` with `"command": "C:\\Users\\[USERNAME]\\.local\\bin\\uvx.exe"`.

Verify: `producthunt · ✔ connected`

---

#### 5e. Final MCP verification

Run `/mcp`. Expected:
```
linkedin    · ✔ connected
reddit      · ✔ connected
producthunt · ✔ connected
```

If any show ✘ failed: re-run the `claude mcp add` command, then restart Cursor.

---

### Step 6: Deploy to Cloudflare Pages

Load the token from `.env`:

```bash
if [ -f .env ]; then
  export $(grep CLOUDFLARE_API_TOKEN .env | xargs)
fi
```

If `.env` doesn't exist or token is empty, print:
```
⚠️ Cloudflare deployment skipped — no API token found.
To enable: copy .env.example to .env, set CLOUDFLARE_API_TOKEN, re-run /setup.
```
Skip to Step 7.

If token is present:
```bash
CLOUDFLARE_API_TOKEN=$CLOUDFLARE_API_TOKEN npx wrangler pages deploy . --project-name rtc-bizdev
```

Print the deployment URL.

---

### Step 7: Verify skills are loaded

```bash
ls .claude/skills/
```

Expected: `pitch-deck`, `sales-onepager`, `investor-brief`, `html-presentation`, `collaborator-deck`, `business-planning`, `pdf-report`

If any are missing: "Contact Réka to restore missing skills from the repo."

---

### Step 8: kakukk alias

**macOS/Linux:**

Check if alias already exists:
```bash
grep -q "kakukk" ~/.zshrc 2>/dev/null && echo "exists" || echo "missing"
```

If missing, add it:
```bash
echo "alias kakukk='cd /path/to/rtc-bizdev && claude --dangerously-skip-permissions'" >> ~/.zshrc
source ~/.zshrc
```

Replace `/path/to/rtc-bizdev` with the actual absolute path of the repo (detect with `pwd` from inside the repo).

Verify:
```bash
grep kakukk ~/.zshrc
```

**Windows (PowerShell):**

```powershell
if (!(Test-Path $PROFILE)) { New-Item -Path $PROFILE -Force }
Add-Content $PROFILE "`nSet-Alias kakukk 'claude --dangerously-skip-permissions'"
```

Verify:
```powershell
Get-Content $PROFILE | Select-String kakukk
```

Tell the user: "Done. From now on, type `kakukk` in any terminal to launch Claude Code in autonomous mode."

---

### Step 9: Final status report

Print a clean summary (adjust ✅/❌ based on what actually succeeded):

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  Roll the Code BizDev Toolkit Setup
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ Claude Code      — verified
✅ Node.js          — verified
✅ Puppeteer CLI    — installed
✅ uv               — installed
✅ UI/UX Pro Max    — installed
✅ Marketing Skills — installed
✅ C-Level Skills   — installed
✅ Business Growth  — installed
✅ Firecrawl        — installed & authenticated
✅ Reddit MCP       — connected
✅ LinkedIn MCP     — connected
✅ Product Hunt MCP — connected
✅ Cloudflare Pages — deployed
✅ Project skills   — all 7 present
✅ kakukk alias     — added
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
You're ready. Try: "Create a sales one-pager for Roll the Code targeting enterprise innovation hubs."
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

If anything failed, list what needs to be fixed and offer to retry that step.
