# ATS Parser Rules & Platform Quirks

## Universal Formatting Rules (All Platforms)

### Section Headings — Use ONLY These
- Summary (not "Profile," "About Me," "Objective")
- Experience (not "Work History," "Employment," "Career")
- Education (not "Academic Background," "Schooling")
- Skills (not "Competencies," "Expertise," "Toolkit")
- Certifications (standalone section, not buried in Education)
- Projects (optional, standalone only)

### Formatting That Crashes Parsers — Remove All
- Tables (even simple 2-column layouts)
- Text boxes
- Headers and footers (contact info in headers is invisible to most ATS)
- Columns / multi-column layouts
- Graphics, logos, icons, lines as design elements
- Special characters: ✓ → • ★ ◆ (use plain hyphens or nothing)
- Fancy bullet styles (use • or plain -)
- Embedded hyperlinks in body text (spell out URLs or remove)
- Footnotes

### Date Format — Standardize Throughout
✅ `Month YYYY – Month YYYY` (e.g., January 2022 – March 2024)
✅ `MMM YYYY` abbreviated (e.g., Jan 2022 – Mar 2024)
❌ Never mix formats within a document

### File Format Guidance
- `.docx` → ATS submission (most compatible, 90%+ of platforms)
- `.pdf` → Direct-to-human only (recruiter email, referral, portfolio)
- Never: `.pages`, `.odt`, `.txt`, image-based PDFs

---

## Platform-Specific Quirks

### Workday
- Parses chronologically — most recent role must be listed first
- Skills section is re-entered into dropdowns manually; still include in document for human review
- GPA and graduation year often required fields; include in Education
- Hates: graphics, columns, non-standard fonts

### Greenhouse
- Strong keyword matching on exact phrase from JD
- Pulls skills from the Skills section first, then scans bullets
- Cover letter often required as free-text entry (not upload)
- Hates: tables, PDFs with images

### Lever
- Parses LinkedIn-style; chronological order critical
- Scores on keyword density, not just presence
- Social URLs (LinkedIn, GitHub) should be in contact section, not hyperlinked body
- Tolerates PDFs better than most ATS

### iCIMS
- Most aggressive parser — strip all formatting
- Reads headers/footers as body text (garbage in output)
- Prefers `.docx` strongly
- Skills must be exact-match to their internal taxonomy when possible

---

## Keyword Optimization Rules

### Extraction Priority (from JD)
1. Job title and title variations
2. Required technical skills / tools / platforms
3. Required soft skills listed explicitly (not implied)
4. Industry-specific terms and certifications
5. Action verbs used in the JD (mirror them back)

### Placement Hierarchy
1. Summary (highest weight — parsed first)
2. Skills section (second weight — structured field)
3. First bullet of most recent role (third weight)
4. Subsequent bullets

### Synonym Coverage Rule
Always include both forms on first use:
- `Search Engine Optimization (SEO)` not just `SEO`
- `Customer Relationship Management (CRM)` not just `CRM`
- `Key Performance Indicator (KPI)` not just `KPI`

### ATS Match Score Rubric (1–100)
| Range | Meaning |
|---|---|
| 85–100 | Top 10% — proceed confidently |
| 70–84 | Strong — minor keyword gaps |
| 55–69 | Moderate — missing key terms |
| 40–54 | Weak — significant gaps, risk of auto-rejection |
| <40 | High rejection risk — major overhaul needed |

Score is calculated as: (keywords matched / total keywords extracted) × density bonus (keywords in summary/skills vs. buried in bullets) × format penalty (deduct for any parser-crashing elements found).
