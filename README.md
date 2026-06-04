<div align="center">
  <h1>GitHub Format Standards</h1>
  <p>A <a href="https://claude.ai/code">Claude Code</a> skill — one command to audit, fix, and ship any project to GitHub.</p>

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

Or install via the [Claude Code plugin marketplace](https://claude.ai/code).

## Usage

In [Claude Code](https://claude.ai/code):

| You say | Triggers |
| :--- | :--- |
| `/GitHub格式规范` | Direct invocation |
| "Share this to GitHub" | Full pipeline |
| "Check my formatting" | Audit + fix only |
| "Create Issue and PR templates" | Generate only |

## The 7-Phase Pipeline

### 1. Root Directory Audit
- Red-flags large files, temp files, build artifacts, [`.env` secrets](https://github.com/github/gitignore), IDE cruft
- Generates `.gitignore` with language-appropriate rules — see [gitignore.io](https://www.toptal.com/developers/gitignore) for reference

### 2. File Naming & Structure
- Enforces lowercase-with-hyphens naming per [Google's file naming conventions](https://google.github.io/styleguide/)
- Moves files into `src/`, `tests/`, `scripts/`, `examples/`, `docs/`

### 3. Document Fixes
- Heading hierarchy, [code block language tags](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks), table alignment
- Chinese/English spacing ([W3C CLReq](https://www.w3.org/TR/clreq/)), proper noun capitalization
- Image paths ([relative or CDN only](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#images))

### 4. Generate Missing Files
- [`LICENSE`](https://choosealicense.com/) (MIT by default), `.gitignore`, [`CONTRIBUTING.md`](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/setting-guidelines-for-repository-contributors), [`SECURITY.md`](https://docs.github.com/en/code-security/getting-started/adding-a-security-policy-to-your-repository)
- [`.github/ISSUE_TEMPLATE/`](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository) + [`.github/PULL_REQUEST_TEMPLATE.md`](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository)

### 5. README Rewrite
- Centered title + badges (modeled after [FastAPI](https://github.com/fastapi/fastapi), [React](https://github.com/facebook/react), [Next.js](https://github.com/vercel/next.js))
- Auto-generated [table of contents with anchor links](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#section-links)
- Structure: Features → Quick Start → Install → Usage → API → Contributing → License

### 6. Bilingual Setup
- Root: English, `zh-CN/`: Chinese — same structure as [this project](https://github.com/20kiki/causal-explanation-protocol)
- Natural translation, not machine translation

### 7. Ship
- [Conventional Commits](https://www.conventionalcommits.org/) (`feat:`, `fix:`, `docs:`)
- [Semantic Versioning](https://semver.org/) tags (`v1.0.0`)
- Creates GitHub repo, pushes, outputs URL

## See Also

- [github-format-demo](https://github.com/20kiki/github-format-demo) — demo of the formatted output
- [causal-explanation-protocol](https://github.com/20kiki/causal-explanation-protocol) — real project using this skill's conventions

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
