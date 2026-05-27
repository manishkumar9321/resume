# CLAUDE.md — AI Assistant Guide for `manishkumar9321/resume`

> Last updated: 2026-05-27

---

## 1. Project Overview

This repository is a **static HTML personal résumé website** for **Manish Kumar**, an Associate Engineer (Automation Lead) at Deutsche Bank, London. There are no build tools, package managers, or server-side code. The site consists of three plain HTML pages and one profile image.

The site is likely served as a **GitHub Pages** static site directly from the `main` branch.

---

## 2. Repository Structure

```
resume/
├── CLAUDE.md          ← this file
├── README.md          ← minimal placeholder (single heading)
├── Manish.jpeg        ← profile photo (40 KB, 400×400 JPEG)
├── index.html         ← main résumé page (landing page)
├── contact.html       ← mailto contact form
└── education.html     ← education history page
```

No hidden config files, no `.gitignore`, no `package.json`, no CI pipeline.

---

## 3. File-by-File Reference

### `index.html` — Main Résumé

| Section | Location (approx. lines) | Notes |
|---------|--------------------------|-------|
| Header (photo + name + links) | 8–25 | Uses `<table>` for two-column layout |
| Professional summary | 28 | Single `<p>` paragraph |
| Key Responsibilities | 30–106 | Unordered list, 23 `<li>` items |
| Domain Expertise | 108–124 | Ordered list, 4 items |
| Working Experience | 126–168 | Bordered `<table>`, 4 employers |
| Education link | 170–172 | Link to `education.html` |
| Skills (primary table) | 173–201 | **Contains bug**: `<tody>` typo |
| Skills (duplicate split table) | 203–244 | **Duplicate + bug**: two `<tody>` typos |

**Career Timeline:**

| Period | Employer |
|--------|----------|
| Jan 2019 – present | Deutsche Bank (London) |
| Jul 2016 – Jan 2019 | Infosys LTD |
| Jan 2015 – Jul 2016 | ADP |
| May 2012 – Dec 2014 | Cognizant Technology Solutions |

### `contact.html` — Contact Form

Simple HTML `<form>` with `action="mailto:manishkumar9321@gmail.com"` and `method="post" enctype="text/plain"`. Fields: name, email, phone, message textarea, submit button. This is a client-side mailto form — it opens the visitor's default email client.

### `education.html` — Education

Unordered list of three qualifications:
- Bachelor of Engineering – Information Technology (TIEIT Bhopal, M.P., India)
- HSC (Higher Secondary Certificate)
- SSC (Secondary School Certificate)

### `Manish.jpeg` — Profile Photo

JFIF JPEG, progressive compression, 40 KB. Referenced in `index.html` via relative path `src="Manish.jpeg"`.

---

## 4. Known HTML Bugs

These are pre-existing issues. Fix them when touched; don't introduce new ones.

| File | Line(s) | Issue | Fix |
|------|---------|-------|-----|
| `index.html` | 175, 208, 226 | `<tody>` typo (3×) | Change to `<tbody>` |
| `index.html` | 129 | `<thead>` is a child of `<tbody>` | Move `<thead>` before `<tbody>` |
| `index.html` | 46–47 | Duplicate "More than 4 Years of experience in Team Leading" list item | Remove one |
| `index.html` | 103–104 | Duplicate "Worked on Task tracking tool like Rally, TFS and Jira" list item | Remove one |
| `index.html` | 173–244 | Entire Skills section is duplicated (first as a single table, then as a nested two-column layout) | Keep only the two-column version; remove lines 173–201 |
| `index.html` | 19 | `</br>` is not valid HTML (`<br>` is a void element) | Remove the `</br>` |
| `index.html` | 28 | `</P>` closing tag with uppercase P (inconsistent casing) | Change to `</p>` |
| `contact.html` | 20 | `</br>` inside `<p>` — invalid void element close | Remove `</br>` |

---

## 5. Technology Stack

| Layer | Technology |
|-------|-----------|
| Markup | HTML5 (static, no templating) |
| Styling | None (no CSS file; browser defaults only) |
| Scripting | None (no JavaScript) |
| Build | None |
| Package manager | None |
| Tests | None |
| Linting | None |
| Hosting | GitHub Pages (inferred) |

