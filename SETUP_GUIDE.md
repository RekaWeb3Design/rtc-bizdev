# RTC BizDev Toolkit — Setup Guide

**For:** Antal Károlyi (Anti)
**Platform:** Windows 11
**Time needed:** ~30 minutes
**Result:** A fully working AI-powered pitch and sales toolkit running inside Cursor

---

## What You're Setting Up

This toolkit lets you generate pitch decks, sales one-pagers, investor briefs, HTML presentations, branded PDF reports, cold emails, and market research — all from plain English prompts inside Claude Code. You type what you need, the AI builds it.

---

## Step 1: Prerequisites

Before you start, make sure you have these three things:

### 1a. Download and Install Cursor

Cursor is an AI-native code editor. It's where you'll run Claude Code.

1. Go to **https://cursor.com**
2. Download the Windows installer
3. Run the installer — accept defaults
4. Open Cursor once to make sure it launches

### 1b. GitHub Account

You need a GitHub account to clone the repo.

1. If you don't have one: go to **https://github.com** and sign up
2. If you already have one: make sure you're logged in

### 1c. Claude Pro Subscription

Claude Code requires a paid Anthropic plan.

1. Go to **https://claude.ai**
2. Subscribe to **Claude Pro** ($20/month minimum)
3. This gives you access to Claude Code with Opus-level models

> **Note:** The $20/month Pro plan works. If you hit usage limits on heavy days, the $100/month Max plan removes them. Start with Pro — upgrade later if needed.

---

## Step 2: Clone the Repo in Cursor

1. Open **Cursor**
2. Press `Ctrl + Shift + P` to open the command palette
3. Type `Git: Clone` and press Enter
4. Paste the repository URL (get this from Reka or the GitHub page)
5. Choose a folder on your machine — something like `C:\Users\Anti\Documents\RTC`
6. When it asks "Open cloned repository?" — click **Yes**

You should now see the project files in the left sidebar: `CLAUDE.md`, `brand/`, `.claude/`, `outputs/`, etc.

---

## Step 3: Install Claude Code

Open a **PowerShell terminal** inside Cursor:

