<div align="center">
  <h1>GitHub Format Standards</h1>
  <p>A Claude Code skill — one command to audit, fix, and ship any project to GitHub.</p>

  <a href="https://github.com/20kiki/github-format-standards/stargazers"><img alt="GitHub stars" src="https://img.shields.io/github/stars/20kiki/github-format-standards?style=social"></a>
  <a href="LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-blue.svg"></a>
  <a href="https://claude.ai/code"><img alt="Platform: Claude Code" src="https://img.shields.io/badge/Platform-Claude%20Code-orange"></a>
</div>

**Language:** [English](README.md) | [简体中文](zh-CN/README.md)

---

## 📋 Table of Contents
- [What It Does](#what-it-does)
- [Installation](#installation)
- [Usage](#usage)
- [The 7-Phase Pipeline](#the-7-phase-pipeline)
- [File Structure](#file-structure)
- [License](#license)

---

## What It Does

Say "share to GitHub" and this skill handles everything:

| Phase | What Happens |
| :--- | :--- |
| 1. Root Audit | Scans for large files, secrets, build artifacts; generates `.gitignore` |
| 2. Structure | Fixes file names (lowercase, no spaces), moves files into `src/` `tests/` etc. |
| 3. Doc Fixes | Aligns tables, tags code blocks, fixes Chinese/English spacing, proper nouns |
| 4. Generate | Creates `LICENSE`, `CONTRIBUTING.md`, `SECURITY.md`, Issue/PR templates |
| 5. README | Rewrites README with centered title, TOC, and top-project structure |
| 6. Bilingual | Sets up `zh-CN/` with full Chinese translation if needed |
| 7. Ship | `git init` → conventional commit → `gh repo create` → push → semantic tag |

## Installation

```bash
git clone https://github.com/20kiki/github-format-standards.git \
  ~/.claude/skills/github-format-standards
```

## Usage

Say `/GitHub格式规范` or "Share this to GitHub" — the full 7-phase pipeline runs.

## The 7-Phase Pipeline

### 1. Root Directory Audit
Red-flags large files (>1MB), temp files, build artifacts, `.env` secrets, IDE cruft. Generates `.gitignore` covering `node_modules/`, `__pycache__/`, `*.pyc`, `.env`, `.DS_Store`, `dist/`, `build/`, IDE directories.

### 2. File Naming & Structure
Enforces lowercase-with-hyphens. Moves source → `src/`, tests → `tests/`, scripts → `scripts/`, examples → `examples/`, docs → `docs/`. Skips restructuring for single-file projects.

### 3. Document Fixes
Heading hierarchy, code block language tags, table alignment. Chinese/English spacing, proper noun capitalization (`GitHub` not `github`). Image paths: relative or CDN only.

### 4. Generate Missing Files
`LICENSE` (MIT by default), `.gitignore`, `CONTRIBUTING.md`, `SECURITY.md`, `.github/ISSUE_TEMPLATE/` (bug report + feature request + config), `.github/PULL_REQUEST_TEMPLATE.md`.

### 5. README Rewrite
Centered title + badges, auto-generated TOC from `##` headings. Structure: Features → Quick Start → Install → Usage → API → Contributing → License.

### 6. Bilingual Setup
Root: English, `zh-CN/`: Chinese. Both have `**Language:**` row linking to each other. Natural translation, not machine style.

### 7. Ship
`git init` → `git add` → commit with conventional format (`feat:`, `fix:`, `docs:`) → `gh repo create` → `git push` → semantic version tag (`v1.0.0`) if releasing.

## File Structure

```
├── SKILL.md                              # Skill (English)
├── README.md                             # This file (English)
├── LICENSE                               # MIT
├── references/
│   ├── readme-template.md
│   ├── issue-template.md
│   ├── pr-template.md
│   └── contributing-template.md
└── zh-CN/
    ├── README.md                         # 简体中文
    └── SKILL.md                          # 简体中文 Skill
```

## License

MIT
