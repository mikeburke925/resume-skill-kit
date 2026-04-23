# AI Writing Rules — Resume & Cover Letter Reference

This file defines all AI-ism detection and removal rules for the resume-rewrite skill. Load it before any AI-writing pass in Phase 1, Phase 2A, Phase 2B, or Phase 3.

---

## Resume-Specific Profile

Apply **`blog` profile strictness** across all resume phases with these modifications:

| Rule | Resume modification |
|---|---|
| Excessive bullets | **Skip** — bullets are structurally correct on a resume |
| Em dashes in bullet lines | **Skip** — acceptable in resume formatting |
| Flagged verb + immediate metric | **Rescue rule** — keep the verb (see below) |
| Em dashes in cover letter | **Zero tolerance** — remove every one |

**Rescue rule:** A flagged verb is acceptable if a specific metric immediately follows it.
- ❌ "Streamlined operations across the org"
- ✅ "Streamlined operations across 6 offices, cutting overhead by $200K"

The rescue rule applies to bullets only. In the Summary and Cover Letter, rewrite the verb regardless.

---

## Priority Order for Resume Passes

Run flags in this order — fix P0 first, then P1, then P2.

### P0 — Credibility killers (fix immediately)
- Vague attributions without sources ("Experts believe," "Studies show")
- Chatbot artifacts ("I hope this helps!", "Great question!", "As of my last update")
- Objective statements (delete entirely, replace with Summary)
- "References available upon request" (delete)

### P1 — Obvious AI smell (fix before any submission)
- Word-list violations (see Tier 1 below): delve, leverage, robust, seamless, utilize, holistic, impactful, synergy, etc.
- Template phrases and slot-fill constructions
- "Results-driven," "proven track record," "passionate professional," "dynamic leader," "go-getter"
- "Responsible for," "worked closely with," "helped to," "assisted with"
- Bold overuse (outside of section headers)
- Spearheaded — use sparingly; if it appears more than once, replace the extras

### P2 — Stylistic polish (fix when time allows)
- Uniform sentence length across all bullets (vary deliberately)
- Transition phrases: Moreover, Furthermore, Additionally
- Significance inflation: "pivotal moment," "watershed," "marking a new era"
- Generic conclusions in cover letter ("I look forward to contributing to your mission")

---

## Tier 1 — Always Replace

These appear 5–20x more often in AI text than human text. Replace on sight.

