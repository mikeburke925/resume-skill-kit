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
version: 1.0.0
license: MIT
---

# Resume Rewrite Skill

A four-phase system for taking a resume from raw to ready-to-submit. Built for use with Claude Code,
Claude.ai, or any AI assistant that supports the agentskills SKILL.md format.

## Quick Reference

| Phase | When to run | Requires | Output |
|---|---|---|---|
| **1 — Full Rewrite** | First time, or resume needs overhaul | Resume (JD optional) | `resume-canonical.md` |
| **2A — Targeted Customization** | Have canonical, need fast JD-specific version | Canonical + JD (+ bullet library if available) | `resume-[company].md` |
| **2B — Full ATS Optimize** | Want deep keyword scoring + audit | Canonical + JD | `resume-[company].md` + keyword report |
| **3 — Cover Letter** | Applying to specific company | JD + what excites the user | `coverletter-[company].md` |

---

## Phase Detection

Ask yourself: what does the user have and what are they asking for?

```
Resume uploaded, no canonical mentioned → Phase 1
Canonical exists + JD provided + user does NOT want a full ATS audit → Phase 2A (Targeted Customization)
Canonical exists + JD provided + "optimize/ATS/score/audit" → Phase 2B (Full ATS Optimize)
"Cover letter" mentioned → Phase 3
Ambiguous → Ask: "Do you want a quick targeted version (swap headline, summary, highlights, tech, and
competencies), or a full ATS keyword audit with scoring?"
```

When Phase 1 is complete, tell the user:
> "Save `resume-canonical.md` — that's your master copy. Bring it back when you're ready to tailor
> for a specific role (Phase 2A or 2B) or write a cover letter (Phase 3)."

---

## Before Any Phase: Load Reference Files

- Always load `references/power-verbs.md` before Phase 1
- Always load `references/ats-rules.md` before Phase 2B
- Phase 2A does not require reference files, but use `references/power-verbs.md` if rewriting bullets
- You do NOT need to load reference files for Phase 3

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
Write a 2–3 sentence power statement answering:
1. Who are you (title + years + domain)?
2. What do you do exceptionally well (1–2 proof points)?
3. What outcome do you drive for employers?

Keep it under 60 words. No "results-driven," "proven track record," "passionate," or "dynamic."

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
After rewriting, scan the full output using the rules from `references/avoid-ai-writing.md`.

Apply **`blog` profile strictness** with these resume-specific modifications:
- **Skip:** excessive bullets rule (bullets are structurally correct on a resume)
- **Skip:** em dash rule in bullet lines (acceptable in resume formatting)
- **Rescue rule:** a flagged verb is acceptable if a specific metric immediately follows it
  - ❌ "Streamlined operations across the org"
  - ✅ "Streamlined operations across 6 offices, cutting overhead by $200K"

Priority order for resume AI-isms to catch:
- P0: "results-driven," "proven track record," "passionate professional," "dynamic leader"
- P1: leveraged, utilized, robust, comprehensive, seamless, impactful, synergy, holistic
- P2: spearheaded (overused — use sparingly), "responsible for," "worked closely with"

**Step 6 — Red Flag Removal**
- Employment gaps: reframe with consulting, freelance, or skills development if true — never fabricate
- Outdated tech: remove or list under "Legacy Systems" if relevant
- Objective statements: delete entirely, replace with Summary
- "References available upon request": delete
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

**Goal:** Surgically update only the five highest-impact sections for a specific role. Fast, no full audit needed.

This is the default customization path. Run Phase 2B only when the user specifically wants keyword scoring.

### Inputs
- Canonical resume (required)
- Job description (required)
- Master bullet library (optional — if provided, use it as the bullet source pool)

### Sections to Update (only these five — touch nothing else)

---

**Section 1 — Top Headline**

Format: `[Exact JD Role Title] | [1–2 Key Words]`

Rules:
- Copy the job title from the JD **exactly** — no paraphrasing, no seniority inflation
- The keyword(s) after the pipe should bridge what the user does to what the role needs
  (e.g., `Strategy & Operations`, `Revenue & GTM`, `Product & Delivery`)
- Keep the whole line under ~70 characters
- Example: `Director of Business Operations | Strategy & Delivery`

---

**Section 2 — Professional Summary**

Write a 2–3 sentence power statement weighted toward the JD.

Rules:
- Sentence 1: Who you are + domain + years (keep consistent with canonical)
- Sentence 2: What you do best, grounded in 1–2 proof points from the canonical that align with this JD
- Sentence 3 (optional): Forward-looking — what you bring to *this specific kind of role*
- Under 65 words total
- Run avoid-AI-writing pass: ban "results-driven," "proven track record," "dynamic," "passionate,"
  "leveraged," "robust"
- Do not fabricate new metrics — only use numbers already in the canonical resume

---

**Section 3 — Select Career Highlights**

Pick 3 bullets for the highlight reel at the top of the resume. These are the 3 most relevant
proof points for this JD.

