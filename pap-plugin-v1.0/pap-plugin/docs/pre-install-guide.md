# Before You Begin

Read this before installing. Each step has a verification test.

---

## The fastest way to prepare

Copy this prompt into any AI assistant (Claude, ChatGPT, etc.)
and it will walk you through everything step by step:

```
I'm setting up a tool called PAP (Personal Automation Platform).
You can learn what it is at: pap-ai.github.io/pap

Please walk me through these steps one at a time, asking me to
confirm each before moving on:

1. Finding or acquiring a suitable always-on machine
   Requirements:
   → macOS or Windows (not Linux, not Chromebook)
   → 8GB RAM minimum (16GB recommended)
   → Made in last 6-7 years
   → Can stay powered on and connected 24/7
   → NOT my main daily computer (security reasons)

2. Wiping the machine clean (factory reset)
   → Ask me what OS it runs and walk me through the exact steps

3. Creating a Claude account at claude.ai
   and subscribing to the Pro plan ($20/month)

4. Creating a Discord account at discord.com

5. Creating a new Discord server and finding the Server ID

6. Creating a GitHub account and a private repository
   called 'platform-config'

7. Connecting my clean machine to the internet
   (WiFi or ethernet)

8. Installing Claude Desktop on the clean machine

After each step, ask "Did that work?" before continuing.
If I get stuck, help me troubleshoot.
```

---

## Or do it yourself — step by step

### Step 1 — Claude account and subscription

- Go to claude.ai → Get started → Pro plan ($20/month)
- Complete signup and payment

✓ Works when: you can open claude.ai and start a conversation.

---

### Step 2 — Discord account and server

**Account:** discord.com → Register → verify email
**Phone:** install Discord from your app store
**Server:** Discord + button → Create My Own → For me and my friends
**Server ID:** Settings → Advanced → Developer Mode ON →
right-click server name → Copy Server ID

✓ Works when: you have Discord on phone and computer, and you have a Server ID number saved.

---

### Step 3 — GitHub account

- github.com/signup → free account → verify email
- Create private repo: + button → New repository →
  name: platform-config → Private → Create

✓ Works when: you can see the platform-config repo in your account.

---

### Step 4 — Your always-on machine

Use a dedicated computer — NOT your daily machine.

Good options:
- Old laptop from friends/family (free)
- Facebook Marketplace or Craigslist: "old laptop" ($50-150)
- Mac Mini M2 new ($599) — designed for always-on use

Minimum specs:
- macOS or Windows (not Linux, not Chromebook)
- 8GB RAM minimum
- Made in last 6-7 years
- Windows: Hyper-V must be available (not on some Windows Home editions)
- Windows ARM: not supported

**Wipe it first:**

Mac: Restart + hold Command+R → Erase Mac → set up as new

Windows: Settings → System → Recovery → Reset this PC → Remove everything

✓ Works when: machine boots with no previous files or accounts.

---

### Step 5 — Connect to internet

Mac: WiFi icon in menu bar → select network → enter password
Windows: WiFi icon in taskbar → select network → enter password

Verify: open a browser, load any website.

For reliable overnight tasks: plug into ethernet (more stable than WiFi).

---

### Step 6 — Install Claude Desktop

On the clean machine:
- claude.ai/download → download for your OS → install
- Sign in with your Claude account

✓ Works when: Claude Desktop opens and you can start a conversation.

---

### Step 7 — Install PAP

In Claude Desktop → Cowork tab → Customize → Add Plugin:
Paste: `github.com/pap-ai/pap`

PAP onboarding starts automatically.

---

## What happens next

Onboarding takes 30-45 minutes total.
First 5-10 minutes on the clean machine, then you move to Discord.
You can stop anywhere — PAP remembers where you left off.

---

## Common issues

**Discord Server ID won't copy:** make sure Developer Mode is on in Discord Settings → Advanced.

**GitHub repo creation fails:** check your email is verified on GitHub.

**Clean machine won't connect to WiFi:** check password, try unplugging/replugging ethernet, restart the machine.

**For anything else:** ask in #help once PAP is set up.