| Replace | With |
|---|---|
| results-driven | (describe the results instead) |
| proven track record | (cite actual results with metrics) |
| passionate professional | (cut — show passion through specifics) |
| dynamic leader | (cut — show leadership through outcomes) |
| go-getter | (cut) |
| leveraged | used |
| utilized | used |
| robust | strong, reliable, solid |
| comprehensive | thorough, complete, full |
| seamless / seamlessly | smooth, easy, without friction |
| holistic / holistically | complete, full (or describe what's included) |
| impactful | effective, significant (or describe the impact) |
| synergy / synergies | (describe the actual combined effect) |
| spearheaded | led, drove, ran (use once max) |
| responsible for | (rewrite with an active verb — what did they do?) |
| worked closely with | partnered with, collaborated with (then state the outcome) |
| helped to | (rewrite with an active verb + metric) |
| cutting-edge | latest, advanced (or name what's new) |
| innovative / innovation | (describe what's actually new) |
| game-changer / game-changing | (describe what specifically changed) |
| thought leader / thought leadership | expert, authority (or describe their actual contribution) |
| best practices | what works, proven methods, standard approach |
| actionable | practical, useful, concrete |
| learnings | lessons, findings, takeaways |
| paradigm | model, approach, framework |
| ecosystem (metaphor) | system, community, network, market |
| deep dive / dive into | look at, examine, explore |
| unpack / unpacking | explain, break down, walk through |
| seamless integration | (describe how it works, or cut) |
| streamline | simplify, speed up (or use rescue rule if metric follows) |
| empower | enable, let, allow |
| at its core | (cut — just state the thing) |
| in order to | to |
| due to the fact that | because |
| serves as | is |
| delve / delve into | explore, dig into, look at |
| utilize | use |
| pivotal | important, key, critical |
| meticulous / meticulously | careful, detailed, precise |
| testament to | shows, proves, demonstrates |
| underscores | highlights, shows |
| overarching | main, central, broad |
| multifaceted | (describe the actual facets, or cut) |
| transformative / transformation | (describe what changed and how) |
| cornerstone | foundation, basis, key part |

---

## Tier 2 — Flag When 2+ Appear in the Same Section

These words are legitimate on their own. Two or more in the same summary or cover letter paragraph signals AI-generated prose.

| Replace | With |
|---|---|
| harness | use, take advantage of |
| navigate / navigating | work through, handle, deal with |
| foster | encourage, support, build |
| elevate | improve, raise, strengthen |
| streamline | simplify, speed up |
| facilitate | enable, help, allow, run |
| resonate / resonates with | connect with, appeal to, matter to |
| spearhead | lead, drive, run |
| revolutionize | change, transform, reshape |
| cultivate | build, develop, grow |
| nuanced | specific, subtle, detailed (or name the actual nuance) |
| crucial | important, key, necessary |
| paramount | most important, top priority |
| bolster | support, strengthen, back up |
| augment | add to, expand, supplement |
| catalyze | start, trigger, accelerate |

---

## Tier 3 — Flag Only at High Density

Normal words that signal AI when overused. Flag when 3+ appear in the same document section.

| Word | Fix |
|---|---|
| significant / significantly | Replace some with specifics: numbers, comparisons |
| effective / effectively | Say how, or cite a metric |
| dynamic / dynamics | Name the actual forces or changes |
| exceptional / exceptionally | Cite what makes it an exception |
| instrumental | Say what role it played |
| world-class / best-in-class | Cite a benchmark or comparison |

---

## Template Phrases — Always Remove

These slot-fill constructions signal that a sentence was generated, not written. If a phrase has an invisible blank where any noun could go and still sound the same, it's too generic.

- "results-oriented professional with a passion for..." → describe what you do and for whom
- "a track record of delivering results in fast-paced environments" → cite an actual result
- "I am a dedicated [job title] with [X] years of experience in [field]" → rewrite S1 as a direct identity statement
- "I would be a great fit for this role" → (cut — show fit through the requirement bullets)
- "I am passionate about [company mission]" → (cut — show it through the opening research sentence)
- "Looking to leverage my skills in a challenging new role" → (cut entirely)
- "dynamic and results-driven [title]" → (cut both words, rewrite)
- "I am a quick learner" → (never — cite a specific example or cut)

---

## Structural Issues to Catch

### Uniform sentence length
If every bullet is the same length (15–25 words), vary deliberately. Mix short punchy bullets (8–12 words) with longer ones (25+). Length variation is a human signal.

### Formulaic Summary opening
If the Summary opens with broad context before identity — "With over X years of experience in [field], I have..."— rewrite to lead with identity and the strongest proof point. Context can come second.

### Cover letter flatness
Cover letters are especially prone to: emotional claims without evidence ("I am passionate about"), vague fit statements ("I would be a great fit"), and soft closes ("I hope to hear from you"). Flag and rewrite all three.

### Transition phrases to remove or rewrite
- "Moreover" / "Furthermore" / "Additionally" → restructure so the connection is obvious, or use "and," "also," "on top of that"
- "In today's [X]" → cut or state specific context
- "It's worth noting that" / "Notably" → just state the fact
- "In conclusion" / "To summarize" → your conclusion should be obvious from the content

---

## Conducting the AI-Writing Pass

### For Phase 1 (full resume)
1. Read the entire output — Summary, all bullets, Skills section
2. Flag every Tier 1 hit. Replace on sight.
3. Flag Tier 2 clusters (2+ in the same section). Rewrite the section.
4. Check the Summary separately against the template phrases list
5. Apply the rescue rule to any flagged verbs in bullets that are followed by a metric — keep them
6. Output a brief log of what was replaced: list the term and its replacement

### For Phase 2A (five sections only)
1. Scan all five generated sections (headline, summary, highlights, tech, competencies)
2. Same rules as Phase 1, applied to just these sections
3. The headline is especially prone to: "results-driven," "dynamic," "innovative" — remove all

### For Phase 2B (full tailored resume)
Same as Phase 1. Run after keyword placement so you're not rewriting keywords that need to match the JD exactly.

### For Phase 3 (cover letter)
1. Full pass: all tiers, all template phrases, all structural checks
2. Zero em dashes — remove every one, regardless of context
3. Second pass specifically for the close — strip all soft hedges ("I'd welcome," "I hope to," "I would love the opportunity")
4. Check the opening line against the hook rules: no "I am writing to apply," no company name, no self-introduction
5. Check every requirement bullet for a metric — if a bullet has no number, flag it and add one or note it for the user

### Log format (include after each pass)
```
AI-WRITING PASS RESULTS:
Terms replaced: [list each term → replacement]
Template phrases removed: [list or "none"]
Structural fixes: [list or "none"]
Em dashes removed: [count or "none"]
Soft hedges removed (cover letter only): [list or "none"]
Clean: [yes / no — if no, note what remains]
```
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
