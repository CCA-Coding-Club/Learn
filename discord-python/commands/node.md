---
title: Commands
type: lesson
---

# Commands

`discord.Client` is great for listening to events, but for building interactive bots you want the **commands extension** — it handles parsing, routing, and errors for you.

---

## Switching to commands.Bot

Replace `discord.Client` with `commands.Bot`:

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

bot.run(TOKEN)
```

`command_prefix='!'` means users trigger commands by typing `!commandname`.

---

## Your First Command

Add a command below the `on_ready` event:

```python
@bot.command()
async def ping(ctx):
    await ctx.send('Pong!')
```

Now type `!ping` in your Discord server — the bot replies with `Pong!`.

### The `ctx` object

`ctx` (Context) is the most important object in the commands extension. It carries everything about where and how the command was called.

| Attribute | What it contains |
|---|---|
| `ctx.send(msg)` | Send a reply to the same channel |
| `ctx.author` | The `Member` who ran the command |
| `ctx.channel` | The channel the command was sent in |
| `ctx.guild` | The server (`Guild`) the command came from |
| `ctx.message` | The original `Message` object |

---

## Command Arguments

Add parameters after `ctx` to accept user input:

```python
@bot.command()
async def greet(ctx, name: str):
    await ctx.send(f'Hello, {name}!')
```

Usage: `!greet Alice` → `Hello, Alice!`

### Multi-word arguments

By default, each word is a separate argument. Use `*` to capture the rest:

```python
@bot.command()
async def say(ctx, *, text: str):
    await ctx.send(text)
```

Usage: `!say hello world` → `hello world`

### Type conversion

discord.py automatically converts arguments to the specified type:

```python
@bot.command()
async def add(ctx, a: int, b: int):
    await ctx.send(f'{a} + {b} = {a + b}')
```

Usage: `!add 3 5` → `3 + 5 = 8`

If the user passes something that can't be converted, discord.py raises a `BadArgument` error (see below).

---

## Command Descriptions

Add a docstring to give your command a description (shown in the built-in `!help` command):

```python
@bot.command()
async def ping(ctx):
    """Replies with Pong! — use this to check if the bot is alive."""
    await ctx.send('Pong!')
```

---

## Basic Error Handling

Use `@bot.event` to catch errors globally:

```python
@bot.event
async def on_command_error(ctx, error):
    if isinstance(error, commands.MissingRequiredArgument):
        await ctx.send(f'Missing argument: `{error.param.name}`')
    elif isinstance(error, commands.BadArgument):
        await ctx.send('Invalid argument type.')
    elif isinstance(error, commands.CommandNotFound):
        pass  # silently ignore unknown commands
    else:
        raise error  # re-raise unexpected errors
```

---

## Putting It All Together

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

@bot.command()
async def ping(ctx):
    """Checks if the bot is alive."""
    await ctx.send('Pong!')

@bot.command()
async def greet(ctx, name: str):
    """Greets a user by name."""
    await ctx.send(f'Hello, {name}!')

@bot.command()
async def add(ctx, a: int, b: int):
    """Adds two numbers together."""
    await ctx.send(f'{a} + {b} = {a + b}')

@bot.event
async def on_command_error(ctx, error):
    if isinstance(error, commands.MissingRequiredArgument):
        await ctx.send(f'Missing argument: `{error.param.name}`')
    elif isinstance(error, commands.BadArgument):
        await ctx.send('Please provide valid arguments.')

bot.run(TOKEN)
```

---

**Next up:** Explore **Slash / Tree Commands** (modern app commands) or jump straight to the **Challenge** where you build your own custom command set.
