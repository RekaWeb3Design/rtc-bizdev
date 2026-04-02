# RTC BizDev Toolkit — Complete Setup Guide

**For:** Antal Karolyi (Anti)  
**Platform:** Windows 11  
**Time needed:** ~30 minutes  
**Last updated:** April 2026

---

## 1. What You'll Have When Done

After following this guide, you'll have a fully operational AI-powered business development toolkit running inside Cursor. From a single terminal prompt, you can:

- **Generate pitch decks** — structured outlines and full slide content for clients, investors, or partners
- **Create sales one-pagers** — branded, PDF-ready documents for any industry or company
- **Build HTML presentations** — dark-themed, animated web presentations you can share via link
- **Write investor briefs** — executive summaries with financials, market sizing, and team profiles
- **Run market research** — live web search, competitor analysis, TAM/SAM/SOM estimates
- **Draft cold emails** — sequenced outreach with follow-ups, tailored to specific targets
- **Generate PDF reports** — multi-page branded documents with auto-generated covers

Everything is branded Roll the Code, follows your tone of voice, and saves to the correct folder automatically. You type what you need in plain English — Claude builds it.

---

## 2. Prerequisites

You need three things before you start. Get these set up first.

### 2a. Cursor (Code Editor)

Cursor is an AI-native code editor built on VS Code. It's where you'll work.

1. Go to **https://cursor.com**
2. Click **Download for Windows**
3. Run the installer — accept all defaults
4. Open Cursor once to confirm it launches

### 2b. GitHub Account

You need a GitHub account to access the project repository.

1. If you don't have one: go to **https://github.com** and sign up (free)
2. If you already have one: make sure you're logged in

### 2c. Claude Pro Subscription

Claude Code requires a paid Anthropic subscription.

1. Go to **https://claude.ai**
2. Subscribe to **Claude Pro** — **$20/month**
3. This gives you access to Claude Code with Opus-level models

> The $20/month Pro plan is sufficient. If you hit usage limits on heavy days, the $100/month Max plan removes them. Start with Pro — upgrade only if needed.

---

## 3. Clone the Repo in Cursor

This downloads the entire toolkit to your machine.

**Option A — Clone via Cursor UI:**

1. Open **Cursor**
2. Press **Ctrl + Shift + P** to open the Command Palette
3. Type **Git: Clone** and press Enter
4. Paste the repository URL: `https://github.com/RekaWeb3Design/rtc-bizdev.git`
5. Choose a local folder — for example: `C:\Users\Anti\Documents\RTC`
6. When it asks **"Open cloned repository?"** — click **Yes**

**Option B — Clone via terminal:**

Open PowerShell and run:

```powershell
git clone https://github.com/RekaWeb3Design/rtc-bizdev.git
```

Then open the cloned folder in Cursor: **File → Open Folder →** select the `rtc-bizdev` folder.

You should now see the project files in the left sidebar: `CLAUDE.md`, `brand/`, `.claude/`, `outputs/`, etc.

> If Cursor asks you to install Git, do it first, then restart Cursor and try again.

---

## 4. Install Claude Code

Open a terminal inside Cursor and install Claude Code globally via npm.

