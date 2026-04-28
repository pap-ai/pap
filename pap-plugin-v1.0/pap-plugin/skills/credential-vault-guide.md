---
name: credential-vault-guide
description: Guides users through password manager setup
  and credential management. Tailored to specific managers.
  Auto-fires during onboarding and when any workspace
  requires a new credential.
triggers:
  - "set up password manager"
  - "add a credential"
  - "PAP Vault"
  - workspace requires new credential
model: claude-sonnet-4-6
---

# Credential Vault Guide

Walks users through PAP Vault setup and credential
management. Tailored to their specific password manager.

## When this fires

During onboarding: PAP Vault creation and population.
After onboarding: when a workspace needs a new credential.

## Initial vault setup

Before asking anything, explain:
"I never see your personal passwords. Credentials
live in your password manager in a section you
create called 'PAP Vault'. You control what goes
there — only what you want me to use. Your personal
passwords stay completely separate."

## Per-manager vault creation

### 1Password

"1. Click 'New Vault' (top of vault list)
2. Name it 'PAP Vault' exactly
3. Don't share it with anyone
4. Click Create

[Done]  [I'm stuck]"

### Bitwarden

"1. In Bitwarden, click 'New' → 'Folder'
2. Name it 'PAP Vault'
3. Save

[Done]  [I'm stuck]

Note: free tier uses Folders. Paid tiers can use
Collections for better isolation."

### KeePassXC

"1. Right-click your database name
2. Select 'New Group'
3. Name it 'PAP Vault'
4. OK

[Done]  [I'm stuck]"

### Other manager

"I don't have specific guidance for your manager,
but the principle is the same: create a separate
folder, vault, or group called 'PAP Vault'. Move
only credentials I should access into that area."

## Adding credentials

When the workspace needs a credential, ask:

"For [service], do you have credentials set up
in your password manager?

[Yes — already in PAP Vault]
[Yes — in a different vault or location]
[No — I need to add it fresh]"

### Already in PAP Vault

"Great. I can see [service] credentials in PAP Vault.
Ready to use when needed."

### In a different location

"Let's move it. In [their manager]:
1. Find [service] in your password manager
2. Right-click (or long-press) the entry
3. Select 'Move to vault' or 'Move item'
4. Choose 'PAP Vault'
5. Confirm

⚠️ If this was in a shared vault (family, work),
it will no longer be shared after moving.
If others need it too, copy instead of move —
but you'll need to keep both copies updated
when the password changes.

[Done — moved]  [Done — copied]  [I need help]"

### Add fresh

"Open [their manager] and create a new entry:
Service: [name]
URL: [URL]
Username: [their username]
Password: [their password]

Save to PAP Vault.
[Done]  [I need help]"

## Sensitive value formats

**API keys:** Save as a Password field.
Username can be the key name or your email.

**Bot tokens:** Save as a Password field.
Username: the bot name.

**OAuth tokens:** Save as a Password field.

**Multi-line credentials (JSON keys):**
Use a Secure Note, not a password field.
Title it with the service name.

## After credential added

"Confirmed. [Service] credentials are now accessible
through PAP Vault. I'll use them only for tasks
you've authorized. Remove the entry from PAP Vault
anytime to revoke access."

## What you never do

Never ask user to share a password in chat.
Never store credentials anywhere except password manager.
Never read credentials from outside PAP Vault.
Never display credential values — confirm presence, not contents.
