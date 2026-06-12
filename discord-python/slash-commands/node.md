---
title: Slash / Tree Commands
type: lesson
---

# Slash / Tree Commands

Slash commands (also called *application commands*) are the modern way to interact with bots. They appear in Discord's UI as you type `/`, complete with autocomplete and built-in argument hints.

---

## Prefix vs Slash Commands

| Feature | Prefix (`!cmd`) | Slash (`/cmd`) |
|---|---|---|
| Discovery | Users must know the prefix | Shows up in Discord's `/` menu |
| Arguments | Parsed from raw text | Typed into labelled fields |
| Response object | `ctx` (Context) | `interaction` (Interaction) |
| Registration | Instant, no sync needed | Must sync with Discord |

---

## The App Command Tree

`bot.tree` is the command tree — a container for all your slash commands.

```python
import discord
from discord.ext import commands
from discord import app_commands
from dotenv import load_dotenv
import os

load_dotenv()
TOKEN = os.getenv('TOKEN')

intents = discord.Intents.default()
bot = commands.Bot(command_prefix='!', intents=intents)
```

---

## Your First Slash Command

```python
@bot.tree.command(name='ping', description='Check if the bot is alive')
async def ping(interaction: discord.Interaction):
    await interaction.response.send_message('Pong!')
```

Notice `interaction` replaces `ctx`. You respond with `interaction.response.send_message()` instead of `ctx.send()`.

---

## Syncing Commands with Discord

Slash commands must be **synced** — sent to Discord's servers so they appear in the UI. Add this to `on_ready`:

```python
@bot.event
async def on_ready():
    synced = await bot.tree.sync()
    print(f'Synced {len(synced)} command(s)')
    print(f'Logged in as {bot.user}')
```

> After syncing, **global** commands can take up to 1 hour to appear for all users. For testing, sync to a specific guild (server) instead — it's instant:
>
> ```python
> TEST_GUILD = discord.Object(id=YOUR_SERVER_ID_HERE)
>
> @bot.event
> async def on_ready():
>     bot.tree.copy_global_to(guild=TEST_GUILD)
>     await bot.tree.sync(guild=TEST_GUILD)
> ```
>
> Find your server ID by enabling Developer Mode (Discord Settings → Advanced), then right-clicking your server name.

---

## Adding Parameters

Use Python type annotations — discord.py uses them to show the right input field in Discord's UI:

```python
@bot.tree.command(name='greet', description='Greet someone')
@app_commands.describe(name='The name to greet')
async def greet(interaction: discord.Interaction, name: str):
    await interaction.response.send_message(f'Hello, {name}!')
```

`@app_commands.describe` adds the small description shown under each parameter in Discord.

### Supported parameter types

| Python type | Discord input |
|---|---|
| `str` | Text field |
| `int` | Number (integer) |
| `float` | Number (decimal) |
| `bool` | True/False toggle |
| `discord.Member` | User picker |
| `discord.TextChannel` | Channel picker |

---

## The Interaction Object

`interaction` gives you everything you need to respond:

| Method / Attribute | Purpose |
|---|---|
| `interaction.response.send_message(content)` | Send the first reply |
| `interaction.followup.send(content)` | Send additional messages after the first |
| `interaction.user` | The member who used the command |
| `interaction.guild` | The server |
| `interaction.channel` | The channel |

> You must respond within **3 seconds** or Discord will show an error. If your code takes longer, defer first:
> ```python
> await interaction.response.defer()
> # ... do slow work ...
> await interaction.followup.send('Done!')
> ```

---

## Full Example

```python
import discord
from discord.ext import commands
from discord import app_commands
from dotenv import load_dotenv
import os

load_dotenv()
TOKEN = os.getenv('TOKEN')

intents = discord.Intents.default()
bot = commands.Bot(command_prefix='!', intents=intents)

@bot.event
async def on_ready():
    synced = await bot.tree.sync()
    print(f'Synced {len(synced)} command(s). Logged in as {bot.user}')

@bot.tree.command(name='ping', description='Check if the bot is alive')
async def ping(interaction: discord.Interaction):
    await interaction.response.send_message('Pong!')

@bot.tree.command(name='add', description='Add two numbers')
@app_commands.describe(a='First number', b='Second number')
async def add(interaction: discord.Interaction, a: int, b: int):
    await interaction.response.send_message(f'{a} + {b} = {a + b}')

bot.run(TOKEN)
```

---

**Next up:** Apply everything in the **Challenge: Custom Command** node.
