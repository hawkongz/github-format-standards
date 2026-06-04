---
name: github-format-standards
description: GitHub project formatting standards — use when preparing a project for GitHub, writing or editing README.md, ISSUE_TEMPLATE, PULL_REQUEST_TEMPLATE, CONTRIBUTING.md, CODE_OF_CONDUCT.md, or any other GitHub documentation. Automatically enforces GitHub best practices for Markdown formatting, document structure, and Chinese-English mixed typography. Trigger even for casual requests like "check my formatting", "polish the README", or "getting ready to publish on GitHub".
---

# GitHub Format Standards

When the user wants to share a project on GitHub, execute the full pipeline below. Do NOT just output rules — take action.

## Full Pipeline

### Phase 1: Audit

Scan the project and report what exists vs. what's missing:

```
Existing:  README.md ✓  CONTRIBUTING.md ✗  .github/ ✗  SECURITY.md ✗
Issues:    3 tables missing alignment, 2 code blocks missing language tags
```

### Phase 2: Fix Existing Files

Go through every `.md` file and fix all issues. Do NOT ask for confirmation — just fix.

- [ ] Headings: `#` spacing, no level skipping
- [ ] Code blocks: every ` ``` ` has a language tag (` ```python `, ` ```bash `)
- [ ] Tables: every separator row has `:---` alignment markers
- [ ] Lists: consistent marker (`*` or `-`), 2-space sub-indent
- [ ] Links: no bare URLs, every image has alt text
- [ ] Chinese spacing: `使用 GitHub` not `使用GitHub`
- [ ] Proper nouns: `GitHub` not `github`, `JavaScript` not `Javascript`
- [ ] File endings: exactly one trailing blank line

### Phase 3: Generate Missing Files

- **`.github/ISSUE_TEMPLATE/`** — bug report + feature request templates, plus `config.yml`
- **`.github/PULL_REQUEST_TEMPLATE.md`** — with summary, test plan, screenshots section
- **`CONTRIBUTING.md`** — how to contribute, dev setup, commit conventions
- **`SECURITY.md`** — responsible disclosure instructions
- **`.gitignore`** — if missing, generate based on project language

### Phase 4: README Polish

Rewrite README to match top-project patterns (React / FastAPI / TensorFlow):

```
(Optional: centered logo)
# [Project Name]
(One-line tagline, no ## heading)
(Optional: badges row)

(Description — start with WHY, then WHAT, no heading)

## Features          ← * **Keyword:** description format
## Quick Start        ← must be copy-paste ready
## Installation
## Usage
## API Reference
## Contributing
## License
```

### Phase 5: Bilingual Support (Chinese projects)

If the project is Chinese or bilingual:

- Root: English `README.md` + English `SKILL.md`
- `zh-CN/`: Chinese `README.md` + Chinese `SKILL.md`
- Both have `**Language:** [English](README.md) | [简体中文](zh-CN/README.md)` at top

### Phase 6: Ship It

After all fixes and files are generated:

1. `git init` if not already a repo
2. `git add` all files (excluding secrets, `.env`, large binaries)
3. Commit with a clear message
4. Create GitHub repo via `gh repo create` if not exists
5. `git push`
6. Output the final GitHub URL

If the user just wants a local preview, stop after Phase 5 and show a summary of all changes.

---

## Summary Format

After completion, always output a table like this:

| Phase | Actions |
| :--- | :--- |
| Audit | 3 issues found: ... |
| Fix | 5 changes across 2 files |
| Generate | Created 4 files: .github/..., CONTRIBUTING.md, ... |
| Polish | Rewrote README structure |
| Ship | Pushed to https://github.com/... |

---

## README Structure Reference

```
(Optional: centered logo with <div align="center">)
# [Project Name](https://website)
(one-line tagline, no ## heading, may be centered)
Badges row

(Description paragraphs — no heading, start with WHY)
## Features            ← * **Keyword:** description
## Demo / Screenshots
## Quick Start         ← 3 minutes to running
## Installation
## Usage
## Configuration
## API Reference
## Contributing
## License
## Acknowledgments
```

Optional: Security, Good First Issues, Related Projects.

## Chinese-Specific Rules

- Chinese + English: `使用 GitHub` (space between)
- Chinese + numbers: `支持 10 个` (space between)
- Proper nouns: `GitHub`, `JavaScript`, `TypeScript`, `Python`, `Node.js`, `React`, `Vue`, `macOS`, `API`, `URL`, `VS Code`, `npm`
- Chinese text → Chinese punctuation `，。：（）`
- English text → English punctuation `,.:()`

## Template References

Read `references/` for full templates when generating files:

- `references/readme-template.md`
- `references/issue-template.md`
- `references/pr-template.md`
- `references/contributing-template.md`
