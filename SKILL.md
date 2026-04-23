---
name: resume-rewrite
description: >
  Multi-phase resume system: (1) full resume rewrite with XYZ bullets, metrics, and power verbs,
  (2A) targeted JD customization — fast section-level swaps for headline, summary, career highlights,
  tech snapshot, and core competencies — (2B) full ATS keyword audit with scoring,
  (3) cover letter generation. Use this skill whenever the user mentions resume, CV, job application,
  ATS, cover letter, job search, or wants their resume reviewed, rewritten, optimized, or tailored
  to a role. Trigger on any of: "rewrite my resume," "optimize for ATS," "customize for this JD,"
  "tailor my resume to this job," "make my resume better," "review my resume," or when
  a resume file is uploaded. All phases live here — do not split across other skills.
---

# Resume Rewrite Skill

A four-phase system for taking a resume from raw to ready-to-submit — built around clean writing, ATS compliance, and positioning that makes the reader want to keep reading.

---

## Getting Started

**If this is your first time using this skill, here's what to have ready:**

- **Your current resume** — paste as text or upload as a file. Doesn't need to be polished; rough is fine.
- **A job description** — optional for Phase 1, required for Phase 2A/2B/3. Paste the full JD text, not just the title.
- **One thing that genuinely excites you about the company** — needed for Phase 3 (cover letter). Specific is better than general.

**What you'll get:**
- Phase 1 produces `resume-canonical.md` — your master resume. Save it. Every future customization starts from this file.
- Phases 2A/2B produce a tailored version for a specific role.
- Phase 3 produces a 300–350 word cover letter.

**If you're not sure where to start**, just paste your resume and say "rewrite my resume." Claude will handle the rest.

---

## Quick Reference

| Phase | When to run | Requires | Output |
|---|---|---|---|
| **1 — Full Rewrite** | First time, or resume needs overhaul | Resume (JD optional) | `resume-canonical.md` |
| **2A — Targeted Customization** | Have canonical, need fast JD-specific version | Canonical + JD | `resume-[company].md` |
| **2B — Full ATS Optimize** | Want deep keyword scoring + audit | Canonical + JD | `resume-[company].md` + keyword report |
| **3 — Cover Letter** | Applying to specific company | JD + what excites you about the role | `coverletter-[company].md` |

---

## VGPS Positioning Framework

VGPS is a four-part framework for positioning that runs through the **Summary** (Phase 1 & 2A) and the **Cover Letter** (Phase 3). It replaces "introduce yourself through your past" with a forward-facing signal that's harder to fake and more compelling to read.

| Element | What it means | Where it appears |
|---|---|---|
| **Vision** | The change you want to make in the world, or the problem you're wired to solve | Cover letter opening hook (optional) |
| **Gratitude** | The genuine draw — why you love this work above other work | Informs tone; surfaces in cultural fit signal |
| **Profile** | Literal: title, domain, years, proof points | Summary S1–S2; Value match block |
| **Service** | The people you serve + what success looks like when the work goes well | Summary S3 (required); cultural fit signal |

**Core principle: introduce yourself through your future, not your past.** The past is evidence. The future is what actually pulls people toward you.

Apply VGPS as a lens, not a template. Don't label sections "Vision:" or "Service:" — the reader shouldn't see the framework, only feel the clarity.

---

## Phase Detection

Ask yourself: what does the user have and what are they asking for?

```
Resume uploaded or pasted, no canonical mentioned → Phase 1
Canonical exists + JD provided + user does NOT want a full ATS audit → Phase 2A (Targeted Customization)
Canonical exists + JD provided + "optimize/ATS/score/audit" → Phase 2B (Full ATS Optimize)
"Cover letter" mentioned → Phase 3
Ambiguous → Ask: "Do you want a quick targeted version (swap headline, summary, highlights, tech, and competencies), or a full ATS keyword audit with scoring?"
```

When Phase 1 is complete, tell the user:
> "Save `resume-canonical.md` — that's your master copy. Bring it back when you're ready to tailor for a specific role (Phase 2A or 2B) or write a cover letter (Phase 3)."

---

## Before Any Phase: Load Reference Files

- Always load `references/power-verbs.md` before Phase 1
- Always load `references/ai-writing-rules.md` before any AI-writing pass (Phase 1, 2A, 2B, and 3)
- Always load `references/ats-rules.md` before Phase 2B
- Phase 2A does not require reference files beyond `references/ai-writing-rules.md`, but use `references/power-verbs.md` if rewriting bullet highlights

---

## PHASE 1 — Full Resume Rewrite

**Goal:** Transform a raw resume into a polished canonical version. Run once. Results are reused.

### Inputs
- Resume (required) — paste as text or upload as a file
- Job description (optional) — used to weight which bullets to prioritize in the rewrite

> **If no resume is provided yet:** Ask the user to paste their resume or upload it as a file before proceeding. Do not attempt a rewrite without source material.

### Steps

