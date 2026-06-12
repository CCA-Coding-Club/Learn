---
title: Cogs
type: lesson
---

# Cogs

As your bot grows, putting everything in one file gets messy. **Cogs** let you split commands and events into separate, reusable modules.

---

## What Is a Cog?

A Cog is a Python class that inherits from `commands.Cog`. You move your commands and event listeners into it, then load it from your main bot file with one line.

---

## Project Structure with Cogs

```
my-bot/
├── bot.py          ← main file, loads cogs
├── .env
└── cogs/
    ├── __init__.py   ← empty file, makes cogs a package
    ├── general.py    ← general commands
    └── moderation.py ← moderation commands
```

---

## Creating a Cog

**`cogs/general.py`**

```python
import discord
from discord.ext import commands

class General(commands.Cog):
    """General-purpose commands."""

    def __init__(self, bot: commands.Bot):
        self.bot = bot

    @commands.command()
    async def ping(self, ctx):
        """Check if the bot is alive."""
        await ctx.send('Pong!')

    @commands.command()
    async def greet(self, ctx, name: str):
        """Greet someone by name."""
        await ctx.send(f'Hello, {name}!')

    @commands.Cog.listener()
    async def on_member_join(self, member):
        channel = member.guild.system_channel
        if channel:
            await channel.send(f'Welcome {member.mention}!')

async def setup(bot: commands.Bot):
    await bot.add_cog(General(bot))
```

Key points:
- Commands become methods with `self` as the first parameter.
- Use `@commands.command()` instead of `@bot.command()`.
- Events use `@commands.Cog.listener()` instead of `@bot.event`.
- The module **must** have an `async def setup(bot)` function at the bottom.

---

## Loading Cogs in bot.py

```python
import discord
from discord.ext import commands
from dotenv import load_dotenv
import os

load_dotenv()
TOKEN = os.getenv('TOKEN')

intents = discord.Intents.default()
intents.message_content = True
bot = commands.Bot(command_prefix='!', intents=intents)

@bot.event
async def on_ready():
    print(f'Logged in as {bot.user}')

async def main():
    async with bot:
        await bot.load_extension('cogs.general')
        await bot.start(TOKEN)

import asyncio
asyncio.run(main())
```

`bot.load_extension('cogs.general')` — the string is the Python module path (dot-separated, same as an `import` statement).

---

## Loading Multiple Cogs

```python
EXTENSIONS = [
    'cogs.general',
    'cogs.moderation',
    'cogs.fun',
]

async def main():
    async with bot:
        for ext in EXTENSIONS:
            await bot.load_extension(ext)
        await bot.start(TOKEN)
```

---

## Hot-Reloading a Cog

During development you can reload a cog without restarting the bot:

```python
@bot.command()
@commands.is_owner()
async def reload(ctx, extension: str):
    """Reload a cog (owner only)."""
    await bot.reload_extension(f'cogs.{extension}')
    await ctx.send(f'Reloaded `{extension}`.')
```

Usage: `!reload general` — reloads `cogs/general.py` without downtime.

---

## Cog with an __init__ that stores state

Cogs can hold instance variables, useful for storing data across commands:

```python
class Counter(commands.Cog):
    def __init__(self, bot):
        self.bot = bot
        self.count = 0

    @commands.command()
    async def count(self, ctx):
        self.count += 1
        await ctx.send(f'Count: {self.count}')
```

---

## Summary

| Concept | Syntax |
|---|---|
| Define a cog | `class MyCog(commands.Cog)` |
| Command in cog | `@commands.command()` |
| Event in cog | `@commands.Cog.listener()` |
| Required export | `async def setup(bot): await bot.add_cog(MyCog(bot))` |
| Load from bot | `await bot.load_extension('cogs.mycog')` |
| Reload at runtime | `await bot.reload_extension('cogs.mycog')` |

---

**You've completed the Discord Bots with Python path!** Your next steps could be:
- Add a database (SQLite or Firestore) to persist data between restarts
- Explore the full [discord.py documentation](https://discordpy.readthedocs.io/en/stable/)
- Build a music bot, moderation bot, or game bot
