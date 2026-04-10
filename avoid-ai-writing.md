# Avoid AI Writing — Reference Rules

Adapted from the [avoid-ai-writing](https://github.com/conorbronsdon/avoid-ai-writing) skill by
Conor Bronsdon (MIT License). Included here as a bundled reference for resume and cover letter
AI-isms detection.

For standalone use, detect-only mode, and the full rule set, see the original skill.

---

## Modes

**`rewrite`** (default) — Flag AI-isms and rewrite the text to fix them.

**`detect`** — Flag AI-isms only. No rewriting. Use when you want to see what's flagged before
deciding what to fix yourself.

---

## What to Remove or Fix

### Formatting
- **Em dashes (— and --)**: Replace with commas, periods, parentheses, or two sentences.
  Hard max: one per 1,000 words.
- **Bold overuse**: Strip bold from most phrases. One bolded phrase per major section at most.
- **Emoji in headers**: Remove entirely.
- **Excessive bullet lists**: Convert to prose paragraphs unless content is genuinely list-like.

### Sentence Structure
- **"It's not X — it's Y"**: Rewrite as a direct positive statement.
- **Hollow intensifiers**: Cut `genuine`, `truly`, `quite frankly`, `to be honest`, `let's be clear`,
  `it's worth noting that`.
- **Vague endorsement**: Cut `worth reading`, `worth a look`, `worth exploring`. Say *why* instead.
- **Hedging**: Cut `perhaps`, `could potentially`, `it's important to note that`. Make the point directly.
- **Compulsive rule of three**: Vary groupings — two items, four items, a full sentence.

---

## Words and Phrases to Replace

### Tier 1 — Always Replace

| Replace | With |
|---|---|
| delve / delve into | explore, dig into, look at |
| landscape (metaphor) | field, space, industry, world |
| tapestry | (describe the actual complexity) |
| realm | area, field, domain |
| paradigm | model, approach, framework |
| embark | start, begin |
| beacon | (rewrite entirely) |
| testament to | shows, proves, demonstrates |
| robust | strong, reliable, solid |
| comprehensive | thorough, complete, full |
| cutting-edge | latest, newest, advanced |
| leverage (verb) | use |
| pivotal | important, key, critical |
| underscores | highlights, shows |
| meticulous / meticulously | careful, detailed, precise |
| seamless / seamlessly | smooth, easy, without friction |
| game-changer / game-changing | describe what specifically changed |
| utilize | use |
| holistic / holistically | complete, full, whole |
| actionable | practical, useful, concrete |
| impactful | effective, significant |
| learnings | lessons, findings, takeaways |
| thought leadership | expert, authority (or describe the actual contribution) |
| best practices | what works, proven methods, standard approach |
| at its core | (cut — just state the thing) |
| synergy / synergies | (describe the actual combined effect) |
| in order to | to |
| serves as | is |
| commence | start, begin |
| endeavor | effort, attempt, try |
| embrace (metaphor) | adopt, accept, use, switch to |

### Tier 2 — Flag When 2+ Appear in the Same Paragraph

| Replace | With |
|---|---|
| harness | use, take advantage of |
| navigate / navigating | work through, handle, deal with |
| foster | encourage, support, build |
| elevate | improve, raise, strengthen |
| streamline | simplify, speed up |
| empower | enable, let, allow |
| spearhead | lead, drive, run |
| revolutionize | change, transform, reshape |
| nuanced | specific, subtle, detailed |
| crucial | important, key, necessary |
| encompass | include, cover, span |
| paramount | most important, top priority |

### Tier 3 — Flag Only at High Density

Only flag when these words make up a noticeable fraction of the text (~3%+).

| Word | What to do |
|---|---|
| significant / significantly | Replace some with specifics: numbers, comparisons, examples |
| innovative / innovation | Describe what's actually new |
| dynamic / dynamics | Name the actual forces or changes |
| scalable / scalability | Describe what scales and to what |
| exceptional / exceptionally | Cite what makes it an exception |
| world-class / state-of-the-art | Cite a benchmark or comparison |

---

## Template Phrases to Avoid

- "a [adjective] step towards [adjective] AI infrastructure" → describe the specific capability
- "Whether you're [X] or [Y]" → pick the audience you're addressing, or cut
- "I recently had the pleasure of [verb]-ing" → just say what happened

## Transition Phrases to Cut

- "Moreover" / "Furthermore" / "Additionally" → restructure or use "and," "also"
- "In today's [X]" / "In an era where" → cut or use specific context
- "It's worth noting that" / "Notably" → just state the fact
- "In conclusion" / "In summary" → your conclusion should be obvious
- "At the end of the day" → cut
- "When it comes to" → just talk about the thing

---

## Resume-Specific Modifications

When applying this to a resume or cover letter:

- **Skip:** excessive bullets rule — bullet structure is correct on a resume
- **Skip:** em dash rule in bullet lines — acceptable in resume formatting
- **Rescue rule:** a flagged verb is acceptable if a specific metric immediately follows it
  - ❌ "Streamlined operations across the org"
  - ✅ "Streamlined operations across 6 offices, cutting overhead by $200K"

**P0 resume AI-isms** (fix immediately):
- "results-driven," "proven track record," "passionate professional," "dynamic leader," "go-getter"

**P1 resume AI-isms** (fix before submitting):
- leveraged, utilized, robust, comprehensive, seamless, impactful, synergy, holistic

**P2 resume AI-isms** (polish if time allows):
- spearheaded (overused — use sparingly)
- "responsible for"
- "worked closely with"

---

## Context Profiles

Pass an optional profile to adjust strictness. Auto-detected from content cues if not specified.

| Profile | Use for | Key adjustments |
|---|---|---|
| `linkedin` | Short-form social posts | Relaxed em dashes, bold OK, bullets OK |
| `blog` | Default long-form prose | All rules at full strength |
| `technical-blog` | Long-form with code/architecture | Technical terms get a pass |
| `investor-email` | High-trust audience | Extra strict on promotional language |
| `docs` | READMEs, documentation | Clarity over voice |
| `casual` | Slack, internal notes | P0 only |

---

## Severity Tiers

**P0 — Credibility killers** (fix immediately)
- Chatbot artifacts: "Great question!", "I hope this helps!"
- Vague attributions without sources: "Experts believe"
- Cutoff disclaimers: "As of my last update"

**P1 — Obvious AI smell** (fix before publishing)
- Tier 1 word-list violations
- Template phrases and slot-fill constructions
- Bold overuse
- "Let's" transition openers

**P2 — Stylistic polish** (fix when time allows)
- Generic conclusions
- Compulsive rule of three
- Uniform paragraph length
- Transition phrases

---

## Tone Calibration

The goal is writing that sounds like a person wrote it. Direct. Specific. The writing should
demonstrate confidence, not assert it.

1. **Vary sentence length** — mix short with long. Fragments are fine.
2. **Be concrete** — replace vague claims with numbers, names, dates, or examples.
3. **Have a voice** — where appropriate, use first person, state preferences, show reactions.
4. **Cut the neutrality** — humans have opinions. Take a position.
5. **Earn your emphasis** — don't tell the reader something is interesting. Make it interesting.