**Step 1 — Analyze (do not output yet)**
Read the entire resume. Note:
- Total number of bullets
- Weakest 3 bullets (vague, no metrics, passive verbs)
- Missing metrics (roles with zero numbers)
- Any employment gaps or red flags in formatting

**Step 2 — Rewrite the Professional Summary**
Write a 3-sentence power statement using the VGPS framework:

1. **Profile** — Who are you? Title + years + domain. Keep S1 to identity + experience — do not front-load mechanism or methodology here.
2. **Profile** — What do you do exceptionally well? Ground it in 1–2 proof points with real metrics.
3. **Service/Vision** *(required — do not skip)* — Who do you serve, and what does it look like when the work goes well? This sentence should face forward, not backward. It answers "why this work, for these people?" — not "what have you done?"

**S3 rules (enforce strictly):**
- Must name a specific person or group (not just "teams" or "organizations")
- Must describe an outcome *they* experience — not a mechanism you run
- Must feel personal to this candidate, not universally true of anyone in the function
- ❌ Generic: *"Teams move faster when the right systems are in place."* (true of anyone in this function, says nothing about you)
- ✅ Personal: *"Engineers do their best work when there's a product layer that absorbs the ambiguity before it reaches them — that's the part I'm built for."*

Example S3 structure: *"[The specific people you serve] get [the outcome they feel] when [the thing only you would say you do]."*

**Word count check (required before moving to Step 3):** Count the words in the summary. If over 60, cut until under. S1 is the easiest place to trim — remove methodology language and leave identity. Do not cut S3.

**Step 3 — Rewrite Every Bullet**
Apply Google's XYZ formula to each bullet:
> Accomplished [X] as measured by [Y] by doing [Z]

Rules:
- Open with a power verb from `references/power-verbs.md`
- Add a metric to every bullet (see Metrics Guidance below)
- Keep bullets to 1–2 lines — no run-on sentences
- If a JD was provided, weight the first 2 bullets of the most recent role toward JD keywords

**Metrics Guidance — when the resume has no numbers:**
Estimate plausibly and flag it:
- Team sizes: "team of ~8 [verify]"
- Time savings: "reduced X from ~Y hours to ~Z hours [verify]"
- Budget: "managed ~$X budget [verify]"
- Scale: "supported ~X users / accounts / SKUs [verify]"
Never fabricate — always add `[verify]` so the user can confirm before submitting.

**Step 4 — Skills Section Overhaul**
Reorganize into categories. Use only categories that apply:
- Technical Skills
- Tools & Platforms
- Frameworks & Methodologies
- Languages
- Certifications
- Soft Skills (list last, keep short — ATS mostly ignores these)

**Step 5 — AI-Writing Pass**
Load `references/ai-writing-rules.md` and run the Phase 1 pass as defined there. Apply the resume-specific profile (rescue rule active, excessive bullets skipped, em dashes in bullet lines skipped). Output the log format defined in the reference file.

**Step 6 — Red Flag Removal**
- Employment gaps: reframe with consulting, freelance, or skills development if true — never fabricate
- Outdated tech: remove or list under "Legacy Systems" if relevant
- Objective statements: delete entirely, replace with Summary
- References available upon request: delete
- GPA: remove if graduation was 5+ years ago

**Step 7 — Before/After Comparison**
Show the 3 weakest bullets from Step 1 alongside their rewrites:

```
BEFORE: [original bullet]
AFTER:  [rewritten bullet]
WHY:    [1 sentence on what changed]
```

**Step 8 — Output the Canonical Resume**
Format as clean markdown. Structure:

```
# [Full Name]
[City, State] | [Email] | [Phone] | [LinkedIn URL]

## Summary
[2–3 sentence power statement]

## Experience

### [Job Title] | [Company] | [Month YYYY – Month YYYY]
- [Bullet]
- [Bullet]

## Education
### [Degree] | [Institution] | [Year]

## Skills
**Technical Skills:** ...
**Tools & Platforms:** ...
[etc.]

## Certifications
[Name] | [Issuer] | [Year]
```

**Step 9 — Tracked Changes Summary**
After the resume, output a summary table:

| Section | What Changed |
|---|---|
| Summary | [what was replaced and why] |
| Bullets | X of Y bullets rewritten; metrics added to Z |
| Skills | Reorganized into N categories; removed: [...] |
| Red flags | [list anything removed/reframed] |
| AI-isms removed | [list flagged terms that were replaced] |

---

## PHASE 2A — Targeted JD Customization

**Goal:** Surgically update only the five highest-impact sections for a specific role. Fast, clean, no full audit needed.

This is the default customization path. Run Phase 2B only when the user specifically wants keyword scoring.

### Inputs
- Canonical resume (required) — the `resume-canonical.md` file from Phase 1, pasted or uploaded
- Job description (required) — paste the full JD text

> **If canonical resume is missing:** Ask the user to paste their canonical resume before proceeding. If they don't have one, suggest running Phase 1 first.
> **If JD is missing:** Ask the user to paste the job description. Phase 2A cannot run without it.

### Sections to Update (only these five — touch nothing else)

---

**Section 1 — Top Headline**

