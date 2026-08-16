# How to Link Claude to Obsidian — Step by Step

A complete setup guide for Windows 11. Estimated time: 15–20 minutes.

---

## What You're Building

A persistent knowledge base that lives in Obsidian and is powered by Claude. Every source you feed it gets turned into cross-referenced wiki pages. Every question you ask pulls from everything you've ever saved. Knowledge compounds over time.

---

## Prerequisites

Before you start, you need:

| Tool | Download | Notes |
|------|----------|-------|
| **Claude desktop app** | [claude.ai/download](https://claude.ai/download) | Free tier works |
| **Obsidian** | [obsidian.md](https://obsidian.md) | Free |
| **Node.js** (LTS) | [nodejs.org](https://nodejs.org) | Required for Claude Code CLI |
| **Git** | [git-scm.com](https://git-scm.com) | Required to clone the vault |

Install all four before continuing.

---

## Step 1 — Fix PowerShell Script Policy

Windows blocks scripts by default. You need to fix this before npm will work.

1. Open **Windows Terminal** or **PowerShell** (search in Start menu)
2. Run:

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

3. Type `Y` and press Enter when prompted

---

## Step 2 — Install the Claude Code CLI

In the same PowerShell window, run:

```powershell
npm install -g @anthropic-ai/claude-code
```

Wait for it to finish. Then verify it worked:

```powershell
claude --version
```

You should see a version number. If not, see Troubleshooting below.

---

## Step 3 — Clone the Vault

Run this in PowerShell:

```powershell
git clone https://github.com/AgriciDaniel/claude-obsidian C:\Users\YOUR_USERNAME\claude-obsidian
cd C:\Users\YOUR_USERNAME\claude-obsidian
bash bin/setup-vault.sh
```

> ⚠️ Replace `YOUR_USERNAME` with your actual Windows username (e.g. `andre`)

This downloads the vault and installs pre-built plugins (Calendar, Thino, Excalidraw, Banners). It also downloads Excalidraw's main.js (~8MB) — wait for the `✓ Setup complete` message.

---

## Step 4 — Optional: Enable the Visual Layout

For the Canvas + Calendar + Thino sidebar layout, run this **before** opening Obsidian:

```powershell
cp "C:\Users\YOUR_USERNAME\claude-obsidian\.obsidian\workspace-visual.json" "C:\Users\YOUR_USERNAME\claude-obsidian\.obsidian\workspace.json"
```

---

## Step 5 — Open the Vault in Obsidian

1. Open **Obsidian**
2. Click **Manage Vaults** → **Open folder as vault**
3. Select `C:\Users\YOUR_USERNAME\claude-obsidian`
4. When prompted, click **Enable community plugins**

---

## Step 6 — Install the Three Required Plugins

In Obsidian:

1. Go to **Settings** (gear icon) → **Community Plugins** → **Browse**
2. Search for and install each of these:
   - **Dataview** — powers dashboard queries
   - **Templater** — auto-fills note frontmatter
   - **Obsidian Git** — auto-commits your vault every 15 minutes

---

## Step 7 — Set Up the Claude Commands

Claude Code looks for custom commands in `.claude/commands/`. Run this to set it up:

```powershell
New-Item -ItemType Directory -Path "C:\Users\YOUR_USERNAME\claude-obsidian\.claude\commands" -Force
Copy-Item "C:\Users\YOUR_USERNAME\claude-obsidian\commands\*" "C:\Users\YOUR_USERNAME\claude-obsidian\.claude\commands\"
```

---

## Step 8 — Open Claude Code in the Vault

This is the most important step. Claude's `/wiki` command only works when Claude Code is launched **from inside the vault folder**.

```powershell
cd C:\Users\YOUR_USERNAME\claude-obsidian
claude
```

A new Claude Code session will open. Type:

```
/wiki
```

You should see a welcome message asking what you want to do. If you see it — **you're done!** 🎉

---

## How to Use It Day-to-Day

### Starting a session
Always launch from the vault:
```powershell
cd C:\Users\YOUR_USERNAME\claude-obsidian
claude
```

### Feed it knowledge
Drop any file (PDF, markdown, transcript, URL) into the `.raw/` folder, then type:
```
ingest [filename]
```
Claude creates 8–15 cross-referenced wiki pages automatically.

### Ask questions
```
what do you know about [topic]?
```
Claude searches your entire wiki and gives a cited answer.

### Save a conversation
```
/save
```
Files the current chat as a wiki note.

### Research a topic autonomously
```
/autoresearch [topic]
```
Claude searches the web, fetches sources, and builds wiki pages on its own.

### Health check
```
lint the wiki
```
Finds orphaned pages, broken links, and gaps.

---

## Troubleshooting

### `claude` is not recognized in PowerShell
**Cause:** Node.js isn't installed or npm global bin isn't in PATH.
**Fix:**
1. Download and install Node.js from [nodejs.org](https://nodejs.org)
2. Close and reopen PowerShell
3. Run `npm install -g @anthropic-ai/claude-code` again

---

### `npm` is blocked / script execution error
**Cause:** PowerShell execution policy is set to Restricted.
**Fix:**
```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```
Type `Y` when prompted, then retry.

---

### `/wiki` says "Unknown command"
**Cause 1:** Claude Code isn't launched from the vault folder.
**Fix:** Close the session, then:
```powershell
cd C:\Users\YOUR_USERNAME\claude-obsidian
claude
```

**Cause 2:** The `.claude/commands/` folder hasn't been created.
**Fix:** Run Step 7 above, then restart Claude Code.

---

### Excalidraw not loading in Obsidian
**Cause:** The `main.js` file (~8MB) isn't downloaded (it's excluded from git).
**Fix:**
```powershell
cd C:\Users\YOUR_USERNAME\claude-obsidian
bash bin/setup-vault.sh
```

---

### Dashboard shows no results in Obsidian
**Cause:** Dataview plugin isn't installed.
**Fix:** Settings → Community Plugins → Browse → install **Dataview**

---

### Graph colors reset after closing Obsidian
**Cause:** Known Obsidian behaviour — color groups don't always persist.
**Fix:** Open Graph view → click the gear icon → re-add Color groups once. They persist permanently after that.

---

### Obsidian not found at `%LOCALAPPDATA%\Obsidian`
**Cause:** Obsidian isn't installed.
**Fix:** Download from [obsidian.md](https://obsidian.md) and run the installer.

---

## Tips

- **The wiki compounds** — the more you ingest, the smarter it gets
- **Use `.raw/` as your inbox** — drop anything in there and ingest it later
- **`/save` everything useful** — treat it like bookmarking, but better
- **The `Stop` hook auto-updates context** — when you end a session, Claude writes a summary to `wiki/hot.md` so the next session picks up where you left off automatically

---

*Based on the claude-obsidian project by [AgriciDaniel](https://github.com/AgriciDaniel/claude-obsidian)*
*Built on Andrej Karpathy's LLM Wiki pattern*
