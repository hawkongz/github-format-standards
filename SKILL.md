---
name: github-format-standards
description: "Use when the user wants to share a project to GitHub. Runs a full pipeline: root audit, file naming and structure, document fixes, generate missing files (LICENSE, .gitignore, CONTRIBUTING.md, Issue/PR templates), README rewrite (centered title, TOC), bilingual setup, git init, conventional commit, gh repo create, push, semantic tag. Triggers on 'share to GitHub' or '/GitHub格式规范'."
---

# GitHub Format Standards

When the user wants to share a project on GitHub, run the full pipeline. **Take action directly — don't just recite rules.**

## Full Pipeline (7 Phases)

### Phase 1: Root Directory Audit

Check the project root for cleanliness:

- **Red flags**: large files (>1MB), temp files (`*.tmp`, `*.bak`, `~*`), build artifacts (`dist/`, `build/`, `*.pyc`), personal config (`.env`, `credentials.*`, `*.pem`), IDE cruft (`.vscode/`, `.idea/`)
- If found: warn the user and add them to `.gitignore`
- Ensure `.gitignore` exists and covers at minimum: `node_modules/`, `__pycache__/`, `*.pyc`, `.env`, `.DS_Store`, `dist/`, `build/`, IDE dirs

```
Root audit:
  ⚠  node_modules/ found — added to .gitignore
  ✓  No large files, no secrets, no build artifacts
  ✓  .gitignore created with 12 rules
```

### Phase 2: File Naming & Directory Structure

**Naming rules**:
- All lowercase, hyphens (`my-project`) or underscores (`my_project`) — pick one style per project
- No spaces, no Chinese characters in file/directory names (unless the project IS multilingual docs)
- Scripts: `scripts/`, examples: `examples/`, docs: `docs/`, tests: `tests/` or `__tests__/`, source: `src/` or `lib/`
- Fix violations immediately — rename files, move things into proper directories

**Structure enforcement**:
```
project/
├── src/           # source code (or lib/)
├── tests/         # test files (or __tests__/)
├── docs/          # documentation (optional, may use README instead)
├── scripts/       # utility scripts
├── examples/      # example usage
├── README.md
├── LICENSE
├── .gitignore
└── CONTRIBUTING.md
```

If the project is small (single script), the flat structure is fine — don't over-engineer.

### Phase 3: Document Audit & Fix

Go through every `.md` file and fix:

- [ ] Headings: `# Title` not `#Title`, no level skipping (`#` → `##` → `###`)
- [ ] Code blocks: every ` ``` ` has a language tag
- [ ] Tables: separator row has `:---` alignment markers
- [ ] Lists: consistent marker (`*` preferred), 2-space sub-indent
- [ ] Commands: every shell command has an explicit interpreter (`python script.py` not `./script.py`; `bash script.sh` not `./script.sh`; `powershell ...` for Windows-specific commands). The reader should never guess how to run a command.
- [ ] Links: no bare URLs, every image has alt text
- [ ] Chinese spacing: `使用 GitHub` not `使用GitHub`; `支持 10 个` not `支持10个`
- [ ] Proper nouns: `GitHub` not `github`, `JavaScript` not `Javascript`
- [ ] File endings: exactly one trailing blank line
- [ ] Image paths: relative or CDN, never absolute local paths

### Phase 4: Generate Missing Files

- **`LICENSE`** (required): default to MIT if the user doesn't specify
- **`.gitignore`** (required): generate based on project language
- **`CONTRIBUTING.md`** (recommended): for any project with >1 file
- **`SECURITY.md`** (recommended): responsible disclosure instructions
- **`.github/ISSUE_TEMPLATE/`**: bug report + feature request + `config.yml`
- **`.github/PULL_REQUEST_TEMPLATE.md`**: summary, test plan, screenshots section

### Phase 5: README Rewrite

Rewrite README to this structure. **Title centered, with table of contents.**

```
<div align="center">
  <h1>[Project Name]</h1>
  <p>One-line tagline — what the project does in 5 seconds</p>

  [![License](...)](LICENSE)
  [![Platform](...)](...)
  [![Stars](...)](...)
</div>

---

## 📋 Table of Contents
- [Features](#features)
- [Quick Start](#quick-start)
- [Installation](#installation)
- [Usage](#usage)
- [API Reference](#api-reference)
- [Contributing](#contributing)
- [License](#license)

---

(Description paragraphs — start with WHY, then WHAT. No heading.)

## ✨ Features
* **Feature 1:** description
* **Feature 2:** description

## 🚀 Quick Start
```bash
# Every command must include its interpreter — no guessing required
python script.py input.txt
bash setup.sh
powershell -Command "..."
```

## 📦 Installation
## 📖 Usage
## 🔧 API Reference
## 🤝 Contributing
## 📄 License
```

**TOC rules**:
- Auto-generate from `##` headings in the README
- Use anchor links: `[Features](#features)`, `[Quick Start](#quick-start)`
- Emoji prefix per section for visual scanning (optional, skip if the user dislikes emojis)

### Phase 6: Bilingual Setup (Chinese projects)

If the project is Chinese or the user wants bilingual docs:

```
project/
├── README.md          # English
├── SKILL.md           # English (if applicable)
├── LICENSE
└── zh-CN/
    ├── README.md      # 简体中文
    └── SKILL.md       # 简体中文 (if applicable)
```

Both README files get `**Language:** [English](../README.md) | [简体中文](README.md)` at the top.

Translate content, don't just copy — the Chinese version should read naturally, not like machine translation.

### Phase 7: Ship It

1. `git init` if not already a repo
2. `git add` all files (exclude secrets, `.env`, binaries)
3. Commit with conventional commit format:

```
type(scope): subject

feat(readme): add installation guide
fix: resolve table alignment in API docs
docs: add CONTRIBUTING.md
```

**Conventional commit types**: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`
**Subject**: ≤72 chars (English), concise (Chinese OK but keep tight)

4. `gh repo create` if remote doesn't exist (public, with description from README tagline)
5. `git push`
6. If this is a release: `git tag v1.0.0` with semantic versioning, push tags
7. Output the final GitHub URL

---

## Summary Format

After completion:

| Phase | Status | Details |
| :--- | :--- | :--- |
| Root Audit | ✓ | .gitignore created, node_modules/ excluded |
| Structure | ⚠ | Renamed `My Script.sh` → `scripts/my-script.sh` |
| Doc Fixes | 6 fixed | 3 tables aligned, 2 code blocks tagged, 1 link fixed |
| Generate | 5 files | LICENSE, .gitignore, CONTRIBUTING.md, Issue/PR templates |
| README | Rewritten | Centered title, TOC, 8 sections |
| Bilingual | Created | zh-CN/READIME.md + zh-CN/SKILL.md |
| Ship | Pushed | https://github.com/... |

---

## Read references/ for Templates

- `references/readme-template.md` — Full README template
- `references/issue-template.md` — Issue template
- `references/pr-template.md` — PR template
- `references/contributing-template.md` — Contributing guide template