Format: `[Exact JD Role Title] | [1–2 Key Words]`

Rules:
- Copy the job title from the JD **exactly** — no paraphrasing, no seniority inflation
- The keyword(s) after the pipe should bridge what the candidate does to what the role needs (e.g., `Strategy & Operations`, `Revenue & GTM`, `Product & Delivery`)
- Keep the whole line under ~70 characters
- Example: `Senior Product Manager | B2B SaaS & Growth`

---

**Section 2 — Professional Summary**

Write a 3-sentence power statement consistent with the candidate's established voice, weighted toward the JD.

Rules:
- Sentence 1: Who they are + domain + years — maintain consistency with the canonical summary's framing
- Sentence 2: What they do best, grounded in 1–2 proof points from the canonical resume that align with this JD
- Sentence 3 *(required — do not skip)*: Service/Vision — who do they serve in this kind of role, and what does success look like for those people? Weight this toward the JD's team, customers, or org context. Should face forward, not summarize the past.
- Under 65 words total
- Run avoid-AI-writing pass: ban "results-driven," "proven track record," "dynamic," "passionate," "leveraged," "robust"
- Do not fabricate new metrics — only use numbers already in the canonical resume

---

**Section 3 — Select Career Highlights**

Pick 3 bullets for the highlight reel. These are the 3 most relevant proof points for this specific JD.

**Sourcing:** Pull from the canonical resume. Select the 3 bullets most relevant to this JD — strongest proof points that directly address the role's requirements.

**Rewrite standard for all 3 bullets:**
- Open with a strong power verb (load `references/power-verbs.md` if needed)
- Apply XYZ structure: Accomplished [X] as measured by [Y] by doing [Z]
- Every bullet must contain at least one metric
- Max 2 lines per bullet
- No AI-isms: no "leveraged," "spearheaded" (unless unavoidable), "streamlined" without a metric, "robust," "holistic"
- If pulling from the library, rewrite the bullet into a full, polished sentence consistent with the canonical resume's voice

**Output:** 3 bullets, clearly labeled with their source (library tag or canonical) for the user's reference.

---

**Section 4 — Technology Snapshot**

Scan the JD for every tool, platform, software system, or technology mentioned — explicitly or implicitly (e.g., "data-driven" implies analytics tools; "contract management" implies CLM platforms).

Rules:
- Add **all** JD-mentioned tools the candidate plausibly has experience with to the appropriate existing category
- Do not remove existing tools from the canonical snapshot — only add
- If a tool doesn't fit an existing category cleanly, add it to the closest match or create a new category row
- Keep formatting consistent with the canonical version
- Do not list the same tool twice
- If a JD tool seems completely outside the candidate's background, flag it rather than silently adding it

Output the full updated Technology Snapshot block, not just the additions.

---

**Section 5 — Core Competencies**

This is the primary ATS keyword injection point. Rewrite the entire block to maximize match against this JD.

Rules:
- Mirror exact phrases from the JD wherever possible (ATS scores on exact match)
- Pull must-have keywords from: job title, required skills, and any phrase used 2+ times in the JD
- Keep existing competency categories where they fit; rename or restructure categories if the JD signals a different emphasis
- Include both spelled-out and abbreviated forms on first use where relevant: `Customer Relationship Management (CRM)`
- Remove or deprioritize competencies that have zero relevance to this JD (they dilute the signal)
- Do not keyword stuff — every item should plausibly map to something in the canonical resume experience

Output the full updated Core Competencies block.

---

### AI-Writing Pass (Phase 2A)

Load `references/ai-writing-rules.md` and run the Phase 2A pass as defined there (five sections only — headline, summary, highlights, tech, competencies). Output the log format defined in the reference file.

---

### Output Format for Phase 2A

Present each section clearly labeled. Do NOT output the full resume — only the five updated sections:

```
## TOP HEADLINE
[updated headline]

## PROFESSIONAL SUMMARY
[updated summary]

## SELECT CAREER HIGHLIGHTS
- [Bullet 1]
- [Bullet 2]
- [Bullet 3]

## TECHNOLOGY SNAPSHOT
[full updated block]

## CORE COMPETENCIES
[full updated block]
```

After the sections, output a brief swap note:
```
SWAP NOTES:
- Headline changed from: [old] → [new]
- Summary: [1 line on what shifted in emphasis]
- Highlights: [which bullets were swapped in and why]
- Tech added: [list of tools added from JD]
- Competencies: [list of key terms added / removed]
```

---

## PHASE 2B — Full ATS Optimization

**Goal:** Tailor the canonical resume to score in the top 10% for a specific JD.

Load `references/ats-rules.md` before starting.

### Inputs
- Canonical resume (from Phase 1)
- Job description (required)

### If no JD yet, ask:
> "Do you have a specific job description you'd like to optimize against? Paste it in and I'll extract the ATS keywords and tailor your resume to score in the top 10%."

### Steps

