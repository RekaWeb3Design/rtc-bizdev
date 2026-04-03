---
name: kakukk
description: Self-documenting slash command that explains the kakukk alias, detects OS, and launches Claude Code in autonomous mode from the BizDev repo. Invoke with /kakukk
---

You are the kakukk launcher — a self-documenting slash command for the Roll the Code BizDev toolkit.

## What is kakukk?

When invoked, first display this explanation:

```
kakukk = navigate to the Roll the Code BizDev repo and launch Claude Code with --dangerously-skip-permissions

This gives Claude full autonomous access — no permission prompts, no sandbox.
Use it when you want uninterrupted workflow on trusted tasks.
```

## Step 1: Ask for confirmation

Ask the user:

```
Do you want to proceed? This will:
  1. Navigate to the BizDev repo
  2. Launch Claude Code with --dangerously-skip-permissions (full autonomous mode)

Type "yes" to continue, anything else to cancel.
```

If the user does NOT confirm, print "Cancelled." and stop.

---

## Step 2: Detect OS

```bash
uname -s 2>/dev/null || echo "Windows"
```

- Output contains `Darwin` → **macOS**
- Output contains `Linux` → **Linux** (follow macOS path, using `~/.bashrc` instead of `~/.zshrc`)
- Command fails or output is `Windows` → **Windows**

---

## Step 3: Detect repo path

Get the absolute path of the current repo:

```bash
pwd
```

Store this as `REPO_PATH`.

---

## Step 4: Launch Claude Code

**macOS / Linux:**
```bash
cd $REPO_PATH && claude --dangerously-skip-permissions
```

**Windows (PowerShell):**
```powershell
Set-Location $REPO_PATH; claude --dangerously-skip-permissions
```

Tell the user:
```
Launching Claude Code in autonomous mode from:
  $REPO_PATH
```

---

## Step 5: Check if shell alias exists

After launch, check whether the `kakukk` alias is already set up for quick access from any terminal.

**macOS:**
```bash
grep -q "kakukk" ~/.zshrc 2>/dev/null && echo "exists" || echo "missing"
```

**Linux:**
```bash
grep -q "kakukk" ~/.bashrc 2>/dev/null && echo "exists" || echo "missing"
```

**Windows:**
```powershell
if (Test-Path $PROFILE) { (Get-Content $PROFILE | Select-String 'kakukk').Length -gt 0 } else { $false }
```

---

## Step 6: Offer to add alias permanently

If the alias is **missing**, ask the user:

```
The kakukk alias is not in your shell profile yet.
Want me to add it so you can type "kakukk" from any terminal?
Type "yes" to add, anything else to skip.
```

If confirmed:

**macOS:**
```bash
echo "alias kakukk='cd $REPO_PATH && claude --dangerously-skip-permissions'" >> ~/.zshrc
source ~/.zshrc
```

**Linux:**
```bash
echo "alias kakukk='cd $REPO_PATH && claude --dangerously-skip-permissions'" >> ~/.bashrc
source ~/.bashrc
```

**Windows:**
```powershell
if (!(Test-Path $PROFILE)) { New-Item -Path $PROFILE -Force }
Add-Content $PROFILE "`nfunction kakukk { Set-Location '$REPO_PATH'; claude --dangerously-skip-permissions }"
```

Print:
```
Done. From now on, type "kakukk" in any terminal to launch Claude Code in autonomous mode from the BizDev repo.
```

If the alias already exists, print:
```
kakukk alias already configured. You're good to go.
```
