# Recovery Guide

What to do when something breaks.

---

## Quick reference

| Problem | Go to |
|---------|-------|
| Claude Desktop closed | Restart it on the clean machine |
| Scheduled task missed | Ask "what did I miss?" in #help |
| Clean machine restarted | Wait 2-3 min, check #pap-status |
| Machine won't boot | See Machine failure below |
| PAP not responding in Discord | See Bot not responding below |
| Connector authentication expired | Check the workspace channel for instructions |
| Full reinstall needed | See Start over below |

---

## Restart Claude Desktop

Claude Desktop must stay open for scheduled tasks.

Mac: Launchpad → Claude → Launch
Windows: Start menu → Claude → Launch

Once open: ask "what did I miss?" in #help.
PAP will catch you up on anything that ran or failed.

---

## After a restart

Claude Desktop is configured to launch automatically.
After restart: wait 2-3 minutes for initialization.
PAP will post to #pap-status when it's back online.

If no Discord message within 5 minutes: see Bot not responding.

---

## Bot not responding

**Step 1 — Check if Claude Desktop is running**
Connect via Tailscale (if configured) or go to the clean machine.
Check if Claude Desktop appears in dock or taskbar.
If not running: open it.

**Step 2 — Check if bot is online**
In Discord, look at the member list — [agent name] should show as online.
If offline, restart the bot:
In Cowork: "Restart the Discord bot connection"

**Step 3 — If bot token expired**
In PAP Vault: find the Discord bot entry.
Go to discord.com/developers/applications → your app → Bot → Reset Token.
Copy new token → update PAP Vault entry.
In Cowork: "The Discord bot token has been updated — please reconnect"

---

## Reconnect a connector

When a connector's authentication expires, PAP posts to the workspace
channel with specific reconnection instructions.

General pattern:
1. You'll see: "[Service] needs to be reconnected. Here's how:"
2. Follow the steps
3. Reply "done" when complete

If you don't see instructions: ask in #help "[Service] seems disconnected"

---

## Machine failure

Your clean machine died, won't boot, or was lost.

**Your data is safe:**
- Workspace files → GitHub platform-config repo
- All outputs → Drive/OneDrive (untouched)
- Second brain → Drive/OneDrive
- Preferences and config → GitHub

**What you need:** a new machine, GitHub credentials, about 20-30 minutes.

**Recovery process:**

Step 1 — Prepare the new machine
Follow the pre-install guide. Stop before installing the PAP plugin.

Step 2 — Install PAP in recovery mode
In Cowork on the new machine:
"I need to restore my Personal Automation Platform from my GitHub backup.
My GitHub username is [username]
My backup repo is [repo name]"

Step 3 — Authenticate GitHub
Provide your GitHub personal access token from your password manager.

Step 4 — Restore runs automatically
PAP pulls backed-up configuration. Takes 15-25 minutes.
Progress updates in Cowork.

Step 5 — Reconnect services
Platform Drive/OneDrive: re-authorize in Claude Desktop connectors.
Discord bot: token restored from vault, reconnects automatically.
Password manager: may need to re-authorize MCP on new machine.
PAP walks you through each with specific steps.

Step 6 — Verify
Ask in #help: "Run a full system validation"

**What you might lose:**
Changes since last nightly backup (up to 24 hours).
Output files in Drive/OneDrive: nothing lost.
Second brain content: nothing lost.

---

## Start over (full reinstall by choice)

1. Go to #uninstall in Discord
2. Follow the pinned card instructions
3. Choose "Export and pause" to save data first
4. After export confirmed: "Full removal"
5. Follow the pre-install guide as a new user

Your output files in Drive/OneDrive are never deleted by PAP removal.

---

## Things that are always safe

Regardless of what goes wrong with PAP:
- Your output files in Drive/OneDrive are never touched
- Your password manager is never modified
- Your Discord server and history are never deleted
- Your GitHub backup runs independently
- Your personal accounts are never affected

PAP is designed so that its failure doesn't take anything important down with it.

---

## Still stuck?

Ask in #help: describe what happened and what you expected.
PAP knows your specific setup and will give targeted guidance.
