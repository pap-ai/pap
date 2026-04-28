---
name: sms-2fa
description: Handles SMS 2FA prompts during automated
  logins. Auto-fires when Computer Use detects an SMS
  verification prompt.
triggers:
  - SMS 2FA prompt detected
  - "verification code"
  - login flow blocked at 2FA step
model: claude-haiku-4-5
---

# SMS 2FA Handler

## The flow

**Step 1 — Don't trigger the SMS yet**
Update message reaction to 🔐.
Post to workspace channel (with buttons, not plain text):

"🔐 I need to complete a login for [service]
but it requires an SMS verification code.

When you're ready, tap below and I'll request
the code. You'll have about 60 seconds to send
it back.

[I'm Ready — Send the Code]
[Remind Me in 30 Minutes]
[Skip This Task]"

**Step 2 — User taps "I'm Ready"**
Computer Use clicks "Send Code" on the website.
Immediately open a modal:
"Enter your verification code:"
[text field — accepts anything, parses the number]

**Step 3 — Parse the code**
Extract from whatever they send:
- "482913" → 482913
- "Your code is 482913" → 482913
- Full SMS text → find 4-12 character alphanumeric sequence
- "482 913" → 482913 (strip spaces/dashes)

If multiple candidates: use the one most resembling
a verification code (pure digits preferred, then mixed).

If no code found: "I couldn't find a code in that.
Can you send just the digits?" [text field]

**Step 4 — Enter code, continue**
Reaction updates to ⏳ then ✅.
Confirm: "Logged in successfully, continuing..."

## Timeout handling

90-second timeout from "Send Code" click.
If expired:
"Code expired.
[Try Again — Send New Code]  [Cancel This Task]"

Reaction stays 🔐 until resolved.

## Multiple attempts

After 3 failures:
"I've tried 3 times. Something's not right.
Pausing and checking if the credentials in
PAP Vault are correct."

## TOTP available

If service offers TOTP and 1Password/vault has it:
Use automatically, no user involvement needed.

## Voice call option

If service requires a phone call:
"This service is calling your phone for verification.
I can't handle voice calls — you'll need to take it."

## What you never do

Never trigger SMS without user readiness.
Never proceed past 2FA without successful entry.
