# resume-rewrite

A skill for Claude that turns a rough resume into a submission-ready one — and keeps it ready for every role you apply to.

---

## What this does

The skill runs Claude through a structured, multi-phase process:

- **Phase 1** rewrites your resume from scratch using the XYZ bullet formula, adds metrics to every bullet, strips AI-style language, and produces a clean canonical file you'll reuse for every application.
- **Phase 2A** takes that canonical file and surgically updates five sections (headline, summary, career highlights, tech snapshot, core competencies) for a specific role. Fast and targeted — no full rewrite.
- **Phase 2B** does a full ATS keyword audit against a job description, scores your match, and tells you exactly what to add and where.
- **Phase 3** writes a 300–350 word cover letter that makes your connection to the role explicit — no inferences required from the reader.

Every phase includes a full AI-writing audit that removes the words and patterns that make resumes sound generated rather than written.

---

## File structure

```
resume-rewrite/
├── SKILL.md                          # Main skill instructions
├── README.md                         # This file
└── references/
    ├── power-verbs.md                # Verb bank organized by domain
    ├── ats-rules.md                  # ATS parser rules and platform quirks
    └── ai-writing-rules.md           # Full AI-ism detection and replacement rules
```

---

## How to install

### Claude Code
1. Copy the `resume-rewrite` folder into your skills directory (typically `.claude/skills/` in your project, or a shared skills folder you reference globally)
2. That's it. Claude Code will load it automatically when triggered.

### Claude.ai (Projects)
1. Open the Project you want to use this skill in
2. In the Project instructions, paste the contents of `SKILL.md` directly, or reference the file if your setup supports it
3. Upload `references/power-verbs.md`, `references/ats-rules.md`, and `references/ai-writing-rules.md` as Project files so Claude can load them on demand

### Other Claude interfaces
Paste the contents of `SKILL.md` into your system prompt or custom instructions. Upload the three reference files as attachments or paste their contents inline.

---

## How to use

### Starting fresh (Phase 1)

Paste your resume or upload it as a file and say:

> "Rewrite my resume."

That's the whole prompt. Claude will run Phase 1 and produce `resume-canonical.md`.

**Save that file.** It's the master copy. Every customization in Phase 2 starts from it.

If you have a target role in mind, paste the job description at the same time:

> "Rewrite my resume. Here's a job description I'm targeting: [paste JD]"

Claude will use it to weight which bullets to prioritize.

---

### Tailoring for a role (Phase 2A — recommended default)

Once you have your canonical resume, paste it along with a job description:

> "Here's my canonical resume and a job description. Give me the targeted customization for this role."

Claude will update only the five highest-impact sections and show you a swap summary of what changed and why.

Use this path when you're applying to multiple roles — it's fast, low-cost, and you keep the canonical intact.

---

### Full ATS audit (Phase 2B)

For roles where you want to know your keyword match score:

> "Run a full ATS optimization on my canonical resume against this job description."

Claude will extract every keyword from the JD, categorize them by priority, embed them in the right sections, calculate an ATS match score (out of 100), and produce a keyword match report.

---

### Cover letter (Phase 3)

> "Write me a cover letter for this role at [Company]. Here's the JD. What excites me about this company is [specific thing]."

The "what excites you" detail is required — Claude will ask for it if you don't include it. Vague answers ("great culture") produce generic cover letters. Specific answers ("their approach to pricing transparency in a market that hides fees") produce targeted ones.

---

## What to have ready

| Phase | Required | Optional |
|---|---|---|
| 1 — Full Rewrite | Your current resume (paste or file) | Job description |
| 2A — Targeted | Canonical resume + job description | — |
| 2B — ATS Audit | Canonical resume + job description | — |
| 3 — Cover Letter | Job description + what excites you | Canonical or tailored resume |

---

## Common questions

**Do I need to run Phase 1 first?**
Yes, if you want Phase 2 to work well. Phase 2A and 2B both take the canonical as input. If your current resume is already strong (clean bullets, real metrics, no formatting issues), you can use it as the canonical — just call it that when you share it.

**How often should I re-run Phase 1?**
Once, unless your work history changes significantly or you're pivoting to a different function. Phase 2A handles role-to-role variation without touching the base.

**My resume has no numbers. Will this work?**
Yes. Phase 1 includes metrics guidance — Claude will estimate plausible numbers (team sizes, time savings, budget ranges) and flag them with `[verify]` so you review before submitting. Expect a quick pass to confirm the estimates.

**What's the canonical resume?**
It's the output of Phase 1 — a clean, well-written, ATS-safe version of your resume that isn't tailored to any specific role. Think of it as your master copy. You bring it back every time you customize for a new role.

**Can I run Phase 2A more than once?**
Yes — once per role you're applying to. Each run produces a separate tailored file (`resume-[Company].md`). The canonical stays untouched.

---

## Credits

Built on the [agentskills.io](https://agentskills.io) SKILL.md format. AI-writing rules adapted from [brandonwise/humanizer](https://github.com/brandonwise/humanizer) vocabulary research. Skill authored by Mike Cregan.
