# resume-skill-kit

> A four-phase Claude skill for rewriting, targeting, and submitting resumes & cover letters that don't get ignored.

---

## What Is This

A Claude skill that takes a resume from raw to ready-to-submit. It handles the whole pipeline:

- **Phase 1 — Full Rewrite**: XYZ bullets, power verbs, metrics, AI-isms removed, red flags cleared
- **Phase 2A — Targeted Customization**: Fast section swaps for a specific JD (headline, summary, highlights, tech, competencies)
- **Phase 2B — Full ATS Optimization**: Keyword extraction, exact-match scoring, format audit
- **Phase 3 — Cover Letter**: 250–300 words, structured to make someone stop scrolling

The output of Phase 1 becomes your canonical resume — a master version you tailor from, not rewrite.
The skill builds on that over time instead of starting from scratch with every application.

> **This is not a spray-and-pray tool.** It's a filter. The more you use it on targeted roles,
> the better your hit rate gets. Phase 2A takes minutes. Phase 1 is where the real work happens —
> do it once, do it right, reuse it.

---

## What's Included

```
resume-skill-kit/
├── SKILL.md                              # Main skill — all four phases
├── references/
│   ├── avoid-ai-writing.md               # AI-isms detection and removal rules
│   ├── power-verbs.md                    # Verb bank organized by function
│   └── ats-rules.md                      # ATS format rules (Workday, Greenhouse, Lever, iCIMS)
├── templates/
│   └── bullet-library-template.md        # Template for your personal bullet bank
├── README.md
└── LICENSE
```

---

## Quick Start

### Claude Code

```bash
# Clone the repo
git clone https://github.com/mikeburke925/resume-skill-kit.git

# In your project root or CLAUDE.md, register the skill path
# Point Claude at SKILL.md to activate it
```

Then in Claude Code:
```
"Rewrite my resume" → Phase 1
"Customize this for [Company]" + paste JD → Phase 2A
"Run a full ATS audit for [Company]" + paste JD → Phase 2B
"Write me a cover letter for [Company]" → Phase 3
```

### Claude.ai (claude.ai Projects)

1. Create a new Project
2. Upload `SKILL.md`, the `references/` folder, and your `bullet-library.md` (once populated)
   as Project files
3. Start a conversation and tell Claude to follow the skill

### Other Claude Tools (Cursor, Copilot, OpenHands, etc.)

Any assistant that supports the [agentskills](https://agentskills.io) SKILL.md format can
use this skill. Point the assistant at `SKILL.md` and it will follow the phase structure.

---

## How to Use It

### Step 1 — Run Phase 1 (once)

Paste your current resume (or upload the file). Optionally include a job description to
weight which bullets get prioritized.

Claude will:
- Rewrite every bullet using Google's XYZ formula
- Add or estimate metrics where they're missing (flagged with `[verify]`)
- Remove red flags, objective statements, and AI-isms
- Output a canonical `resume-canonical.md`

Save that file. It's your master copy.

### Step 2 — Build Your Bullet Library (ongoing)

Copy `templates/bullet-library-template.md` and rename it to `master-bullet-library.md`.
After Phase 1, move your best bullets into it organized by tag (OPERATIONS, REVENUE, GTM, etc.).

The bullet library is what makes Phase 2A get better over time — more bullets = more options
for the skill to find the right proof points per role.

### Step 3 — Apply to Roles (Phase 2A or 2B)

Paste a job description and your canonical resume. Choose:

- **Phase 2A** (default): Fast swap of 5 sections — best for most applications
- **Phase 2B**: Full keyword audit + ATS score — best when you really want this role

### Step 4 — Write the Cover Letter (Phase 3)

Paste the JD and tell Claude one thing that genuinely excites you about the company.
The skill writes a 250–300 word letter structured to actually get read.

---

## File Reference

| File | What it does |
|---|---|
| `SKILL.md` | Main skill with all phases and logic |
| `references/avoid-ai-writing.md` | Rules for stripping AI-isms from bullets and prose |
| `references/power-verbs.md` | Verb bank for opening bullets — organized by function |
| `references/ats-rules.md` | ATS format rules for Phase 2B audits |
| `templates/bullet-library-template.md` | Starting template for your personal bullet bank |

---

## Customizing the Skill

The skill is designed to be edited. A few things worth adjusting before your first run:

**`references/power-verbs.md`** — Remove verbs that don't match your industry. Add domain-specific
ones. A finance resume and an engineering resume shouldn't share the same verb bank.

**`templates/bullet-library-template.md`** — Rename the tags to match your career. The default
tags are generic by design. If your work centers on a specific function, add tags that reflect that.

**`SKILL.md` — Section 2 (Professional Summary rules)** — The summary rewrite uses neutral
defaults. If you have an established voice or structure you want preserved, add it here under
a "Voice Notes" section so Claude keeps it consistent across applications.

---

## ATS Coverage

The `references/ats-rules.md` file covers known behavior on:

| Platform | Coverage |
|---|---|
| Workday | ✓ |
| Greenhouse | ✓ |
| Lever | ✓ |
| iCIMS | ✓ |
| Taleo | Partial (legacy) |

Rules are based on tested behavior as of 2025. ATS platforms update regularly — if you hit
a parsing issue on a platform not listed, open an issue or PR.

---

## Credits

- AI-isms detection rules adapted from [avoid-ai-writing](https://github.com/conorbronsdon/avoid-ai-writing)
  by Conor Bronsdon (MIT License)
- XYZ bullet formula from Google's re:Work hiring documentation
- ATS rules compiled from tested behavior across major applicant tracking platforms

---

## License

MIT — see [LICENSE](LICENSE)
