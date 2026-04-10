# ATS Rules Reference

Use this file during Phase 2B (Full ATS Optimization) to audit resumes for formatting and
structural issues that cause ATS systems to misparse or drop candidates before a human sees them.

Tested against Workday, Greenhouse, Lever, and iCIMS. Rules may vary by platform version.

---

## What ATS Systems Do

Applicant Tracking Systems parse your resume into structured fields: name, contact info,
work history, education, and skills. If the parser can't read your resume, it may:
- Mis-assign job titles to the wrong company
- Drop bullets it can't parse
- Score you 0% on keyword matching despite having the right skills
- Reject the file outright

A resume that looks great in PDF may be unreadable to an ATS. These rules prevent that.

---

## Format Rules

### File Format
- **Submit `.docx` or plain `.pdf` when possible.** Some ATS systems handle both; others prefer one.
  When in doubt, `.docx` parses more reliably.
- **Never submit a scanned PDF.** Scanned resumes are images — ATS cannot read them.
- **Avoid PDF created from Canva, Adobe Illustrator, or design tools.** These often use text
  as image layers that ATS can't parse.

### Layout
- **Single column only.** Multi-column layouts confuse ATS parsers — content from column 2
  gets merged into column 1, or dropped entirely.
- **No tables for main content.** Tables may not be read left-to-right by older parsers.
  Use plain text with consistent spacing.
- **No text boxes.** Content in text boxes is frequently invisible to ATS.
- **No headers/footers for key content.** Name, contact info, and job titles in the header/footer
  area may not be parsed.

### Fonts and Styling
- **Standard fonts only.** Stick to: Arial, Calibri, Georgia, Garamond, Times New Roman, Helvetica.
  Decorative fonts often get stripped or misrendered.
- **No font sizes below 10pt.** Small text may be skipped by parsers.
- **Avoid colored text for key content.** Some parsers strip color and may lose text.

---

## Content Rules

### Section Headers
- Use standard section names. ATS systems look for keywords like "Work Experience," "Education,"
  "Skills," and "Certifications." Creative headers like "Where I've Been" may not be recognized.
- Acceptable variations:
  - Work Experience / Experience / Professional Experience
  - Education / Academic Background
  - Skills / Technical Skills / Core Competencies
  - Certifications / Licenses & Certifications

### Contact Information
- Include: name, city/state, email, phone, LinkedIn URL
- Do NOT include: full street address (privacy risk), headshot/photo, date of birth, gender,
  marital status
- Format email as plain text, not as a hyperlink-only clickable — some parsers drop the text

### Dates
- Use consistent date format throughout: `Month YYYY` or `YYYY` only
- Do not abbreviate inconsistently: `Jan 2022` and `January 2022` in the same document
  confuses date parsing
- For current roles: `Month YYYY – Present`

### Bullets
- Use standard bullet characters: `•` or `-`. Avoid custom symbols or emoji.
- Keep bullets as plain text. Nested bullets are often dropped.
- Do not put important keywords only in a table, text box, or sidebar — they may not be indexed.

### Keywords
- Use the exact phrasing from the job description, not just synonyms.
  ATS scores keyword **exact match**. "Project Management" and "PM" are scored separately.
- Include both the spelled-out form and abbreviation on first use:
  `Customer Relationship Management (CRM)`
- Do not hide keywords (white text on white background, font size 1). Modern ATS systems
  detect this and may penalize or flag the application.

---

## Common ATS Killers (Quick Checklist)

Run through this before submitting Phase 2B output:

- [ ] File is `.docx` or ATS-safe `.pdf` (not scanned, not from a design tool)
- [ ] Single-column layout — no tables, text boxes, or multi-column sections
- [ ] Contact info is in the body, not only in the header/footer
- [ ] Section headers use standard names
- [ ] Dates are consistent in format throughout
- [ ] No decorative fonts, colored text, or very small font sizes
- [ ] Bullets use standard characters (`•` or `-`)
- [ ] Keywords from the JD appear as exact-match phrases in the resume text
- [ ] Acronyms and spelled-out forms both appear (at least on first use)
- [ ] No hidden text

---

## Platform-Specific Notes

| Platform | Known quirks |
|---|---|
| **Workday** | Parses sections strictly. Non-standard headers are often mis-filed. Always use "Work Experience" not "Career History." |
| **Greenhouse** | Generally robust. Multi-column PDFs still cause problems. Handles `.docx` well. |
| **Lever** | Strong PDF support. Watch for text boxes — they're silently dropped. |
| **iCIMS** | Older parser. Very sensitive to layout. Single column + `.docx` is safest. |
| **Taleo** | Legacy system still used at large enterprises. Least forgiving. Plain text fallback sometimes needed. |

---

## Notes

ATS platforms update regularly. These rules reflect common behavior across major systems as of 2025.
When in doubt, submit in the simplest possible format — ATS rewards parseable over pretty.
