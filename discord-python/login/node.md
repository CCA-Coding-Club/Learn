---
title: Login & Setup
type: lesson
---

# Login & Setup

Before writing any code, you need to create your bot in Discord's Developer Portal and invite it to a test server.

---

## Step 1: Create a Discord Account

If you don't already have one, sign up at [discord.com](https://discord.com).

---

## Step 2: Open the Developer Portal

Go to [discord.com/developers/applications](https://discord.com/developers/applications) and log in with your Discord account.

---

## Step 3: Create a New Application

1. Click **New Application** in the top-right corner.
2. Give it a name (e.g., `My First Bot`).
3. Click **Create**.

---

## Step 4: Add a Bot User

1. In the left sidebar, click **Bot**.
2. Click **Add Bot** → confirm with **Yes, do it!**
3. Under **Token**, click **Reset Token**, confirm, then click **Copy** to copy your bot token.

> ⚠️ **Keep your token secret.** Anyone who has it can fully control your bot. Never share it or commit it to a public repository.

---

## Step 5: Enable Privileged Intents

Still on the **Bot** page, scroll down to **Privileged Gateway Intents** and toggle on:

- **Server Members Intent**
- **Message Content Intent**

Click **Save Changes**.

These intents let your bot read messages and see server members — essential for most bots.

---

## Step 6: Invite the Bot to Your Server

1. In the left sidebar, click **OAuth2 → URL Generator**.
2. Under **Scopes**, check `bot` and `applications.commands`.
3. Under **Bot Permissions**, check at minimum:
   - Send Messages
   - Read Message History
   - Use Slash Commands
4. Copy the generated URL, open it in your browser, select your test server, and click **Authorize**.

Your bot now appears in the server's member list as offline — that's expected until you run the code.

---

## What You Have Now

| Item | Where to find it |
|---|---|
| Bot token | Discord Developer Portal → Your app → Bot → Token |
| Test server | Your own Discord server where you can test freely |

---

**Next up:** Install Python and write the code that brings your bot online.
