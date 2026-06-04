<div align="center">
  <h1>GitHub Format Standards</h1>
  <p>A Claude Code skill — one command to audit, fix, and ship any project to GitHub.</p>

  [![GitHub stars](https://img.shields.io/github/stars/20kiki/github-format-standards?style=social)](https://github.com/20kiki/github-format-standards/stargazers)
  [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
  [![Platform: Claude Code](https://img.shields.io/badge/Platform-Claude%20Code-orange)](https://claude.ai/code)
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
| 3. Doc Fixes | Aligns tables, tags code blocks, fixes Chinese/English spacing, corrects proper nouns |
| 4. Generate | Creates `LICENSE`, `CONTRIBUTING.md`, `SECURITY.md`, Issue/PR templates |
| 5. README | Rewrites README with centered title, TOC, and top-project structure |
| 6. Bilingual | Sets up `zh-CN/` with full Chinese translation if needed |
| 7. Ship | `git init` → commit (conventional format) → `gh repo create` → push → tag |

## Installation

```bash
git clone https://github.com/20kiki/github-format-standards.git \
  ~/.claude/skills/github-format-standards
```

## Usage

In Claude Code:

| You say | Triggers |
| :--- | :--- |
| `/GitHub格式规范` | Direct invocation |
| "Share this to GitHub" | Full pipeline |
| "Check my formatting" | Audit + fix only |
| "Create Issue and PR templates" | Generate only |

## The 7-Phase Pipeline

### 1. Root Directory Audit
- Red-flags large files, temp files, build artifacts, `.env`, IDE cruft
- Generates `.gitignore` with language-appropriate rules

### 2. File Naming & Structure
- Enforces lowercase-with-hyphens naming
- Moves files into `src/`, `tests/`, `scripts/`, `examples/`, `docs/`

### 3. Document Fixes
- Heading hierarchy, code block language tags, table alignment
- Chinese/English spacing, proper noun capitalization
- Image paths (relative or CDN only)

### 4. Generate Missing Files
- `LICENSE` (MIT by default), `.gitignore`, `CONTRIBUTING.md`, `SECURITY.md`
- `.github/ISSUE_TEMPLATE/` + `.github/PULL_REQUEST_TEMPLATE.md`

### 5. README Rewrite
- Centered title + badges, auto-generated TOC
- Structure: Features → Quick Start → Install → Usage → API → Contributing → License

### 6. Bilingual Setup
- Root: English, `zh-CN/`: Chinese
- Natural translation, not machine translation

### 7. Ship
- Conventional commits (`feat:`, `fix:`, `docs:`)
- Semantic versioning tags (`v1.0.0`)
- Creates GitHub repo, pushes, outputs URL

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