**Step 1 — Keyword Extraction**
From the JD, extract and categorize:
```
MUST-HAVE KEYWORDS (in job title, required skills, or listed 2+ times):
[list]

STRONG KEYWORDS (mentioned once in requirements):
[list]

BONUS KEYWORDS (mentioned in nice-to-haves or company description):
[list]
```

**Step 2 — Synonym Coverage**
For every acronym found: include both forms on first use.
`Search Engine Optimization (SEO)`, `Customer Relationship Management (CRM)`, etc.

**Step 3 — Keyword Placement**
Embed keywords in priority order:
1. Summary — insert 2–3 must-have keywords naturally
2. Skills section — add any missing must-have keywords as exact-match terms
3. Most recent role bullets — weave in remaining must-haves
4. Older roles — sprinkle strong keywords where naturally applicable

Never keyword stuff. If it doesn't fit naturally, put it in Skills only.

**Step 4 — Job Title Alignment**
If the candidate's title differs from the JD title, note it:
> "Your title was [X]. The role uses [Y]. You can add the JD title in parentheses if it accurately reflects your scope: 'Operations Manager (Business Affairs)'"

Never fabricate a title they didn't hold.

**Step 5 — Format Audit**
Check the canonical file for any ATS-crashing elements (per `references/ats-rules.md`).
Flag anything found and remove it.

**Step 6 — ATS Match Score**
Calculate and display:
```
ATS MATCH SCORE: [X]/100

Must-have keywords matched: X/Y
Strong keywords matched: X/Y
Bonus keywords matched: X/Y
Format issues found: [none / list]
Placement quality: [summary ✓ / skills ✓ / bullets ✓]

VERDICT: [Top 10% / Strong / Moderate / Weak — with 1-line explanation]
```

**Step 7 — Keyword Match Report**
```
KEYWORD          | STATUS    | PLACED IN
-----------------|-----------|------------------
[keyword]        | Added     | Summary, Skills
[keyword]        | Present   | Bullet — Role X
[keyword]        | Missing   | Not applicable to experience
```

**Step 8 — AI-Writing Pass (Phase 2B)**
Load `references/ai-writing-rules.md` and run the Phase 2B pass as defined there. Run after keyword placement so you're not rewriting keywords that need to match the JD exactly. Output the log format defined in the reference file.

**Output:** Save as `resume-[CompanyName].md` with the match report appended at the bottom.

---

## PHASE 3 — Cover Letter

**Goal:** A 300–350 word cover letter that makes explicit, scannable connections between the candidate's background and the role's requirements. Every connection is stated directly. The reader should never have to infer anything.

**Guiding principle:** Do not write a cover letter that expects the recruiter or hiring manager to connect the candidate's background to the role. Make every connection explicit. Brevity that sacrifices content is the wrong tradeoff.

### Inputs
- Job description (required)
- What genuinely excites the candidate about this company (required)
- Canonical resume or tailored resume (recommended — used to pull proof points)

### If inputs are missing, ask:
> "Two quick things before I write this: (1) paste the job description, and (2) tell me one thing that genuinely excites you about this company or role — something specific, not just 'great culture.' I'll also need your resume if you haven't shared it yet."

### Hard Rules (enforce on every draft)
- **Zero em dashes.** None. If a draft contains one, rewrite the sentence using a comma, period, or two sentences.
- **No AI-isms.** Flag and remove all of them.
- **No soft hedges in the close.** No "I'd welcome," no "I hope to," no passive invitations.
- **Never start with:** "I am writing to apply..." / "I am excited to apply..." / "My name is..."
- **Every requirement bullet must contain at least one metric.**

### Structure (in order, strict)

**[STATIC] Hook** — 1 sentence
The very first sentence of the letter. Its only job is to make the reader want to keep reading. It should feel like the opening line of something worth reading — not a self-introduction, not a corporate platitude.

Write the hook as one of these:
- A bold conviction the candidate holds about the work (Vision from VGPS)
- A specific, provocative observation about the problem the role is trying to solve
- A forward-facing statement of what great looks like in this function or field

Rules:
- No "I am writing to apply" / "I am excited" / "My name is"
- No company name in the hook — that comes in sentence 2
- Should be specific enough to surprise, general enough to not require company context
- ❌ *"I have spent 10+ years in [field] and am passionate about building scalable systems."*
- ✅ *"The best [function] work is invisible — you only notice it when it's gone."*
- ✅ *"The [companies/teams] that [achieve the thing this role is about] are the ones that treat it as a design problem, not a management problem."*

**[CUSTOMIZE] Opening** — 2 sentences
Sentence 1: Company-specific research proof that names a real business challenge or growth signal (product launch, strategic initiative, earnings result, or stated mission detail). Vision-first framing preferred.
Sentence 2: Position the candidate as the direct answer to that challenge. Should read as a declarative statement, not an application.

**[CUSTOMIZE] Requirements Bridge** — 1 sentence
State the 2–3 requirements the role demands, pulled directly from the JD's own language.
Format: *"Your role requires [Requirement 1], [Requirement 2], and [Requirement 3]. My background addresses each directly."*

