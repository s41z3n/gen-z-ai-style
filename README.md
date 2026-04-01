# Gen Z AI Style Guide 🧠

A single system prompt that teaches any AI to write in a punchy, Gen Z voice. No corporate fluff. No filler. Every word earns its place.

## What's in it

Four files:
- `SYSTEM-PROMPT.md` — the main prompt (voice rules, hooks, formatting, use cases)
- `VOCAB.md` — 1,100+ Gen Z terms organized by category (human-readable)
- `vocab.json` — same vocabulary in machine-readable JSON (for APIs, scripts, dynamic injection)
- `INTEGRATION.md` — setup guide for every AI platform (ChatGPT, Claude, Cursor, OpenClaw, APIs)

Drop it into:
- ChatGPT / Claude / Gemini system prompts
- Cursor / Windsurf / Claude Code rules
- Any AI tool that takes custom instructions
- Blog generators, carousel makers, social tools
- **Any AI agent via `vocab.json`** — programmatic integration ready

## What it teaches

- **Voice & tone** — direct, confident, relatable
- **Vocabulary swaps** — corporate speak → real speak
- **1,100+ Gen Z terms** — slang, abbreviations, reactions, tech, gaming, business
- **Hooks & openers** — stop the scroll
- **Formatting rules** — short sentences, bold, line breaks
- **Use cases** — blog posts, carousels, threads, YouTube, emails, product descriptions
- **Anti-patterns** — what to catch and rewrite immediately
- **Machine-readable JSON** — for AI agent integration and dynamic injection

## Before / After

**Corporate:**
> "Furthermore, it's worth noting that our platform leverages cutting-edge AI to optimize workflow efficiency."

**Gen Z:**
> "So basically — this uses AI to make your work faster. No cap."

**Corporate:**
> "In today's fast-paced digital landscape, businesses must adapt to survive."

**Gen Z:**
> "Nobody's talking about this, but here's the thing about going digital..."

## How to use

### Option 1: Copy-Paste (30 seconds)
1. Open `SYSTEM-PROMPT.md`
2. Copy the whole thing
3. Paste into your AI's system prompt / custom instructions
4. Done

### Option 2: Programmatic (for AI agents)
1. Load `vocab.json`
2. Filter by category or intensity as needed
3. Inject random terms into your system prompt
4. See `INTEGRATION.md` for code examples

### Option 3: Platform Setup
See `INTEGRATION.md` for step-by-step guides:
- ChatGPT Custom Instructions
- Claude Projects
- Cursor / Windsurf / Claude Code rules
- OpenClaw AGENTS.md
- API integration (Python/JS)
- Custom GPT Actions

That's it. One file. Works everywhere.

## See It In Action

**Before (corporate):**
> "Furthermore, it's worth noting that our platform leverages cutting-edge AI to optimize workflow efficiency."

**After (Gen Z):**
> "So basically — this uses AI to make your work faster. No cap."

**Before:**
> "In today's fast-paced digital landscape, businesses must adapt to survive."

**After:**
> "Nobody's talking about this, but here's the thing about going digital..."

## Demo: Live Integration

Here's how an AI agent loads and uses this repo in real-time:

```python
# Load the vocab
import json, random
with open('vocab.json') as f:
    vocab = json.load(f)

# Pick 10 random high-intensity terms
hot = [t for t in vocab['terms'] if t['intensity'] >= 4]
sample = random.sample(hot, 10)

# Build system prompt
vocab_text = "\n".join(f"- {t['term']}: {t['meaning']}" for t in sample)
system = f"""Write in Gen Z voice. Sprinkle these naturally:
{vocab_text}
Short sentences. No corporate speak. Have opinions."""

# → Every AI response now sounds Gen Z
```

See `INTEGRATION.md` for full setup guides, code samples, and platform-specific instructions.

## Why it works

People scroll fast. Corporate speak gets skipped. Gen Z voice stops the scroll because it sounds like a real person talking — not a press release.

Short sentences. Real words. No fluff.

## Data Sources

- **Original research** — curated from social media, TikTok, Twitter, Discord
- **Gabb.com** — comprehensive teen slang reference (gabb.com/blog/teen-slang/)
- **Community contributions** — PRs and issues welcome

## Contributing

Found a Gen Z term we missed? Open a PR or issue. We want this to be the definitive reference.
Add terms to both `VOCAB.md` (human-readable) and `vocab.json` (machine-readable).

## License

MIT — use it however you want.
