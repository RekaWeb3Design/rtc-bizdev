---
name: setup
description: Run this skill once to set up the full Roll the Code bizdev toolkit. Installs all plugins, Firecrawl, and verifies the environment. Invoke with /setup
---

You are the Roll the Code BizDev Toolkit setup agent. Your job is to install everything Anti needs in one go — minimal manual steps: after a fresh clone, copy `.env.example` to `.env` and set `CLOUDFLARE_API_TOKEN`, and provide a Firecrawl API key when prompted.

## Setup sequence

Run each step in order. Print a clear status line after each step: ✅ Done or ❌ Failed.

**If you just cloned this repo:** Copy `.env.example` to `.env` (same folder as the repo root), open `.env`, and replace the placeholder with your real Cloudflare API token for `CLOUDFLARE_API_TOKEN`. `.env` is in `.gitignore` and must never be committed to GitHub.

### Step 1: Verify Claude Code version
Run: `claude --version`
Print the version. If it fails, tell the user to restart the terminal.

### Step 2: Install plugins

Run these commands one by one using the Claude Code plugin system. Since you cannot run slash commands directly, instruct the user to run them manually — but print all commands clearly so they can copy-paste in sequence:

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

### Step 3: Install system dependencies

Run each check and install in order:

**3a. Node.js**
```bash
node --version
```
If missing or command not recognized, print:
"⚠️ Node.js not found. Install from https://nodejs.org (LTS version), then re-run /setup"
Stop here.

> ⚠️ **Windows PATH note:** If the command is not recognized after install, close and reopen PowerShell.
> If still not working, run: `$env:PATH += ";C:\Program Files\nodejs"`

**3b. Puppeteer CLI**
```bash
npm install -g puppeteer-cli
```
Verify with:
```bash
puppeteer --version
```

> ⚠️ **Windows PATH note:** If the command is not recognized after install, close and reopen PowerShell.
> If still not working, run: `$env:PATH += ";$env:APPDATA\npm"`

**3c. uv (Python package installer)**
Install via PowerShell:
```powershell
irm https://astral.sh/uv/install.ps1 | iex
```
After install, the user must either close and reopen the terminal, OR run:
```powershell
$env:PATH += ";C:\Users\$env:USERNAME\.local\bin"
```
Verify with:
```bash
uv --version
```

> ⚠️ **Windows PATH note:** If the command is not recognized after install, close and reopen PowerShell.
> If still not working, run: `$env:PATH += ";C:\Users\[username]\.local\bin"`

### Step 4: Install Firecrawl

Run the following bash commands:

```bash
# Check if npm is available
npm --version
```

If npm is not available, print:
"⚠️ npm not found. Install Node.js from https://nodejs.org (LTS version), then re-run /setup"
Stop here.

If npm is available, continue:

```bash
# Install Firecrawl CLI globally
npm install -g firecrawl-cli
```

Then prompt the user:
"Please paste your Firecrawl API key (get it free at https://firecrawl.dev):"

Wait for input, then run:
```bash
firecrawl auth <API_KEY>
```

Verify with:
```bash
firecrawl --version
```

### Step 5: Install MCP servers

⚠️ **IMPORTANT — Windows PATH issue:**
After installing uv, the `uvx` command is NOT automatically available in Cursor's integrated terminal. You must always use the full path:
`C:\Users\[username]\.local\bin\uvx.exe`

Replace `[username]` with your actual Windows username (e.g. "User", "Anti").
To find your username, run: `$env:USERNAME`

---

**5a. Install uv (required for Reddit and LinkedIn MCPs)**

Run in PowerShell:
```powershell
irm https://astral.sh/uv/install.ps1 | iex
```

Close and reopen PowerShell after installation.
Verify with full path:
```powershell
C:\Users\$env:USERNAME\.local\bin\uvx.exe --version
```

If this works, uv is correctly installed.

⚠️ Do NOT use just "uvx" in Cursor's terminal — it will not be found.
Always use the full path: `C:\Users\[username]\.local\bin\uvx.exe`

---

**5b. Reddit MCP**

Requirements:
- You must be logged into Reddit in your browser before using this MCP
- No API key needed — uses Reddit's public API

Run in PowerShell (inside the rtc-bizdev folder):
```powershell
claude mcp remove reddit
claude mcp add reddit -- C:\Users\$env:USERNAME\.local\bin\uvx.exe mcp-reddit
```

Verify in Claude Code (kakukk → /mcp):
`reddit · ✔ connected`

---

**5c. LinkedIn MCP — Login (MUST run in separate Windows terminal)**

⚠️ This step CANNOT be run inside Cursor's integrated terminal.
It opens an interactive browser login that requires a standalone window.

Open a separate Windows terminal:
- Press Win+X → Terminal
- OR press Win+R → type "powershell" → Enter