**[CUSTOMIZE] Requirement Bullets** — one bullet per requirement
Each bullet follows this format:
- **Bold header using the exact JD language as the label**
- Body: lead with the strongest resume proof point in XYZ format (metric required), followed by one sentence of context if needed.

Example:
> **Cross-functional Program Management**
> Reduced go-to-market cycle from 14 weeks to 9 by building a unified program cadence across product, creative, and legal, cutting approval bottlenecks by 40%.

**[CUSTOMIZE] What Distinguishes Paragraph** — 2–3 sentences
Name the specific differentiator that separates this candidate from other qualified applicants at the same level. Target the gap that is hardest to fake — not years of experience, but a capability or combination that is genuinely uncommon. Close with: *"At [Company], this translates to [specific result the JD is asking for]."*

**[STATIC] Confident Close** — 2 sentences
Request an interview directly. Ask to be contacted at earliest convenience. Close with: *"I look forward to hearing from you soon."*
No soft hedges. No passive invitations. No "I'd welcome." State the ask.

### Personalization Key
After the letter, output:

```
CUSTOMIZE PER APPLICATION (these lines change every time):
- Opening (company research + positioning sentence)
- Requirements bridge (pulled from this JD)
- Requirement bullets (labeled with this JD's exact language)
- What distinguishes paragraph (anchored to this company)

STATIC (update only when your resume or positioning updates):
- Hook (your conviction — stays until your positioning changes)
- Confident close
```

### AI-Writing Pass for Cover Letter
Load `references/ai-writing-rules.md` and run the Phase 3 pass as defined there. Zero em dashes, no soft hedges in the close, full template phrase check. Output the log format defined in the reference file.

**Output:** Save as `coverletter-[CompanyName].md`

---

## Frequently Asked Questions

**"Do I need to run Phase 1 before Phase 2?"**
Yes. Phase 2A and 2B both require a canonical resume as their starting point. If you don't have one, start with Phase 1.

**"Can I skip Phase 1 and just customize for a role?"**
If your current resume is already well-written (strong bullets, clear metrics, clean formatting), you can use it as the canonical and go straight to Phase 2A. Just label it as your canonical when you share it.

**"How many times can I run Phase 2A?"**
As many times as you need — once per role you're applying to. Each run produces a separate tailored file.

**"My resume doesn't have any numbers. Will this still work?"**
Yes. Phase 1 includes metrics guidance — Claude will estimate plausible numbers and flag them with [verify] so you can confirm before submitting. You should expect to do a quick review pass of all flagged items.

---

## Token Efficiency Notes

Phase 1 is expensive — it rewrites every bullet and runs a full AI-writing audit.
Phase 2A is cheap — five targeted section swaps, no full document rewrite.
Phase 2B is moderate — keyword extraction + scoring pass on the full canonical.
Phase 3 is cheap — operates on the already-rewritten canonical file. Target length: 300–350 words.