1. In Cursor, press `` Ctrl + ` `` (backtick) to open the integrated terminal
2. Make sure it's set to **PowerShell** (check the dropdown in the top-right of the terminal panel)
3. Run this one-liner:

```powershell
npm install -g @anthropic-ai/claude-code
```

Wait for it to finish. Then verify:

```powershell
claude --version
```

You should see a version number like `1.x.x`.

> **If `npm` is not recognized:**
> You need Node.js first. Go to **https://nodejs.org**, download the **LTS** version, install it, then **close and reopen Cursor** before trying again.

> **If `claude` is not recognized after install:**
> Close and reopen PowerShell (or the entire Cursor app). If still not working, run:
> ```powershell
> $env:PATH += ";$env:APPDATA\npm"
> ```
> Then try `claude --version` again.

---

## Step 4: Open Claude Code

In the same terminal inside Cursor, type:

```powershell
claude
```

Claude Code will start up. You'll see a prompt where you can type natural language commands. This is your main workspace — you talk to Claude here, and it reads/writes files in the project.

On first launch, it will ask you to authenticate with your Anthropic account. Follow the prompts — it opens a browser window for login.

---

## Step 5: Run /setup

Inside Claude Code, type:

```
/setup
```

This runs the automated setup agent. Here's what it does, step by step:

| Step | What it does | What you need to do |
|---|---|---|
| Verify Claude Code | Checks your Claude Code version | Nothing — automatic |
| Install plugins | Prints plugin install commands | Copy-paste each command into Claude Code, one by one |
| Install Node.js | Checks if Node.js is available | Nothing if already installed |
| Install Puppeteer | Installs PDF generation tool | Nothing — automatic |
| Install uv | Installs Python package runner | May need to reopen terminal (see below) |
| Install Firecrawl | Installs web scraping tool | You'll paste your API key (see Step 6) |
| Install Reddit MCP | Adds Reddit research capability | Nothing — automatic |
| Install LinkedIn MCP | Adds LinkedIn research capability | You'll log in via browser (see below) |
| Verify skills | Checks all 7 project skills are present | Nothing — automatic |
| Status report | Shows what's installed and what's not | Review and fix any failures |

### What to expect

The setup takes about 15-20 minutes. Most of it is automated. You'll be asked to:
1. Copy-paste plugin install commands (about 8 commands)
2. Paste your Firecrawl API key
3. Log into LinkedIn in a separate browser window

---

## Step 6: Get Your Firecrawl API Key

Firecrawl lets the toolkit search the web and scrape pages for market research.

1. Go to **https://firecrawl.dev**
2. Sign up for a free account
3. Go to your dashboard and copy your **API key**
4. When the setup agent asks for it, paste it in

> **Good news:** The free tier is enough for normal use. You get 500 scrapes/month. If you need more, paid plans start at $19/month.

---

## Step 7: LinkedIn MCP Login

This is the one step that **cannot run inside Claude Code**. It opens an interactive browser login, which doesn't work in Claude Code's terminal.

Here's what to do when the setup agent reaches this step:

1. **Open a separate PowerShell window** (not the one inside Cursor)
   - Press `Win + X`, then click **Terminal** or **PowerShell**
2. Run:
   ```powershell
   uvx linkedin-scraper-mcp --login
   ```
3. A browser window will open — log into your LinkedIn account
4. Once login is complete, go back to Claude Code and tell it you're done
5. The setup agent will then register the LinkedIn MCP server

> **If `uvx` is not recognized:**
> Close and reopen PowerShell. If still not working, run:
> ```powershell
> $env:PATH += ";C:\Users\$env:USERNAME\.local\bin"
> ```
> Then try the command again.

---

## Windows Troubleshooting

These are the most common issues on Windows. All of them have the same root cause: Windows doesn't update the PATH automatically after installing new tools.

### Problem: "command not recognized" after installing something

**Solution:** Close and reopen PowerShell (or restart Cursor entirely).

If that doesn't work, here are the manual PATH fixes for each tool:

| Tool | Manual PATH fix |
|---|---|
| `node` / `npm` | `$env:PATH += ";C:\Program Files\nodejs"` |
| `claude` | `$env:PATH += ";$env:APPDATA\npm"` |
| `puppeteer` | `$env:PATH += ";$env:APPDATA\npm"` |
| `firecrawl` | `$env:PATH += ";$env:APPDATA\npm"` |
| `uv` / `uvx` | `$env:PATH += ";C:\Users\$env:USERNAME\.local\bin"` |

### Problem: "wkhtmltopdf" mentioned somewhere

**Ignore it.** We use **Puppeteer** for PDF generation, not wkhtmltopdf. If any old documentation mentions wkhtmltopdf, it's outdated. Puppeteer is already installed by `/setup`.

### Problem: LinkedIn login doesn't work inside Claude Code

**This is expected.** The LinkedIn login opens an interactive browser — it must run in a standalone PowerShell window, not inside Claude Code. See Step 7 above.

### Problem: Plugin install commands fail

Make sure you're running them **inside Claude Code** (after typing `claude`), not in a regular PowerShell prompt. Plugin commands like `/plugin marketplace add ...` are Claude Code commands, not shell commands.

---

## Step 8: Verify Everything Works

After `/setup` completes with all green checkmarks, run this test prompt inside Claude Code:

```
Create a sales one-pager for Roll the Code targeting enterprise innovation hubs in the UK.
```

If everything is working, Claude Code will:
1. Read the brand guide and CLAUDE.md automatically
2. Generate a professional one-pager in Roll the Code branding
3. Save it to the `outputs/` folder
4. Offer to create an HTML version

If you see output in `outputs/` — you're good to go.

---

## Quick Reference: Daily Commands

These are the commands you'll use most often. Type them inside Claude Code.

### Pitch & Sales Materials

| What you want | What to type |
|---|---|
| Sales one-pager | `Create a one-pager for [client/industry]` |
| Pitch deck outline | `Create a pitch deck for [audience]` |
| Investor brief | `Create an investor brief for [context]` |
| HTML presentation | `Create an HTML presentation for [topic]` |
| Branded PDF report | `Generate a PDF report on [topic]` |
| Partner/collaborator deck | `Create a collaborator deck for [partner]` |
| Full pitch package (all formats) | `Assemble a complete pitch package for [client]` |

### Research

| What you want | What to type |
|---|---|
| Market research | `Research the market for [industry/segment]` |
| Competitor analysis | `Find competitors in [space] and compare` |
| Company research | `Research [company name] — what do they do, recent news` |
| Industry trends | `What are the latest trends in [industry]?` |

### Strategy & Planning

| What you want | What to type |
|---|---|
| Business plan section | `Write the GTM strategy section of our business plan` |
| Cold email sequence | `Write a cold email sequence for [target]` |
| Pricing strategy | `Help me think through pricing for [offering]` |
| Go-to-market plan | `Create a GTM plan for [market/segment]` |

### Utility

| What you want | What to type |
|---|---|
| Run setup again | `/setup` |
| See what skills exist | Ask: `What skills do you have?` |
| Create a new skill | `/skill-creator` |

---

## Folder Structure

After setup, your project looks like this:

```
rtc-bizdev/
  CLAUDE.md              ← Brain of the toolkit (context, tone, strategy)
  SETUP_GUIDE.md         ← This file
  brand/
    brand.md             ← Colors, fonts, logo, voice rules
    assets/              ← Logo, photos, fonts (when ready)
  outputs/               ← All generated documents land here
  .claude/
    skills/              ← 7 skill templates (pitch-deck, pdf-report, etc.)
    agents/              ← Sub-agents (setup, pitch-assembler, market-researcher)
```

**You almost never need to edit these files manually.** Claude Code reads them automatically. If you want to update the brand colors, edit `brand/brand.md`. If you want to change how pitches are structured, edit the relevant skill in `.claude/skills/`.

---

## Getting Help

- **Something broke?** Type your problem into Claude Code — it can usually diagnose and fix it.
- **Need a new document type?** Type `/skill-creator` to build a new skill template.
- **Want to update branding?** Edit `brand/brand.md` — all skills pick it up automatically.
- **Repo issues?** Contact Reka.

---

*Setup guide last updated: April 2026*
