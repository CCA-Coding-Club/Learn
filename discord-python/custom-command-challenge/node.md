---
title: "Challenge: Create a Custom Command!"
type: challenge
---

# Challenge: Create a Custom Command!

Time to put everything together. Build a Discord bot that demonstrates what you've learned so far.

---

## Requirements

Your bot must have **at least 3 custom commands**. Each command must work correctly when tested in your Discord server.

### Mandatory

- [ ] At least **one command that accepts one or more arguments**
  - Example: `!greet Alice` or `!add 3 7`
- [ ] At least **one command that sends a formatted response** — use f-strings, multiple lines, or an embed (you'll learn embeds in the next node, but feel free to try)

### Recommended stretch goals

- [ ] Implement at least one command as a **slash command** using `bot.tree.command`
- [ ] Add a **help-style command** that lists what your bot can do
- [ ] Handle a **bad argument** gracefully (e.g., user passes text when you expect a number)

---

## Ideas

Stuck on what commands to build? Here are some ideas:

| Command | What it does |
|---|---|
| `!roll <sides>` | Roll a dice with N sides |
| `!flip` | Flip a coin (heads or tails) |
| `!reverse <text>` | Reverse the given text |
| `!repeat <n> <text>` | Repeat a message N times |
| `!ask <question>` | Magic 8-ball style random answer |
| `!square <n>` | Return n² |
| `!weather <city>` | Fetch real weather data from a free API |

---

## Submitting Your Code

When your bot is working:

1. Copy all of your bot's Python code.
2. Head to the **[Challenges page](/pages/challenges.html)** on this site.
3. Find the **"Custom Discord Command"** challenge and submit your code there.

Your submission will be saved and visible to other club members for inspiration.

---

## What We're Looking For

| Criteria | Description |
|---|---|
| It runs | `python bot.py` starts without errors |
| Commands respond | Each command produces the correct output when tested |
| Arguments work | Argument-based commands handle both valid and invalid input |
| Code is readable | Variable names make sense; no redundant comments |

---

Once you've submitted, the next two nodes — **Embeds** and **Cogs** — will unlock. You can tackle them in either order.