**Never re-run Phase 1** unless the user explicitly says "rewrite from scratch" or uploads a new resume.
**Default to Phase 2A** for JD customization unless the user specifically asks for scoring or a full ATS audit.
When in doubt, ask: "Do you want a quick targeted version, or a full ATS keyword audit with scoring?"
Canonical exists + JD provided + "optimize/ATS/score/audit" → Phase 2B (Full ATS Optimize)
"Cover letter" mentioned → Phase 3
Ambiguous → Ask: "Do you want a quick targeted version (swap headline, summary, highlights, tech, and competencies), or a full ATS keyword audit with scoring?"
```

When Phase 1 is complete, tell the user:
> "Save `resume-canonical.md` — that's your master copy. Bring it back when you're ready to tailor for a specific role (Phase 2A or 2B) or write a cover letter (Phase 3)."

---

## Before Any Phase: Load Reference Files

- Always load `references/power-verbs.md` before Phase 1
- Always load `references/ats-rules.md` before Phase 2B
- Phase 2A does not require reference files, but use `references/power-verbs.md` if rewriting bullet highlights
- You do NOT need to load them for Phase 3

---

## PHASE 1 — Full Resume Rewrite

**Goal:** Transform a raw resume into a polished canonical version. Run once. Results are reused.

### Inputs
- Resume (required) — paste or file upload
- Job description (optional) — used to weight which bullets to prioritize

### Steps

**Step 1 — Analyze (do not output yet)**
Read the entire resume. Note:
- Total number of bullets
- Weakest 3 bullets (vague, no metrics, passive verbs)
- Missing metrics (roles with zero numbers)
- Any employment gaps or red flags in formatting

**Step 2 — Rewrite the Professional Summary**
Write a 3-sentence power statement using the VGPS framework:

1. **Profile** — Who are you? Title + years + domain.
2. **Profile** — What do you do exceptionally well? Ground it in 1–2 proof points.
3. **Service/Vision** *(required — do not skip)* — Who do you serve, and what does it look like when the work goes well? This sentence should face forward, not backward. It answers "why this work?" not "what have you done?"

Example S3 structure: *"[The people/orgs you serve] get [the outcome] when [the thing you uniquely do]."*

Keep the whole summary under 60 words. No "results-driven," "proven track record," "passionate," or "dynamic." S3 is the hardest sentence to write well — resist the urge to make it another proof point. It should read as conviction, not credential.

**Step 3 — Rewrite Every Bullet**
Apply Google's XYZ formula to each bullet:
> Accomplished [X] as measured by [Y] by doing [Z]

Rules:
- Open with a power verb from `references/power-verbs.md`
- Add a metric to every bullet (see Metrics Guidance below)
- Keep bullets to 1–2 lines — no run-on sentences
- If a JD was provided, weight the first 2 bullets of the most recent role toward JD keywords

**Metrics Guidance — when the resume has no numbers:**
Estimate plausibly and flag it:
- Team sizes: "team of ~8 [verify]"
- Time savings: "reduced X from ~Y hours to ~Z hours [verify]"
- Budget: "managed ~$X budget [verify]"
- Scale: "supported ~X users / accounts / SKUs [verify]"
Never fabricate — always add `[verify]` so the user can confirm before submitting.

**Step 4 — Skills Section Overhaul**
Reorganize into categories. Use only categories that apply:
- Technical Skills
- Tools & Platforms
- Frameworks & Methodologies
- Languages
- Certifications
- Soft Skills (list last, keep short — ATS mostly ignores these)

**Step 5 — Apply Avoid-AI-Writing Pass**
After rewriting, scan the full output using the rules from the `avoid-ai-writing` skill.

Apply **`blog` profile strictness** with these resume-specific modifications:
- **Skip:** excessive bullets rule (bullets are structurally correct on a resume)
- **Skip:** em dash rule in bullet lines (acceptable in resume formatting)
- **Rescue rule:** a flagged verb is acceptable if a specific metric immediately follows it
  - ❌ "Streamlined operations across the org"
  - ✅ "Streamlined operations across 6 offices, cutting overhead by $200K"

Priority order for resume AI-isms to catch:
- P0: "results-driven," "proven track record," "passionate professional," "dynamic leader," "go-getter"
- P1: leveraged, utilized, robust, comprehensive, seamless, impactful, synergy, holistic
- P2: spearheaded (overused — use sparingly), "responsible for," "worked closely with"

**Step 6 — Red Flag Removal**
- Employment gaps: reframe with consulting, freelance, or skills development if true — never fabricate
- Outdated tech: remove or list under "Legacy Systems" if relevant
- Objective statements: delete entirely, replace with Summary
- References available upon request: delete
- GPA: remove if graduation was 5+ years ago

**Step 7 — Before/After Comparison**
Show the 3 weakest bullets from Step 1 alongside their rewrites:

```
BEFORE: [original bullet]
AFTER:  [rewritten bullet]
WHY:    [1 sentence on what changed]
```

**Step 8 — Output the Canonical Resume**
Format as clean markdown. Structure:

```
# [Full Name]
[City, State] | [Email] | [Phone] | [LinkedIn URL]

## Summary
[2–3 sentence power statement]

## Experience

### [Job Title] | [Company] | [Month YYYY – Month YYYY]
- [Bullet]
- [Bullet]

## Education
### [Degree] | [Institution] | [Year]

## Skills
**Technical Skills:** ...
**Tools & Platforms:** ...
[etc.]

