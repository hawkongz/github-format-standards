---
name: github-format-standards
description: "Use when the user wants to share a project to GitHub. Runs a full pipeline: root audit, file naming and structure, document fixes (headings, code-block language tags, table alignment, explicit command interpreters), generate missing files (LICENSE, .gitignore, CONTRIBUTING.md, Issue/PR templates), README rewrite (centered title, TOC), bilingual setup, git init, conventional commit, gh repo create, push, semantic tag. Triggers on: 'share to GitHub', '/GitHub格式规范', '上传到 GitHub', '发布到 GitHub', '推到 GitHub', '发到 GitHub', '上传GitHub', '发布GitHub'."
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
- [ ] No vague/informal expressions: replace "你懂的", "you know the drill", "just works" with precise instructions. Use clean `macOS / Linux:` format for platform labels, never "you already know 😄"

### Phase 4: Generate Missing Files

- **`LICENSE`** (required): default to MIT if the user doesn't specify
- **`.gitignore`** (required): generate based on project language
- **`CONTRIBUTING.md`** (recommended): for any project with >1 file
- **`SECURITY.md`** (recommended): responsible disclosure instructions
- **`.github/ISSUE_TEMPLATE/`**: bug report + feature request + `config.yml`
- **`.github/PULL_REQUEST_TEMPLATE.md`**: summary, test plan, screenshots section

### Phase 5: README Rewrite

Rewrite README to this structure. **Title centered, with table of contents.**

#### Badge Color Standard (required)

Every badge uses an explicit shields.io color. If the project has no standard color, default to `lightgrey`. Never leave color unset — shields.io defaults to `green`, which reads as "passing/healthy" and is misleading for non-status badges.

| Badge | Color | Example |
| :--- | :--- | :--- |
| License (MIT) | `yellow` | `[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)` |
| License (Apache 2.0) | `blue` | `[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)` |
| License (GPL v3) | `blue` | `[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)` |
| Platform: Claude Code | `blue` | `[![Platform](https://img.shields.io/badge/Platform-Claude%20Code-blue)](https://code.claude.com)` |
| Platform: Python | `3776AB` | `[![Python](https://img.shields.io/badge/Python-3776AB)](https://python.org)` |
| Platform: Node.js | `339933` | `[![Node.js](https://img.shields.io/badge/Node.js-339933)](https://nodejs.org)` |
| Platform: Shell/Bash | `4EAA25` | `[![Shell](https://img.shields.io/badge/Shell-4EAA25)]()` |
| GitHub Stars | social | `[![Stars](https://img.shields.io/github/stars/owner/repo)](https://github.com/owner/repo)` |

**Badge rules (read before placing any badge):**
1. **3 badges minimum** every README: License, Platform, Stars
2. License badge links to the repo's `LICENSE` file
3. Platform badge links to the platform's official site (omit link if no canonical URL)
4. Stars badge is a shields.io GitHub social badge — no explicit color, auto-styled
5. Badges sit immediately below the tagline in the centered header `<div>`
6. Do NOT use custom/arbitrary colors. Pick from the table above. Unlisted platforms default to `lightgrey`.
7. Never skip the color segment. `...badge/Platform-Claude%20Code` (no color) → `green` — broken semantics.

```
<div align="center">
  <h1>[Project Name]</h1>
  <p>One-line tagline</p>

  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
  [![Platform](https://img.shields.io/badge/Platform-Claude%20Code-blue)](https://code.claude.com)
  [![Stars](https://img.shields.io/github/stars/owner/repo)](https://github.com/owner/repo)
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

> **Beginner-friendly format required.** Every Quick Start must answer: where to run commands, what to paste, and "is it done?".

**Template:**
```
> **What you need:** [prerequisites — e.g. "python 3.8+"]

**Step 1 — Open terminal**
- macOS / Linux: Open Terminal
- Windows: Win + R, type `powershell`, Enter

**Step 2 — Download only the files the skill needs**

[State which files and why: e.g. "The skill is a single SKILL.md" or "needs SKILL.md + eyes.py"]

macOS / Linux:
`mkdir -p ... && curl -o ... raw.githubusercontent.com/...`

Windows (PowerShell):
`New-Item ... && Invoke-WebRequest ...`

**Step 3 — Done.** [How to verify, how to trigger the skill]

> To update: re-run the same commands.
```

**Rules:**
- **Download only what the skill needs to function.** Never `git clone` the whole repo — README, LICENSE, zh-CN/ are for GitHub readers, not for the skill. A pure SKILL.md skill needs 1 file; a skill with scripts needs only those scripts + SKILL.md.
- Provide both Unix (`curl`) and Windows (`Invoke-WebRequest`) commands. The reader should never need to install `git` just to get a skill.
- No vague hand-waving. Tell the reader exactly what files they're getting and why.
- If the skill has extra deps (pip packages, API keys), list them as numbered steps before "Done"
- End with a clear confirmation: what indicates success, how to trigger the skill

## 📦 Installation
## 📖 Usage
## 🔧 API Reference
## 🤝 Contributing
## 📄 License
```

**Topics section** (add before Contributing):
- Required: a `## Topics` section with clickable GitHub topic links
- Format: `[`tag-name`](https://github.com/topics/tag-name)` — each tag links to GitHub's topic discovery page
- Include 5-8 relevant topics that describe the project's language, platform, and domain
- Add `[Topics](#topics)` to the TOC

**TOC rules**:
- Auto-generate from `##` headings in the README
- Use anchor links: `[Features](#features)`, `[Quick Start](#quick-start)`
- **Critical — emoji in headings breaks anchors:** GitHub strips emoji from heading IDs and prepends `-`. `## 🔍 The Problem` → `#-the-problem` (NOT `#the-problem`). Always verify TOC anchors match actual heading IDs.
- **No dead TOC links:** Every TOC entry must have a corresponding `##` heading in the document. Remove any TOC entry that lacks its target heading.
- **Every `##` heading emoji must be unique across the document.** No two sections may share the same emoji — duplicate emojis cause anchor ambiguity and degrade visual scanning. Audit all headings before finalizing.
- **Emoji set reference (pick from these, no repeats):** `📋` commands/list, `⌨️` keyboard/shortcuts, `💬` conversation/chat, `🔧` config/setup, `🚀` quickstart/workflow, `📦` installation/packaging, `🧠` strategy/thinking, `📚` resources, `✨` features, `📌` topics/tags, `🤝` contributing, `📄` license, `🔍` problem/investigation, `📖` usage/guide
- Emoji prefix per section for visual scanning (optional, skip if the user dislikes emojis)
- **After writing README, verify at least 2 random TOC links:** use WebFetch on the raw GitHub README to confirm the rendered heading IDs match the TOC anchors

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