---

## 6. Development Workflow

### Making Changes

Because there are no build tools, the workflow is straightforward:

1. **Edit** the relevant `.html` file directly.
2. **Validate** mentally (or with a browser) — there is no automated linter.
3. **Commit** with a clear message.
4. **Push** to the appropriate branch (see below).

### Branch Strategy

| Branch | Purpose |
|--------|---------|
| `main` | Production — served as GitHub Pages |
| `claude/*` | Feature/documentation branches created by AI assistants |

Always develop on a `claude/*` feature branch and open a PR to `main` unless explicitly told otherwise.

### Deployment

No CI/CD pipeline. GitHub Pages auto-deploys from the `main` branch root. Changes are live within ~1 minute of merging to `main`.

### Testing

There is no automated test suite. Manual testing means:
- Opening the HTML files in a browser
- Checking all internal links (`contact.html`, `education.html`, image path)
- Verifying the mailto form opens correctly
- Checking the LinkedIn external link

---

## 7. Content Conventions

### Tone & Style

- Professional, first-person implicit (no "I" pronoun used in bullet lists)
- British English spelling (the owner is based in Leamington Spa, UK)
- Skill ratings expressed as asterisks: `*****` = 5/5, `****` = 4/5

### HTML Style

- Two-space indentation (with inconsistencies — match the surrounding code)
- Lowercase tag names preferred (some uppercase exists; normalise to lowercase)
- Attributes use `=` with `"double quotes"`
- Tables are used for layout (this is intentional for the résumé grid style — do not convert to CSS Grid/Flexbox unless explicitly asked)
- No `class` or `id` attributes currently in use (except the textarea in `contact.html`)
- No external stylesheets or CDN links

### Linking

- Internal links are relative: `href="contact.html"`, `href="education.html"`
- Image path is relative: `src="Manish.jpeg"`
- The LinkedIn URL uses the full `https://` scheme

---

## 8. AI Assistant Instructions

### What to Do

- **Fix typos and HTML bugs** listed in §4 when you touch those sections.
- **Preserve the overall structure and content** — this is a personal document; don't restructure without being asked.
- **Keep all changes on a feature branch** and commit with descriptive messages.
- **Validate HTML mentally** before committing — pay attention to properly nesting `<thead>` outside `<tbody>`, closing tags, void elements (`<br>`, `<hr>`, `<input>`, `<meta>`).
- **Preserve the mailto address** `manishkumar9321@gmail.com` exactly.

### What Not to Do

- **Do not add CSS frameworks** (Bootstrap, Tailwind, etc.) unless explicitly requested.
- **Do not add JavaScript** unless explicitly requested.
- **Do not remove any professional information** (experience, skills, employers).
- **Do not change the profile photo filename** (`Manish.jpeg`) — it is referenced by `index.html`.
- **Do not invent or fabricate employment history, dates, or skills.**
- **Do not convert the table-based layout** to CSS unless asked.
- **Do not create a `package.json`** or add any build tooling unless asked.

### Commit Message Format

Use imperative mood, present tense:

```
Fix <tody> typo → <tbody> in skills tables

Fix duplicate list items in Key Responsibilities section

Add CSS styling for improved readability
```

End every commit message with the session URL on its own line (already handled by the harness).

---

## 9. Potential Improvements (Reference Only)

These are ideas — **do not implement without being asked**:

- Add a `<link rel="stylesheet">` for basic styling (font, spacing, colour)
- Add `<meta name="viewport">` for mobile responsiveness
- Add `<meta name="description">` for SEO
- Replace star-rating system with a proper visual (progress bars, icons)
- Add a navigation bar linking all three pages
- Add `aria-label` and accessibility attributes
- Add `.gitignore` (e.g., to ignore OS files like `.DS_Store`)
- Fix the duplicate Skills section (keep the two-column nested table layout)
- Add `favicon.ico` / `<link rel="icon">`

---

## 10. Quick Reference

| Task | Command |
|------|---------|
| View site locally | Open `index.html` in a browser |
| Check git status | `git status` |
| Switch to feature branch | `git checkout -b claude/<description>` |
| Stage all changes | `git add -A` |
| Commit | `git commit -m "Your message"` |
| Push branch | `git push -u origin <branch-name>` |
