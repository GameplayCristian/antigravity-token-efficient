# Antigravity Token Efficient

One-click installer. Reduces output verbosity in [Google Antigravity](https://antigravity.google) (VS Code AI coding assistant). Drop-in, no code changes.

**[Leer en Español](README_ES.md)**

---

## The Problem

By default, AI models in Antigravity:
- Open every response with "Sure!", "Great question!", "Absolutely!"
- End with "I hope this helps! Let me know if you need anything!"
- Use em-dashes, smart quotes, Unicode characters
- Restate your question before answering
- Add unsolicited suggestions beyond what you asked
- Over-engineer code with abstractions you never requested

All of this wastes tokens. None of it adds value.

## Benchmark Results

Same prompt: *"What does bot.py do?"*

| | Without Rules | With Rules |
|---|---|---|
| Words | ~400 | ~70 |
| Reduction | — | **~82%** |
| Numbered sections | 5 | 0 |
| Filler phrases | Yes | No |
| Unsolicited suggestions | Yes | No |

**Same information. Zero signal loss. ~80% fewer output tokens.**

### Before (without rules)

```
Great question! 😊 I can see you're working with a really interesting project.
Let me take a look at that file for you. The bot.py file is the main engine
of your Clash of Clans automation bot. It handles the complete lifecycle...
[400+ words with 5 numbered sections, greetings, and filler]
...I hope this helps! Feel free to ask if you need anything else! 🚀
```

### After (with rules)

```
bot.py is the main automation script for Clash of Clans. Connects to
BlueStacks via ADB, captures screen with OpenCV for template matching,
trains troops, searches for villages meeting resource thresholds in
config.json, and launches attacks via ataque.py.
```

## Installation

### Option 1: One-Click Installer (Recommended)

1. Download `install_rules_EN.bat`
2. Double-click it
3. Done. Rules are installed globally for all projects.

### Option 2: Manual

Copy the contents of [`GEMINI.md`](GEMINI.md) to:

```
C:\Users\<YourUsername>\.gemini\GEMINI.md
```

Create the `.gemini` folder if it doesn't exist.

## How It Works

Antigravity reads `GEMINI.md` from `~/.gemini/` at the start of every conversation. The rules in this file instruct the model to:

- Skip greetings, farewells, and filler
- Respond in 2-3 lines for simple questions
- Never restate the user's question
- Never give unsolicited suggestions
- Go straight to the result

The rules are model-agnostic and work with all models available in Antigravity (Gemini, Claude, etc.).

## Files

| File | Description |
|---|---|
| `GEMINI.md` | The rules file (reference copy) |
| `install_rules_EN.bat` | One-click installer (English rules) |
| `install_rules_ES.bat` | One-click installer (Spanish rules) |

## When This Helps vs When It Doesn't

**Works best for:**
- Regular coding sessions with high output volume
- Repeated structured tasks where verbosity compounds
- Teams who need consistent, parseable output

**Not worth it for:**
- Single short queries (the file adds input tokens every message)
- Exploratory work where detailed explanations are the point

## Override Rule

User instructions always win. If you explicitly ask for a detailed explanation, the model will follow your instruction. The rules never fight you.

## Uninstall

Delete `C:\Users\<YourUsername>\.gemini\GEMINI.md` or clear its contents.

## Credits

Inspired by [claude-token-efficient](https://github.com/drona23/claude-token-efficient) by Drona Gangarapu. Adapted for Google Antigravity.

## License

MIT - free to use, modify, and distribute.
