# Integration Guide — Gen Z AI Style

How to inject Gen Z voice into any AI agent. Copy-paste ready.

---

## 🚀 Quick Start (30 seconds)

1. Open your AI's system prompt / custom instructions
2. Copy the contents of `SYSTEM-PROMPT.md`
3. Paste it in
4. Done. Every response now sounds Gen Z.

---

## 📋 Platform-Specific Setup

### ChatGPT (Custom Instructions)

1. Go to **Settings → Personalization → Custom Instructions**
2. In "How would like ChatGPT to respond?", paste:
```
You write in a punchy Gen Z voice. See attached style guide.
Short sentences. No corporate fluff. Have opinions.
Vocab: no cap, bussin, mid, slaps, fire, valid, based, cooked, W/L, periodt.
Full reference: [paste SYSTEM-PROMPT.md here]
```
3. Save → every conversation uses Gen Z voice

### Claude (Projects)

1. Create a new **Project**
2. In Project Knowledge, upload:
   - `SYSTEM-PROMPT.md`
   - `VOCAB.md` (or `vocab.json` for structured access)
3. In Project Instructions, paste:
```
Follow the style guide in project knowledge. Gen Z voice always.
Short sentences. Bold takes. No filler. Every word earns its place.
```
4. All chats in this project use Gen Z voice

### Claude Code / Cursor / Windsurf (Rules File)

Create a rule file in your project root:

**Claude Code** → `CLAUDE.md`:
```markdown
# Writing Rules
Follow the Gen Z style guide at [path/to/SYSTEM-PROMPT.md].
All user-facing text, docs, and comments use Gen Z voice.
```

**Cursor** → `.cursorrules`:
```markdown
Write all documentation and user-facing text in Gen Z voice.
Reference: [path/to/SYSTEM-PROMPT.md]
Style: short sentences, bold takes, no corporate speak.
```

**Windsurf** → `.windsurfrules`:
```markdown
Gen Z writing style for all docs and UI text.
See SYSTEM-PROMPT.md for full guide.
```

### OpenClaw (AGENTS.md / SOUL.md)

Add to your SOUL.md or AGENTS.md:
```markdown
## Writing Style
- ALL content uses Gen Z lingo (lowercase, opinionated, casual)
- Reference: /path/to/gen-z-ai-style/SYSTEM-PROMPT.md
- Vocab: /path/to/gen-z-ai-style/vocab.json
- Key terms: ate, bussin, mid, slay, no cap, fr fr, its giving, W/L, cooked, goes hard
- Avoid corporate speak: no "utilize", "leverage", "comprehensive"
```

### API Integration (Programmatic)

Use `vocab.json` to inject terms dynamically:

```python
import json

# Load the vocabulary
with open('vocab.json') as f:
    vocab = json.load(f)

# Build a random vocab sample for system prompt
import random
sample = random.sample(vocab['terms'], 20)
vocab_text = "\n".join(f"- {t['term']}: {t['meaning']}" for t in sample)

system_prompt = f"""You write in Gen Z voice.
Use these terms naturally (don't force them):
{vocab_text}

Rules: short sentences, no corporate speak, have opinions.
"""

# Use with any LLM API
response = openai.chat.completions.create(
    model="gpt-4",
    messages=[
        {"role": "system", "content": system_prompt},
        {"role": "user", "content": "Write a blog post about AI agents"}
    ]
)
```

### Custom GPT (Actions)

1. Create a Custom GPT
2. In Instructions, paste `SYSTEM-PROMPT.md` contents
3. Add an Action that fetches `vocab.json` from GitHub:
```
GET https://raw.githubusercontent.com/s41z3n/gen-z-ai-style/main/vocab.json
```
4. The GPT can dynamically pull vocab terms as needed

---

## 🔧 Advanced Integration

### Filter by Category

`vocab.json` has categories you can filter:

```python
# Get only core slang (must-know terms)
core = [t for t in vocab['terms'] if t['category'] == 'core']

# Get only tech/developer terms
tech = [t for t in vocab['terms'] if t['category'] == 'tech']

# Get high-intensity terms only (4-5)
intense = [t for t in vocab['terms'] if t['intensity'] >= 4]
```

### Dynamic Vocab Injection

Instead of a static prompt, inject random terms per conversation:

```python
def build_prompt(topic=None, num_terms=15):
    with open('vocab.json') as f:
        vocab = json.load(f)

    terms = vocab['terms']
    if topic:
        # Bias toward relevant categories
        relevant = [t for t in terms if topic in t.get('example', '').lower()]
        other = [t for t in terms if t not in relevant]
        sample = random.sample(relevant, min(num_terms//2, len(relevant))) + \
                 random.sample(other, min(num_terms//2, len(other)))
    else:
        sample = random.sample(terms, min(num_terms, len(terms)))

    vocab_block = "\n".join(f"- **{t['term']}**: {t['meaning']}" for t in sample)

    return f"""Write in Gen Z voice. Sprinkle these terms naturally:
{vocab_block}

{vocab['anti_patterns'][0]} ← NEVER write like this.
Short sentences. Bold takes. No filler."""
```

### Validation Script

Check if generated content uses Gen Z voice properly:

```python
def validate_genz(text, vocab_path='vocab.json'):
    with open(vocab_path) as f:
        vocab = json.load(f)

    terms_used = [t['term'] for t in vocab['terms'] if t['term'].lower() in text.lower()]
    anti_patterns = [p for p in vocab['anti_patterns'] if p.lower() in text.lower()]

    return {
        'genz_terms_used': len(terms_used),
        'terms': terms_used,
        'anti_patterns_found': anti_patterns,
        'score': len(terms_used) - len(anti_patterns) * 3,
        'verdict': 'bussin' if len(terms_used) >= 3 and not anti_patterns else 'mid'
    }
```

---

## 📊 Term Stats

- **Total terms:** 1,100+
- **Categories:** 12 (core, agreement, reactions, money, tech, gaming, social, lifestyle, abbreviations, descriptors, phrases, parental)
- **Intensity range:** 1 (subtle) → 5 (maximum impact)
- **Sources:** Original research + gabb.com teen slang database
- **Format:** Markdown (VOCAB.md) + JSON (vocab.json)

---

## 💡 Tips

1. **Don't overdo it.** 3-5 slang terms per paragraph max. Forced slang is cringe.
2. **Match intensity to context.** Blog posts = intensity 3-4. Tweets = 4-5. Docs = 2-3.
3. **Use `vocab_swaps`** from the JSON — replace corporate words automatically.
4. **Start with hooks** from the JSON `hooks` array for engaging openers.
5. **End with closers** from the JSON `closers` array for strong CTAs.

---

## 🔗 Links

- **Repo:** github.com/s41z3n/gen-z-ai-style
- **vocab.json:** Machine-readable, filterable, API-ready
- **SYSTEM-PROMPT.md:** Full style guide (copy-paste into any AI)
- **VOCAB.md:** 1,100+ terms organized by category (human-readable)

---

**TL;DR:** Copy SYSTEM-PROMPT.md → paste into your AI → done. For programmatic use, load vocab.json and inject terms dynamically. One repo, works everywhere.