**Sourcing order:**
1. If a bullet library was provided, pull from there first — it has the widest selection
2. If a bullet appears in both the canonical and the library, prefer the canonical (it has been updated)
3. If a relevant bullet exists only in the library, use it — but **rewrite it** to current standards

**Rewrite standard for all 3 bullets:**
- Open with a strong power verb (load `references/power-verbs.md` if needed)
- Apply XYZ structure: Accomplished [X] as measured by [Y] by doing [Z]
- Every bullet must contain at least one metric
- Max 2 lines per bullet
- No AI-isms: no "leveraged," "spearheaded" (unless unavoidable), "streamlined" without a metric,
  "robust," "holistic"
- Library bullets may read like fragments — rewrite them into polished sentences in the voice of
  the canonical resume

**Output:** 3 bullets, each labeled with its source (library tag or canonical) for the user's reference.

---

**Section 4 — Technology Snapshot**

Scan the JD for every tool, platform, software system, or technology mentioned — explicitly or
implicitly (e.g., "data-driven" implies analytics tools; "contract management" implies CLM platforms).

Rules:
- Add **all** JD-mentioned tools to the appropriate existing category. Assume the user has experience.
- Do not remove existing tools from the canonical snapshot — only add
- If a tool doesn't fit an existing category cleanly, add it to the closest match or create a new row
- Keep formatting consistent with the canonical version (`Category: Tool | Tool | Tool`)
- Do not list the same tool twice

Output the full updated Technology Snapshot block, not just the additions.

---

**Section 5 — Core Competencies**

This is the primary ATS keyword injection point. Rewrite the entire block to maximize match against
this JD.

Rules:
- Mirror exact phrases from the JD wherever possible (ATS scores on exact match)
- Pull must-have keywords from: job title, required skills, and any phrase used 2+ times in the JD
- Keep existing competency categories where they fit; rename or restructure if the JD signals
  a different emphasis
- It is acceptable to add entirely new competency items — assume the user can speak to them given
  their background
- Include both spelled-out and abbreviated forms on first use: `Customer Relationship Management (CRM)`
- Remove or deprioritize competencies with zero relevance to this JD (they dilute the signal)
- Do not keyword stuff — every item should plausibly map to something in the canonical resume

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
> "Do you have a specific job description you'd like to optimize against? Paste it in and I'll
> extract the ATS keywords and tailor your resume to score in the top 10%."

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
For every acronym found, include both forms on first use.
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
> "Your title was [X]. The role uses [Y]. You can add the JD title in parentheses if it accurately
> reflects your scope: 'Operations Manager (Business Affairs)'"

Never fabricate a title they didn't hold.

**Step 5 — Format Audit**
Check the canonical for ATS-crashing elements (per `references/ats-rules.md`). Flag and remove anything found.

**Step 6 — ATS Match Score**
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

### Inputs
- Job description (required)
- What genuinely excites the user about this company (required)

### If inputs are missing, ask:
> "Two quick things before I write this: (1) paste the job description, and (2) tell me one thing
> that genuinely excites you about this company or role — something specific, not just 'great culture.'"

### Structure (in order, strict)

**[CUSTOMIZE] Opening Hook** — 1 sentence
Connect a specific piece of their experience to the company's current challenge.
Never start with: "I am writing to apply for..." / "I am excited to apply..." / "My name is..."

**[CUSTOMIZE] Company Research Proof** — 1–2 sentences
Reference something real: a product launch, strategic initiative, earnings result, or mission detail.
Proves homework was done.

**[STATIC] Value Match** — 2–3 sentences
The 3 capabilities the user brings that directly solve what the JD is asking for.
Pull from canonical resume. This block changes minimally per application.

**[STATIC] Spotlight Achievement** — 1–2 sentences
One quantified result that proves they've already done the job's most important task.
Pull best XYZ bullet from canonical resume.

**[CUSTOMIZE] Cultural Fit Signal** — 1 sentence
Connect their work style or values to the company's mission using the user's "what excites me" input.
Must not sound rehearsed. No: "I believe strongly in your mission."

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
- Cultural fit signal
- First 90 days initiative

STATIC (update only when your resume updates):
- Value match paragraph
- Spotlight achievement
- Confident close
```

### AI-Writing Pass for Cover Letter
Apply `references/avoid-ai-writing.md` at `blog` profile, full strictness.
Cover letters are especially prone to: "I am passionate about," "proven track record,"
"dynamic environment," "I would be a great fit," "I am a quick learner."
Flag and replace all of them.

**Output:** Save as `coverletter-[CompanyName].md`

---

## Token Efficiency Notes

Phase 1 is expensive — it rewrites every bullet and runs a full AI-writing audit.
Phase 2A is cheap — five targeted section swaps, no full document rewrite.
Phase 2B is moderate — keyword extraction + scoring pass on the full canonical.
Phase 3 is cheap — operates on the already-rewritten canonical file.

**Never re-run Phase 1** unless the user explicitly says "rewrite from scratch" or uploads a new resume.
**Default to Phase 2A** for JD customization unless the user specifically asks for scoring or a full audit.
When in doubt, ask: "Do you want a quick targeted version, or a full ATS keyword audit with scoring?"