1. In Cursor, press **Ctrl + `** (backtick) to open the integrated terminal
2. Make sure the terminal is set to **PowerShell** (check the dropdown in the top-right of the terminal panel)
3. Run this command:

```powershell
irm https://claude.ai/install.ps1 | iex
```

4. Wait for it to finish, then verify:

```powershell
claude --version
```

You should see a version number like `1.x.x`.

> **⚠️ If `claude` is not recognized after install:**  
> Close and reopen PowerShell (or restart Cursor entirely). If still not working, run:
> ```powershell
> $env:PATH += ";C:\Users\$env:USERNAME\.local\bin"
> ```
> Then try `claude --version` again.

---

## 5. Launch Claude Code

1. In the Cursor terminal, make sure you're in the project folder:

```powershell
cd "C:\Users\Anti\Documents\RTC\rtc-bizdev"
```

(Adjust the path to wherever you cloned the repo.)

2. Start Claude Code:

```powershell
claude
```

3. On first launch, it will ask you to authenticate with your Anthropic account. Follow the prompts — it opens a browser window for login.

Once authenticated, you'll see a prompt where you can type natural language commands. This is your main workspace.

---

## 6. Run /setup

Inside Claude Code, type:

```
/setup
```

This runs the automated setup agent that installs everything else. Here's what it does:

| Step | What happens | Your action |
|---|---|---|
| Verify Claude Code | Checks version is installed | Nothing — automatic |
| Install plugins | Prints 8 plugin commands | Copy-paste each command one by one |
| Check Node.js | Verifies Node is available | Nothing if already installed |
| Install Puppeteer | Installs PDF generation tool | Nothing — automatic |
| Install uv | Installs Python package runner | May need to reopen terminal |
| Install Firecrawl | Installs web research tool | Paste your API key (see Step 7) |
| Install Reddit MCP | Adds Reddit research | Nothing — automatic |
| Install LinkedIn MCP | Adds LinkedIn research | Login via browser (see Step 7) |
| Deploy to Cloudflare | Publishes the portal | Needs `.env` with API token |
| Verify skills | Checks all 7 skills present | Nothing — automatic |
| Final report | Shows green/red status | Review and fix any failures |

The setup takes about 15-20 minutes. Most is automated.

---

## 7. Manual Steps After /setup

These steps require your input during or after the setup process.

### 7a. Firecrawl API Key

Firecrawl powers web search and page scraping for market research.

1. Go to **https://firecrawl.dev**
2. Sign up for a free account
3. Go to your dashboard and copy your **API key**
4. When the setup agent asks for it, paste it in

> The free tier gives you 500 scrapes/month — plenty for normal use.

### 7b. LinkedIn MCP — Login

This is the one step that **must run outside Claude Code**. It opens an interactive browser login that doesn't work inside Claude Code's terminal.

1. **Open a separate PowerShell window** — press **Win + X**, then click **Terminal** or **PowerShell**
2. Run:

```powershell
uvx linkedin-scraper-mcp --login
```

3. A browser window opens — log into your LinkedIn account
4. Once login is complete, close the browser and go back to Claude Code
5. Tell the setup agent you're done — it will register the LinkedIn server

### 7c. LinkedIn MCP — Register

After login is confirmed, the setup agent runs this automatically. If you need to do it manually:

```powershell
claude mcp add linkedin -- uvx linkedin-scraper-mcp
```

### 7d. Cloudflare Deployment

The BizDev portal is deployed to Cloudflare Pages under the Roll the Code account. Here's how to get your API token:

1. Go to **https://dash.cloudflare.com**
2. Log in with your **@rollthecode.com** email (ask Reka for access to the Roll the Code Cloudflare account)
3. Once logged in, go to **My Profile -> API Tokens**
4. Get your token — either:
   - **Option A:** Use the existing **"RTC BizDev"** API token — ask Reka to share it securely
   - **Option B:** Create your own — click **"+ Create Token"** -> **"Edit Cloudflare Workers"** template -> Zone: **rollthecode.com** -> Create
5. Copy the token (you only see it once!)
6. In the repo root, open `.env` (copy from `.env.example` if missing)
7. Replace `your_token_here` with your token
8. Save — this file stays on your machine only, never pushed to GitHub

> **⚠️ Never share your `.env` file or paste your API token in chat, email, or Claude Code prompts.** The token grants write access to the Cloudflare deployment. Treat it like a password.

Once your `.env` is set, the `/setup` agent deploys automatically. To deploy manually at any time:

```powershell
npx wrangler pages deploy . --project-name rtc-bizdev
```

> The **rollthecode.com** Cloudflare account is managed by Reka. Contact her for access if needed.

---

## 8. Windows Troubleshooting

Every issue on this page has the same root cause: **Windows doesn't update PATH automatically after installing new tools.** Here's how to fix each one.

### "Command not recognized" after installing something

**First try:** Close and reopen PowerShell (or restart Cursor entirely).

**If that doesn't work**, use the manual PATH fix for the specific tool:

| Tool | Manual PATH fix |
|---|---|
| `node` / `npm` | `$env:PATH += ";C:\Program Files\nodejs"` |
| `claude` | `$env:PATH += ";$env:APPDATA\npm"` |
| `puppeteer` | `$env:PATH += ";$env:APPDATA\npm"` |
| `firecrawl` | `$env:PATH += ";$env:APPDATA\npm"` |
| `uv` / `uvx` | `$env:PATH += ";C:\Users\$env:USERNAME\.local\bin"` |

### uv Not Installed

If `/setup` can't find `uv`, install it manually:

```powershell
irm https://astral.sh/uv/install.ps1 | iex
```

Then close and reopen PowerShell before continuing.

### wkhtmltopdf Mentioned Somewhere

**Ignore it.** We use **Puppeteer** for PDF generation, not wkhtmltopdf. If any old documentation mentions it, it's outdated. Puppeteer is installed automatically by `/setup`.

### LinkedIn Login Doesn't Work Inside Claude Code

**This is expected.** The LinkedIn login opens an interactive browser window — it must run in a standalone PowerShell window, not inside Claude Code. See Step 7b above.

### Plugin Commands Fail

Make sure you're running them **inside Claude Code** (after typing `claude`), not in a regular PowerShell prompt. Commands like `/plugin marketplace add ...` are Claude Code commands, not shell commands.

> **⚠️ General rule:** After installing *anything* on Windows, close and reopen your terminal. This fixes 90% of "not recognized" errors.

---

## 9. First Test — Verify Everything Works

After `/setup` completes with all green checkmarks, run this test prompt inside Claude Code:

```
Create a sales one-pager for Roll the Code targeting enterprise innovation hubs in the UK.
```

If everything is working, Claude Code will:

1. Read the brand guide and CLAUDE.md automatically
2. Generate a professional one-pager in Roll the Code branding
3. Save it to `outputs/sales/one-pagers/`
4. Update `outputs/files-index.json`
5. Offer to create an HTML or PDF version

**If you see output in the `outputs/` folder — you're good to go.**

Try a few more to explore the toolkit:

```
Create an HTML presentation about Roll the Code for a CTO audience.
```

```
Research the UK enterprise IT services market — TAM/SAM/SOM.
```

```
Assemble a complete pitch package for a mid-size UK fintech company.
```

---

## 10. Daily Usage — Slash Commands & Prompts

These are the commands and prompts you'll use every day inside Claude Code.

### Generating Materials

| What you want | What to type |
|---|---|
| Sales one-pager | `Create a one-pager for [client/industry]` |
| Pitch deck | `Create a pitch deck for [audience]` |
| Investor brief | `Create an investor brief for [context]` |
| HTML presentation | `Create an HTML presentation for [topic]` |
| PDF report | `Generate a PDF report on [topic]` |
| Collaborator deck | `Create a collaborator deck for [partner name]` |
| Full pitch package | `Assemble a complete pitch package for [client]` |

### Research & Strategy

| What you want | What to type |
|---|---|
| Market research | `Research the market for [industry/segment]` |
| Competitor analysis | `Find competitors in [space] and compare` |
| Company research | `Research [company name] — what do they do?` |
| Cold email sequence | `Write a cold email sequence for [target]` |
| GTM strategy | `Create a GTM plan for [market/segment]` |
| Pricing strategy | `Help me think through pricing for [offering]` |

### System Commands

| What you want | What to type |
|---|---|
| Re-run setup | `/setup` |
| See available skills | Ask: `What skills do you have?` |
| Create a new skill | `/skill-creator` |
| Deploy to Cloudflare | Ask: `Deploy the portal to Cloudflare` |

### Folder Structure

All generated files go here automatically:

```
outputs/
  pitches/investors/      Investor briefs, fundraising decks
  pitches/clients/        Client pitch decks and proposals
  pitches/partners/       Collaborator and white-label decks
  sales/one-pagers/       Sales one-pagers by industry or client
  sales/proposals/        Detailed proposals and scoping docs
  sales/emails/           Cold email sequences and follow-ups
  research/market/        Market sizing, TAM/SAM/SOM
  research/competitors/   Competitor analysis
  research/leads/         Company research
  reports/pdf/            All PDF files
  reports/html/           All HTML presentations
```

### Tips

- **Be specific.** "Create a one-pager for Barclays innovation team" works better than "make a one-pager."
- **Mention the audience.** Claude adjusts tone for CTOs vs. investors vs. partners.
- **Ask for iterations.** "Make it shorter," "add pricing," "make the CTA stronger" — it remembers context.
- **Brand updates propagate.** If you edit `brand/brand.md`, all future outputs pick it up automatically.

---

## Getting Help

- **Something broke?** Type your problem into Claude Code — it can usually diagnose and fix itself.
- **Need a new document type?** Type `/skill-creator` to build a new skill template.
- **Want to update branding?** Edit `brand/brand.md` — all skills pick it up automatically.
- **Repo issues?** Contact Reka.

---

*Setup guide by Roll the Code. Last updated April 2026.*
