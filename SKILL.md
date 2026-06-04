---
name: github-format-standards
description: GitHub project formatting standards — use when preparing a project for GitHub, writing or editing README.md, ISSUE_TEMPLATE, PULL_REQUEST_TEMPLATE, CONTRIBUTING.md, CODE_OF_CONDUCT.md, or any other GitHub documentation. Automatically enforces GitHub best practices for Markdown formatting, document structure, and Chinese-English mixed typography. Trigger even for casual requests like "check my formatting", "polish the README", or "getting ready to publish on GitHub".
---

# GitHub Format Standards

When the user is preparing a project to share on GitHub, inspect and fix all documentation formatting per the rules below.

## Workflow

1. **Scan**: find all `.md` files and `.github/` directory templates
2. **Check**: audit each file against every rule below
3. **Fix**: correct issues immediately without waiting for user confirmation
4. **Summarize**: list every change made and the reason for each

---

## 1. Markdown General Rules

### 1.1 Heading Hierarchy

- `#` H1 = file title (exactly one per file)
- `##` H2 = major sections
- `###` H3 = subsections, and so on
- **Never skip levels** (e.g., `#` followed directly by `###` is forbidden)
- Blank line before and after each heading
- One space after `#` before text: `# Title` not `#Title`

### 1.2 Code Blocks

- **Always specify the language**: use ` ```python ` not bare ` ``` `
- Common language tags: `python`, `bash`, `javascript`, `typescript`, `json`, `yaml`, `html`, `css`, `sql`, `dockerfile`, `shell`
- Use `bash` for command-line examples; prefix commands with `$` to distinguish from output

### 1.3 Tables

- Alignment markers: `:---` (left), `:---:` (center), `---:` (right)
- Header and separator must have the same number of columns
- Prefer left alignment for mixed Chinese-English tables

### 1.4 Links & Images

- Use `[text](url)` for links, avoid bare URLs
- Use `![alt text](url)` for images, always write meaningful alt text
- Reference-style links for repeated URLs

### 1.5 Lists

- Unordered lists: use `*` (React, TensorFlow, FastAPI all use `*`)
- Chinese projects may prefer `-`; pick one and stay consistent
- Sub-lists indented **2 spaces**
- Feature lists: use `* **Keyword:** description` format (React style)

### 1.6 Blank Lines & Spacing

- Blank line before each heading (except at start of file)
- Blank line before and after each code block
- Blank line before and after each table
- Blank line before and after each list
- File must end with exactly **one** blank line

---

## 2. README.md Standard Structure

Structure README per the patterns used by top projects (React / FastAPI / TensorFlow):

```
(Optional: centered logo with <div align="center">)
# [Project Name](https://website)   ← title often links to the site
(One-line tagline, no ## heading, can be centered)
(Optional: badges row, separated by &middot; or spaces)

(Description paragraphs start directly — no "## Introduction" heading)
Paragraph 1: what the project is, what problem it solves.
Paragraph 2: key features or technical highlights.

## Features
## Demo / Screenshots
## Quick Start             ← most important section — get running in 3 minutes
## Installation
## Usage
## Configuration
## API Reference
## Contributing
## License
## Acknowledgments
```

**Key principles** (validated against top projects):
- **No `## Introduction` heading** — React, FastAPI, TensorFlow all start with plain paragraphs
- Lead with WHY (problem solved), then WHAT (how it works)
- "Quick Start" determines whether visitors stay — commands must be copy-paste ready

### HTML in Markdown (common & recommended)

Top projects regularly mix HTML into Markdown:

```markdown
<!-- Centering -->
<div align="center">
  <img src="logo.png" alt="Logo">
</div>

<!-- Collapsible details -->
<details>
<summary>Click to expand</summary>
Collapsed content here.
</details>
```

### Optional but recommended sections

- **Security**: responsible disclosure instructions (Next.js style)
- **Good First Issues**: guide new contributors (React/Next.js style)
- **Related Projects / Ecosystem**: cross-promotion (FastAPI → Typer style)

---

## 3. GitHub Template Files

### 3.1 ISSUE_TEMPLATE

Location: `.github/ISSUE_TEMPLATE/` or `.github/ISSUE_TEMPLATE.md`

Must include: description, reproduction steps (for bugs), expected behavior, actual behavior, environment info, screenshots/logs (optional).

### 3.2 PULL_REQUEST_TEMPLATE

Location: `.github/PULL_REQUEST_TEMPLATE.md`

Must include: change summary, reason for change, test plan, screenshots (for UI changes), linked issue (`Closes #123`).

### 3.3 CONTRIBUTING.md

Must include: how to submit issues, how to submit PRs, code style requirements, local dev setup, testing requirements.

---

## 4. Chinese-Specific Rules

### 4.1 Spacing

**Add a space** between:
- Chinese and English: `使用 GitHub 托管` (not `使用GitHub托管`)
- Chinese and numbers: `支持 10 个节点` (not `支持10个节点`)

**No space** between:
- Chinese punctuation and Chinese text
- English words and English punctuation

### 4.2 Proper Noun Capitalization

Common terms with correct capitalization:
GitHub, JavaScript, TypeScript, Python, Node.js, React, Vue, macOS, API, URL, HTML, CSS, JSON, YAML, VS Code, npm, pip

### 4.3 Punctuation

- **Chinese paragraphs**: use Chinese punctuation `，` `。` `：` `（）`
- **English paragraphs**: use English punctuation `,` `.` `:` `()`
- Code, filenames, commands wrapped in backticks: `` `config.json` ``, `` `npm install` ``

---

## 5. Checklist

### Markdown basics
- [ ] No heading level skipping (`#` → `##` → `###`)
- [ ] Code blocks have language tags
- [ ] Tables aligned with consistent column counts
- [ ] Links have descriptive text (no bare URLs)
- [ ] Images have alt text
- [ ] List indentation consistent (2 spaces recommended)
- [ ] File ends with one blank line

### README
- [ ] One-line tagline after title
- [ ] Install / Quick Start section present
- [ ] Commands are copy-paste ready
- [ ] License is clear

### Chinese projects
- [ ] Spaces between Chinese and English
- [ ] Spaces between Chinese and numbers
- [ ] Proper noun capitalization correct
- [ ] Punctuation matches language

---

## 6. Common Mistakes Quick Reference

| Wrong | Right | Reason |
| :--- | :--- | :--- |
| `#Title` | `# Title` | Missing space after `#` |
| ```` ``` ```` | ```` ```python ```` | Missing language tag |
| `使用GitHub` | `使用 GitHub` | Missing space between Chinese/English |
| `支持10个` | `支持 10 个` | Missing space between Chinese/numbers |
| `[https://...](https://...)` | `[Docs](https://...)` | Link missing description |
| `Github` / `github` | `GitHub` | Incorrect proper noun capitalization |
| File ends without blank line | File ends with one blank line | POSIX compliance |

---

## 7. Template References

Full templates in `references/` directory:

- `references/readme-template.md` — full README template
- `references/issue-template.md` — Issue template
- `references/pr-template.md` — Pull Request template
- `references/contributing-template.md` — Contributing guide template
