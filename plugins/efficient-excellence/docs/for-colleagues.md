# Efficient Excellence — a plain-English guide

For a non-technical (but AI-forward) colleague who wants to use this.

## What it is
A Claude Code plugin that automatically uses the *right* AI model for each part of a job — the top models for the hard thinking, fast and cheap ones for the simple bits, and plain code (no AI at all) for anything mechanical. You get top-quality results without paying top-tier cost or waiting for everything.

## How to install and use
1. Open **Claude Code** and paste these two lines. (Opening the repo link in a browser doesn't install it — these commands do.)
   ```
   /plugin marketplace add gguerecaadair/efficient-excellence-marketplace
   /plugin install efficient-excellence@vse-edu-bm-plugins
   ```
2. Set your main model to **Opus** — type `/model` and pick Opus. This is the "coordinator" that routes everything.
3. **Start a fresh chat.** That's it — it now runs automatically, with nothing to switch on per task.

*Optional, for maximum quality every session:* add `"model": "opus", "effortLevel": "xhigh"` to your `~/.claude/settings.json` — or just ask Claude Code to do it for you.

## How it works
Every request goes first to a smart **coordinator** (Opus). It reads what you've asked, breaks it into pieces, and sends each piece to the best-suited option:

- **Mechanical work** — collecting data, merging files, counting, running tests → done as plain code, **zero AI cost**.
- **Quick, simple parts** — looking things up, tables, tidy-ups, reading across files → **fast, low-cost models** (Sonnet).
- **The hard thinking** — planning, tricky problems, and double-checking important work before it ships → the **most capable models, at full depth** (Opus and Fable).

It all happens on its own — you don't pick anything. The result is top-quality where it matters, and quick and economical everywhere else.

## One handy lever
For a job that deserves the absolute best effort, type **`ultracode`** in your message — that turns everything up to maximum for that one task.

## How you'll know it's working
A small readout at the bottom of Claude Code shows the running cost of the session, and the AI tells you which model handled each hard step.