Run:
```powershell
C:\Users\$env:USERNAME\.local\bin\uvx.exe linkedin-scraper-mcp --login
```

A browser window will open. Log into your LinkedIn account.
Wait for: "Profile saved to C:\Users\[username]\.linkedin-mcp\profile"
Then come back here.

---

**5d. LinkedIn MCP — Register**

After login is confirmed, run in the rtc-bizdev folder:
```powershell
claude mcp remove linkedin
claude mcp add linkedin -- C:\Users\$env:USERNAME\.local\bin\uvx.exe linkedin-scraper-mcp
```

Verify in Claude Code (kakukk → /mcp):
`linkedin · ✔ connected`

---

**5e. Product Hunt MCP**

Requirements:
- The `PRODUCT_HUNT_TOKEN` is stored in your `.env` file
- Contact Réka to get the real token value before this step

Step 1: Copy `.env.example` to `.env`:
```powershell
Copy-Item .env.example .env
```

Step 2: Open `.env` and replace `REPLACE_WITH_YOUR_DEVELOPER_TOKEN` with the real token Réka provided.

Step 3: Add the MCP to Claude Code by running kakukk, then paste this prompt:

> Edit the file `C:\Users\[USERNAME]\.claude.json`
> Find the "projects" section, then find the entry for this project:
> `C:\Users\[USERNAME]\Documents\RTC - Roll The Code\RTC\RTC Hubs\RTC - BizDev\rtc-bizdev`
> Inside that project's "mcpServers" object, add this new entry:
> ```json
> "producthunt": {
>   "type": "stdio",
>   "command": "C:\\Users\\[USERNAME]\\.local\\bin\\uvx.exe",
>   "args": ["--from", "product-hunt-mcp", "product-hunt-mcp"],
>   "env": {
>     "PRODUCT_HUNT_TOKEN": "PASTE_YOUR_TOKEN_HERE"
>   }
> }
> ```
> Replace `[USERNAME]` with the actual Windows username.
> Replace `PASTE_YOUR_TOKEN_HERE` with the token from the `.env` file.
> Do not change anything else.

Verify in Claude Code (kakukk → /mcp):
`producthunt · ✔ connected`

---

**5f. Final verification**

Run kakukk, then `/mcp`. You should see all three connected:
```
linkedin   · ✔ connected
reddit     · ✔ connected
producthunt · ✔ connected
```

If any show ✘ failed:
- Check that you used the full uvx path, not just "uvx"
- Close Cursor completely and reopen
- Re-run the `claude mcp add` command for the failing server

### Step 6: Deploy to Cloudflare Pages

Load the Cloudflare API token from the `.env` file and deploy:

```bash
# Check if .env exists and contains the token
if [ -f .env ]; then
  export $(grep CLOUDFLARE_API_TOKEN .env | xargs)
fi
```

If `.env` doesn't exist or `CLOUDFLARE_API_TOKEN` is empty, print:
```
⚠️ Cloudflare deployment skipped — no API token found.
To enable auto-deploy:
  1. Copy .env.example to .env
  2. Set CLOUDFLARE_API_TOKEN=your_token_here
  3. Re-run /setup
```
Skip to Step 7.

If the token is present, deploy:
```bash
CLOUDFLARE_API_TOKEN=$CLOUDFLARE_API_TOKEN npx wrangler pages deploy . --project-name rtc-bizdev
```

Print the deployment URL from the output.

### Step 7: Verify skills are loaded

Check that the `.claude/skills/` directory contains the expected skills:
```bash
ls .claude/skills/
```

Expected: `pitch-deck`, `sales-onepager`, `investor-brief`, `html-presentation`, `collaborator-deck`, `business-planning`, `pdf-report`

If any are missing, print which ones and say: "Contact Réka to restore missing skills from the repo."

### Step 8: PowerShell Alias — kakukk

Add a `kakukk` alias to Anti's PowerShell profile so Claude Code launches automatically without permission prompts:

```powershell
if (!(Test-Path $PROFILE)) { New-Item -Path $PROFILE -Force }
Add-Content $PROFILE "`nSet-Alias kakukk 'claude --dangerously-skip-permissions'"
```

Verify the alias was added:
```powershell
Get-Content $PROFILE | Select-String kakukk
```

Tell the user: "Done. From now on, type `kakukk` in any terminal to launch Claude Code in autonomous mode."

### Step 9: Final status report

Print a clean summary:

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
✅ Reddit MCP       — installed (uvx full path)
✅ LinkedIn MCP     — installed & authenticated (separate terminal required)
✅ Product Hunt MCP — installed (token from .env)
✅ Cloudflare Pages — deployed
✅ Project skills   — all 7 present
✅ kakukk alias     — added to PowerShell profile
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
You're ready. Try: "Create a sales one-pager for Roll the Code targeting enterprise innovation hubs."
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

If anything failed, list what needs to be fixed and offer to retry that step.
