---
title: Creating the Bot
type: lesson
---

# Creating the Bot

Time to write Python code that connects to Discord and brings your bot online.

---

## Prerequisites

- Python 3.10 or newer — download from [python.org](https://www.python.org/downloads/)
- A bot token from the previous step

---

## Step 1: Set Up Your Project

Create a folder for your bot and open it in your editor (VS Code recommended).

```
my-bot/
├── bot.py
└── .env
```

---

## Step 2: Install discord.py

Open a terminal in your project folder and run:

```bash
pip install discord.py python-dotenv
```

- **discord.py** — the library that talks to Discord's API
- **python-dotenv** — loads secrets from a `.env` file so you never hardcode your token

---

## Step 3: Store Your Token Safely

Create a `.env` file in your project folder:

```
TOKEN=paste_your_token_here
```

> Never commit `.env` to Git. Add it to `.gitignore`:
> ```
> .env
> ```

---

## Step 4: Write bot.py

```python
import discord
from dotenv import load_dotenv
import os

load_dotenv()
TOKEN = os.getenv('TOKEN')

intents = discord.Intents.default()
intents.message_content = True

client = discord.Client(intents=intents)

@client.event
async def on_ready():
    print(f'Logged in as {client.user}')

client.run(TOKEN)
```

### What each part does

| Line | Purpose |
|---|---|
| `load_dotenv()` | Reads `.env` and puts variables into the environment |
| `os.getenv('TOKEN')` | Retrieves the token without hardcoding it |
| `discord.Intents` | Controls which events Discord sends to your bot |
| `intents.message_content = True` | Required to read message text |
| `@client.event` | Registers an event handler |
| `on_ready()` | Called once when the bot successfully connects |
| `client.run(TOKEN)` | Starts the bot — this line blocks until the bot stops |

---

## Step 5: Run Your Bot

```bash
python bot.py
```

You should see:

```
Logged in as My First Bot#1234
```

Check your Discord server — the bot should now show as **online**.

---

## Understanding the Event Loop

discord.py uses Python's `asyncio` library under the hood. All event handlers are `async def` functions. You must `await` any call that might take time (sending a message, fetching a user, etc.).

```python
@client.event
async def on_message(message):
    if message.author == client.user:
        return  # ignore the bot's own messages
    if message.content == 'hello':
        await message.channel.send('Hello!')
```

`on_message` fires every time a message is sent in any channel your bot can see.

---

## Troubleshooting

| Problem | Likely cause |
|---|---|
| `LoginFailure` | Token is wrong or revoked — reset it in the Developer Portal |
| Bot online but not responding | Missing `message_content` intent |
| `ModuleNotFoundError: discord` | Run `pip install discord.py` again |

---

**Next up:** Learn how to add proper commands so users can interact with your bot.
