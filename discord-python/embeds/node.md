---
title: Embeds
type: lesson
---

# Embeds

Embeds are rich, styled message cards that make your bot's responses much more readable and professional than plain text.

---

## What Is an Embed?

An embed is a bordered card inside a Discord message. It can have a title, description, colour bar, fields, footer, thumbnail, and image.

---

## Creating a Basic Embed

```python
@bot.command()
async def info(ctx):
    embed = discord.Embed(
        title='Bot Info',
        description='This is my custom Discord bot.',
        color=discord.Color.blue()
    )
    await ctx.send(embed=embed)
```

The three most common constructor arguments:

| Argument | Type | Purpose |
|---|---|---|
| `title` | `str` | Bold header at the top |
| `description` | `str` | Main body text (supports markdown) |
| `color` | `discord.Color` or `int` | The coloured left-side bar |

### Colour options

```python
discord.Color.blue()
discord.Color.green()
discord.Color.red()
discord.Color.gold()
discord.Color.purple()
discord.Color.from_rgb(255, 128, 0)  # custom RGB
0x2ecc71                              # raw hex integer
```

---

## Adding Fields

Fields let you display key-value pairs in a grid layout:

```python
embed = discord.Embed(title='Server Stats', color=discord.Color.green())
embed.add_field(name='Members', value='42', inline=True)
embed.add_field(name='Channels', value='15', inline=True)
embed.add_field(name='Owner', value='Alice', inline=False)
await ctx.send(embed=embed)
```

- `inline=True` — fields sit side by side (up to 3 per row)
- `inline=False` — field takes its own full-width row

---

## Thumbnail and Image

```python
embed.set_thumbnail(url='https://example.com/small-icon.png')
embed.set_image(url='https://example.com/wide-banner.png')
```

- **Thumbnail** — small image in the top-right corner
- **Image** — large image at the bottom of the embed

You can also use the guild's icon or a user's avatar:

```python
embed.set_thumbnail(url=ctx.guild.icon.url)
embed.set_thumbnail(url=ctx.author.display_avatar.url)
```

---

## Author and Footer

```python
embed.set_author(
    name=ctx.author.display_name,
    icon_url=ctx.author.display_avatar.url
)
embed.set_footer(text='CCA Coding Club Bot', icon_url=ctx.guild.icon.url)
```

---

## Timestamp

Add a timestamp to the footer area:

```python
import datetime

embed = discord.Embed(
    title='Current Time',
    timestamp=datetime.datetime.now(datetime.timezone.utc)
)
```

---

## Embed Limits

Discord enforces strict character limits. Exceeding them raises an `HTTPException`.

| Field | Limit |
|---|---|
| Title | 256 characters |
| Description | 4096 characters |
| Field name | 256 characters |
| Field value | 1024 characters |
| Footer text | 2048 characters |
| Number of fields | 25 |
| Total embed size | 6000 characters |

---

## Full Example

```python
import discord
from discord.ext import commands
import datetime
from dotenv import load_dotenv
import os

load_dotenv()
bot = commands.Bot(command_prefix='!', intents=discord.Intents.default())

@bot.command()
async def profile(ctx, member: discord.Member = None):
    """Show a member's profile card."""
    member = member or ctx.author  # default to command caller

    embed = discord.Embed(
        title=member.display_name,
        description=f'Member of {ctx.guild.name}',
        color=member.color if member.color != discord.Color.default() else discord.Color.blurple(),
        timestamp=datetime.datetime.now(datetime.timezone.utc)
    )
    embed.set_thumbnail(url=member.display_avatar.url)
    embed.add_field(name='Joined Server', value=member.joined_at.strftime('%b %d, %Y'), inline=True)
    embed.add_field(name='Account Created', value=member.created_at.strftime('%b %d, %Y'), inline=True)
    embed.set_footer(text=f'ID: {member.id}')

    await ctx.send(embed=embed)

bot.run(os.getenv('TOKEN'))
```

Usage: `!profile` or `!profile @Alice`

---

**Next up:** Learn about **Cogs** to keep your growing bot organised as you add more commands.