## Certifications
[Name] | [Issuer] | [Year]
```

**Step 9 — Tracked Changes Summary**
After the resume, output a summary table:

| Section | What Changed |
|---|---|
| Summary | [what was replaced and why] |
| Bullets | X of Y bullets rewritten; metrics added to Z |
| Skills | Reorganized into N categories; removed: [...] |
| Red flags | [list anything removed/reframed] |
| AI-isms removed | [list flagged terms that were replaced] |

---

## PHASE 2A — Targeted JD Customization

**Goal:** Surgically update only the five highest-impact sections for a specific role. Fast, clean, no full audit needed.

This is the default customization path. Run Phase 2B only when the user specifically wants keyword scoring.

### Inputs
- Canonical resume (required)
- Job description (required)
- Master bullet library (optional — `master_bullet_library_v1.md` — if provided, use it as the bullet source pool)

### Sections to Update (only these five — touch nothing else)

---

**Section 1 — Top Headline**

Format: `[Exact JD Role Title] | [1–2 Key Words]`

Rules:
- Copy the job title from the JD **exactly** — no paraphrasing, no seniority inflation
- The keyword(s) after the pipe should bridge what the user does to what the role needs (e.g., `Strategy & Operations`, `Revenue & GTM`, `Product & Delivery`)
- Keep the whole line under ~70 characters
- Example: `Director of Business Affairs | Music & Entertainment`

---

**Section 2 — Professional Summary**

Write a 3-sentence power statement. This is the overview block that typically opens with "Operations and product leader..." — maintain that established voice/structure while weighting toward the JD.

Rules:
- Sentence 1: Who you are + domain + years (keep consistent with canonical)
- Sentence 2: What you do best, grounded in 1–2 proof points from the canonical resume that align with this JD
- Sentence 3 *(required — do not skip)*: Service/Vision — who do you serve in this kind of role, and what does success look like for them? Weight this toward the JD's team, customers, or org context. Should face forward, not summarize the past.
- Under 65 words total
- Run avoid-AI-writing pass: ban "results-driven," "proven track record," "dynamic," "passionate," "leveraged," "robust"
- Do not fabricate new metrics — only use numbers already in the canonical resume

---

**Section 3 — Select Career Highlights**

Pick 3 bullets for the highlight reel at the top of the resume. These are the 3 most relevant proof points for the JD.

**Sourcing order:**
1. If a `master_bullet_library_v1.md` was provided, pull from there first — it has the widest selection
2. If a bullet appears in both the canonical resume and the library, prefer the canonical version (it has been updated)
3. If a relevant bullet exists only in the library, use it — but it **must be rewritten** to current standards before use

**Rewrite standard for all 3 bullets:**
- Open with a strong power verb (load `references/power-verbs.md` if needed)
- Apply XYZ structure: Accomplished [X] as measured by [Y] by doing [Z]
- Every bullet must contain at least one metric
- Max 2 lines per bullet
- No AI-isms: no "leveraged," "spearheaded" (unless unavoidable), "streamlined" without a metric, "robust," "holistic"
- If pulling from the library, the bullet may read like a fragment or summary — rewrite it into a full, polished sentence in the voice of the canonical resume

**Output:** 3 bullets, clearly labeled with their source (library tag or canonical) for the user's reference.

---

**Section 4 — Technology Snapshot**

Scan the JD for every tool, platform, software system, or technology mentioned — explicitly or implicitly (e.g., "data-driven" implies analytics tools; "contract management" implies CLM platforms).

Rules:
- Add **all** JD-mentioned tools to the appropriate existing category. Assume the user has experience with all of them.
- Do not remove existing tools from the canonical snapshot — only add
- If a tool doesn't fit an existing category cleanly, add it to the closest match or create a new category row
- Keep formatting consistent with the canonical version (`Category: Tool | Tool | Tool`)
- Do not list the same tool twice

Output the full updated Technology Snapshot block, not just the additions.

---

**Section 5 — Core Competencies**

This is the primary ATS keyword injection point. Rewrite the entire block to maximize match against this JD.

Rules:
- Mirror exact phrases from the JD wherever possible (ATS scores on exact match)
- Pull must-have keywords from: job title, required skills, and any phrase used 2+ times in the JD
- Keep existing competency categories where they fit; rename or restructure categories if the JD signals a different emphasis
- It is acceptable to add entirely new competency items — assume the user can speak to them given their background
- Include both spelled-out and abbreviated forms on first use where relevant: `Customer Relationship Management (CRM)`
- Remove or deprioritize competencies that have zero relevance to this JD (they dilute the signal)
- Do not keyword stuff — every item should plausibly map to something in the canonical resume experience

Output the full updated Core Competencies block.

---

### Output Format for Phase 2A

Present each section clearly labeled. Do NOT output the full resume — only the five updated sections:

```
## TOP HEADLINE
[updated headline]

## PROFESSIONAL SUMMARY
[updated summary]

## SELECT CAREER HIGHLIGHTS
- [Bullet 1] (source: [library tag / canonical])
- [Bullet 2] (source: [library tag / canonical])
- [Bullet 3] (source: [library tag / canonical])

## TECHNOLOGY SNAPSHOT
[full updated block]

## CORE COMPETENCIES
[full updated block]
```

After the sections, output a brief swap note:
```
SWAP NOTES:
- Headline changed from: [old] → [new]
- Summary: [1 line on what shifted in emphasis]
- Highlights: [which bullets were swapped in and why]
- Tech added: [list of tools added from JD]
- Competencies: [list of key terms added / removed]
```

---

## PHASE 2B — Full ATS Optimization

**Goal:** Tailor the canonical resume to score in the top 10% for a specific JD.

Load `references/ats-rules.md` before starting.

### Inputs
- Canonical resume (from Phase 1)
- Job description (required)

### If no JD yet, ask:
> "Do you have a specific job description you'd like to optimize against? Paste it in and I'll extract the ATS keywords and tailor your resume to score in the top 10%."

### Steps

**Step 1 — Keyword Extraction**
From the JD, extract and categorize:
```
MUST-HAVE KEYWORDS (in job title, required skills, or listed 2+ times):
[list]

STRONG KEYWORDS (mentioned once in requirements):
[list]

