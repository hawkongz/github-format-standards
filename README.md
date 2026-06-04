<div align="center">
  <h1>GitHub Format Standards</h1>
  <p>A Claude Code skill that automatically formats project docs per GitHub best practices.</p>
</div>

**Language:** [English](README.md) | [简体中文](zh-CN/README.md)

[![GitHub stars](https://img.shields.io/github/stars/20kiki/github-format-standards?style=social)](https://github.com/20kiki/github-format-standards/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Platform: Claude Code](https://img.shields.io/badge/Platform-Claude%20Code-orange)](https://claude.ai/code)

**Inspect first, then correct. Audit item by item, enforce consistency.**

---

## What It Does

Tired of manually fixing formatting every time you share a project on GitHub? This skill handles it:

* **Markdown standards**: heading hierarchy, code block language tags, table alignment, consistent list indentation
* **README structure**: reorganize per patterns from React / FastAPI / TensorFlow and other top projects
* **Template generation**: Issue templates, PR templates, CONTRIBUTING.md, SECURITY.md
* **Chinese-specific rules**: spacing between Chinese/English, proper noun capitalization, punctuation matching

## Installation

```bash
# Clone into Claude Code skills directory
git clone https://github.com/20kiki/github-format-standards.git \
  ~/.claude/skills/github-format-standards
```

Or place `SKILL.md` in any directory recognized by Claude Code as a skill.

## Usage

In Claude Code:

- `/GitHub格式规范` — direct invocation
- "Check my formatting" — auto-trigger
- "Polish the README before publishing to GitHub" — auto-trigger
- "Create Issue and PR templates" — auto-trigger

## Workflow

1. Scan all `.md` files and `.github/` directory
2. Check each file against the rules, fix issues immediately
3. Output a change summary with the reason for each fix

## Rules Covered

| Category | Details |
| :--- | :--- |
| Markdown basics | No heading level skipping, language-tagged code blocks, aligned tables, described links, alt text on images, consistent list indentation |
| README structure | Title+tagline→Badges→Description→Features→Quick Start→Install→API→Config→Contributing→License |
| Community files | ISSUE_TEMPLATE, PULL_REQUEST_TEMPLATE, CONTRIBUTING.md, SECURITY.md |
| Chinese specifics | Spacing between Chinese/English, proper noun capitalization, Chinese punctuation for Chinese paragraphs |

## Rules Derived From Real Projects

Formatting rules are based on analysis of actual top repositories:

* **List marker `*`**: used by React, TensorFlow, FastAPI
* **Feature list style**: `* **Keyword:** description` pattern from React
* **Centered title + badges**: from FastAPI / Next.js / TensorFlow
* **`<details>` collapsible sections**: from FastAPI docs
* **Project structure tree**: from most mature projects

## File Structure

```
├── SKILL.md                              # Skill main file (English)
├── README.md                             # This file (English)
├── LICENSE                               # MIT
└── zh-CN/
    ├── README.md                         # 中文说明
    └── SKILL.md                          # 中文 Skill 文件
```

## License

MIT