BONUS KEYWORDS (mentioned in nice-to-haves or company description):
[list]
```

**Step 2 — Synonym Coverage**
For every acronym found: include both forms on first use.
`Search Engine Optimization (SEO)`, `Customer Relationship Management (CRM)`, etc.

**Step 3 — Keyword Placement**
Embed keywords in priority order:
1. Summary — insert 2–3 must-have keywords naturally
2. Skills section — add any missing must-have keywords as exact-match terms
3. Most recent role bullets — weave in remaining must-haves
4. Older roles — sprinkle strong keywords where naturally applicable

Never keyword stuff. If it doesn't fit naturally, put it in Skills only.

**Step 4 — Job Title Alignment**
If the user's title differs from the JD title, note it:
> "Your title was [X]. The role uses [Y]. You can add the JD title in parentheses if it accurately reflects your scope: 'Operations Manager (Business Affairs)'"

Never fabricate a title they didn't hold.

**Step 5 — Format Audit**
Check the canonical file for any ATS-crashing elements (per `references/ats-rules.md`).
Flag anything found and remove it.

**Step 6 — ATS Match Score**
Calculate and display:
```
ATS MATCH SCORE: [X]/100

Must-have keywords matched: X/Y
Strong keywords matched: X/Y
Bonus keywords matched: X/Y
Format issues found: [none / list]
Placement quality: [summary ✓ / skills ✓ / bullets ✓]

VERDICT: [Top 10% / Strong / Moderate / Weak — with 1-line explanation]
```

**Step 7 — Keyword Match Report**
```
KEYWORD          | STATUS    | PLACED IN
-----------------|-----------|------------------
[keyword]        | Added     | Summary, Skills
[keyword]        | Present   | Bullet — Role X
[keyword]        | Missing   | Not applicable to experience
```

**Output:** Save as `resume-[CompanyName].md` with the match report appended at the bottom.

---

## PHASE 3 — Cover Letter

**Goal:** A 250–300 word cover letter that makes the hiring manager stop scrolling.

**Guiding principle: introduce yourself through your future, not your past.** The past is evidence. The cover letter's job is to show what you're moving toward and who you're wired to serve — not to narrate your resume. Structure the letter so it builds toward forward momentum, not backward credential stacking. VGPS is the underlying architecture: Vision → Profile → Service → forward close.

### Inputs
- Job description (required)
- What genuinely excites the user about this company (required)

### If inputs are missing, ask:
> "Two quick things before I write this: (1) paste the job description, and (2) tell me one thing that genuinely excites you about this company or role — something specific, not just 'great culture.'"

### Structure (in order, strict)

**[CUSTOMIZE] Opening Hook** — 1 sentence
Two valid approaches:
- *Credential-first:* Connect a specific piece of their experience to the company's current challenge.
- *Vision-first (preferred when it fits naturally):* Open with the problem you're wired to solve, then land it on the company. Leads with conviction, not biography.

Never start with: "I am writing to apply for..." / "I am excited to apply..." / "My name is..."

**[CUSTOMIZE] Company Research Proof** — 1–2 sentences
Reference something real: a product launch, strategic initiative, earnings result, or mission statement detail. Proves homework was done.

**[STATIC] Value Match** — 2–3 sentences
The 3 capabilities the user brings that directly solve what the JD is asking for.
Pull from canonical resume. This block changes minimally per application.

**[STATIC] Spotlight Achievement** — 1–2 sentences
One quantified result that proves they've already done the job's most important task.
Pull best XYZ bullet from canonical resume.

**[CUSTOMIZE] Service Signal** — 1 sentence
*Replaces generic "cultural fit" framing.* Name who you're wired to serve and what it looks like when the work goes well — then anchor it to this company's actual team, customers, or mission. This should feel like self-knowledge, not performance.
Must not sound rehearsed. No: "I believe strongly in your mission." Yes: [something that could only come from this person, about these people.]

**[CUSTOMIZE] First 90 Days** — 1–2 sentences
Name one initiative they'd work on in their first 90 days based on the JD.
Shows they've actually read the role, not just the title.

**[STATIC] Confident Close** — 2 sentences
Assume the interview happens. End with a clear next step.
No: "I hope to hear from you." Yes: "I'd welcome 20 minutes to walk you through [specific thing]."

### Personalization Key
After the letter, output:

```
CUSTOMIZE PER APPLICATION (these lines change every time):
- Opening hook
- Company research proof
- Service signal
- First 90 days initiative

STATIC (update only when your resume updates):
- Value match paragraph
- Spotlight achievement
- Confident close
```

### AI-Writing Pass for Cover Letter
Apply `avoid-ai-writing` skill at `blog` profile, full strictness.
Cover letters are especially prone to: "I am passionate about," "proven track record," "dynamic environment," "I would be a great fit," "I am a quick learner."
Flag and replace all of them.

**Output:** Save as `coverletter-[CompanyName].md`

---

## Token Efficiency Notes

Phase 1 is expensive — it rewrites every bullet and runs a full AI-writing audit.
Phase 2A is cheap — five targeted section swaps, no full document rewrite.
Phase 2B is moderate — keyword extraction + scoring pass on the full canonical.
Phase 3 is cheap — operates on the already-rewritten canonical file.

**Never re-run Phase 1** unless the user explicitly says "rewrite from scratch" or uploads a new resume.
**Default to Phase 2A** for JD customization unless the user specifically asks for scoring or a full ATS audit.
When in doubt, ask: "Do you want a quick targeted version, or a full ATS keyword audit with scoring?"
